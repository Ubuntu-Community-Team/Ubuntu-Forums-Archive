---
title: "Script shell bash - Selecccion de fichero de un directorio"
date: 2016-01-12
forum: General Help
---

### Post by btomas2 on 2016-01-12
Hola a todo@s

Soy nueva en scripting y quisiera saber si me podríais ayudar a generar un script que recorra directorios en busca de ficheros .flv 
para su posterior tratamiento.

Imagino que tengo que usar un bucle for y el comando ls.


Muchas gracias de antemano.
Saludos.

---

### Post by kjohri on 2016-01-13
For example,

for i in *.flv
do
ls -l $i
done

---

### Post by slickymaster on 2016-01-13
Hi btomas2, welcome to the forums.

Please write your posts in English unless you are participating in a Loco Forum, where you are permitted to use another language if it is in common use in that Loco Forum and understood by the Loco Forum staff. We have many users from many different countries, and English is the common language of these forums.

---

