---
title: "System Monitor - no File Systems tab ?"
date: 2016-10-23
forum: General Help
---

### Post by oygle on 2016-10-23
Apparently there is meant to be a *File Systems* tab in System Monitor.

[https://help.ubuntu.com/stable/ubuntu-help/disk-capacity.html](https://help.ubuntu.com/stable/ubuntu-help/disk-capacity.html)

Nope, not there.  :(

---

### Post by deadflowr on 2016-10-23
KDE, or GNOME?
gnome has it for it's system monitor tool (gnome-system-monitor)
kde doesn't for it's system monitor tool (ksysguard)
If in Kubuntu, you'd have ksysguard.

Ubuntu w/unity uses the gnome-system-monitor package.
File system tab is still there.

---

### Post by oygle on 2016-10-24
> **deadflowr said:**
> KDE, or GNOME?

KDE (Kubuntu).

There used to be a *Disk Usage Analyzer.*. It's not there now in 16.04.1 - I think it is called "Baobab" ?

Just needed a GUI display of where the disk total is being used. Reformatted an old Windows HDD today, so now have over 200 Gb there to help spread the load a bit.

Thanks  :)

---

### Post by fenrice on 2016-10-24
Why not just run baobab with "alt-f2" ? There is also k4dirstat that I use for the same purpose, I think it has more options for deleting files and such as well. ncdu is a good command line one too, but I think it has issues with btrfs if you are using that file system.

---

### Post by oygle on 2016-10-25
> **fenrice said:**
> Why not just run baobab with "alt-f2" ? There is also k4dirstat that I use for the same purpose, I think it has more options for deleting files and such as well. ncdu is a good command line one too, but I think it has issues with btrfs if you are using that file system.

Neither baobab or k4dirstat are installed by default in Kubuntu 16.04 Xenial Xerus. Just using "ext4" for filing systems. Will install baobab as all I need is to display folder sizes, and the ability to view down a tree structure.

---

### Post by oygle on 2016-10-25
Installed **baobab** and got this error msg

> 
Could not scan some of the folders contained in "/"

Error opening directory '/tmp/systemd-private-f8a1f05146a4481c8f3a916462b7ef92-systemd-timesyncd.service-1Suha4': Permission denied

...which of course didn't appear if I used

```
sudo baobab
```

---

### Post by mastablasta on 2016-10-25
if it's a gui app it should be kdesudo baobab.

what about using kdeutils package and then KDiskFree ?

---

### Post by oygle on 2016-10-25
> **mastablasta said:**
> if it's a gui app it should be kdesudo baobab.

okay thanks.  :)

> **mastablasta said:**
> what about using kdeutils package and then KDiskFree ?

Searched for kdeutils package in Synaptic, not found ? Looked at **KDiskFree** via Synaptic. It doesn't look as cluttered as **Baobab**, however is it able to open up a directory tree and view all the sub paths to see what each path contains, space wise ?  (see attached screen dump).
[ATTACH=CONFIG]271790[/ATTACH]

---

### Post by oygle on 2016-12-23
**KDiskFree** only shows the 2 devices mounted. It wouldn't expand folders at all. Not useful for me. :)

**Baobab** is okay though.

---

