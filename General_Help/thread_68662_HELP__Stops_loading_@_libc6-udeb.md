---
title: "HELP:  Stops loading @ libc6-udeb"
date: 2005-09-23
forum: General Help
---

### Post by khurdp on 2005-09-23
Hello,
  a colleague gave me a 5.04 Ubuntu CD (from Ubuntu) which I tried on my new Dell Dimension 3000 computer. I could select language country, keyboard type etc. After loading some modules, the load stops at libc6-udeb. This is what i see when i switch to 3rd virtual monitor
loading (i think) ...............ide/ide-generic.ko
...............................................ide/ide-floppy.ko
...............................................ide/ide-disk.ko
...............................................cdrom/cdrom.ko
...............................................ide/ide-cd.ko
...............................................isofs/isofs.ko

4th virtual monitor
last line is
................. anna [9593] : WARNING **: bad md5sum

  well i thought this might be a bad disk so I downloaded 5.10, burnt it to a CD-RW and tried again. Same thing - it stops at libc6-udeb, the 3rd virtual monitor is the same but the 4th monitor is slightly different this time:
................anna[11976]: WARNING **: bad md5sum.

The md5sum of the downloaded iso is correct. The drive seems to be fine - i was able to write data DVD+RW, mp3's on CD-RW, burn some other DVD/CD. The other thing is that the original(free from Ubuntu) 5.04 disk would load on my compaq presario 900 laptop without any problems. I haven't tried the 5.10 but i have a feeling it would load on my laptop too.

Please help.

Thank you,
Prasad

---

### Post by khurdp on 2006-01-04
Anybody with questions, suggestions or advice....

Please help,
Prasad

---

### Post by Klaser on 2006-01-18
I have the same problem on my amd 2600 no one seem to know the reason.

---

### Post by jhemono on 2006-02-04
Hello,
Here's a solution which seems to work : [http://ubuntuforums.org/showthread.php?t=82017](http://ubuntuforums.org/showthread.php?t=82017)
... But not with my computer lol.

---

