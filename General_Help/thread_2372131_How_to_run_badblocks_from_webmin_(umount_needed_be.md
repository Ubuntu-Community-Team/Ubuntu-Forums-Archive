---
title: "How to run badblocks from webmin (umount needed before execution)"
date: 2017-09-21
forum: General Help
---

### Post by madumi on 2017-09-21
I'm new to linux, so I'm just feeling my way around at the moment...

I have webmin installed & use it to access a NAS that has no screen/keyboard (it's tucked away in my garage), but I would like to check my hard drives intensively every now and then for errors (hence I figured badblocks would work).

I'm not sure if I should be executing through e2fsprogs, or chfs (not sure if/how that's an option)?

I wanted to save the output once badblocks finishes, so, for a non-system hard drive sdc mounted at mountpoint_c, I figured I could put this in Webmin-->system-->scheduled commands:
```
sudo umount /mnt/mountpoint_c
sudo badblocks -nv -o /home/USER/badblocks_results_hddc.txt /dev/sdc 
```
I didn't know if the "scheduled commands" module should contain commands that included sudo, if the scheduled command was set to run as user: "root"

Thoughts? Is there a better way to do this? naturally, I couldn't use this code for a system drive...

---

### Post by madumi on 2017-09-23
Any hints on how to run badblocks from webmin?

When I check the file badblocks_results_hddc.txt from the code above, it looks like it was created too early to have executed fully... and the file is empty.

How could I run a command from webmin that will confirm that badblocks actually completed?

thanks!

---

### Post by dragonfly41 on 2017-09-23
I have webmin running on my localhost for development purposes.
 
 You have webmin running on your remote (garage) server.
 
 I tried running the badblocks command but received this ...
 
 > sudo: no tty present and no askpass program specified
 
 I have read that there is a work around by passing password through stdin.
 But that seems not too good an idea.
 
 > sudo -S ./binary

This directs sudo to read the password from the standard input, stdin.

Stepping back a bit could you not run instead ...

Webmin > Hardware > SMART Drive Status

You can edit module configuration and add extra smartctl commands.

---

### Post by efflandt on 2017-09-23
badblocks can check a "partition" for bad blocks, but /dev/sdc is not a partition, it is a drive. The first partition on that drive would be /dev/sdc1.

Hard drives reserve space to automatically remap good sectors in place of bad sectors regardless of OS. So normally you would not even see bad blocks until all of the error sites are used up, at which point you have a problem if the OS starts encountering bad blocks that it has trouble reading or writing to.

If you install **smartmontools** (or is already installed), I think **smartd** automatically periodically checks any drives that are active (not in standby or deeper sleep), and you can check drives specifically with **smartctl**, in which case you would check entire drives instead of partitions.

I have never used webmin. Whenever I managed web servers or web content, I would log in directly with ssh and use the terminal to do anything (typically FreeBSD, sometimes Linux, or NetBSD with shell account, or SunOS at my original ISP which is what got me into Linux to make developing CGI scripts easier than in Windows over 20 years ago when what later became Internet Explorer was Mosaic beta being developed by UIUC college students).

---

### Post by madumi on 2017-09-27
Thanks so much for input...

@efflandt
OK, so I gather from what you're saying that badblocks should be run on partitions instead of drives, correct? i.e. /dev/sdc1  Would it break functionality to run badblocks on /dev/sdc  ?

@dragonfly41
I'll look into the available configurations in Webmin > Hardware > SMART Drive Status... So far I've been using the System > scheduled commands portion of webmin, which seems to elevate the badblocks command sufficiently to execute it...

I've had bad experiences in the past relying solely on SMART... So my plan was to use badblocks as an additional layer of testing on top of the SMART extended tests (eg. 1) run SMART extended 2) run badblocks, 3) run SMART extended & check if bad block count changes)...
Any other suggestions for monitoring drive reliability?

---

### Post by cariboo on 2017-09-27
Using ssh to access your NAS is way less complicated than using webmin, you unmount /dev/sdc1 and then run badblocks from the command line. To see all the available options, type:

```
man badblocks
```

from the command prompt.

---

