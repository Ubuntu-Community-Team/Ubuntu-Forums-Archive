---
title: "problema con rarcrack (este archivo no existe)/rarcrack problem (this file does not.."
date: 2013-10-24
forum: General Help
---

### Post by Spiritualite on 2013-10-24
hola este es mi primer post en este maravilloso foro que tanto me ayudo, ahora es mi turno de ayudar...

bueno, el problema comenzo cuando baje un archivo zip de un soft con contraseña que el genio que colgo el archivo olvido, entonces despues de preguntar y googlear un poco recuri a rarcrack....

entonces cuando lo instale siguiendo este tuto:

[http://linuxzone.es/rarcrack-recupera-las-contrasenas-de-archivos-comprimidos/](http://linuxzone.es/rarcrack-recupera-las-contrasenas-de-archivos-comprimidos/)

lo ejecute con el comando normal... primer error

sudo rarcrack archivox.zip

luego me di cuenta de la novatada que habia hecho y busque un poco de sintazix de este programa y me di cuenta que era asi:

sudo rarcrack /home/tuusuario/tucarpeta/tuarchivo.zip --type zip (aqui en rojo es donde  se debe poner la extension del archivo si es zip o rar o tbz o lo que sea y demas esta decir que tu usuario tu carperta y tu archivo son nombres que se encuentran en tu propio sistema)

bueno hasta aqui si no has tenido problema tal vez te pase lo que a mi
me salia el error:

ERROR: The specified file (<filename>) is not exists or 
you don't have a right permissions!


luego encontre esta pagina 

[http://sourceforge.net/p/rarcrack/bugs/9/](http://sourceforge.net/p/rarcrack/bugs/9/)

donde dice que el error se encuentra en los archivos rarcrack.c y rarcrack.h que se encuentran en la carpeta del programa que descargaste y que debes copiar y compilar y la verdad yo de programacion no se ni un pepino asi que abri los archivos con gedit y pegue el texto como indica en el link anterior y reinstale como si no tubiera el programa luego volvi a intentar 


sudo rarcrack /home/uario/carpeta/archivox.zip --type zip

y me funciono pero la contraseña que salia no era para nada entonces se me prendio el foquito....
el programa se supone que debe trabajar igual con rar que con zip pero en mi busqueda vi mas resultados en los rar que en los zip asi que:
copie mi archivo y lo pegue en la misma carpeta luego renombre mi archivo como rar ejecute el comando y listo FUNCIONO, claro que aun sigue buscando la clave pero esta corriendo cuando obtenga los resultados volvere apostear... gracias por leer y no aburrirse.

---

### Post by Elfy on 2013-10-24
This is an English forum, please either post in English or you can visit other local language speaking resources.

[http://loco.ubuntu.com/teams/](http://loco.ubuntu.com/teams/)

closed

---

