---
title: "Ubuntu MATE 15.04, doesn't boot anymore"
date: 2015-05-01
forum: General Help
---

### Post by elytron on 2015-05-01
Need some help. I had a working install of Ubuntu MATE version 15.04, but now the OS wont boot to login. In an attempt to disable the "Guest Login Account" I made a change. Believe that I added a line of text to the /etc/lightdm/lightdm.conf file. ```
allow-guest=false
``` After the addition, I did a reboot. Now my system won't boot, just gets stuck on the Ubuntu-Mate bootsplash. Not sure what went wrong, please help me fix my system.

---

### Post by Geoffrey_Arndt on 2015-05-01
Boot with a Live linux disk (something light would be good - like xubuntu . . or your original Mate install disk).   

  You should be able to compare an original file from Mate Live CD to the one you changed & change it back to default condition (using sudo & gedit) and saving the file . .

(sudo gedit /etc/lightdm/lightdm.conf)

---

### Post by elytron on 2015-05-02
I boot from a USB thumb drive, then deleted the /etc/lightdm/lightdm.conf file that I had created. Your suggestion helped, and my computer works again. Thanks!

I still want to figure out how to disable the guest account though. Oh well, I will try again another time.

---

