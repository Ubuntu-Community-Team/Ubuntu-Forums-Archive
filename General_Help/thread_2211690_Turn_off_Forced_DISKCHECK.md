---
title: "Turn off Forced DISKCHECK?"
date: 2014-03-17
forum: General Help
---

### Post by frogotronic on 2014-03-17
Hi,

  Last week I turned on a forcediskcheck (after repartioning my drive using gPARTED Live CD) using:

```
sudo touch /forcefsck
sudo reboot
```

Now, everytime I reboot, the disk gets checked (nothing is found).  Is there a way to make it not check everytime, but go back to the normal interval?

---

### Post by ajgreeny on 2014-03-17
You should not have to turn off that forced-check; it should only run the next time you boot the system.

I wonder if using gparted on a partition has caused some filesystem eror which fsck is not managing to clear properly.  I presume you are not getting any other problems booting the system?

Let's see the output of ```
sudo tune2fs -l /dev/sda1 | grep -i mount && sudo tune2fs -l /dev/sda1 | grep -i state
```assuming sda1 is your root partition; change the command if it different for you.

---

### Post by frogotronic on 2014-03-17
Correct.  No other errors.  I have my home partition different from my boot (see attached png from gParted).[ATTACH=CONFIG]251237[/ATTACH]


```
$ sudo tune2fs -l /dev/sda1 | grep -i mount && sudo tune2fs -l /dev/sda1 | grep -i state

Last mounted on:          /
Default mount options:    user_xattr acl
Last mount time:          Mon Mar 17 09:38:31 2014
Mount count:              1
Maximum mount count:      -1
Filesystem state:         clean
```

---

### Post by ajgreeny on 2014-03-17
Nothing wrong there, so I am baffled.

See if there is still the file on your system called forcefsck that is not disappearing after the boot up as it should.

Update your file database first with **sudo updatedb** then run **locate forcefsck**

---

### Post by frogotronic on 2014-03-17
yep, it's there in the root -I'm going to nuke it

---

### Post by frogotronic on 2014-03-17
Yep, worked.  There's also a file called 0 - should I delete that as well?

---

### Post by ajgreeny on 2014-03-17
Great!

That's solved that then, or I hope it has.

I have no idea about the file called 0.  Was it made at the same time, as far as you can remember, and what is in it if you can open it.

By the way, I have my system set to check the filesystem every two months using **sudo tune2fs -1 2m /dev/sda2**

I realise you did the forcecheck following use of gparted, but for some reason which I can't fathom, the devs removed the default check every 30 boots, and did not replace it with anything else.  Maybe it's not needed these days; maybe I'm just a bit paranoid; but I feel much safer when I know the check will be done at regular intervals.  It only takes about 10 or 15 seconds on my new system, so why not?

---

### Post by frogotronic on 2014-03-17
Yeah, I agree - I think that there should be a regularly scheduled checkdisk

---

