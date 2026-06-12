---
title: "software update thinks I'm out of disk space"
date: 2014-06-26
forum: General Help
---

### Post by Apollo8 on 2014-06-26
When I ran a software update this evening, I got the following:

[B]The upgrade needs a total of 92.8 M free space on disk '/boot'. Please free at least an additional 5,809 k of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.
[/B]
There was nothing in the trash. I ran sudo apt-get clean. I rebooted several times. The system wont update. There are 105 free GB on the SSD. I am not out of disk space. What is wrong with this thing? I am running 14.04 64 bit.

---

### Post by Bashing-om on 2014-06-26
Apollo8; Hello.

Often times it is not "disk space" rather "/directory" space that the package manager is referring to. Like here most likely /boot.
In release 14.04  the developers have been hard at work and have implemented the ability of apt-get to remove old kernels.
What results from terminal command:
```

sudo apt-get autoremove

```

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-06-27
You may have room on the SSD but not the OS partition (or the /boot partition, if you have one).

Open Synpatics or Software Centre and do a search for 'linux image'. Open a terminal and run this:

uname -r

That will tell you the kernel you are using. Now, remove all other images that aren't that that you've found with SC or Synaptics. Good idea to keep the kernel just before the one you're using (and naturally, the one you're using!) and kill the rest. 

Once done, reboot and try the update again. ;)

---

### Post by Apollo8 on 2014-06-27
Tried your suggestion. Didn't do anything. Software update still gives the same message.

---

### Post by Apollo8 on 2014-06-27
uname -r returns this: 3.13.0-29-generic


When I search for linux image in the software it displays all kinds of apps for sale.

---

### Post by oldfred on 2014-06-27
Did you empty trash?

Removing kernels should have made space.

Post this:
sudo parted -l
df -h

While server type installs with RAID or LVM may need a separate /boot partition, most desktops do not and then you have all the space in / (root) to share with all types of updates.

---

### Post by deadflowr on 2014-06-27
The easiest way to remove install packages via synaptic is to first click on the option Status, then Installed in the left side pane.
Then run a search for linux-image.
Make a note of the image currently in use.
look at any others not that one and right-click and select remove completely.
(The package linux-image-generic, is almost always the current kernel in use, so keep that)
Then when all are selected, click on apply, and begin the removal.

As well, I also remove the linux-headers packages, in the same way.
But that is optional at this point, since they aren't in the boot directory.

Anyway, my two cents...

---

### Post by Apollo8 on 2014-06-27
This fixed it:

  	 	 	 	   ```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
```

---

### Post by Bucky Ball on 2014-06-28
Please mark thread as solved thanks. 

I have added [code] tags to your last post. Please use them instead of bold for you terminal output. Click 'Edit Post' to see the syntax. Thanks.

---

### Post by erikthedrink on 2014-09-04
Thanks much, worked!

---

