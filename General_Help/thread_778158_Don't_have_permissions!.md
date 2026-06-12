---
title: "Don't have permissions?!"
date: 2008-05-01
forum: General Help
---

### Post by Mecharuva on 2008-05-01
I updated to v8.04 Ubuntu just the other day, and all has gone fine (not mentioning the sound errors, freaking Creative...)
Except now, on the ONLY account I have set up here, I have no permissions to access "Home" and "Secondary"; not /home, but "Home" as in my primary Hard Drive, holding my Windows stuffs.  "Secondary" should be obvious.
Whenever I try to click on it from "Places" I get:
CANNOT MOUNT VOLUME.
You are not privileged to mount the volume 'Home'.
Hope that's enough info.

---

### Post by jcwmoore on 2008-05-01
I think you need to be a super user to do that.  you do this with the "sudo" command.  i think you need to press <ALT> + <F2> and type in "gksudo nautilus" enter your password and then you should be able to mount the other partitions.

or you can do it via command line ...

```
sudo mount /dev/sda#
```

the /dev/sda# should be replaced with the location of the partition you want to mount

---

### Post by Mecharuva on 2008-05-01
Okay that almost worked, now I get:
Cannot mount volume.
Unable to mount the volume 'Home'.
Details
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1':  Operation not supported
Mount is denied because NTFS is marked to be in use.
Choose one action:

Choice 1:  If you have Windows then disconnect the external
devices by
      clicking on the 'Safely Remove Hardware' icon in the
Windows
     taskbar then shutdown Windows cleanly.

Choice 2:  If you don't have windows (blah blah, I have Windows.)

I'm guessing it's because I tried to run a game, and Windows rebooted the PC, and I just went to Linux?
I bet that's it.

---

### Post by jcwmoore on 2008-05-01
> **Mecharuva said:**
> Okay that almost worked, now I get:
Cannot mount volume.
Unable to mount the volume 'Home'.
Details
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1':  Operation not supported
Mount is denied because NTFS is marked to be in use.
Choose one action:

Choice 1:  If you have Windows then disconnect the external
devices by
      clicking on the 'Safely Remove Hardware' icon in the
Windows
     taskbar then shutdown Windows cleanly.

Choice 2:  If you don't have windows (blah blah, I have Windows.)

I'm guessing it's because I tried to run a game, and Windows rebooted the PC, and I just went to Linux?
I bet that's it.

YES, you are correct.
i have seen this before, it is caused by an unsafe windows shutdown, reboot into windows and give it a "proper windows shutdown"...

---

### Post by Mortenib on 2008-05-02
I have a similar problem, but Windows has crashed, so I cant do the save shutdown:(

No I'm trying to find a way to "reset" the HDD. I'm running Ubuntu to do a backup of my files before formating and reinstall Windows. 

Anybody???

---

