---
title: "apt-get remove perl"
date: 2007-10-13
forum: General Help
---

### Post by New-b on 2007-10-13
o-hell

I am very new to linux and ubuntu and were trying to install perl, but somehow i could not make it work..
them I wanted to remove perl. So I wrote in terminal "sudo apt-get remove perl"    and walked away ......

now everything is gone.....

can't start the gui, what has happend, plz plz plz help me...

---

### Post by aJayRoo on 2007-10-13
Oh dear! Perl is actually installed by default anyway as it is rather important for many applications to function. If you ask to remove perl you should have seen a (large) list of other packages that will have to be removed also as they depend on perl being installed, and been prompted "Do you want to continue [Y/n]?". This list contains, among hundreds of other things, Gnome and even the X-Server (the graphical system of linux). In short, if you saw this list and just pressed y to remove all of them anyway you will have just removed a considerable portion of your system and removed most functionality... Oops! I'm not sure of the best way to proceed as I don't know which packages and libraries were deleted, personally I think I would go with a complete reinstall of the operating system. I know you don't want to hear this but this is a great lesson in not just pressing yes! Make sure that you read those messages that apt gives you, or bad things can and will happen.

---

### Post by Abild on 2007-10-13
I have to agree with the above post... A reinstall may unfortunately be the only way of getting things up and running again.
However, if you access a terminal you can try running
sudo apt-get install ubuntu-minimal ubuntu-desktop
Those packages should depend on everything that gets installed by default (i think). If you're lucky your system will start working again :)

---

### Post by New-b on 2007-10-14
managed to start gdm from command line and then did the apt-get install ubuntu-minimal ubuntu-desktop.


I'm up and running again :guitar:

I knew Linux could do it, thanks.......

---

