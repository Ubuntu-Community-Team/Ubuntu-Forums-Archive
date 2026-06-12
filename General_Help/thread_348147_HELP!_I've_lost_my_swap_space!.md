---
title: "HELP! I've lost my swap space!"
date: 2007-01-28
forum: General Help
---

### Post by megamaced on 2007-01-28
Hi. I've lost my swap space. This is what happened:

1. Using Xubuntu Edgy Eft, I used the Hibernation feature.
2. Turned on my laptop later and got an error. Something like 'Swap signature invalid'. Or 'couldn't read signature'.
3. Got to the desktop and opened up GNOME system monitor. Noticed I had no swap!
4. Rebooted immediately, but still had no swap space
5. Went into Gparted and noticed the swap space was now unreadable and corrupt.
6. Decided to reformat the swap using Gparted.
7. Checked FSTAB for a swap entry, it reads:

```
UUID=5b89c5e7-e6e4-4156-8032-76b71c3cea1e none swap sw 0 0
```

8. I typed 'sudo mount -a', but it did nothing.
9. I rebooted, but still no swap!

How should I go about registering the swap space in Xubuntu? ATM I am SSH'ing into my machine for fear I run out of memory. LOL

---

### Post by taurus on 2007-01-28
Replace the UUID for your swap with the actual device like /dev/hda5 (or whatever it is).

```
/dev/hda5 none swap sw 0 0
```
Otherwise, post the output of this command.

```
sudo fdisk -l
```

---

### Post by hanzomon4 on 2007-01-28
My swap disappeared to, I went to gparted and clicked swapon in the properties-rtclick menu and it turned on. Anyone no why this happens

---

### Post by megamaced on 2007-01-28
I restarted in Recovery mode and like magic my swap came back! :D 

Strange

---

### Post by casaschi on 2007-01-28
If your swap file had changed UUID, you need to do few things to get it mounted properly and used properly by suspend/hibernate, full instruction here:
[http://ubuntuforums.org/showthread.php?t=287962](http://ubuntuforums.org/showthread.php?t=287962)

---

