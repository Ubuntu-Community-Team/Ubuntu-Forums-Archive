---
title: "Script not working on boot and stalling too?"
date: 2007-04-01
forum: General Help
---

### Post by Pichu0102 on 2007-04-01
I'm trying to get Jungledisk to run and davfs to mount it on boot, and I did the following things to do so:

Added this line to the startup programs in the sessions dialog under preferences

```
sh /home/pichu0102/jungle.sh
```

And this is the script I pieced together at that point:

```
#!/bin/sh
cd /home/pichu0102/jungledisk
./jungledisk
sleep 10
mount /media/netdrive
```

Now, I'm having two problems:
A. The script does not do anything once I log in like another script I set to work on boot
B. When I try to run the script manually by pressing alt+f2, it stops at this point:
```
./jungledisk
```
And it will not continue with the script until I close the aforementioned program, which generally renders it pointless. It runs okay when I use the terminal, but that leaves an open terminal, which I don't want to have open.
Any suggestions?

---

### Post by acormack on 2007-04-01
I think you would be better off asking over here:

[http://forum.jungledisk.com/viewtopic.php?t=173](http://forum.jungledisk.com/viewtopic.php?t=173)

---

### Post by ecor6633 on 2007-09-26
have you tried replacing :
./jungledisk
with :
./jungledisk &
or :
exec ./jungledisk &


I already read such thing in other sh scripts

---

