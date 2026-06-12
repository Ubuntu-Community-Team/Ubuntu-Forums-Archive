---
title: "Someone please please help!"
date: 2008-02-25
forum: General Help
---

### Post by baudday on 2008-02-25
Basically, I had my graphics driver working fine, except for the fact that I couldn't get wow to run well on my computer. Then I followed [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide"), and it ended up messing everything up. I have a 1280 x 1024 screen, but the highest it'll go now is 800x600. I'm not sure what to do. On top of that, I have the restricted driver enabled, but it says it's not in use. When I try to uncheck the enable box, it says xorg.conf doesn't exist. I am able to edit xorg.conf however, but there's nothing in the file. I honestly have no idea what's going on, and it really sucks. I can get it back to 1280 x 1024, but then the color is all messed up. Help would greatly be appreciated, I'm writing this in Safe Graphics mode now. I have an ATI Radeon X850 graphics card.

---

### Post by taurus on 2008-02-25
Try reconfiguring your X server again with

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by baudday on 2008-02-25
```
willem@Tank:~$ dpkg-reconfigure -phigh xserver-xorg
/usr/sbin/dpkg-reconfigure must be run as root
willem@Tank:~$ shutdown -r now
shutdown: Need to be root
```

---

### Post by croto on 2008-02-25
```

sudo dpkg-reconfigure -phigh xserver-xorg
sudo shutdown -r now

```

---

### Post by baudday on 2008-02-26
no that didn't fix it

---

### Post by Crafty Kisses on 2008-02-26
> **baudday said:**
> no that didn't fix it

Here try this, this should work.
```
sudo -i
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by baudday on 2008-02-26
man i really wish that would've worked, but unfortunately the color is still off, and it's slow.

---

### Post by baudday on 2008-02-26
when i run these two commands it deletes my xorg.conf file

```
sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv
```

---

### Post by UK-Wobbie on 2008-02-26
> **baudday said:**
> Basically, I had my graphics driver working fine, except for the fact that I couldn't get wow to run well on my computer. Then I followed [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide"), and it ended up messing everything up. I have a 1280 x 1024 screen, but the highest it'll go now is 800x600. I'm not sure what to do. On top of that, I have the restricted driver enabled, but it says it's not in use. When I try to uncheck the enable box, it says xorg.conf doesn't exist. I am able to edit xorg.conf however, but there's nothing in the file. I honestly have no idea what's going on, and it really sucks. I can get it back to 1280 x 1024, but then the color is all messed up. Help would greatly be appreciated, I'm writing this in Safe Graphics mode now. I have an ATI Radeon X850 graphics card.

You can have a go using Envy!
It will yet you install your ATI Video card drivers.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
It may fix your Xserver!

---

