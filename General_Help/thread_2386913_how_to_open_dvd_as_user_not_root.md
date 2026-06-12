---
title: "how to open dvd as user not root??"
date: 2018-03-12
forum: General Help
---

### Post by sdowney717 on 2018-03-12
I insert the DVD-RAM disk.
If it mounts, not always will it, it always mounts as root privileges.

I format the disc as udf
```
scott@scott-MS-7596:~$ mkudffs /dev/sr0 
filename=/dev/sr0
label=LinuxUDF
uuid=5aa55c8902060b39
blocksize=2048
blocks=2236704
udfrev=2.01
start=0, blocks=16, type=ERASE 
start=16, blocks=4, type=VRS 
start=20, blocks=76, type=ERASE 
start=96, blocks=16, type=MVDS 
start=112, blocks=16, type=ERASE 
start=128, blocks=4, type=LVID 
start=132, blocks=124, type=ERASE 
start=256, blocks=1, type=ANCHOR 
start=257, blocks=2236190, type=PSPACE 
start=2236447, blocks=1, type=ANCHOR 
start=2236448, blocks=96, type=ERASE 
start=2236544, blocks=16, type=RVDS 
start=2236560, blocks=143, type=ERASE 
start=2236703, blocks=1, type=ANCHOR 
```

Sometimes pmount will mount as root, sometimes as user.
I really would like to simply put in a formatted DVD, and it have it appear in file manager, mounted as ME, not root. Without having to use the terminal.
Just like windows, stick in DVD, it appears and you can write files onto it.

scott@scott-MS-7596:~$ pmount  /dev/sr0
scott@scott-MS-7596:~$

---

### Post by sdowney717 on 2018-03-12
I think I solved this.
I created a new folder as /media/cderom/
I changed permissions on that folder to 777

I put this into fstab

/dev/sr0 /media/cderom udf defaults,auto,user,ro 0 0


And now it opens the DVD disc as ME so I can write files onto the disk.


Question is, why did I have to modify the config to open DVD as me? Why were they opening as root? This is something weird going on? Do other people have DVD's mount as root user?

---

### Post by sdowney717 on 2018-03-12
Also why do I have to type in my user password to eject the disc in the tray?
Or in terminal I can eject with 
'sudo eject'

---

