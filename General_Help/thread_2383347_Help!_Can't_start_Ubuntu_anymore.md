---
title: "Help! Can't start Ubuntu anymore"
date: 2018-01-23
forum: General Help
---

### Post by michaelibre on 2018-01-23
Hi everyone,

At starting the computer I get this message:
(it is a picture made with my phone hosted on a image storage page as I didn't find the way to upload a picture on the forum in the phone format of the forum) :
[https://ibb.co/e1y16w](https://ibb.co/e1y16w)

I started the computer with a live USB and could access normally to the hard drive... 

Thank you for your help

---

### Post by Bashing-om on 2018-01-23
michaelibre; Hey :

To run that file system repair:

oldfred says ->
```

sudo fdisk -lu ## to know for sure that sda1 is your target
#From liveUSB so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see: man e2fsck
sudo e2fsck -f -y -v /dev/sda1
fsck http://www.thegeekstuff.com/2012/08/fsck-command-examples/

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by michaelibre on 2018-01-24
It worked, thank you. Please explain me how this can happen? I didn't do anything special. What does this kind of problem mean? Without a life USB at hand, I would have been doomed!

---

### Post by Bashing-om on 2018-01-24
michaelibre; Welp;

Glad fsck resolved the issue.
> 
 Please explain me how this can happen? 


Lots of things can get the file system's tail in a knot .
Ranges anywhere from powering the system down before any caches are written back to disk ( not supposed to happen - system is good about cleaning up prior to shutting down), a glitch in the sata controller or disk controller, a sudden loss of power - hard drive failure ; cable connections, bad cable, weak power supply  ... and the list can go on and on ......

If it happens again we be looking at the SMART status of the hard drive(s)

It's all ones and zeros
[INDENT][INDENT]but, they gotta be in the right place at the right time[/INDENT][/INDENT]

---

