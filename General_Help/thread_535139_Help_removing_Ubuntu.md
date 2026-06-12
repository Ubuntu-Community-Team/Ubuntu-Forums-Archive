---
title: "Help removing Ubuntu"
date: 2007-08-26
forum: General Help
---

### Post by Gravite on 2007-08-26
I deleted the partition that contains ubuntu but when i restart my comp. It still shows that ubuntu is there. How can i remove it so that i only have 1 boot?

---

### Post by be4truth on 2007-08-26
What else than Ubuntu is installed on your computer?

---

### Post by mikaelsnavy on 2007-08-26
If it is windows, check out [http://ubuntuforums.org/showthread.php?t=508927&highlight=remove+ubuntu]("http://ubuntuforums.org/showthread.php?t=508927&highlight=remove+ubuntu")

---

### Post by Gravite on 2007-08-26
i was dual booting window vista and ubuntu but i wanna install PClinuxOS so i gotta remove Ubuntu

edit: btw i already deleted the partition but i am able to boot to window with no problem. The link above needs to correct his error and i don't even have a Ubuntu CD so i can't do anything right now

---

### Post by Dark Star on 2007-08-26
LMAO :p PCLOS is too bad for me :p btw just format the drive in which you have ubuntu ;)

---

### Post by Gravite on 2007-08-26
i did but everytime i restart computer theres always 2 os to select from which is Ubuntu and vista but i already deleted the ubuntu parition...

---

### Post by Dark Star on 2007-08-26
Do edit the Grub :) or From run type"msconfig" in "Run" and browse to "Boot.ini" tab and then simply delete the entry of the OS you've removed ....

---

### Post by Salpiche on 2007-08-26
I am not sure about on vista, but on Xp if you boot from the cd and go to install/repair it would put you on command prompt from where you can use "fixmbr" and/or "fixboot" in order to recover the win boot.

---

### Post by astralsin on 2007-08-26
just let the pclinuxos install  overwrite the mbr with a new grub configuration.  that's what you want, right?  to dual boot windows and pclos?  at any rate, if you've got 2 seperate drives for the operating systems, change your linux drive to master and install the mbr there, that way you can use the windows drive without having to touch that mbr

---

