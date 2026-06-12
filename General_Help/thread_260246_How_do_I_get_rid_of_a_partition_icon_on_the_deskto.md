---
title: "How do I get rid of a partition icon on the desktop?"
date: 2006-09-18
forum: General Help
---

### Post by ThunderWhale on 2006-09-18
Hi, I'm very new to Linux.  I just installed it for the first time last week.  So far, I'm loving it!  But, there's this icon on my desktop that's driving me insane!  It's actually my Windows XP partition.  I'd like to know how to unmount it (is that right?)  and make it so it never goes on my desktop.  

Here's a picture :  [http://img359.imageshack.us/img359/1779/screenshotot5.png](http://img359.imageshack.us/img359/1779/screenshotot5.png)

Thanks a lot for help!

---

### Post by jd65pl on 2006-09-18
you could right click on it then click unmount to solve the issue now.

To stop it mounting next time you boot edit the file remove the entry
/etc/fstab

```
sudo gedit /etc/fstab 
```

Thanks

J

---

### Post by moma on 2006-09-18
1) Start the Terminal program (gnome-terminal) from the Applications -> Accessories menu.

2) Umount your Windows partition
$ [COLOR="Green"]sudo umount /dev/hda1[/COLOR]

3) Edit /etc/fstab and comment out the line that mounts /dev/hda1 (or what ever the NTFS or FAT drive is).
$ [COLOR="Green"]sudo gedit  /etc/fstab[/COLOR]
Look for a line that begins with /dev/hda1 and put a **#** in front of it.

---

### Post by blackened on 2006-09-18
The previous two posts show you how to unmount and keep the icon from showing on the desktop, but if you do this, then you won't have access to the windows partition. Mount it somewhere other than /media to keep it from showing on the desktop, Or use gconf-editor and go to apps-->nautilus-->desktop and deselect volumes_visible.

---

### Post by ThunderWhale on 2006-09-18
Thanks guys that worked, but now when I rebooted, I have this icon on my desktop called : "proc"  I tried the same steps to unmount it, but it wouldn't let me.  It said: "device in use"  I had no other operations running at the time.

---

### Post by ThunderWhale on 2006-09-18
Ah, nevermind.  I fixed that "proc" problem.  I figured out how to unmount it.  Is that a good idea though? To unmount it?  I don't really know if what was in there was important...

---

### Post by Average Joe on 2006-09-19
AFAIK you only see an icon on the desktop if something is mounted in /media. I changed my windows mount point in /etc/fstab to /windows. And I created a directory /windows of course. Now it doesn't show up as an icon on the desktop anymore. But it is still mounted, so I do have access to it.

---

