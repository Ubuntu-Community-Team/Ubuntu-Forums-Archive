---
title: "general installing issues ._."
date: 2008-05-29
forum: General Help
---

### Post by tommytrying2linux on 2008-05-29
hey, i know theres already a few thread about these, but ive been having alot of trouble trying to install my drivers for my ATi card, it keeps telling me permission denied even when ive logged in sudo, and sudo su

> ******@*****-desktop:~/Desktop$ ./ati-driver-installer-8-5-x86.x86_64.run
-bash: ./ati-driver-installer-8-5-x86.x86_64.run: Permission denied


> root@*****-desktop:/home/******/Desktop# ./ati-driver-installer-8-5-x86.x86_64.run
bash: ./ati-driver-installer-8-5-x86.x86_64.run: Permission denied


any help would be appreciated, some person i met on IRC suggested that i use chmod, but i did not understand what he was talking about.. could using chmod solve my problem? :( :(

---

### Post by phidia on 2008-05-29
You shouldn't need to alter permissions on the ATI installer unless something odd has been done to your system and using sudo should give you permission anyway. 
What version of ubuntu are you using. I see from the output you supplied that you have a 64 bit version. That shouldn't cause a driver install problem though.
Have you read and tried the methods for [ATI driver install here]("http://ubuntuforums.org/showthread.php?t=515573")?

---

### Post by tommytrying2linux on 2008-05-29
thanks will look at it right away :)

-edit thanks worked, ending up using the envy program :P

---

