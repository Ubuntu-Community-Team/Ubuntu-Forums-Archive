---
title: "Can't install the backported xorg to 12.04.2"
date: 2013-02-14
forum: General Help
---

### Post by marcjero on 2013-02-14
Hello,

I found that quantat xorg stack is available in updates. I was using the xorg edgers ppa until now because I needed an updated driver for my laptop (intel 915 chipset). So I decided to purge the xorg edgers ppa and then install kernel and xorg from quantal using the ubuntu updates repository.

I had no problem about the kernel but I'm struggling with the xorg stack. I tried to install xorg-xserver-lts-quantal package but ended with a broken X display. In fact ubuntu-desktop (and many other packages) is removed and I suppose this is my problem.

So I would like to know if there a special procedure to follow to switch to quantal xorg ? I'm interested to know if anyone installed the xorg backport fine ?

Thanks

---

### Post by marcjero on 2013-02-14
I solved the problem running this command after refreshing packages:
sudo apt-get install xserver-xorg-lts-quantal libgl1-mesa-glx-lts-quantal

But this uninstalled wine and playonlinux; Do you know a way to install them with quantal xorg ?

---

### Post by marcjero on 2013-02-14
Ok I think there is definately a mess between wine and the renamed xorg packages. I created a dummy wine package to be able to install playonlinux. Playonlinux can download wine runtime directly so it's a good workaround for me. Anyway I'm interested to know if anyone install wine with quantal xorg successfully.

---

### Post by mc4man on 2013-02-14
> **marcjero said:**
> Ok I think there is definately a mess between wine and the renamed xorg packages. I created a dummy wine package to be able to install playonlinux. Playonlinux can download wine runtime directly so it's a good workaround for me. Anyway I'm interested to know if anyone install wine with quantal xorg successfully., 

On a 32 bit install it should be fine, 64 bit is another story.

Managed to get it in but took a bit experimenting & editing some control files. Can't say it's worth the effort, (over an hour) & whether all correct.
screen 1 some of the lts including the i386 package highlighted
screen 2 wine, ect. (showing upgradeable because I repacked those 3 with altered control files

Wait till they square up 64 bit (when no idea

---

### Post by marcjero on 2013-02-15
Yes it's 64 bits version, forgot to mention that. Thanks I will wait for a fix then.

---

### Post by dino99 on 2013-02-15
Thats what i've reported:

[https://bugs.launchpad.net/ubuntu/+source/xorg-lts-quantal/+bug/1125413](https://bugs.launchpad.net/ubuntu/+source/xorg-lts-quantal/+bug/1125413)

note: subscribe (affect me too) if you are concerned.

---

### Post by mc4man on 2013-02-15
The 12.04.1 to 12.04.2 with lts X upgrade is possible but as seen you need to remove a **lot** of packages first then put most if not all back before logging out.

Did it the other day as a test, worked out ok (re-installing ubuntu-desktop was the final test that all was ok before logging out.

Can't imagine there is any intention for users to do this so we'll see how your report goes...

---

