---
title: "Slow fsck and Resource Usage"
date: 2014-07-16
forum: General Help
---

### Post by Joshua on 2014-07-16
Trying to run fsck.ext4 on an external storage device with a 2TB partition.  The command works for several hours and them seems to fail.  Unfortunately, it is a little hard to tell exactly what is failing since I only have remote access right now (SSH) and sometimes the connection is interrupted before we get an error.  When I monitor the process with TOP it shows it with very low CPU usage, 0.0% - 0.3%, and sort of high memory usage, pegged at 60.6%.

Can anyone help me diagnose why the check won't finish or why it's taking so long?

---

### Post by Joshua on 2014-07-16
I've been doing more research on this and realized I might need to add some detail to get useful answers (and not waste anyone's time).

- This is on a minimal server system with 12.04 that is used to do backups using rsync.  So I only have command line tools.
- The disk in question is an external drive we used to store the backups and it started reporting errors a while back.  We suspected it was an issue with frequent power outages so we're trying to run the file system check to fix errors that were introduced.
- fsck was finding and fixing errors until it stopped.  So we've been running it repeatedly trying to get further and further through the file system check, but now it seems hung up - which is why I started looking at CPU and memory usage.
- Regardless, it seems like it shouldn't take over 5 hours to complete.  Top is currently reporting

```
Mem:   1024872k total,   886656k used,   138216k free,   181156k buffers
Swap:  1046524k total,    13092k used,  1033432k free,    18028k cached
```

and for CPU I have:

```
$ lscpu
Architecture:          i686
CPU op-mode(s):        32-bit
Byte Order:            Little Endian
CPU(s):                1
On-line CPU(s) list:   0
Thread(s) per core:    1
Core(s) per socket:    1
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 13
Stepping:              8
CPU MHz:               798.000
BogoMIPS:              1595.89
```

---

### Post by oldfred on 2014-07-16
The commands I use and suggest are this, but not sure how SSH into your system may change it?
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

I think the -v option has it show verbose output which may or may not be an advantage. 
See man e2fsck

Any abnormal shutdown especially if writing will corrupt any file system. If important server better to have battery backup.

---

### Post by Joshua on 2014-07-16
Thanks for the input.

I'm using (with the correct device location):

```
$ sudo fsck.ext4 -vy /dev/sd*xy*
```

If I read your suggestion properly, the options for e2fsck would be:

-C0 to output a progress bar
-p to automatically fix problems that don't require intervention
-f to force a check even if it doesn't look like the system needs a check
-v for verbose outpout

I'll try the e2fsck instead with the "y" option as well, but I don't see why it should be much different than what I tried.  isn't fsck just a front end for all the filesystem specific tools?
Would things like the "y" or "C0" option cause issues with system resources?

---

### Post by oldfred on 2014-07-16
It may be the same.

The only info that I see on e2fsck is that it will force a filecheck even if the ext4 system says it is not needed. 

With ext4 fsck now runs real fast as it relies somehow on filesystem to report an error and if no errors it then does not have to do anything.

---

### Post by Joshua on 2014-07-16
Well, I tried using:

```
$ sudo e2fsck -C0 -f -v -y /dev/sdb1
```

and it doesn't seem to have sped anything up.

It's on Pass 1 (at about 11%) and the CPU and memory are around 2-3% and 50.8%.  Seems like it should be moving faster, but I'll need to wait for a while to really tell if it's exibiting the same behavior.

---

### Post by Joshua on 2014-07-17
There deffinitely hasn't been any change.  It's been running since my last post, but top says it's only used about 4 hours of CPU time.  RAM use is pegged at 60.6% and CPU use pops to 0.3% every several seconds.

Maybe there is a better way to handle this?

---

### Post by oldfred on 2014-07-17
You posted that swap seems to have some use? It that is the case then that would be why it is so slow.

---

