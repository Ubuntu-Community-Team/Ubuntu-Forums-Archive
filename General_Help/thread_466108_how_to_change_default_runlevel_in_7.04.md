---
title: "how to change default runlevel in 7.04?"
date: 2007-06-06
forum: General Help
---

### Post by Darth_tater on 2007-06-06
i recently set up a 7.04 box as a quick server (going out of town, and i need vpn access...so i jsut set up a VPN server)  but the thing is, i didnt have time to DL the server edition or anything else, so i am stuck with teh default gnome manager.

my questsion(s) are simeple:

1) how can i make it so that (like the server edition) i am welcomed by the traditional text based login prompt... and *if* i need to startup the GUI then i should just type "startx"
[INDENT]i have been doing some research, and apparently i need to edit /etc/inittab but such a file does not exist on my server... and if i do need to create it, what should i put in it?[/INDENT]
2) i read things that say Ubuntu is running at runlevel 2, but i thought runlevel 5 was for X window manager!?!

Ps: thanks for the help... and mods, sorry if this is a dupe. please delete if it is found to be a dupe.

---

### Post by taurus on 2007-06-06
One way is to remove the GUI login screen--gdm--and it will boot directly into a console.

<Ctrl><Alt>F2
```
sudo aptitude remove gdm
```

---

### Post by Darth_tater on 2007-06-06
> **taurus said:**
> One way is to remove the GUI login screen--gdm--and it will boot directly into a console.

<Ctrl><Alt>F2
```
sudo aptitude remove gdm
```

nooooo i think you mis understood me.

i dot want to remove it, i just want to disable it

so that way when i press the power button, the system will continue to boot normally right up until it *would* load Xwindowserver

this is a server so a GUI is not needed 98% of the time (i know my way around CLI, but i was born/raised on windows and a GUI is some what of a comfort object/easy to use status indicator.) so i would like it if i could jsut have the server boot w/o a resource hogging GUI, but have it there if/when it is needed.

thanks.

---

### Post by mattie_linux on 2007-06-06
**1./etc/inittab. **
You're right. It's gone. It left as of Edgy Eft, as Ubuntu now manages start-up services with "upstart."
The file does exist in pre-Edgy Ubuntu's, and other flavors of Linux, so you were not crazy to look there :).

[B]2. default runlevel in Ubuntu
[/B]
 In redhat/suse, the default run level is 5. I came from RH, and like you, expected the same in Ubuntu. After the "upstart" transition, the notion of runlevels is supposedly gone, but if forced to choose, the default run level is actually 2 in Ubuntu, not 5.

**2. You don't want GNOME to start at boot, how?**

So yes, in other flavors of Linux, you'd probably just change run levels, because on run level would have X, and another wouldn't.  But in Ubuntu, *all* run levels start GNOME, so here's an easier way:

In[FONT=Courier New] **/etc/rc2.d**[/FONT], you will see a file S13gdm.  This starts the GNOME system.
Simply change that file to K13gdm.

[FONT=Courier New]**# sudo mv  S13gdm K13gdm**[/FONT]

(It's possible the number between the "S" and the "gdm" will be slightly different than 13. That's OK.)

This leaves the package installed, but just not started at boot.

To start X later, run:

**# sudo /etc/init.d/gdm start**.

---

### Post by Darth_tater on 2007-06-06
wow.  thanks for posting the quick reply

i shall post back in a few min after i make the suggested changes.

---

### Post by Darth_tater on 2007-06-06
i tired it... and it worked!

but, it should be noted that you must run /etc/init.d/gdm as root

so actually you need to run ```
sudo /etc/init.d/gdm start 
```

---

### Post by mattie_linux on 2007-06-06
OK. great! I just edited my post to reflect your correction. (I had another typo to fix there anyway).

---

### Post by KenLiou on 2007-06-09
mv /etc/rc2.d/S13gdm /etc/rc2.d/K13gdm

---

### Post by etank on 2007-06-12
I just found this on LaunchPad [https://answers.launchpad.net/ubuntu/+source/upstart/+question/6585](https://answers.launchpad.net/ubuntu/+source/upstart/+question/6585). It helps shed some light on what you are asking about.

---

### Post by ruggersway on 2007-07-31
I know this is a little late, but I used a similar approach when setting up the server edition.  After installing gdm and editing the rc*.d entries as suggested already, for *comforts* sake rc5 now starts gdm.  After logging into rc2, 

# init 5

Gives you a clean start gnome login, just as

# /etc/init.d/gdm start

The difference is using init moves you to runlevel 5 instead of just starting another service in runlevel 2.  

This way you can tweak to remove unnecessary services from runlevel 2, then actually changing runlevels is more efficient and useful.


-//etank - good link.

-rugger

---

### Post by Kpax1 on 2007-09-14
I tried this:

mv /etc/rc2.d/S13gdm /etc/rc2.d/K87gdm

now, even after changing it back to S13gdm, I am unable to login to gnome. I get an error message that says:

session lasted less than 10 seconds... etc...

Does anybody have any suggestions? I am trying to install Nvidia drivers in runlevel 3. I am in the process of downloading Fedora if this doesn't work.

---

### Post by orangey on 2007-09-14
kpax, off topic question, but I was wondering, how did you install a vpn server on ubunut?

---

### Post by Kpax1 on 2007-09-14
I did not install a VPN. I am trying to change the default runlevel to 3. I thought that disabling S13gdm would stop gnome from starting. The instructions on the Nvidia page for installing their drivers recommend installation is done at runlevel 3--before X server initialized. I simply am having a hard time wrapping my head around runlevels in Ubuntu.

---

### Post by ruggersway on 2007-09-17
kpax -

mv /etc/rc2.d/S13gdm /etc/rc2.d/K87gdm

disables gdm in runlevel 2, which you'll still boot into.  Runlevels in Ubuntu are kind of all the same, with the obvious exceptions of 0 and 6.  Runlevel 2-5 I think are all the same, it is up to you to customize the runlevels.  Disabling gdm should satisfy what you are trying to do with the nvidia install.

I've never had much luck with the drivers directly from nvidia.  One of my laptops runs on nvidia and I just used apt to install.

# apt-get install nvidia-glx

There are several good tutorials online to follow - just google how-to nvidia ubuntu or something

[http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html)

This is one I looked at to install the drivers on my system.  If you don't want beryl, just look at the section on "Install the Latest Nvidia Drivers"

I've not had troubles with disabling/enabling gdm keeping me from logging in, however, I had trouble with nvidia drivers, initially, messing up gdm so it would not run.  

As always, make a backup of /etc/X11/xorg.conf prior to making changes to it.  If your gdm login fails you can always restore the xorg.conf and restart gdm.  

But for simplicities sake, unless you have a real need for the official nvidia drivers, I'd stick with what you find in the ubuntu repos.  Hope this helps.

-rugger

---

