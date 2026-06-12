---
title: "Quick bugs found after fresh install of Ubuntu 13.04"
date: 2013-04-26
forum: General Help
---

### Post by leon.vitanos on 2013-04-26
**^^found**

1. I don't want Ubuntu one. So i thought that if i Uninstall Ubuntu one, "Ubuntu one" indicator will be removed.. well it doesn't and after a restart i see this..
[IMG]http://i.imgur.com/cs82F2t.jpg[/IMG]

2. Online results are turned off and i still see them , peerfect

[IMG]http://i.imgur.com/hFJdFDx.jpg[/IMG]

3. I cannot suspend my computer. When i wake up pc from suspend it freezes and i am force to crash it....................

---

### Post by dino99 on 2013-04-26
open synaptic (install it if needed)
purge ubuntu-desktop (only a meta-package)
purge all the ubuntuone* packages

---

### Post by leon.vitanos on 2013-04-26
> **dino99 said:**
> open synaptic (install it if needed)
purge ubuntu-desktop (only a meta-package)
purge all the ubuntuone* packages

Thanks! First one fixed. 
The other 2 any idea what is happening?

---

### Post by dino99 on 2013-04-26
Just need to be a bit curious and tweak:
- System Settings
- unity-tweak-tools

and also glance at .xsession-errors & /var/log/dmesg mainly

---

### Post by leon.vitanos on 2013-04-26
> **dino99 said:**
> Just need to be a bit curious and tweak:
- System Settings
- unity-tweak-tools

and also glance at .xsession-errors & /var/log/dmesg mainly

I took another screenshot..
its system settings and unity tweak tool both saying online results are turned off.
you can see that in the filter->sources of my dash searching , the sources is set to all.. isn't it supposed to be disabled.?
[http://i.imgur.com/u61PNXG.png](http://i.imgur.com/u61PNXG.png)

---

### Post by JonPaul on 2013-04-26
> **LeonTastyDev said:**
> **^^found**

3. I cannot suspend my computer. When i wake up pc from suspend it freezes and i am force to crash it....................

hi Leon

I have this same problem and suspect it is a problem with this kernel - it worked fine on 13.04 alpha with the 3.5 kernel. 

What type of PC do you have. Mine is an HP G60. 

Spinnekop

---

### Post by JonPaul on 2013-04-26
on your second point I did sudo apt-get remove unity-lens-shopping

---

### Post by leftbas on 2013-04-26
I have the same problem with suspend and hibernate. I have an Asus Zenbook UX-31E. Just upgraded to Raring last night. Kinda frustrated. Edit: it worked beautifully in 12.04 and 12.10, but now they both act as if I wanted to lock the screen.

---

### Post by leftbas on 2013-04-26
Follow-up: Yup, it's the kernel, alright. I kept 3.5.0.27 after the update, and when I boot up to it, Raring will suspend and hibernate with no trouble. It seem that 3.8.0.19 is the culprit. I'm glad I didn't blow 3.5 away yet!

---

### Post by leon.vitanos on 2013-04-29
> **leftbas said:**
> Follow-up: Yup, it's the kernel, alright. I kept 3.5.0.27 after the update, and when I boot up to it, Raring will suspend and hibernate with no trouble. It seem that 3.8.0.19 is the culprit. I'm glad I didn't blow 3.5 away yet!

So how did you fixed it? Can you provide some links?

---

### Post by leftbas on 2013-05-02
I don't program, so I don't have a fix. However, I found a link to a page that shows how to make an older kernel boot by default in GRUB ([http://askubuntu.com/questions/216398/set-older-kernel-as-default-grub-entry](http://askubuntu.com/questions/216398/set-older-kernel-as-default-grub-entry)). I haven't tried it, because I keep hoping the Ubuntu devs will post a kernel patch and that will be that. So far no such luck, so I may just fool around with the grub configuration file.

---

### Post by leftbas on 2013-05-02
I also found an office bug report here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1175113](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1175113).

Anyone affected by this suspend/resume bug with the 3.8.0-19-generic kernel should click the link above, and then click 'does this bug affect you' link just below the title. The more people who identify with this bug, I believe it will be resolve faster.

---

