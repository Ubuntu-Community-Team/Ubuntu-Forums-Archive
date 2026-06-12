---
title: "Cannot display this video mode?"
date: 2007-10-17
forum: General Help
---

### Post by mike868y on 2007-10-17
I have ubuntu running under ubuntu and when i start up i get a black screen with the words cannot display this video mode. after like a minute it goes to the login screen. Its not really a problem.. just annoying...Are there drivers or something i need to fix this?

---

### Post by Pumalite on 2007-10-17
Are you running from hard disk or Live CD?

---

### Post by dabl on 2007-10-17
> **mike868y said:**
> 

cannot display this video mode. after like a minute it goes to the login screen.

 

I think this message is coming from your monitor or LCD -- I think the driver is set to a refresh rate beyond the range that your monitor can handle.  So it is resetting itself within its range, and then proceeding to put up the login screen.

What is your graphics chip, and what are the refresh and sync ranges for your monitor?

---

### Post by mike868y on 2007-10-18
@pumalite   I guess i'm runnning it off the hard drive.. its installed under wubi

@dabl   my graphics card is an ati radeon x300.. at least i think so... and the refresh rate under the ubuntu screen resolution prefrences is 75hz. The monitor is a flat screen dell lcd

---

### Post by hanzomon4 on 2007-10-19
I got the same problem. I can't see the usplash during boot and it looks like the screen is adjusting, in fact I think it says that just before gdm pops up. This is a first for me, all my other ubuntu installs didn't have this problem. I have an nvidia Geforce Fx 5500 and a dell E153FP monitor, res is 1024x768 at a refresh rate of 60hz.

---

### Post by mike868y on 2007-10-20
anyone have an option?

---

### Post by petersjm on 2007-10-20
> **mike868y said:**
> anyone have an option?

I do :D

I just managed to fix this myself. Been bugging me since I installed Gutsy. It seems that Gutsy's usplash reads your screen size wrongly. In order to fix it, enter Terminal/Konsole and type:

```
sudo gedit /etc/usplash.conf
```

(Replace "gedit" with your editor of choice.) Now adjust the YRES and XYES values to your proper screen size values (i.e. 1024 x 768 etc). Save and close the file. Now, back in Terminal, you need to commit the changes to your boot memory so it works on reboot. Type this:

```
sudo update-initramfs -u
```

Let Terminal do it's thinking, then when you're back at the prompt, exit Terminal and reboot. Everything *should* be working fine now - at least that's what I did and it worked for me. I got the fix from somewhere else on these forums, but can't find it now. Thanks to whoever it was! :D

---

### Post by hanzomon4 on 2007-10-22
Dude you ******* kick ***!!!!! Just add a dash to that last command ```
sudo update[COLOR="Red"]**-**[/COLOR]initramfs -u
```

---

### Post by petersjm on 2007-10-23
> **hanzomon4 said:**
> Dude you ******* kick ***!!!!! Just add a dash to that last command ```
sudo update[COLOR="Red"]**-**[/COLOR]initramfs -u
```

Don't I? :D And yeah, I forgot the dash! Thanks for that.

---

### Post by NStoker on 2008-02-01
I have the same problem, except It stays in the black screen forever, before this happened it changed my video setting to costom. Could someoene please help me as I can't even get into the login screen?
Thanks!

---

### Post by mmxbass on 2008-02-02
I've had this problem ever since upgrading to my Geforce 8800 GTS from my old video card. Monitor was the same as before, etc. I always assumed that usplash just wasn't ready for my card yet.

Personally I would just edit the boot conf and turn usplash off entirely, it looks nice but it only serves to slow things down.

---

