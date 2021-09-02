# Delilah-Rest-

Inicio, Estas instrucciones le permitirán obtener una copia del proyecto que se ejecuta en su máquina local para fines de desarrollo y pruebas. Siga las siguientes instrucciones para saber cómo desplegar el proyecto. Requisitos previos Instalar y configurar los siguientes programas que serán necesarios para el correcto funcionamiento de la aplicación
Disponer de un Editor de Texto, recomiendo el uso de VsCode. Instalar y configurar un motor de base de datos MYSQL. Instalar NodeJS en el sistema operativo. Instalar Postman que es una herramienta que nos ayudará a realizar consultas de prueba a nuestra API. Instalación A continuación encontrarás una serie de pasos que te indican lo que debes ejecutar para tener un entorno de desarrollo local funcionando Este paso es totalmente opcional ya que te proporciona una pequeña base de datos de prueba Desde tu monitor de base de datos, ejecuta el archivo database.sql ubicado dentro de la carpeta Back-End. Ahora, una vez abierto el proyecto desde tu editor de texto, abre la terminal de VsCode, asegúrate de estar en la ruta de la carpeta Back-End y ejecuta la siguiente línea de comando, con la que se instalarán todas las dependencias necesarias npm install Ya instaladas todas las dependencias para este proyecto; vamos a crear un archivo dentro de la misma carpeta Back-End llamado ".env" donde vamos a colocar la siguiente información

USER= aquí pon tu usuario de la base de datos

PASS= aquí pon tu contraseña de la base de datos

NAME_DB= delilah_resto

HOST= localhost

JWT_SECRET= aquí poner una palabra secreta

Desde el terminal, ejecute la siguiente línea de comandos npm start

delilahresto@1.0.0 start C:\Users\diazk\Documents\Projects\DelilahResto\DelilahResto\Back-End node index.js

Servidor iniciado... Ejecutando (por defecto): SELECT 1+1 AS result Ejecutando (por defecto): CREATE TABLE IF NOT EXISTS user (id INTEGER(10) NOT NULL auto_increment , firstname VARCHAR(50) NOT NULL, lastname VARCHAR(50) NOT NULL, phone VARCHAR(15) NOT NULL, address VARCHAR(100) NOT NULL, email VARCHAR(50) NOT NULL, profile VARCHAR(10) NOT NULL, password VARCHAR(255) NOT NULL, PRIMARY KEY (id)) ENGINE=InnoDB; Ejecutando (por defecto): CREATE TABLE IF NOT EXISTS requests (id INTEGER(10) NOT NULL auto_increment , status VARCHAR(50) NOT NULL, Payment_method VARCHAR(30) NOT NULL, createdAt DATETIME NOT NULL, updatedAt DATETIME NOT NULL, userId INTEGER(10), PRIMARY KEY (id), FOREIGN KEY (userId) REFERENCES user (id) ON DELETE SET NULL ON UPDATE CASCADE) ENGINE=InnoDB; La base de datos está conectada Ejecutando (por defecto): CREATE TABLE IF NOT EXISTS product (id INTEGER(10) NOT NULL auto_increment , name VARCHAR(50) NOT NULL, description VARCHAR(255) NOT NULL, type VARCHAR(20) NOT NULL, price VARCHAR(20) NOT NULL, image VARCHAR(255) NOT NULL, PRIMARY KEY (id)) ENGINE=InnoDB; Ejecutando (por defecto): CREATE TABLE IF NOT EXISTS order (quantity INTEGER(10) NOT NULL, createdAt DATETIME NOT NULL, updatedAt DATETIME NOT NULL, productId INTEGER(10) , requestId INTEGER(10) , PRIMARY KEY (productId, requestId), FOREIGN KEY (productId) REFERENCES product (id) ON DELETE CASCADE ON UPDATE CASCADE, FOREIGN KEY (requestId) REFERENCES requests (id) ON DELETE CASCADE ON UPDATE CASCADE) ENGINE=InnoDB; Ejecutando (por defecto): SHOW INDEX FROM requests Ejecutando (por defecto): SHOW INDEX FROM user Ejecutando (por defecto): SHOW INDEX FROM product Ejecutando (por defecto): SHOW INDEX FROM order En este punto tu aplicación debería ser totalmente funcional.

Ejecución de las pruebas Para saber más sobre la ejecución de pruebas, podrías consultar el archivo spec.yaml. También puedes encontrar un archivo llamado DelilahResto.postman_collection.json ubicado dentro de la carpeta Postman, que puedes importar a tu Postman para facilitar las pruebas de los diferentes EndPoints de nuestra API
