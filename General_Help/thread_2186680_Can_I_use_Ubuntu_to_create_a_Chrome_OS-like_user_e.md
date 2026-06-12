---
title: "Can I use Ubuntu to create a Chrome OS-like user experience?"
date: 2013-11-08
forum: General Help
---

### Post by jhilp on 2013-11-08
I have a stupid question for anyone who's knowledgeable enough to answer it.  I'd love to find a nice, modern operating system that's similar to Chrome OS, where you basically have a desktop with little more than a browser, movie player, and file manager. Problem is, you can't buy Chrome OS, and Chromium OS seems to be unreliable at best (for me).  My question is, is it possible to take a standard Ubuntu distro, and remove all programs that I don't want/need through the Software Center to make a lightweight program that does just what I want it to?  Or are there a lot of core operating system files that can't be easily removed, which would prohibit my idea from working? I really like Ubuntu, so to me it would be ideal to use it's stability and simplicity to create such an OS. I'm a fairly seasoned Ubuntu user, but am very inexperienced when it comes to in-depth software stuff.  Any advice would be appreciated!

[SIZE=4]**Sorry if I rambled on too much.  In a nutshell, I want to know if it's possible to make Ubuntu a more lightweight operating system by simply removing programs in the Software Center.**[/SIZE]

---

### Post by Bucky Ball on 2013-11-08
You're better going the other way and building from the bottom rather than reducing from a full install. That is pretty impossible to get back to bare essentials.

Your best bet is a minimal install:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It installs the kernel (go for 12.04 LTS as you won't need to upgrade until 2017), reboots and takes you to a command line where you install the rest, in your case probably a lightweight desktop environment of your choice (xfce4 is good and light), Chrome and a movie player (you could just go for VLC which will cover audio too). And that's it. It will fly. ;)

---

### Post by Bucky Ball on 2013-11-08
You're better going the other way and building from the bottom rather than reducing from a full install. That is pretty impossible to get back to bare essentials.

Your best bet is a minimal install:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

It install the kernel, reboots and takes you to a command line where you install the rest, in your case probably a lightweight desktop environment of your choice (xfce4 is good and light), Chrome and a movie player (you could just go for VLC which will cover audio too). And that's it. It will fly. ;)

---

### Post by jhilp on 2013-11-08
Awesome! That's a big help! My next question is, how do I know what commands to use to install the desktop environment, web browser, etc.?

---

### Post by Megaptera on 2013-11-08
Removed incorrect info - apologies!

---

### Post by jhilp on 2013-11-08
Thanks for the help! One more question, is it possible to install the Ubuntu Software Center instead of Synaptic?  If so, what is the command line? Also, is the Software Center considerably heavier than Synaptic Package Manager?

---

### Post by Bucky Ball on 2013-11-08
```
sudo apt-get install xfce4 xterm synaptic vlc xorg gdm pcmanfm
```

Installing synaptics only will NOT be enough: there won't even be a desktop environment. As I mentioned, you install EVERYTHING! The mini install installs the kernel ONLY.

Note: pcmanfm is a lightweight file manager from Lubuntu. You might prefer Nautilus or Thunar. Choice is yours. Or don't install one and use Synaptics to do it. 

After install, once you have run your 'sudo apt-get' and installed what you want, reboot. If you get to a blank screen and not a desktop, type in 'startx'. That should do it. 

* Note: you could add other things to the line above, including chrome if if you know what the command line instruction is to install it (simply chrome-browser or something maybe?).

* Important Note: DO NOT install '*buntu-desktop'. If, for instance, you install 'ubuntu-desktop' you are effectively installing Ubuntu, rendering this whole procedure a waste of time. You may as well have installed Ubuntu as the '-desktop' command drags in EVERYTHING, all apps, dependencies, the lot. You don't want that. 

* Note: Yes, Software Centre is heavier, and besides, you don't need it. It and Synaptics do the same thing exactly. Don't know the command line instruction to install it, you'd need to look it up. In reality, you don't need either of them as they are really just front ends for the 'apt-get' or 'aptitude' command. You could do everything they do through a terminal (the most lightweight of all). ;)

Good luck. ;)

---

### Post by jhilp on 2013-11-08
How do I install the desktop environment, browsers, etc.?  When I chose the xubuntu desktop option after installing the minimal install, it installed the whole Xubuntu operating system.

---

### Post by jhilp on 2013-11-08
So can I just run that command the way its typed:
sudo apt-get install xfce4 xterm synaptic vlc xorg gdm pcmanfm

or do I need to run sudo apt-get install for each item?

Where does "startx" get me to?

You're definitely right about installing '*buntu-desktop'! I just found out what it does the hard way.

Thanks for your help!!

---

### Post by Bucky Ball on 2013-11-09
Yep, just try again and use the line below exactly as typed. No need to install individually, that will install the lot. xfce4 is the desktop environment used for Xubuntu, but there are others. lxde (lubuntu DE) is another option, but there are lots. 

You'll only need to use 'startx' if, after you have installed and then run the 'sudo apt-get' line to install your apps, you reboot and it takes you to a command line and not the desktop.

```
sudo apt-get install xfce4 lxterminal synaptic vlc getdeb xorg pcmanfm network-manager
```

That's all you need for a basic setup. As mentioned previously, you will have synaptics installed so anything else you want you can install from there easily (or via a terminal - lxterminal - with apt-get). Note, I have replaced 'xterm' (the regular terminal emulator) with 'lxterminal' (used by Lubuntu and lighter) in the line here. Use this line as it is slightly different and improved. ;)

* Note: Be aware that it might take a little tweaking and research to get this exactly how you want it and running smoothly once it's running, but it will be well worth the effort (and you'll find plenty of help here and online elsewhere). Once you're there you will have a fairly rock solid (very few moving parts!) and very fast OS. You'll probably never use a standard install again! I haven't. (I started with Ubuntu, discovered xfce and used that as the DE in Ubuntu, then thought why not just use Xubuntu, then thought 'I don't need all this' so tried the minimal install with xfce DE, and the rest is, as they say, history.)

PS: Further note. The install line I have given does NOT include a web browser or email client. I assume you want to use chrome browser, so you would add:

chromium-browser

... to the end of that line. If you use thunderbird, just add that to the end of the line, so:

```
sudo apt-get install xfce4 lxterminal synaptic vlc getdeb xorg pcmanfm network-manager chromium-browser thunderbird
```

... and you're pretty good to go. Be aware that you can replace the apps later. For instance, if you prefer wicd over network manager later, just install that and remove network-manager. You can also install other desktop environments, log out, choose from the 'Sessions' pop up menu at the login screen, login. Easy. ;)

---

### Post by Bucky Ball on 2013-11-09
Further to all this, I helped someone else with one of these and just received a PM to tell me they used this line:
```

sudo apt-get install xfce4 firefox network-manager
```

Their machine is up and running just fine. You might want to replace 'firefox' with 'chomium-browser'. The choice is yours.

---

