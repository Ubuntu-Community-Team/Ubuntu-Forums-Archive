---
title: "Trouble with Drivers"
date: 2012-11-07
forum: General Help
---

### Post by dmahesh22 on 2012-11-07
I'm using Ubuntu 10.04,it is working fine,but the problem is when I use 21 inches monitor then 20% of screen is displaying with black background,if I use 17 inches or smaller then there is no issues,what might be wrong ?

---

### Post by houseworkshy on 2012-11-08
It does sound like a driver issue.  Have you installed a proprietry driver and if so what is it. If not to do so System>Administration>Hardware Drivers.  
You could also install a small diagnostics program called sysinfo which finds details of your hardware.  Either via one of the gui software installers or with "sudo apt-get install sysinfo" enterered in the terminal.  Once in it will put a link in your Applications>System tools menu from which you can run it or enter "sysinfo" in the terminal.  One of it's options is to save a file which will be a text file of your hardware spec's.  Attaching that file to a post is a lot easier than typing it all out.  The info would help with the diagnostics. 
Oh and welcome to the forums by the way.  I don't know if you are new to Ubuntu as well as here but, as an aside, if you are you may find this handy
 [http://ubuntu-manual.org/](http://ubuntu-manual.org/)  It's a free download and well worth having in ones documents.  An excellent well written overview IMHO

---

### Post by dmahesh22 on 2012-11-08
I'm attaching sysinfo file,Thanks for your replay

---

### Post by houseworkshy on 2012-11-24
First sorry for the late reply.  I'd glanced at your reply but then life happend and as I'd looked and there hadn't been another post it didn't show in my user cp.  
Our systems are very similar and I think that all you need to do is install the drivers as mentioned above.  I didn't explain my shorthand and should have done.
The "to do so System>Administration>Hardware Drivers." bit was in referance to menues.  So click on the System menu at the top of your screen to start, each ">" meant 'from that menu click on' .  From that lot you will end up with a box which explains itself.  Because it's an admin action you will be asked for your password at the opening hardware drivers stage.  
A reboot will be needed for the new drivers to take effect.  Usually on a fresh install one is prompted to do all this, if that didn't happen it's odd.

---

### Post by 3rdalbum on 2012-11-24
Regardless of whether you have the best driver installed or not, your resolution is not set up correctly. Usually, when Ubuntu boots up it detects the resolution of the monitor and adjusts itself to suit.

Go to the Cog Menu at the top-right corner of the screen and come down to Displays. The popup menu at the top allows you to set the resolution; try turning the resolution up. 1920x1080 is probably the correct resolution for the monitor.

If you don't get any options, it's possible that the lower resolution has been specified in the X configuration file. The easiest way to fix it, then, is to remove the file and let Ubuntu start autodetecting the settings again.

Paste this text into the terminal:

```
sudo rm /etc/X11/xorg.conf
```

Then reboot.

---

