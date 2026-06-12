---
title: "Acces denied..."
date: 2012-12-24
forum: General Help
---

### Post by Agent26 on 2012-12-24
Hi there all and happy xmas, 
I keep getting this.....

child process "/usr/share/rhythmbox" (Permission denied)
 

and i am not sure how to get permission to open my desktop launchers I added. (the gnome way) In Xubuntu I can make files executable in the permissions but it doesn't seem to work in ubuntu, sure it's something simple.

Thank you.:D

---

### Post by Luigi2012SM64DS on 2012-12-24
> **Agent26 said:**
> Hi there all and happy xmas, 
I keep getting this.....

child process "/usr/share/rhythmbox" (Permission denied)
 

and i am not sure how to get permission to open my desktop launchers I added. (the gnome way) In Xubuntu I can make files executable in the permissions but it doesn't seem to work in ubuntu, sure it's something simple.

Thank you.:D
Hi, what command are you trying to run? and are you typing sudo before you type the command?

---

### Post by Agent26 on 2012-12-25
Hi, I have been attempting to place desktop launchers on my desktop, I can get them up OK but they just wont open, I tried first to sign in as root but no change. I have not tried to open them in terminal though, I was just right clicking the icon and then getting the message.

child process "/usr/share/rhythmbox" (Permission denied)

Transmission is the same too, all of them.

Is there a terminal code that I can interchange the app name to give me permissions.

When right clicking the icons I can give myself read, read write or none permissions and even tick a checkbox to say it will open but no joy.

---

### Post by dino99 on 2012-12-25
tweaking the folders/files permission is the worst way for resolving issues, and the better one to brake everything, be aware ):P

sudo apt-get purge rhythmbox
sudo apt-get install rhythmbox

sudo dpkg-reconfigure -phigh -a
(can take a while, be patient, dont stop it yourself)

---

