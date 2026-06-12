---
title: "Limewire installation"
date: 2005-04-04
forum: General Help
---

### Post by Patrick on 2005-04-04
Goodday folks :-P 

I installed LimeWire through this Howto [http://ubuntuguide.org/temp/#limewire](http://ubuntuguide.org/temp/#limewire)

But, when i do Applications , Internet . Limewire it says 

Details: Failed to execute child process "/opt/LimeWire/LimeWire" (No such file or directory)

( When i change the command to opt/LimeWire/runlime.sh nothing happens . )

So or i do something wrong or the howto is not good  :-k

---

### Post by Psquared on 2005-04-04
I couldn't get it to work either. In my case it was something to do with java, but I could never figure it out. Java worked with everything else. I just installed aMule instead and it works fine for me.

---

### Post by Patrick on 2005-04-05
[QUOTE=Psquared]I couldn't get it to work either. In my case it was something to do with java, but I could never figure it out. Java worked with everything else. I just installed aMule instead and it works fine for me.[/QUOTE]


Java is working because Azureus is working flawless. 

Anybody has some tips

---

### Post by bored2k on 2005-04-05
[QUOTE=Patrick]Java is working because Azureus is working flawless. 

Anybody has some tips[/QUOTE]
 Here is what i did to get limewire 4.8 pro to work:
created my own ubuntu java package, installed it, and created a script with
#!/bin/sh
cd ~/Limewire/ && sh runLime.sh

and made a launcher with it.
[http://ubuntuforums.org/showthread.php?t=22646&goto=lastpost](http://ubuntuforums.org/showthread.php?t=22646&goto=lastpost)

---

### Post by Patrick on 2005-04-05
[QUOTE=bored2k]Here is what i did to get limewire 4.8 pro to work:
created my own ubuntu java package, installed it, and created a script with
#!/bin/sh
cd ~/Limewire/ && sh runLime.sh

and made a launcher with it.
[http://ubuntuforums.org/showthread.php?t=22646&goto=lastpost](http://ubuntuforums.org/showthread.php?t=22646&goto=lastpost)[/QUOTE]

Dont think its the solution, because it cant find the folder ( look at the error message in the fisrt post ) 

Maybe anybody else an idea ?

---

### Post by bored2k on 2005-04-05
[QUOTE=Patrick]Dont think its the solution, because it cant find the folder ( look at the error message in the fisrt post ) 

Maybe anybody else an idea ?[/QUOTE]
 First of all there is no file by the name of /opt/LimeWire/LimeWire. There is Limewire.jar, Limewire.ico, Limewire.dll so, of course it is never running dude.

You either java -jar /opt/Limewire/Limewire.jar or sh runLime.sh. It simply cant open a file that doesnt exist.

---

### Post by jiyuu0 on 2005-04-05
sorry... i took the older version...

corrected... plz check
[http://ubuntuguide.org/temp/#limewire](http://ubuntuguide.org/temp/#limewire)

---

### Post by Patrick on 2005-04-05
[QUOTE=jiyuu0]sorry... i took the older version...

corrected... plz check
[http://ubuntuguide.org/temp/#limewire](http://ubuntuguide.org/temp/#limewire)[/QUOTE]

Roger

---

### Post by psyco on 2005-04-13
Hi, I have installed limewire and java, however when limewire runs, appears a window saying: "Limewire was unable to use the specified directory for saving files. Please try a different directory" but I have modified the access to the directory using chmod, however doesn't work, any idea?

---

### Post by psyco on 2005-04-13
I'm afraid that limewire is unable to locate the "html engine", It seems that doesn't find firefox

---

