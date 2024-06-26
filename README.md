<img  src=https://flask.palletsprojects.com/en/3.0.x/_images/flask-horizontal.png align="center" border="1" >

[Flask](https://flask.palletsprojects.com/en/3.0.x/) es un FrameWork liviano para Python; muy útil para desarrollar rápidamente aplicaciones web; proporciona los conceptos básicos para el enrutamiento de URL y la representación de páginas.

Con Flask es posible crear una aplicación simple de tres o más páginas que utilicen una plantilla base común [1]. A lo largo del camino, experimentando una serie de características de Visual Studio Code [2]; como el uso de la terminal, el editor, el depurador, fragmentos de código y más.

## Extensiones de Flask

[Flask](https://flask.palletsprojects.com/en/3.0.x/) se denomina marco "micro" porque no proporciona directamente funciones como validación de formularios, abstracción de bases de datos, autenticación, etc. En cambio, estas características las proporcionan paquetes especiales de Python llamados extensiones Flask. Las extensiones se integran perfectamente con Flask para que parezcan parte del propio Flask. Por ejemplo, Flask no proporciona un motor de plantillas de páginas, pero la instalación de Flask incluye el motor de plantillas Jinja de forma predeterminada. Por conveniencia, normalmente hablamos de estos valores predeterminados como parte de Flask.

## Cómo usar Flask en Linux (por ejemplo *Ubuntu*)
* Cree un entorno virtual para ejecutar aplicaciones Python (ver notas)
    * python -m venv venv
* Active el entorno virtual "venv"; puede usar el nombre de su preferencia en vez de "venv".
    *  source ./venv/Scripts/activate
* Instale Flask en el entorno virtual
    * python -m pip install flask

Ahora se tiene un ambiente autónomo listo para escribir código Flask. 

   Revise el: [Tutorial de para usar Flask en Visual Code](https://code.visualstudio.com/docs/python/tutorial-flask)

## Flask en Godaddy
 [cPanel](https://www.godaddy.com/es/help/consultar-el-panel-de-control-para-mi-cuenta-de-hosting-de-linux-8884) es una plataforma que permite administrar sitios web que se encuentran dentro de un hosting.  [Godaddy](https://www.godaddy.com) usa esta herramienta para facilitar las aplicaciones instaladas. En el caso de una aplicación Python, cPanel tiene una utilidad llamada: **"Setup Python App"**; que presenta algunos campos para configurar.
 
 * Application root
    *  Es la dirección física de la aplicación en un servidor que se corresponde con su URI. Aca se cargan los archivos correspondientes a la página web que esta desarrollando. Todo lo referido a Flask. Godaddy crea un entorno virtual para instalar la aplicación, ejemp. source /home/xxxx/virtualenv/public_html/xyz.com /home/iu4gg8fd7roq/virtualenv/public_html/cenitlab.com/BC_flask. Pero solo es necesario declarar en el campo, a continuación del nombre de dominio seleccionado, el nombre del directorio que se requiera en el entorno virtual. Ejemp. para el dominio xyz.com, so se pone nada en el campo y entonces la aplicación se ejecuta en la raiz del dominio.
 * Application URL
    * URL de la aplicación. Un enlace HTTP/HTTPS a la aplicación.
 * Application startup file
    * Archivo de inicio de la aplicación. Normalmente el archivo, que Godaddy pone automáticamente: *passenger_wsgi.py*
 * Application Entry point
    * Punto de entrada de la aplicación. Configure el objeto invocable wsgi para su aplicación. Esto si se deja en blanco, es rellenado por godaddy con: *application*
 * Passenger log file
    * Archivo de registro de eventos. No es necesario completar; ver documentación si se require. Nota: Puede definir la ruta junto con el nombre del archivo (por ejemplo, /home/iu4gg8fd7roq/logs/passenger.log).
    * Inicialmente Godaddy crea el archivo *passenger.log* con algún contenido, el cual debe de borrarse y sustituir -unicamente- por: `from hello_app.views_test import app as application`. Donde *hello_app* es el directorio donde se encuentra el archivo python principal de la aplicacion *views_test.py*. Este archivo se puede actualizar, si se hace una actualización o se clona la aplicación desde GitHub.
 * Configuration files
    * Archivo de configuración para los requerimientos de la aplicación. Normalmente: *requirements.txt*. Una vez adicionado se debe de bajar la pestaña que dice "Run pip Install" para que se instale el contenido descrito por el archivo en el entorno. El contenido de este archivo también se puede instalar o verificar manualmente desde la cónsola.
        * Primero entrando al entorno virtual (con el comando proporcionado por la misma herramienta *Setup Python App* al inicio de la ventana).
        * Ejecutando el instalador *pip* para el contenido del archivo *requirements.txt*: `pip install check-requirements-txt`
 * Execute python script
    * Comando para ejecutar (por ejemplo, /path/to/manage.py migrar). 
 * Environment variables
    * Variables de entornos. Muy útiles para proteger data sensible.
  
  
#### Notas: 
* Se debe de instalar "Flask" desde el entorno virtual activado, usando la cónsola: `python -m pip install flask`. Pero primero se debe de crear la "WEB APPLICATIONS", para que se cree el entorno virtual y luego trabajar en él.
* Cada vez que se crea una "WEB APPLICATIONS" usando la utilidad "Setup Python App", se crea o actualiza el archivo *passenger.log*; por lo tanto es recomendable revisar para corregir cualquier cambio.
* Se puede crear el entorno virtual manualmente y comenzar a trabajar a partir de eso (en este caso instalado en cgi-bin; pero puede ser donde prefiera):

   * Instale en python la librería para entorno virtual; en Godaddy ya está instalada por defecto.
      * $ python3 -m pip install virtualenv
   * *Navegue al directorio *CGI-BIN*, que debe de estar debajo de *public_html**
      * $ cd $home
      * $ cd public_html/cgi-bin
   * Cree el entorno virtual *venv*, puede ser el nombre de su preferencia.
      * $ virtualenv venv
   * Active en entorno virtual
      * $ source venv/bin/activate
      * $ pip install Flask
      * $ deactivate

Rommel Contreras (abril de 2024)

[1]: https://github.com/microsoft/python-sample-vscode-flask-tutorial "El proyecto de código completo de un tutorial de Flask se puede encontrar en GitHub: python-sample-vscode-flask-tutorial"

[2]: https://code.visualstudio.com/docs/python/tutorial-flask "Código de Visual Estudio"

### Referencias:
* [Get your Flask Python app live on Cpanel](https://medium.datadriveninvestor.com/installing-python-3-10-and-flask-on-godaddy-updated-ebe764ab78a7)
* [Setting Up a Simple Flask App on GoDaddy](https://github.com/nicholasvad/flask_on_godaddy)
* [Setting GoDaddy hosted site to use Python3/Flask](https://benincampus.blogspot.com/2020/09/setting-godaddy-hosted-site-to-use.html)
* [How to install and configure Python on a hosted server](https://www.godaddy.com/resources/skills/how-to-install-and-configure-python-on-a-hosted-server)

