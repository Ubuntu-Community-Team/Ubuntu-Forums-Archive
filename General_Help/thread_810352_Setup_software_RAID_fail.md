---
title: "Setup software RAID fail"
date: 2008-05-28
forum: General Help
---

### Post by carfield on 2008-05-28
I was following this guide to try to setup software RAID but fail, after restart my computer cannot boot...

[http://translate.google.com/translate?u=http%3A%2F%2Fcha.homeip.net%2Fblog%2Farchives%2F2007%2F12%2Flinux_software.html&hl=en&ie=UTF8&sl=zh-CN&tl=en](http://translate.google.com/translate?u=http%3A%2F%2Fcha.homeip.net%2Fblog%2Farchives%2F2007%2F12%2Flinux_software.html&hl=en&ie=UTF8&sl=zh-CN&tl=en)

I am able to go to the GRUB menu, and the process is running, after checking HDD and CDROM information, the boot process halt...

I am using 64bit Desktop version of ubuntu... is this release miss something that require to setup software RAID? Or if this guide is outdated already?

---

### Post by whoismoses on 2008-06-13
Once the boot process halts, what does it say?  Does it say press Ctrl+D to continue?

---

### Post by carfield on 2008-06-14
Nothing... it just halt there, it doesn't say press Ctrl+D

---

### Post by DaDawn on 2008-06-14
can you boot into the system at all??

---

### Post by whoismoses on 2008-06-14
Here are the instructions I followed.  The author kind of missed two things.

[http://mywheel.net/blog/index.php/software-raid-in-ubuntu/](http://mywheel.net/blog/index.php/software-raid-in-ubuntu/)

The first thing is that you need to write the mdadm conf file in the /etc directory.

```
mdadm –detail –scan –verbose >> /etc/mdadm.conf
```

The second thing is that you need to make sure the md is loaded into your kernel.  If not you need to put it in your startup script for mdadm in your /etc/init.d directory.  I just put the following line after the variable declaration.

```
modprobe md
```

---

### Post by fjgaude on 2008-06-14
From my experience you don't have to have a mdadm.conf file. Of course you have to have a kernel that has md in it. All recent kernels do, at least for the last two years.

When you start up a new system, all I ever do is install mdadm and then do this:

```
sudo --assemble --scan
```

And that's it. A cutdown .conf file gets made automatically. Has worked for me through two motherboards changes and many kernel updates, upgrades.

---

### Post by whoismoses on 2008-06-14
I have the latest version of Ubuntu and for some reason I have to modprobe md to get thing working on startup...

---

### Post by fjgaude on 2008-06-14
> **whoismoses said:**
> I have the latest version of Ubuntu and for some reason I have to modprobe md to get thing working on startup...

Have you mounted your array in fstab?

Strange, I've never had to do what you do.

---

### Post by whoismoses on 2008-06-14
> **fjgaude said:**
> Have you mounted your array in fstab?

Strange, I've never had to do what you do.

Yes I mounted it in fstab.  Once I did that it tried to auto mount and failed.  I had to then press CTRL+D to boot.  Once I booted I had to do the modprobe and then manually mount.

---

### Post by carfield on 2008-06-15
> **whoismoses said:**
> Here are the instructions I followed.  The author kind of missed two things.

[http://mywheel.net/blog/index.php/software-raid-in-ubuntu/](http://mywheel.net/blog/index.php/software-raid-in-ubuntu/)

The first thing is that you need to write the mdadm conf file in the /etc directory.

```
mdadm –detail –scan –verbose >> /etc/mdadm.conf
```

The second thing is that you need to make sure the md is loaded into your kernel.  If not you need to put it in your startup script for mdadm in your /etc/init.d directory.  I just put the following line after the variable declaration.

```
modprobe md
```
I think this is the problem, because I haven't do this...

---

