---
title: "Intel Driver."
date: 2006-12-31
forum: General Help
---

### Post by M_the_C on 2006-12-31
Hi,
   I have been installing Xubuntu my sisters old computer (I don't mean it used to be hers, it really is old) and have been trying to play DVDs but have been getting stuttering playback .

I know I setup the DVD libs properly as it has worked on the main computer.

So I decided to try installing the Intel proprietry drivers.  I downloaded them but in the help it keeps mentioning XFree86 and I can't get it to work.  Do I need XFree86?  What is it and how do I set it up.  Is there another way of setting up the driver?

[COLOR="PaleTurquoise"]Also, I accidentally overwrote the X file and now I can't get back into Xfce.  Can I fix this or do I need to re-install?[/COLOR]

Would appriciate help for any of the questions.
Thanks.

---

### Post by taurus on 2006-12-31
Boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by M_the_C on 2006-12-31
> **taurus said:**
> Boot into recovery mode from GRUB menu and reconfigure your X again with

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

Thanks.
1 problem solved.  Now can anyone answer the others?

---

### Post by taurus on 2006-12-31
Are you talking about the problem with the Intel driver for your onboard graphic card?

---

### Post by M_the_C on 2006-12-31
I'm trying to play DVDs.

When I start playing one it jumps and stutters.  There is a blue line around the mouse and when I move the window around it leaves a blue background until it settles.  I looked into this and found some threads saying this is probably a problem with the driver.

So I tried installing the official Intel driver.  But I don't know how.  I converted the rpm into a deb and installed it.  I don't know from here how to set it up.  I've done the Nvidia driver on the main computer so I know how to edit the xorg.conf.  But I don't know what name to put in.

I tried reading the instructions from Intel, but it talked about setting up XFree86.

It is an old computer:

800Mhz
128MB RAM
Intel 82810e Built in Graphics

---

### Post by taurus on 2006-12-31
First of all, you don't have nVidia graphic card so you can't just install nVidia driver for your card.  It's not going to work.  

Now, look in /etc/X11/xorg.conf to see which "Driver" do you use!  I suspect it is "i810" in there...
Applications -> Accessories -> Terminal
```
cat /etc/X11/xorg.conf
```

Now, this could be the meat of your problem.  With 128MB of RAM and running Gnome, you are really pushing your system to a limit there!  With that amount of RAM, you are probably better off running Xubuntu!!!

---

### Post by M_the_C on 2006-12-31
> **taurus said:**
> 
Now, this could be the meat of your problem.  With 128MB of RAM and running Gnome, you are really pushing your system to a limit there!  With that amount of RAM, you are probably better off running Xubuntu!!!

Sorry I should have mentioned that I have installed Xubuntu on the old computer and was only using Nvidia as an example.

As for the driver, yes it is them i810 driver.  Would installing Intels driver solve this, or is the computer too old to be playing DVDs.  It does play them in WinME.  I was hoping it would in Xubuntu.

---

