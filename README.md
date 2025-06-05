# Envío de Comandos MQTT desde un sitio web utilizando Flask

## Templete enviar-comando
Se agrega un nuevo template a los existentes. En él se muestra un formulario que permite seleccionar el sensor de destino (obtenido desde la base de datos) y los comandos setpoint y destello. Para el primer comando, se muestra un selector numérico para elegir la temperatura, y para el segundo comando, se muestra un texto indicando que solamente hay que presionar el botón de enviar.
A esta ruta se ingresa con los métodos *GET* (solamente muestra el formulario) y *POST* (donde se envía el formulario).
## Publicación por MQTT
Luego de recibir los datos mediante el método POST se llama a una función que publica por MQTT el valor en el topico "*id_sensor*"/"*comando*", esto se ejecuta dentro de un try-except que dependiendo del resultado crea un "[Flashing With Categories](https://flask.palletsprojects.com/en/stable/patterns/flashing/)" con la categoría "*success*" si se envía correctame y "*error*" en el caso contrario. La publicación se realiza de manera asíncrona pero esto no es necesario debido a que es una tarea bloqueante.
## Modificaciones de Navegación
Se agrega el botón "*Enviar*" en el nav para ir a la pagina que permite publicar y se agrega la opción "*HOME*" para volver a la pagina inicial donde se muestran los contactos, y las opciones de crear, editar y eliminar los mismos.

