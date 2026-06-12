---
title: "URGENT: Black GDM can't login  (mouse only appearing)"
date: 2008-02-18
forum: General Help
---

### Post by josephdaniel on 2008-02-18
I have just been using my laptop running ubuntu 7.10 just normally. I had just uninstalled Anjuta IDE through synaptic by choosing the completely remove option. 

Right after Anjuta was removed successfully, I tried to open the Software Sources to add an unofficial repository but it didn't open. I tried opening Synaptic which didn't open either. So I resarted the computer, this time I had the gdm login screen didn't appear. Only a black screen with the white circle busy mouse pointer. 

After reading some posts, I tried the following commands in recovery mode

dpgk-reconfigure xserver-xorg

dpgk-reconfigure gdm

but nothing changed.

I tried installing wdm and icewm to gain access to the computer anyway, wdm can successfully log on to icewm but not a single program works (not even xterm). I tried using wdm to log on to gnome but it fails. After validating my username and password, I get a black screen for some seconds then I am prompted for my data again through wdm.

I've removed wdm and icewm. Now I am back without gdm working. Sorry if I am talking too much, but I really have some assignments to finish on my laptop and I am very frustrated. I can't afford setting everything again. Besides what I mentioned above nothing else has changed in ubuntu. It has been running well for over 2 months now.

Waiting for help ASAP,
Thanks a lot.

---

### Post by strabes on 2008-02-18
> **josephdaniel said:**
> After reading some posts, I tried the following commands in recovery mode

dpgk-reconfigure xserver-xorg

dpgk-reconfigure gdm

but nothing changed.

Those commands should be:```
sudo **dpkg**-reconfigure xserver-xorg
sudo **dpkg**-reconfigure gdm
```

---

### Post by josephdaniel on 2008-02-18
That's a typo. I wrote them correctly in the terminal and they worked but had no effect on my problem.

---

