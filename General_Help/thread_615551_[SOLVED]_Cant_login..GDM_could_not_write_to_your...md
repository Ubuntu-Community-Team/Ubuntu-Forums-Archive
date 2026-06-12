---
title: "[SOLVED] Cant login..GDM could not write to your..."
date: 2007-11-17
forum: General Help
---

### Post by kubilaycan on 2007-11-17
I left my ubuntu on while i was at work. it was downloading stuff. when i came back i realized deluge, my torrent client, was frozen. so i forced quit it. everything else seemed fine.. 

i rebooted into windows to play some pes 2008. now when i want to go back into ubuntu, its all ok until the login screen. when i enter my details and say "login", i get this message..

"GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. in any case, it is not possible to log in. please contact your system admin." 

and then it goes back to the login screen.

it could be very well that i am out of disk on my ubuntu partition..there was little left and i started some download tasks without making sure there was enough space for them. 

so... now how do i delete stuff to make space on my ubuntu partition so i can log on, when i have to be logged on in the first place to delete them? 

i cannot access my ubuntu partition from my xp session, since it cannot read ext3. 

i need help..

---

### Post by wooster on 2007-11-17
Sorry to hear you ran out of disk space. I'll try to give some advice to help. At the  login screen press ctrl + alt + f1 which will take you to a virtual terminal where you can login. Type your username and password there. It should log you in where you can run this command. If you aren't able to login through the virtual terminal try booting in recovery mode and running the command.

```
sudo apt-get clean
```
This command should free up a couple hundred megabytes for you. It basically just clears the cache of package apt keeps around.

When you finish running that command press ctrl + alt + f7. That will return you to the gdm login screen. Now see if you can login successfully.

---

### Post by kubilaycan on 2007-11-17
i solved the problem and am writing this from my beloved ubuntu..

i read some other threads and they said i had to go into recovery mode (you go here during the "grub" menu when it asks u what ubuntu u want (generic or recovery) or windows if u have) and then type 

sudo apt-get clean

this will delete your temp donwloaded files so hopefully it will free enough space to let u log in again. 

cheers..

---

### Post by kubilaycan on 2007-11-17
thx wooster for the help.. we were writing our posts at the same time i guess...

i appreciate your help

---

