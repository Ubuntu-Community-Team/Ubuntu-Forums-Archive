---
title: "Ubuntu will not load!"
date: 2008-04-13
forum: General Help
---

### Post by ZeroFive1 on 2008-04-13
So today I installed a evga 8800 gts with around 320 mb of video ram. It works great and runs great, on windows.

But, if I log into ubuntu, the top third of the screen turns light gray, then goes black.

In recovery mode, first it cannot mount hda2 (my windows partition), then it cannot load gnome or any gtk thing, for that matter.

If I boot the the liveCD, same dealio, will not show anything. On the 64 bit it goes straight to black, on the 32bit it loads then goes to black, but not before making some beeping noise.

I also installed 2 gigs of ram and a new power source.

Any help?

Thank you. I would hate to have to uninstall ubuntu.

---

### Post by warp99 on 2008-04-14
Did you configure the drivers to the new video card **before** you installed the card?

Edit:
Can you boot to a command prompt in recovery mode?

---

### Post by ZeroFive1 on 2008-04-14
No.

And yes, I can go into terminal.

I will try to see if other linux liveCDs and the Hardy Beta will yield something.

---

### Post by warp99 on 2008-04-14
Well you can load the new drivers from the terminal and restore your settings. Boot into recovery mode then issue the following:

```
apt-get install --reinstall linux-restricted-modules-$(uname -r) nvidia-glx-new
```
once those are installed issue the following:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
choose nvidia as your driver. When completed issue a 'sudo reboot'

if that does not repair the problem it may be specific to this thread and post:

[http://ubuntuforums.org/showthread.php?p=4125964#post4125964](http://ubuntuforums.org/showthread.php?p=4125964#post4125964)

---

### Post by ZeroFive1 on 2008-04-15
Ok, thanks a lot, now it works, but only in recovery mode.

In normal, same deal, I get the grey. I'm suspicious it's the splash screen. How do I disable it?

---

### Post by warp99 on 2008-04-15
You can use the boot option vga= xxx or just remove the word 'splash' from you kernel line during boot:

[https://help.ubuntu.com/community/BootOptions?highlight=%28bootoptions%29](https://help.ubuntu.com/community/BootOptions?highlight=%28bootoptions%29)

At least with vga= xxx you get to keep your splash screen. 

Please mark the post as [Solved] when your done reading this. Thanks.

---

### Post by ZeroFive1 on 2008-04-16
It doesn't seem to work, but for now I'll use recovery mode.

Thanks!

Marked as solved.

---

