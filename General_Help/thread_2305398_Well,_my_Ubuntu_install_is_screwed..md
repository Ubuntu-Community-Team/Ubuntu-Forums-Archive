---
title: "Well, my Ubuntu install is screwed."
date: 2015-12-05
forum: General Help
---

### Post by RocketPenguin on 2015-12-05
Ever since I began using Ubuntu on and off (about 8 years ago) I have always had graphics driver problems. Always. No matter what type of GPU(s) I had, always ended up coming here because it couldn't figure it out.
And here I am, again.

Long story short, I think I've seriously messed up xorg/nouveau/nvidia drivers/Ubuntu desktop/and unity. Or a combination of the above. Currently, my splash screen is black and white (I dual boot) and when I boot to Ubuntu, I keep getting this message, " fsck from util-linux 2.26.2" and something about my partition, clean, number of files, and number of blocks.
I am really close to just "screw it, all the work I've put into the os can go down the drain, reinstall."

Could anyone help me fix this? As for what I have done, it involved reinstalling ubuntu-desktop, reinstalling nvidia drivers, uninstalling nvidia drivers, installing nouveau, reinstalling xorg xserver, installing xubuntu desktop environment, uninstalling xubuntu IDE, wiping all config files, and a bunch more through TTY. 

I use a laptop, Asus n61j
It has:
8gb ram
Intel i5 450m
Intel GPU
Nvidia geforce 325m
And a 260gb ssd with windows installed alongside Ubuntu

How should I go about pretty much reinstalling Ubuntu, minus losing all of my installed programs, work, and files? 
Sorry I don't have much on what I did do... Just assume I did the worst possible.

Thanks for your time and help!

---

### Post by cariboo on 2015-12-05
Ignore the fsck message, as all it is telling you is that hard drive is working OK. You didn't say what Nvida driver you are using, but if you go to the[ Nvidia driver download]("http://www.nvidia.com/Download/index.aspx?lang=en-us") page. It says you need the driver version 340.96 which is in the repositories.

---

### Post by RocketPenguin on 2015-12-05
How do ignore the message? It shows up in white text on a black background, there is no cursor, and i cannot input any text. The only thing I can do is open up a TTY terminal.
I downloaded Nvidia's drivers from their website, installed them, and if i remember correctly, that's what started my whole issue.
Reason the stock drivers weren't good enough for me, was because there was this serious diagonal screen tearing that was getting on my nerves...
And the fact that it has Optimus/dual gpu switching doesn't make it any easier...

---

### Post by buzzingrobot on 2015-12-05
Don't assume the latest Nvidia drivers are always what you need.  Go by what the Nvidia site says is the right driver for your card.

---

### Post by RocketPenguin on 2015-12-05
I did go by what Nvidia's site said. I didn't get the Beta or anything. Now I'm stuck without a GUI.

---

### Post by Vladlenin5000 on 2015-12-05
Again, your required driver version is in the repositories and that is what you should have used. The nvidia website is good mostly to check what version they recommend. Whenever possible you should use the drivers from the Ubuntu repositories because those are the ones tested for your specific release.

In command line do:
```
sudo apt-get purge nvidia*
```

Reboot. Now you're back with the default *nouveau* (open source).
Then, find and install the recommended drivers in System Settings > Software & Updates (14.04) / Software Properties (15.10) > Additional drivers. That's it.

Certain nvidia integrated chips like yours can be tricky. They often work with a specific driver version only.

---

### Post by grahammechanical on 2015-12-05
I have 2 installations of Xenial Xerus (16.04 development branch). One install is using the open source video driver Nouveau and it has a loading purple splash screen. The other is using the Nvidia driver and it does not have the purple splash screen. So, I always see the fsck message and it never stops Linux from starting Ubuntu and presenting a log in screen.

Actually, it is just a system message that you would ignore if it was hidden behind a splash screen. In my opinion you did more to screw up the desktop by installing & then uninstalling an alternative desktop environment because the uninstalling part is never completely effective.

As for not having a GUI desktop ... use the Advanced options for Ubuntu sub-menu at the boot menu and select recovery mode and then Resume. That might get you to a working desktop. From recovery mode we can also get to a root shell prompt which might be needed to purge the proprietary video driver. To exit the root shell prompt just type Exit and that will take you back to the recovery mode menu.

Regards.

---

### Post by RocketPenguin on 2015-12-05
I did use those in the repositories first... Thing is, none of them made any difference. The diagonal screen tearing persisted.

Still have the fsck message, except now it continuously flashes.

---

### Post by RocketPenguin on 2015-12-05
Yes, but the fsck doesn't go away. I let it sit for an hour without change. Now, it flashes, screen turns off, turns back on, flashes, and repeats indefinitely. 

I'll try recovery mode, and see what i can do.

---

### Post by RocketPenguin on 2015-12-05
Update: if I go into recovery mode, I still cannot get a functional GUI. The failsafe graphics boot says it cannot detect my GPU settings, and that I have to do it manually. 
What would the command be to purge nvidia's driver?

Edit: still flashes

---

### Post by Vladlenin5000 on 2015-12-05
> **grahammechanical said:**
> (...) From recovery mode we can also get to a **root shell prompt** which might be needed to purge the proprietary video driver. To exit the root shell prompt just type Exit and that will take you back to the recovery mode menu.

My bold. This is a CLI (command line interface). You can also try CTRL+ALT+F1 in your normal (non-GUI) boot. Either way you need to login by typing your username ENTER password ENTER before anything else.
The command to purge nvidia has been posted already in post#6.

---

### Post by RocketPenguin on 2015-12-05
Yes, I have used TTY, and yes, I have entered that command. 

> 
[COLOR=#000000]Still have the fsck message, except now it continuously flashes.[/COLOR]

---

### Post by buzzingrobot on 2015-12-05
The command to remove previously installed Nvidia packages was given earlier in the thread.

If you've installed any of the drivers provided by Nvidia, you need to follow Nvidia's guidance to delete them.  They are not released by Nvidia as Ubuntu packages so the Ubuntu package manager (apt-get, etc.) is unaware of their presence on the system and cannot remove them.

---

### Post by RocketPenguin on 2015-12-05
From searching around, there is no "Nvidia Guidance" on deleting their drivers. 
All i found was this: [http://askubuntu.com/questions/128113/how-do-you-remove-nvidias-proprietary-drivers](http://askubuntu.com/questions/128113/how-do-you-remove-nvidias-proprietary-drivers)
And i did it all, and now the only difference is that my screen doesn't flash anymore.

The driver i installed (Which could very well be gone by now, from all the commands I've typed in...) is [COLOR=#000000][FONT=Trebuchet MS]NVIDIA-Linux-x86_64-340.96
Link: [/FONT][/COLOR]http://www.nvidia.com/download/driverResults.aspx/95165/en-us

What i still dont get is why does fsck util-linux keep popping up...

---

### Post by RocketPenguin on 2015-12-05
Ok, so an update:

I ended up going through this tutorial: [http://www.allaboutlinux.eu/remove-nouveau-and-install-nvidia-driver-in-ubuntu-15-04/](http://www.allaboutlinux.eu/remove-nouveau-and-install-nvidia-driver-in-ubuntu-15-04/)
Which gave me a black screen, even the backlight turned off.
So, i simply sudo apt-get purge nvidia* and then sudo apt-get install nvidia-common or something like that, and now i have a GUI!
But the fun doesn't end just yet.
My login screen is all sorts of weird, kinda looks like lxde login, but the background is corrupted or something, all sorts of black and chunks of random colors. Chrome isn't liking it, my google pages come in blank (Confirmed from earlier a GPU driver issue). And i have about a zillion errors. (How do you copy and paste a "report an error"?) The drivers are all sketchy-like, serious screen tearing, and browser pages load from top to bottom, chunk by chunk. 
Which driver should i use: [IMG]http://imgur.com/9GDbHOO[/IMG]   [http://imgur.com/9GDbHOO](http://imgur.com/9GDbHOO)

The crash log says something about Compiz crashed with SIGSEGV or something.

---

