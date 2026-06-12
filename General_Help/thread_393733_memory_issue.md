---
title: "memory issue"
date: 2007-03-26
forum: General Help
---

### Post by superspak on 2007-03-26
i have a problem concerning my laptop, im a person who likes to listen to music and have firefox with 10 tabs open at all times, but then after an hour firefox takes up all my ram, which is 512 mb, and it instantly freezes and i have to hold down the power button to kill the laptop, any suggestions? should i use some other web browser or what?

---

### Post by coxy on 2007-03-26
I would have expected the system to use your swap partition. Do you have one? If your not sure run the command:

> free -m

The output should look something like this:

> 
             total       used       free     shared    buffers     cached
Mem:           250        155         94          0          0        120
-/+ buffers/cache:         35        214
Swap:          486          0        486


If swap reads a total of 0 then you don't have one and this may well be the cause of your issue.

---

### Post by superspak on 2007-03-26
holy crap i dont have a swap!:(  i think ill just make one with qtparted , so it would fix my problem? last time i let the installer do my partitions

---

### Post by coxy on 2007-03-26
It should help, although swap is not a replacement for memory and does not run anywhere near as quick. I have never actually re-sized a partition with qtparted but I know it can be done. There will be someone around the forums that can offer you some good advice on doing it, just make sure you take a backup first.

You will need between 1.5x and 2.0x the amount of memory you have installed so for 512 MB of RAM a swap partition would be 768 MB or 1024 MB. I usually go with double but that is just my opinion.

---

### Post by coxy on 2007-03-26
I have just done a quick search and GParted will suit your needs. Have a look at their HOWTO for resizing a partition:

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by superspak on 2007-03-26
ok i made a swap, but ubuntu doesnt see it, does it have to be at the beginning of the drive? because its at the end of the drive

---

### Post by Ramses de Norre on 2007-03-26
Is it in fstab? Add a line like this:```
/dev/??? none            swap    sw              0       0
``` And fill in the right device node.

---

### Post by superspak on 2007-03-26
well i put that in fstab, with the ??? being hda3 which is where the swap is located, but it didnt work, so now, im moving the boot partitions to the end of the drive and making the swap at the beginning to see if thatll work

---

### Post by kpkeerthi on 2007-03-26
sudo swapon /dev/hda3

---

### Post by superspak on 2007-03-26
well, i took all this time, about 2 hours to move my boot partiton, and now, the swap is at the beginning of the drive, well, i used swapon in gparted, and it worked it sees the swap now, thanks everyone, hopefully now it wont freeze up now under heavy load of firefox and music :)

---

