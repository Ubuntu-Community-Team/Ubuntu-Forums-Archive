---
title: "Won't boot (flashing rgb screen)."
date: 2007-02-25
forum: General Help
---

### Post by Innova on 2007-02-25
I just installed Ubuntu on my computer.  After the installation I removed the CD and rebooted. 

GRUB came up, and I selected Ubuntu, kernel 2.6.17-10-generic.  The splash screen loads and after the progress meter finishes, I hear a bongo-like sound, and the screen flashes red, green, and blue.

I'm assuming that there is something wrong with the video drivers, but I'm not sure where to look to fix it.  I am able to get into the recovery mode without a problem.

My video card is nVidia 6800GS based.

Can anyone help?

---

### Post by Innova on 2007-02-25
I looked at /etc/X11/xorg.conf, and noticed that it had my monitor as "InFocus".  I have a projector hooked up to the DVI port on the card, an a 17" LCD on the VGA.  Right now I am trying to use the VGA/LCD.

I tried editing xorg.conf to get it to work, but no luck.  Anyone have any suggestions on how to modify the file to get it to work with my 6800GS and LCD?  I can worry about the projector later.

---

### Post by happyface_0 on 2007-03-04
I have this exact problem and I'm bumping this thread just in case anybody has an idea of the solution. The thing for me, is that I only have a single monitor on a 6600GT.

I've tried going into single mode with grub and thats the only possible way to see anything and running *dpkg-reconfigure xserver-xorg* but no luck.

Please help, I've been trying to fix this for awhile now! :mad:

---

### Post by Innova on 2007-03-04
I eventually did get it to work.   I had to install the nvidia driver, I just could not get nv to work at all.

Try this, happyface:  [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by happyface_0 on 2007-03-04
I followed your advice and did these steps:
```
in grub changed to single mode
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.2-0ubuntu1_all.deb //dload envy
dpkg -i envy_0.8.2-0ubuntu1_all.deb //install envy
envy //run envy
typed 1 to run the nvidia install script, success
telinit 6 //restart the system
```
Once I got back into Ubuntu, there was still flashy colors. I took a screenshot of just what it looks like.
[[IMG]http://img357.imageshack.us/img357/9698/flashycolsci6.th.jpg[/IMG]](http://img357.imageshack.us/my.php?image=flashycolsci6.jpg)

---

### Post by Innova on 2007-03-04
Did the installation (option #1 in the envy script) work correctly?  Any error messages from that step?

---

### Post by Pikestaff on 2007-03-04
I had a very similar problem once, except that I always got the flashing lines when using the LiveCD... what I had to do to get it to work was to install from the LiveCD under a different resolution (when you put in the LiveCD, you can press I think F4 or something and choose a lower resolution like 1024x786, 60Hz) and then that enabled me to install it and not see those lines.  Once it was installed I was stuck at 1024x786 but reconfiguring xorg and specifying the resolution and drivers I wanted (I had to choose nvidia, *not* nv or vesa) fixed that.

I don't know if that will help or not, my problem was mostly with the LiveCD and it sounds like you already have it installed.  What I would try is to boot into recovery mode, type this:

```
dpkg-reconfigure xserver-xorg
```

And then choose mostly the default options but choose "nvidia" when it asks you what drivers you want to use... reboot and see if it works then.  Good luck!

---

### Post by happyface_0 on 2007-03-04
> **Innova said:**
> Did the installation (option #1 in the envy script) work correctly?  Any error messages from that step?

The only error I got was it failing to run *nvidia-xconfig*.

I'v ran *dpkg-reconfigure xserver-xorg* a few times, choosing *nv* as my driver.

Is there a way to install the nvidia xconfigurator?

---

### Post by jimbob on 2007-03-04
I have an Nvidia GeForce 6600 and it never would run with the nv driver.

Do you have nvidia-glx installed?  If so, substitute nvidia for nv after running your dpkg routine and itshould work.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by happyface_0 on 2007-03-04
> **jimbob said:**
> I have an Nvidia GeForce 6600 and it never would run with the nv driver.

Do you have nvidia-glx installed?  If so, substitute nvidia for nv after running your dpkg routine and itshould work.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

I tried installing nvidia-glx and then dpkg-reconfigure again with nvidia instead of nv.
I get a 'no screens' error with that.

**I GOT THE DAMN THING TO RUN, ALL I HAD TO DO WAS RUN THE NVIDIA INSTALL UTILITY FROM THEIR SITE.**

---

