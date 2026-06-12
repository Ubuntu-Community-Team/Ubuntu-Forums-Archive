---
title: "Getting GRUB back"
date: 2008-05-14
forum: General Help
---

### Post by 50words on 2008-05-14
I recently set up a new computer with one partition for Ubuntu, and one for OpenSUSE KDE. I installed Ubuntu first, then OpenSUSE. After installing OpenSUSE, I ended up with a different boot menu.

How do I get back to nice, simple GRUB, without reinstalling Ubuntu?

Will this be a recurring problem as I update OpenSUSE? Is there a way to stop OpenSUSE from installing/updating its own bootloader?

---

### Post by rubicon on 2008-05-14
What do you mean, "different menu"?

I guess /boot/grub/menu.lst is just been modified. Because I don't think the GRUB in Ubuntu and the one in SUSE radically differ.

---

### Post by 50words on 2008-05-14
I didn't realize they both used GRUB. It looks very different.

So I can expect the boot menu to change as each distro updates from its own repositories, then?

---

### Post by nick_h on 2008-05-14
You will have two versions of grub and two /boot/grub/menu.lst files.  The SUSE version will be active because it was the last one installed.  

To change the active grub, type:
```
sudo grub
```

Now select the filesystem containing the grub you want using the root command:
```
root (hd?,?)
```
(replace the ? with your drive and partition)

Next install grub to your MBR:
```
setup (hd0)
```

and then quit:
```
quit
```

References:
[How to restore Grub from a live Ubuntu cd.](http://ubuntuforums.org/showthread.php?t=224351) (no need to boot from a live cd in this case)
[Grub manual](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by meierfra. on 2008-05-14
Just reinstall grub to point to your ubuntu partition.

[URL="http://ubuntuforums.org/showthread.php?t=224351"]
http://ubuntuforums.org/showthread.php?t=224351[/URL]

You don't need to use a live cd. Same method works from Ubuntu or Suse.


But you will have to add Suse to your Ubuntu grub menu. From a ubuntu terminal:

```
gksudo gedit /boot/grub/menu.lst
```

Add this to the end of the file:


title Suse
configfile (hd0,2)/boot/grub/menu.lst

Here (hd0,2) needs to be replaced by the actual location  of your Suse partition. You can find the correct numbers by looking at the Suse menu.lst 


Now if you choose Suse at the Grub menu at boot up it will display the Suse Grub menu. To avoid this:

In a Suse terminal

```
su

kwrite /boot/grub/menu.lst
```

Change

timeout 10 

to 

timeout 3


and 


#hiddenmenu

to 

hiddenmenu

---

### Post by strabes on 2008-05-14
The GRUB link in my signature will help you reinstall grub.

---

