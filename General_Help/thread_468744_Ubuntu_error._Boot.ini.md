---
title: "Ubuntu error. Boot.ini"
date: 2007-06-09
forum: General Help
---

### Post by arvin2212 on 2007-06-09
Guys i've tried installing ubuntu but had an error later on and then when i restarted my computer i get this error, operating system cannot be loaded. Well previously i had 2 partition of windows in my computer and i installed ubuntu on the 2nd partition. Now when i restart my pc, i dont get the select which operating system menu but i get the error stated above. I thought my files on the windows partition are all gone , but i tried inserting the ubuntu live disk and saw that all my windows files on the other partiton(which is not the ubuntu partition) and my windows files are all still there. Then i saw my boot.ini file and it goes like this

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /noexecute=optin

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP(Arvin) Home Edition"

c:\grldr="Ubuntu"


So i need to remove this part right --> " c:\grldr="Ubuntu" " ? but i couldnt do so. whenever i tried chaging it, i get a permission error that goes like this, "Could not save the file /media/Local Disk/boot.ini. " "You are trying to save the file on a read-only disk. Please check that you typed the location correctly and try again." . I've tried google-ing the problem but no solution worked..so guys , i hope some of u would be able to help me...

---

### Post by arvin2212 on 2007-06-09
BUMP:popcorn::popcorn::popcorn:

---

### Post by hikaricore on 2007-06-09
How exactly did you install ubuntu?  Was it from a live cd?  Or was it one of the windows based installers?

I've never known a livecd to modify the boot.ini file.

Also you might want to mention what version you installed so we all know what we're dealing with.  ^_^

---

### Post by arvin2212 on 2007-06-09
Hmm its from the live CD.  Version 7.04. :D i really hope this matter can be solved cause i have critical data in my other windows partition..

The cd's are sent to me by Ubuntu. :D .

---

### Post by arvin2212 on 2007-06-09
help please..........

---

