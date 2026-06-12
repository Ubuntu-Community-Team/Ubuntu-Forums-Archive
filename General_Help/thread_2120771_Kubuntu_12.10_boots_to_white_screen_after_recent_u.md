---
title: "Kubuntu 12.10 boots to white screen after recent update"
date: 2013-02-27
forum: General Help
---

### Post by djpemberton on 2013-02-27
Today I updated my system after a while away (moving). It wasn't able to do all the updates for some reason (can't remember the error message). so, i tried to restar. Now when I turn the system on it boots to a white screen. I have tried to fix it by booting into recovery mode in order to try running the remaining updates, but to no avail. It doesn't ever get me to a prompt when I choose the network option.

Please help quickly.

---

### Post by dabl on 2013-02-27
With such sparse information, I see no alternative but to boot a live CD and from there, mount your root partition, chroot in, and try to clear the dpkg problem and update it.  If you can do that, it probably will resume booting correctly.

[**[color=green]How to chroot[/color]**](https://help.ubuntu.com/community/BasicChroot)

Once you are chrooted in, do these things:

```
sudo apt-get clean
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

If you get errors, capture them and post back if it's not clear what you need to do.  If you can finish the dist-upgrade, then exit the chroot and your system should boot again.

---

### Post by djpemberton on 2013-02-27
Thanks,

I have already started the iso download. For some reason, I had disposed of my previous live cd. The connection is slow, so it will take a while, but I'll let you know how it works.

---

### Post by dabl on 2013-02-27
Any Linux live CD would work -- it doesn't have to be a *buntu, and it doesn't have to be a current version.

Although, according to the weather reports, you have nothing better to do, today, anyway.

;-)

---

### Post by djpemberton on 2013-02-27
The chroot guide is Greek to me. I don't really know what it is supposed to do. I may have to just reinstall the os. I'll just have to figure out how to at least backup my pictures and virtual box running windows first. love Linux, but it is sometimes a major pain -- usually at the worst time.

---

### Post by djpemberton on 2013-02-27
Oh yes, and my home dir is encrypted

---

### Post by djpemberton on 2013-02-27
Which part of the instructions on the chroot guide do I follow?

---

### Post by djpemberton on 2013-02-27
Well, I have looked at the chroot guide in your post. I have googled it and looked at some other related items. I am now more confused about what "chroot" does than ever.

---

### Post by djpemberton on 2013-02-27
I have attached a picture of when I try to get in using a recovery mode. When I select "enable networking" I get the result in the picture. It just hangs there and I don't know how to get out of it.

---

### Post by djpemberton on 2013-02-28
OK, I was able to get back in with a combination of your advice and some from elsewhere. Everything is basically in working order after the update. However, it did change my login screen to a horrible background, with nothing looking pretty. Once I get logged in, everything seems to look the same, except for notifications and some menus, which are transparent in some place when they shouldn't be.

---

### Post by dabl on 2013-02-28
Sorry I didn't get back to this one earlier.  The screenshot shows it hanging on fsck, which is not unheard of, depending on the nature of the problem.  I keep a bootable Parted Magic Live USB stick for such occasions -- if you fsck it that way, then *buntu will be happy to proceed with the boot, and then you can fix whatever is the problem.  So now it is booting and letting you log in?  If the only remaining issue is the appearance of the KDM greeter, that is controlled by System Settings > Login Screen.

---

### Post by djpemberton on 2013-03-01
There's more than that. My notifications and some menus aren't looking right either. Also, open programs aren't being shown on my taskbar anymore, though the settings are correct.

---

### Post by dabl on 2013-03-01
So the boot seems smooth, no errors?  Take a look at dmesg and make sure there are no hardware issues remaining.  If it all looks good, then I would advise re-naming the folder ~/.kde/share/config to ~/.kde/share/config_bak, and then rebooting.  A new default KDE desktop and panel will be available, and you'll have to re-do any custom configurations that you had.

---

