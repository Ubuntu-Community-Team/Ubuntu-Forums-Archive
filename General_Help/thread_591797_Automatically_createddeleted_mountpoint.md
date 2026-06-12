---
title: "Automatically created/deleted mountpoint"
date: 2007-10-25
forum: General Help
---

### Post by hrod beraht on 2007-10-25
When I insert a USB memory stick, a folder at **/media/memorystick** is automatically created.
When the memory stick is unmounted, that folder disappears.
That makes a lot of sense since if the folder isn't there it makes it pretty obvious that the memory stick is not mounted.

Is it possible to do a mount like that with a smbfs/cifs network folder? That is, where it only shows the folder when the network folder is actually mounted?

Bob

---

### Post by drs305 on 2007-10-25
I don't use automounting or fstab entries since the samba share is on another computer that isn't always on. I have two shortcuts on the panel. The share only shows up in the nautilus left pane when it is mounted. This is a windows share on a network with username and password.

For your purposes, the mount point I created is /media/test

To mount and display the samba share:
```
smbmount //192.168.0.XXX/maindirectory /media/test -o username=XXX,password=XXXX
```

To unmount:
```
smbumount /media/test
```

I had the share mounted in fstab but always had it displaying in nautilus whether it was mounted or not, so I no longer have it listed there. I have the two shortcuts on the ubuntu panel so it only takes a double click to open and display the share or to close it.

---

### Post by hrod beraht on 2007-10-26
> **drs305 said:**
> The share only shows up in the nautilus left pane when it is mounted. ...the mount point I created is /media/test

That seems to be a pretty workable solution.

Interestingly, if I mount something under /media in Fedora 7, it dos *not* automatically put it in the Places menu like Ubuntu does. Anyone know why and what the differences between the two are?

Bob

---

### Post by tweedledee on 2008-01-02
> **hrod beraht said:**
> That seems to be a pretty workable solution.

Interestingly, if I mount something under /media in Fedora 7, it dos *not* automatically put it in the Places menu like Ubuntu does. Anyone know why and what the differences between the two are?

Bob

I've posted a script to do exactly that, for an unlimited number of shares, here: [http://ubuntuforums.org/showthread.php?t=637258](http://ubuntuforums.org/showthread.php?t=637258)

I think the difference between Fedora and Ubuntu is just a difference in the default Nautilus settings, I believe (although am not certain without double-checking) that you can control this behavior in the Nautilus settings available through gconf-editor.

---

