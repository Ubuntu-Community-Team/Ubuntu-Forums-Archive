---
title: "Cannot login?"
date: 2006-12-11
forum: General Help
---

### Post by Daneeka on 2006-12-11
I'm really sorry to post two help threads so quickly, but since I restarted my machine, I can no longer sign in.

I type my user and pass, and it accepts, but then nothing loads, the monitor 'clicks' and then it just goes back to the login screen.

No settings have changed since my last login... I can't figure it out. Any ideas?

Thanks again.

---

### Post by taurus on 2006-12-11
At the GUI login screen, press <Ctrl><Alt>F2 and log in.  Paste the output of this command here!

```
ls -la ~/.dmrc
```

---

### Post by Daneeka on 2006-12-11
```
-rw------- 1 tom tom 26 2006-12-12 11:29 /home/tom/.dmrc
```

Is that right?

(I'm on a different computer, so I couldn't copy and paste)

---

### Post by taurus on 2006-12-11
That's right although some people have it as 

```
-rw--rw--rw
```
Did you install anything, like a driver, for your graphic card?

---

### Post by Daneeka on 2006-12-11
The only things I installed were the updates that pop up in the top right hand corner.

I haven't changed anything else.

I didn't manage to mount my hdd before I restarted, because the 'disk' option isn't in my system menu for some reason.
I'm not sure if that would have anything to do with it, thuogh.

---

### Post by Daneeka on 2006-12-11
Weird... I restarted and logged in and it worked just fine!?!

Thanks for you help, Taurus.
Now, if I can just figure out how to mount this hdd, and figure out why 'disk' isn't in my system menu...

THANKS!

---

### Post by taurus on 2006-12-11
Paste the output of this command here and I will walk you through mounting it.

```
sudo fdisk -l
```
(Tell me which one you want to mount...)

---

### Post by Daneeka on 2006-12-11
I type that in 'terminal', yes?

It just moves to the next line, and has a '>'.
There isn't anything else there... :-k

---

### Post by taurus on 2006-12-11
Yes, you type that command in a terminal, Applications -> Accessories -> Terminal.  Remember the last one is a letter l as in larry, not the pipe thing on your keyboard...

---

### Post by Daneeka on 2006-12-11
```
Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       24133   193848291   83  Linux
/dev/hdb2           24134       24321     1510110    5  Extended
/dev/hdb5           24134       24321     1510078+  82  Linux swap / Solaris
```

That's what it comes up with. :)
I'm not sure what is what... I'd like to mount the 200gb drive, though... whichever that is!

---

### Post by taurus on 2006-12-11
Sorry but your /dev/hdb is already mounted because Ubuntu is using it (/dev/hdb1 for / and /dev/hdb5 for swap)!!!  This command from a terminal will tell you so...

```
df -h
```

---

### Post by Daneeka on 2006-12-11
Well, I guess that makes sense... hah.

Umm, do you know how I can see how much space is left on the drive?
Thanks again, so much!

Very helpful.

---

### Post by taurus on 2006-12-11
```
df -h
```

---

