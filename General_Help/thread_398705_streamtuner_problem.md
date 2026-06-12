---
title: "streamtuner problem"
date: 2007-04-01
forum: General Help
---

### Post by zx50 on 2007-04-01
when i try to tune in with stream tuner i get an error posted in my attachment. anyone know why and how to fix it?

---

### Post by alien21010 on 2007-04-01
Well its because Xmms is not installed on your machine.  You can either install xmms (a media player) or install one of your choice.  Basically all you need to do is go to the preferences, find where it asks you to select a music player, and then alter the command to use the music player that you have installed.  To do that, just replace the word xmms with whatever you would normally use.

---

### Post by zx50 on 2007-04-01
i done the last part of your advise and it works now.  thanks.

---

### Post by airtonix on 2007-04-14
and his next problem like me will be  that xmms doesnt provide command line interface to load a url...only a file.

so when you tell it to > $ xmms -q [http://radio.internode.on.net:8080](http://radio.internode.on.net:8080)it will happily open up xmms then see that a file called [http://radio.internode.on.net:8080](http://radio.internode.on.net:8080) does not exist in the current working directoy of xmss(your home folder), adnd throw up a file selection box so you can choose a file.

i thought of doing this : 

> echo %q > ~/streamtuner.m3u; xmms -q ~/streamtuner.m3ubut the same thing happened. it couldn't find the file. or i suspect the file wasnt even created.

so maybe my syntax is not right but that there above should print the URI into a file calle streamtuner.m3u and then load xmms with the view to load the previously created file.

well get back on this.

---

