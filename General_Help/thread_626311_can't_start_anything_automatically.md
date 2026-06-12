---
title: "can't start anything automatically"
date: 2007-11-28
forum: General Help
---

### Post by Tyke91 on 2007-11-28
Every time I add a new program to my "Sessions" manager under preferences, it automatically gets deleted from the list when I close the window.

I'm trying to get Kiba-Dock to start when I log in, but no matter what I do, I can't get it to work. This has happened to me before with other programs (I'd like amarok to start as well). There is also a possibly related problem with my chron application or program (whatever it is). entries do not work, even if they normally work in a terminal (hell... even the example listed on the tutorial websites won't work)

does anyone know why?

does it have to do with any system specs that I might have?

I'm running Ubuntu 7.10 on a dell dimension E520 with an Intel Core2 Duo processor, I've got a gig of ram and 80 gigs of space on my ubuntu partiton ( I dual boot xp). I use an Nvidia 7300 LE graphics card.

---

### Post by mpierce on 2007-11-29
If you are using Gnome can't help you but if you use KDE, go to your home folder and open a terminal:
1) cd .kde/Autostart
2) ln -s "program name" . (notice the dot after the program name) e.g.,
     ln -s /usr/bin/amarok

Program will startup automatically when you log in.

Hope this helps...

---

### Post by Tyke91 on 2007-11-29
sorry, should have said that I'm using gnome.

---

### Post by beczka2005 on 2007-12-10
Which version of ubuntu did you even install on this system? For version 7.10 the keyboard doesn't respond during installation, and when the countdown ends the system hangs!

---

### Post by Tyke91 on 2007-12-10
I am using 7.10,  but I fail to see how your keyboard affects this post. please don't hijack the thread

---

### Post by theoutdoors on 2007-12-15
> **Tyke91 said:**
> Every time I add a new program to my "Sessions" manager under preferences, it automatically gets deleted from the list when I close the window.

I'm trying to get Kiba-Dock to start when I log in, but no matter what I do, I can't get it to work. This has happened to me before with other programs (I'd like amarok to start as well). There is also a possibly related problem with my chron application or program (whatever it is). entries do not work, even if they normally work in a terminal (hell... even the example listed on the tutorial websites won't work)

does anyone know why?

does it have to do with any system specs that I might have?

I'm running Ubuntu 7.10 on a dell dimension E520 with an Intel Core2 Duo processor, I've got a gig of ram and 80 gigs of space on my ubuntu partiton ( I dual boot xp). I use an Nvidia 7300 LE graphics card.

Hi,

I have just had the same problem when trying to get Avant Window Navigator to start automatically - every time I added my script to start it using the "Sessions" manager under preferences, it automatically got deleted from the list when I closed the window.

After some investigation, I found in ~/.xsession-errors that files could not be saved to the directory ~/.config/autostart. I had errors like this in ~/.xsession-errors:

** (gnome-session-properties:6031): WARNING **: Could not save /home/me/.config/autostart/script_to_launch_awn.desktop file

I found the ~/.config/autostart directory was missing. Instead there was a file called autostart. I had previously added startup scripts without any problems on my laptop, which also has gutsy on it. On my laptop the autostart directory was there. I have no idea why it would be there on my laptop but not on my desktop, but I have done the following to remove the autostart file that was on my desktop and create an autostart directory instead:

cd ~/.config
rm autostart
mkdir autostart
chmod 700 autostart

I gave it the same permissions as the one that was already on my laptop.

That solved the problem for me... it would be nice to know what caused the problem though, if anyone knows? thanks.

---

