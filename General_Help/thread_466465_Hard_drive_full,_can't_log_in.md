---
title: "Hard drive full, can't log in"
date: 2007-06-06
forum: General Help
---

### Post by Hawke on 2007-06-06
My hard drive is full, and I cannot log on.  I get to the login screen, and enter my information, but it just puts me right back to the username prompt.  I read the suggestions that were posted under a previous thread about this, but they did not help.  I don't know any terminal commands or anything, so I would need a guide written for an incredible linux noobie.  I am running off the LiveCD right now.  I tried two suggestions I found elsewhere too, but they didn't work.
One was to open the terminal at the login screen and type in 'sudo apt-get clean'.  This seems to have done nothing, and I am still unable to log in.
I also tried:
1. Create a folder on the desktop in your LiveCD session called "temp"
2. Open a terminal window and type "sudo mount /dev/sda1 /home/ubuntu/Desktop/temp/"
3. Open the temp folder on your desktop and the files should appear in it
but when I did this, I get this error in the terminal after typing step 2:
mount:  special device /dev/sda1 does not exist

If someone could help me it would be greatly appreciated :D.  running off the LiveCD is very slow.

---

### Post by Bohlio on 2007-06-06
Are you 100% sure that the device is sda1? Once you get the hard drive mounted you can easily delete a few unnecessary things and then boot up normally and "Clean" out your system a little bit.

---

### Post by Hawke on 2007-06-06
I don't know what an 'sda1' device is.  I just copied that directly off the instructions.  Was I supposed to replace 'sda1' with something else?

I just want to know how to 'mount' this liveCD so I can go manually delete some stuff.

---

### Post by BrokeBody on 2007-06-06
> **Hawke said:**
> I don't know what an 'sda1' device is.  I just copied that directly off the instructions.  Was I supposed to replace 'sda1' with something else?


Well then, I need some more info about your system.

First, do you have any other operating system on your machine, such as Windows for instance?

---

### Post by Hawke on 2007-06-06
No, just Ubuntu 6.10.  

It's a Compaq Evo N410c, 20g HD.

---

### Post by BrokeBody on 2007-06-06
> **Hawke said:**
> No, just Ubuntu 6.10.  


Then try putting hda1 instead of sda1.

---

### Post by Bohlio on 2007-06-07
When you are running off the LiveCD, Type in the command ```
df -Th
``` When that pops up, you should see an entry that is ext3, and in the same line, there should be something that says "/dev/????" That is what you replace /dev/sda1 with and it should mount your partition.
Here is an Example of mine, As you can see, My ext3 partition is /dev/sda5.
```
chad@chad-desktop:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext3     19G  3.0G   15G  17% /
varrun       tmpfs    506M   96K  505M   1% /var/run
varlock      tmpfs    506M     0  506M   0% /var/lock
procbususb   usbfs    506M  128K  505M   1% /proc/bus/usb
udev         tmpfs    506M  128K  505M   1% /dev
devshm       tmpfs    506M   16K  506M   1% /dev/shm
lrm          tmpfs    506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile
/dev/sda2  fuseblk    125G   69G   57G  55% /media/windows

```

---

