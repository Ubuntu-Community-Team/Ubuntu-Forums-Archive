---
title: "Stop opening external HDD folders on startup"
date: 2015-06-21
forum: General Help
---

### Post by eddie26 on 2015-06-21
Hi all,

I have an Orico multiple HDD dock attached through USB to a Intel NUC running Ubuntu 14.1.

On startup, it opens every HDD, requiring me to close each of them.  This gets annoying eventually.

Is it possible to fix this?

Any advice will be greatly appreciated.

---

### Post by Bucky Ball on 2015-06-21
Only plug the dock in when it's required rather than having it permanently plugged in? If not being used, a waste of electricity and resources anyway. 

Do you have the drives in the dock set to mount at boot in the /etc/fstab file? Perhaps show us a copy of that.

```
nano /etc/fstab
```

Post that file here, please, between code tags (see last link in my signature). :)

Or do you mean it opens a file manager window for every partition on every drive, not that the drives are auto-mounted at boot?

---

### Post by eddie26 on 2015-06-27
Thanks for your reply, Bucky Ball.

What I meant is that it opens a file manager window for every partition on every drive.  I use that computer as an HTPC running Kodi, with all media stored on those hard drives, so I do want it to mount all of them on startup (perhaps not the 1 GB extra partitions which were created out of nowhere).  I just don't like having to close 6 file manager windows every time I turn it on.  I'll be able to post the file tomorrow.

---

### Post by matt_symes on 2015-06-27
Hi

What desktop environment are you running under Kodi ?

In Xubuntu you need to disable 'browse removable media when inserted' from Advanced->Volume management in the properties menu entry in Thunar, but what you will need to do will depend on what desktop environment you are using.

Kind regards

---

### Post by eddie26 on 2015-06-28
Here is the fstab file: 

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=3c36fc91-2489-4b40-a7ba-8a3c1880b1a4 /               ext4    errors=remoun$
# swap was on /dev/sda5 during installation
UUID=3b8a5a8a-1502-44ed-bbd2-9a3dcfcf5aa8 none            swap    sw           $
```

I'm running regular ubuntu (not xubuntu) with Kodi installed normally.

---

### Post by Skaperen on 2015-06-28
in **System Settings>System/Details>Removable Media** what settings does it show?

---

### Post by matt_symes on 2015-06-28
Hi

it sounds like it may be a Nautilus setting.

I don't currently have Ubuntu installed on any machine but I will install it in a VM and look for you if you don't find success.

I think the last poster is on the right track though so work with him.

Kind regards

---

### Post by coffeecat on 2015-06-28
> **eddie26 said:**
> I'm running regular ubuntu (not xubuntu) with Kodi installed normally.

Having no experience of Kodi, I don't know how that works, but if you are running the Ubuntu Unity desktop, this askubuntu page should help:

[http://askubuntu.com/questions/191527/disable-auto-opening-nautilus-window-after-auto-mount](http://askubuntu.com/questions/191527/disable-auto-opening-nautilus-window-after-auto-mount)

If you use the dconf-editor option, and untick automount-open, be mindful of this warning which is in description for that dconf entry:

> If set to true, then Nautilus will automatically open a folder when media is automounted. This only applies to media where no known x-content/* type was detected; for media where a known x-content type is detected, the user configurable action will be taken instead.

I think that means that things such as media with photos, or CDs will still open a window unless you change the configurations in System Settings -> Details -> Removable Media.

---

### Post by matt_symes on 2015-06-28
Hi

That sounds like just the ticket coffeecat.

BTW Kodi is the new name for what was XBMC.

I used to run it running over X windows with no desktop environment on Arch but now run it on one of my Raspberry PI instead.

Kind regards

---

### Post by eddie26 on 2015-07-05
> **coffeecat said:**
> Having no experience of Kodi, I don't know how that works, but if you are running the Ubuntu Unity desktop, this askubuntu page should help:

[http://askubuntu.com/questions/191527/disable-auto-opening-nautilus-window-after-auto-mount](http://askubuntu.com/questions/191527/disable-auto-opening-nautilus-window-after-auto-mount)

If you use the dconf-editor option, and untick automount-open, be mindful of this warning which is in description for that dconf entry:



I think that means that things such as media with photos, or CDs will still open a window unless you change the configurations in System Settings -> Details -> Removable Media.

This worked.  Thank you :D

Thanks to everyone else who responded as well.

---

### Post by Bucky Ball on 2015-07-05
Good news. Please mark thread as solved. See second link in my signature. :)

---

