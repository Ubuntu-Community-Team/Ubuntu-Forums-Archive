---
title: "Automount NTFS partitions"
date: 2007-09-20
forum: General Help
---

### Post by vampire666eng on 2007-09-20
How to automatically boot one or more NTFS partitions (at start up) and that they are displayed on the desktop?
Is there an option I have to insert in the /etc/fstab file?

Is there a way to avoid to insert at every start up in the terminal the command: "sudo mount -a"

P.S. How to do the same with the Filesystem system (let it display on the desktop)?

Thanks.

---

### Post by luctor on 2007-09-20
install ntfs-3g
that took care of mount my windows ntfs drive on boot-up

---

### Post by ajgreeny on 2007-09-20
You need to add a line to your /etc/fstab file as root.
First back up your fstab with
gksudo cp /etc/fstab /etc/fstab.bak
Then edit the file with gksudo gedit /etc/fstab
and add the following line:-

/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

You may need to make sure you have the /media/windows folder first.  If not do
sudo mkdir /media/windows
in a terminal.

You also need to ensure your windows partition is hda1.  If not change that to the correct identification in the fstab added line.

---

### Post by vampire666eng on 2007-09-20
Thanks you both for the replies.
II have already ntfs-3g isntalled on ubuntu (heh...the automount partitions disappeared from my desktop after I installed it (also the Filesystem)...in fact I had them before that).

I have already changed my /etc/fstab. :(
Since I installed ntfs-3g, the fstab I have it's slighly different (changed acordinly):

```
UUID=E0ECE3E5ECE3B3C6 /media/hdb1     ntfs-3g     nls=utf8   0    1
```

Since I have ntfs-3g installed I use that entry in fstab (and not ntfs)....and the "umask=0222" I had to remove, because if I keep it in fstab I don't have the option to write on NTFS partitions (only read).

Thanks for your help guys. It's really appreciated.

---

### Post by vampire666eng on 2007-10-18
I installed ubuntu 7.10 and everything runs fine now. ;)

---

