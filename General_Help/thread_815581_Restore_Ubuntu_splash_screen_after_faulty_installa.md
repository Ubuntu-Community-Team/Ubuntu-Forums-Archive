---
title: "Restore Ubuntu splash screen after faulty installation of usplash themes"
date: 2008-06-01
forum: General Help
---

### Post by MachineHead on 2008-06-01
Hi everyone,

Recently I tried to install a splash screen from gnome-look.org.
Follow this link to view the download I used:
[http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468](http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468)

I was almost at the end of the installation procedure when the console gave me back some errors.
After trying to redo some steps taken, I thought it was solved but a reboot gave me no nice flashy splash screen at all.
Instead I get the text based splash now.
Just Linux showing me in console/text based what is being started and checked when either booting the system or exciting.

I would like to restore the Ubuntu splash in which you see the Ubuntu logo with the bar filling up (Orange, standard splash screen)

If you know the magic words to make the console obey me, please help me out :)

Regards,

MachineHead

---

### Post by nick_h on 2008-06-01
Have a look at your /boot/grub/menu.lst file.  Are you specifying *splash* as a kernel option?

If you are then maybe try reconfiguring the *usplash* package.

---

### Post by logos34 on 2008-06-01
if you can't fix it directly thru menu.lst as nick suggested above, there's a usplash config option in startupmanager

sudo apt-get install startupmananger

this too:
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_change_the_USplash_Screen_on_startup.2Fshutdown](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_change_the_USplash_Screen_on_startup.2Fshutdown)

---

### Post by MachineHead on 2008-06-18
Hey Logos and Nick,

Thanks for the reply's.
I've installed the GUI to manage the startup screen.
Can't reboot at the moment, cause I'm downloading but I will let you know the result.

Regards,

MachineHead

---

### Post by babylon2233 on 2008-06-18
I having the same problem before but after I remove the default theme, Everything works fine

---

