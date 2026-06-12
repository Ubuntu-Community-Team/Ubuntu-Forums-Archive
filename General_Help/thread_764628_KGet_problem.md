---
title: "KGet problem"
date: 2008-04-24
forum: General Help
---

### Post by Jawshie on 2008-04-24
Whenever I try to download files with KGet, it attempts to save it to the root directory (or at least I assume because of the error I get). I didn't change any settings before the problem started. Since it started I have tried two things: 
a)   sudo dpkg-reconfigure kget
which failed

b)   In Kget settings, I tried to set all file extensions (*) to download to /home/[user]/MyDownloads
which also does not work

What can I do?

Here is the error message I get:
"Access denied.
Could not write to /file.txt"

Does anybody have any suggestions?

---

### Post by thaednevol on 2009-07-29
Después de un tiempo sin usar Kget decidí utilizarlo nuevamente, pero surgió un problema. Resulta que al darle comenzar nueva descarga, mostraba el mensaje de error:

Acceso denegado

No se puede escribir en /"elarchivo.extension".part

Solution

At least, it was solved for me, I clcked in Settings -> Advanced -> Add new transfers as 

I chose Delayed, and besides, I chose  not to use last folder

And that's all, I hope it works

Solución

Bueno, por lo menos me funcionó a mi, Lo que hice fue ir a Configuración -> Avanzado -> Agregar nuevas transferencias como

Y escogí Atrasado

Además, deshabilité Modo Usar último directorio.... espero que funcione

---

