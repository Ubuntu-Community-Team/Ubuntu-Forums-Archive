---
title: "[SOLVED] USB HDD breaks USB Mouse, bricks system."
date: 2007-10-28
forum: General Help
---

### Post by brownbat on 2007-10-28
*final update: memtest and further testing confirmed that all the troubles were likely caused by an old faulty memory stick.*

I have a 300 GB external HDD, formatted as . When I plug it in and begin to transfer files, the Copying files bar comes up, and the time remaining increases to a very large amount. Then three things happen:
a) my USB mouse stops responding
<time passes>
b) the copying files dialog stops changing
<time passes>
c) the serial keyboard stops responding.

When I reboot, the system is corrupted, and requires an fsck on my main (internal) drive before working properly again. (Maybe "bricks" is an exaggeration, but it refuses to boot into anything besides BusyBox or the LiveCD.) *More info [here]("http://ubuntuforums.org/showthread.php?t=594338")*.

How would I go about diagnosing such a problem?

Thanks for any help you can provide,
Thomas

---

### Post by mahousaru on 2007-10-28
Ouchies sounds like an issue I had with my Asus A7N8X mobo.  There was an issue between the timing of the nforce 2 USB controller and certain USB storage chips.  I got the same type of symptoms where my system would start slugging, my other USB devices would start playing up and copying files over a certain size would end up corrupt.

To fix my problem I basically got a new USB card and disabled my onboard ones so no one accidently used them.  

Check forums for your mobo to see if anyone has reported these types of errors.

I would do a memtest just incase, but tbh it doesn't sound like that is causing the problem.

Since it is a 300GB HDD I'm guessing it is externally powered so it shouldn't be a power issue.

---

### Post by brownbat on 2007-10-28
The second time I crashed the system by copying files, no BusyBox, just straight to Grub Error 17.

Forgot what Ubuntu was calling my partition for a minute, couldn't remember where I should point fsck.  

Rebooting after that second fsck, and the Ubuntu splash screen / loading bar just hangs indefinitely, while the keyboard steadily blinks its Caps Lock and Scroll Lock indicators as if begging for help.

Now I'm running sudo lshw from the LiveCD to determine my mobo. I also have a PCI to USBx4 that might be causing the trouble. It'd be pretty depressing if I was knocked back to two USB ports.

I'm on an ASUS A7V266-E, I'll see what I can find on the forums.

(I did just buy two new sticks of RAM a couple weeks back, maybe I'll run a memtest while I'm searching.)

I'll post with more info when I have it.

---

### Post by brownbat on 2007-10-28
From booting into recovery mode, I get:
```

kjounrald starting. Commit intervale 5 seconds
EXT3-sf: mounted filesystem with ordered data mode.
Begin: running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.
run-init: /sbin/init: No such file or directory
Kernel panic - not syncing: Attempted to kill init!

```

---

### Post by brownbat on 2007-10-28
Btw - If you're running memtest, be sure to bring a book. Just took me 10 minutes to get through 1% of tests. I'll post again in 17 hours when the tests are complete.

---

### Post by brownbat on 2007-10-28
We had a memtest error!

I'm testing the sticks individually now, and on the first one, it's going much faster. From 10+ minutes for the first % down to 44 seconds. I'm reassurred this won't take an entire week to fix.

It's possible I had a USB problem too... guess we'll see.

*Update: new sticks I purchased tested fine individually. Maybe it's one of my slots?*

---

### Post by brownbat on 2007-10-28
My oldest stick of RAM was causing the errors. Straight to the trash.

Now when I reboot, I get :
```

run-init: /sbin/init: No such file or directory
Kernel panic - not syncing: Attempted to kill init!

```

fsck and parted show a clean drive. Not sure what to do now. Is there a way to restore /sbin/init without a whole reinstall?

---

### Post by brownbat on 2007-10-28
Moved to the narrower question to [a new thread](http://ubuntuforums.org/showthread.php?t=595421), putting this one on hold for now.

---

