---
title: "[SOLVED] How to choose which operating system to boot from Ubuntu"
date: 2007-10-29
forum: General Help
---

### Post by bmccorm2 on 2007-10-29
I think my title details my question, but i will try to clarify as much as possible:

I am trying Ubuntu from Mandriva Linux and Mandriva has this neat little feature (maybe a package?) that when you click the restart button, it gives you the choice of which operating system you would like to boot into (without choosing it from the BIOS).

Does anyone know how or which package gives this functionality?  I have been scouring the forums and have yet to find anything.  

Thanks

---

### Post by Shazaam on 2007-10-29
Grub.

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

Unless you are talking about window managers (kde, gnome, icewm, etc).

---

### Post by bmccorm2 on 2008-02-08
Hi and thanks for the reply.  And yes I am talking about window managers.  I mainly use my system remotely, so i would love to be able to choose which OS to boot into while in the OS (because i obviously cannot control my machine while it is in the BIOS).

---

### Post by neurostu on 2008-02-08
The only way I know of the specify which OS boots is to edit the grub.conf file.

  So what you can do is to create a couple back up grub.conf files (like grub.1.conf grub.2.conf or grub.ubuntu.conf grub.madrivia.conf). then use a script to overwrite the current grub.conf with the grub.XXXX.conf of your chosing.

Each grub.XXXX.conf is identical to the normal grub.conf only that it specifies a different default os.

Then write a shell script that takes care of copying your conf files and you're good to go, you can change the default os remotely and in a terminal.

---

### Post by bmccorm2 on 2008-02-10
Thanks for the reply neurostu.  I think it is a great idea but I ran into one little caveat.  I made a script that will change the grub.conf to default to windows, so next time i restart it does indeed boot into windows.  But then I am in windows and have no way of getting back to Ubuntu!  So i basically did the same thing in Windows, wrote a script that will mount the ext2 linux volume, change the grub.conf file and reboot.  However, Linux does not like it when windows modifys its files, so whenever I restart into Linux it thinks the filesystem is dirty and has to run a check on that filesystem.  It still boots (eventually), it just takes a while.  (And did i mention that windows is a pain in the @#$$ while trying to reboot/shutdown remotely?) 

Thanks for the response I am going to mark this thread as solved.

---

