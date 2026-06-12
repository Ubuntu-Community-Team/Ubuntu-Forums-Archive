---
title: "Dual Monitor Issues..."
date: 2008-05-18
forum: General Help
---

### Post by evilwombat on 2008-05-18
Okay, so I am a complete n00b at Linux in general. I downloaded Ubuntu Hardy Heron to my 250gig WD Passport. I finally managed to get it up and running and was happy with it. The only other problems I've had is the mozilla firefox 3b5 bug about the flash, and the Grub Error 21 when the passport isn't plugged in... but it seems to be mildly under control for the time being.
Anywho...

I purchased a 17 inch Gateway Flatscreen yesterday and came home and set it up after booting into windows vista, and it is fantastic.
I came and tried to check it with Ubuntu and as most of you know, the dual monitors are kind of irritating to set up.
Through the use of 3 or 4 different tutorials I came up with a solution that worked decently well. Now my problem is
When I try to save my edited X configuration file with my NVidia X Driver settings I get this error

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

There are several xorg.conf variation files in the /etc/x11/ folder (xorg.conf~, xorg.conf1, xorg.conf_backup.,xorg.conf_backup) I think I created these on accident when messing with one of the tutorials.
I think I need to delete these to get it to save, but thats just what I think.
How would I arrange this to where I can save my xconfig to run my second monitor???:confused:

Thank you for any help.
-Sutton

---

### Post by duncanyoyo1 on 2008-05-18
Well, I spent pretty much all of yesterday looking around for this, and here is what I got

Open up a terminal and copy and paste in
```
sudo apt-get install nvidia-settings
```

then in the terminal type 
```
sudo nvidia-settings
```
and click on X Server Display Configuration

You should be able to get it from there, it's pretty much like Windows. 
I would suggest using the TwinView configuration.


That should work. :)

---

