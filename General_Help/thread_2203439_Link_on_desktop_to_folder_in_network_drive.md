---
title: "Link on desktop to folder in network drive"
date: 2014-02-03
forum: General Help
---

### Post by mmcl26554 on 2014-02-03
I have a network drive attached to a raspberryPi this seems to work well.   However, inside the drive is a folder (networkdrive) which contains all the folders and files I have stored there.   When I mount the drive from other linux computers on my network I can put a link to the mounted drive on the desktop but cannot make a link to the folder with the files I've stored.   No problem doing this on a windows machine.   When I try to do it with Ubuntu I get an error message "does not support a symbolic link".  Is there a way to do this with Ubuntu or is it not possible?
When posting answers please be aware of the fact I am a beginner.
Michael

---

### Post by ajgreeny on 2014-02-03
I'm not sure about nautilus, but using thunar, which you could install in any of the *ubuntu family, you can right click on a folder or file and choose "Send to Desktop (as link)" which I assume would work in unity, if that is the DE you use.

Worth trying? Or did I misunderstand the problem?

---

### Post by mmcl26554 on 2014-02-03
That's exactly what I was looking for, thanks for the help!
Michael

---

### Post by ajgreeny on 2014-02-04
Assuming that worked you could also have used the terminal to do the same with command ```
ln -s /path/to/source/foldername/ /path/to/destination/foldername/
```

---

### Post by mmcl26554 on 2014-02-04
When I use thunar it works but is very slow when I click on the icon on the desktop.   However, I have the data in a folder on the external usb drive connected to the Raspberry Pi I was thinking of moving the files to the root of the drive and eliminate the folder.   This might work better.
Michael

---

### Post by ajgreeny on 2014-02-05
There is no reason why a single folder would make any difference to the transfer speed.

Could it just be that your network speeds are slow for some reason, or perhaps the folder on the desktop is to a partition that is not mounted until you click on it.  Do you have a line  in /etc/fstab to mount the drive/partition at boot?

---

### Post by mmcl26554 on 2014-02-05
When I go to the folder directly through the already mounted network drive it is fast, if I click on the folder icon on the desk top it is slow, very slow to open up.   However, since there was no particular reason I had the data in a folder I moved it all to the root of the drive so now I have the mounted drive on the desktop and when I click on it there is the data and it's fast.   The folder with a duplicate of the files as I didn't want to delete them until the transfer was complete and valid.  So, I can still experiment with it if I want.   
Michael.

---

### Post by ajgreeny on 2014-02-05
Very strange why that should be so but that just shows how much there is that I don't know!

---

### Post by mmcl26554 on 2014-02-05
And I know even less, but I'm learning and trying to keep my 72 year old brain active!
Michael

---

