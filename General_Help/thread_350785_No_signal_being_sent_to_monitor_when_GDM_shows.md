---
title: "No signal being sent to monitor when GDM shows"
date: 2007-02-01
forum: General Help
---

### Post by v8YKxgHe on 2007-02-01
Hey,

My PC was working fine last night, there were no updates I needed to do but when I came to turn my PC on this morning (after I shut it down last night) it would boot up fine and show the boot process, but as soon as it got to the GDM screen I just lost all signal to my monitor - I did however hear the default GDM Ubuntu sound, and if I type my username and password I can actually login.

What is also weird is if I press ctrl+alt+f3 for example, I just get a big ugly purple box instead of what I'm suppose to get (I've had this problem for a while now, but thought nothing of it since I never use them).

Why am I suddenly loosing all signal to my monitor?? The graphics card is fine as I'm typing this from my WinXP install on another hard drive. :confused: :confused:

---

### Post by bustanil on 2007-02-01
I can't say to much, as your problem is "weird". As trating point, why don't you check your screen refresh rate and resolution configuration at /etc/X11/xorg.conf file.

---

### Post by hikaricore on 2007-02-01
If all else fails boot in rescue mode and login.

Then backup your xorg.conf file:

```
sudo cp /etc/X11/xorg.conf /etc/X11.xorg.conf.backup
```

Then reconfigure your X server:

```
sudo dpkg-reconfigure xserver-xorg
```

Then go through the prompts step by step checking to make sure everything is set as it should be.  This may possibly restore your access to GDM / X.  You can test this after by either rebooting:

```
sudo reboot -t now
```

Or by typing:

```
sudo gdm
```

From the terminal.

Good luck,

--Aaron

---

### Post by v8YKxgHe on 2007-02-01
Thanks for the help guys, but I think I found the problem (though not solved it). I recently brought a KVM Switch and set it up last night, it all worked fine and had no problems with it. When I got home from college I took the monitor cable out of the KVM switch and back into the PC as normal and it worked fine (after a reboot, which was weird).

Also, do KVM switches _need_ power? There is a power connector socket thingy, but when I plugged the Keyboard and Mouse in it turned it's self on - I guess it's getting it's power the same as a mouse/keyboard would? But why is there a power connector on it? :confused:

---

### Post by kpatz on 2007-02-01
Make sure the KVM is switched so the monitor is connected to the Ubuntu box when GDM starts up.  That way monitor autodetection can occur.

---

