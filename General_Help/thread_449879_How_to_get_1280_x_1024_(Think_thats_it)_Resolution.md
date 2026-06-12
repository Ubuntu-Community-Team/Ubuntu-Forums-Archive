---
title: "How to get 1280 x 1024 (Think thats it) Resolution"
date: 2007-05-20
forum: General Help
---

### Post by Linux_Noobie on 2007-05-20
Just installed 7.04 but stuck at 1024 x 768
How do i get the higher res?

---

### Post by bashologist on 2007-05-20
> **Linux_Noobie said:**
> Just installed 7.04 but stuck at 1024 x 768
How do i get the higher res?

Try "System" -> "Administration" -> "Restricted Driver Manager". What drivers are you using? What graphics card?

---

### Post by Linux_Noobie on 2007-05-20
Intel Extreme 2.
No drivers..

Also im not going into terminal because i borked my install that way last time

---

### Post by squeezy on 2007-05-20
You're going to have to use the Terminal, I'm sure :p

I thought this was funny though, just the other day I was trying to get rid of 1280x1024 :p

---

### Post by deadlikeoscar on 2007-05-20
I just manually added it to my xorg config file because I didn't select it as an option when I first installed it and it was faster to do it that way.

---

### Post by Linux_Noobie on 2007-05-20
k how do i do it in xorg.conf?

---

### Post by deadlikeoscar on 2007-05-20
Well, if you want to try it(you said you have no drivers installed so I can't be sure it will support 1280 X 1024) it's pretty easy. Most people will give you the back up your xorg.conf file speech but that is up to you because you really shouldn't mess anything up. I know you don't like the terminal but this will be painless and it is only to open up the file with the correct permissions.

Open the terminal and type sudo gedit /etc/X11/xorg.conf

Scroll down to the bottom of the file and find where it says 

SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"

Yours shouldn't have any reference to 1280x1024 yet but you need to add it to each section--so it looks like mine. There are about 6 sections you need to change--the depth section is numbered differently for each one. Now just save the file.

This should only add the OPTION to use 1280x1024 when you go to System-->Preferences-->Screen Resolution. Like I said, I can't guarantee that it will display properly when you select 1280x1024 and reboot the system. If it won't boot into X when you reboot you can probably just type Ctrl + Alt +F2 if you aren't already at a command line and log in. Then you will need to type sudo dpkg-reconfigure xserver-xorg and set up xorg like you did when you first installed Ubuntu. If you decide to do this I would print this out just incase you need it and can't log in to X. Good luck if you decide to try it.

---

### Post by jerrylamos on 2007-05-20
Take a look at my post "Workarounds" on "Installation & Upgrades".  
Directly editing xorg.conf can be troublesome, I've had much better luck with the following.  (Note, there are no spaces before the - except for the -phigh.)
sudo dpkg-reconfigure -phigh xserver-xorg
It will ask you what driver to use, screen resolution, etc.  If it went O.K., then
sudo killall gdm
startx
You can safely look at xorg.conf with
less /etc/X11/xorg.conf
which is a browser and can't change the file.  Use q to quit.

Cheers, Jerry

---

