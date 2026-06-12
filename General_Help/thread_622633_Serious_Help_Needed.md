---
title: "Serious Help Needed"
date: 2007-11-25
forum: General Help
---

### Post by leapcow on 2007-11-25
ok guys, i'm completely new to linux. i got this computer to help setup a website with my friend. all the site files are on this computer and i can't lose them

now the problem. i really don't know what happened. one second i was using ubuntu trying to get my sound working (still haven't got that working BTW). i installed 3d chess and knight cuz i finally gave up on the whole sound thing (both from package manager) then i rebooted to maybe get the sound working. the only problem is when it was shutting down, the... unboot?... screen said xubuntu. this obviously surprised me and i got a bit worried. and as you can guess when i rebooted the computer it was running xubuntu. I DO NOT WANT THIS. i wanted to go back to just ubuntu. (daper drake (this is what i've been using)) so i tried a few things online but when other things didn't work i (a complete n00b to all this) tried to fix it my own way A.K.A. i went to the package manager and searched for anything with xfce or xubuntu in the name and... completely removed it... i feel so stupid.

so now when i boot it comes up xubuntu log in screen... and when i log in it goes to the rat runnin on the wheel. but when that screen goes away its just a blank blue screen and i can't do anything. but if i tap the power button on the tower i get shut down options

PLEASE HELP. i need this back up asap...

thx in advance,
leapcow

---

### Post by jcsteele on 2007-11-25
Can you see if you still have the ubuntu-desktop package installed....you will def. need it.  When you start the system and it halts at the blue screen, you should be able to press "CTRL+ALT+F1" which will bring you to a terminal, where you can login.  From there, issue:

sudo apt-get install ubuntu-desktop

If its not there, it will be installed...if it is already present, it will notify you.  If it has to download and install the program, try a reboot afterwards to see if that fixes the problem.  

You also might want to run a sudo apt-get autoremove as well

//jcs

---

### Post by leapcow on 2007-11-25
it says desktop is already installed and it says auto remove is an invalid command

---

### Post by jcsteele on 2007-11-25
Make sure you do not have a space between the "auto" and "remove" it should be exactly how I typed it above...

---

### Post by leapcow on 2007-11-25
i did... still nothin

---

### Post by bettlebrox on 2007-11-25
It's not a problem to have Xubuntu packages installed on Ubuntu. Basically, all the Ubuntu hybrids are just Ubuntu but with a different window manager. On the login screen you should be able to choose Gnome as your default window manager and be back to a default Ubuntu looking desktop.

---

### Post by jcsteele on 2007-11-25
you might try setting a password for the root account by typing "sudo passwd root" and then trying to login to your desktop with the root account...this will at least let us know whether your system is semi-functional, as the command I sent you above SHOULD be working properly.

//jcs

---

### Post by leapcow on 2007-11-26
thx so much guys. i went to the choose session and chose gnome only and it booted up with desktop working and old ubuntu

thanks so so so much...

so uh... any suggestions on fixing my sound?

---

### Post by oodledoodle on 2007-11-26
try typing *alsamixer* into the console and use the arrow keys to turn the volume up. if that fails, what soundcard are you using?

---

### Post by leapcow on 2007-11-27
i'm already done that

i went through everything here: 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

and i found my boards site and got drivers and installed em

---

### Post by leapcow on 2007-12-20
any ideas?

---

### Post by TeaSwigger on 2007-12-20
Hello, 

Probably best to start a thread with "no sound" or such on the title so to better the odds of attracting folks who know more about that. Also post your specific sound card, specs and anything else you think may be related. Really it's hard to be too specific. Right now folks might not know where to start. I sure don't beyond what was suggested. Anys, luck.

P.S. if you still have the Xubuntu usplash (screen during booting), to change your usplash back to Ubuntu, enter this in a terminal:

```
sudo update-alternatives --config usplash-artwork.so
```

Choose usplash. Then run in a terminal:

```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

When that's done it should be using the one you chose.

---

