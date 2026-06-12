---
title: "Constant hard drive usage freezes computer"
date: 2007-12-02
forum: General Help
---

### Post by emid on 2007-12-02
For the last two days, my pc seems to have the hard drive light running constantly.  I mean 100% of the time.  If I leave the computer and come back the next morning it is locked up completely, can't ssh in or anything.  does anyone know what could be causing this out of the blue?

---

### Post by LinuxLuver29 on 2007-12-02
Well, It sounds like you might have to many processes running at once.  Have you tried to reboot your computer, if not I would so that it can clear out all of those processes.  Also, if that doesn't work, I would just reinstall Ubuntu completely.

---

### Post by atlfalcons866 on 2007-12-02
how much ram do you have? it could be accessing the swap if you have little ram. I have 1GB of ram and it hardly touches the swap.

---

### Post by emid on 2007-12-02
I don't think it has to do with the number of processes because I have been running a similar configuration for quite a while with no problems.  I have rebooted, essentially after every morning when I have found the computer locked up.  Once I reboot the computer is functional but the hard drive light is constantly engaged.

I have 2 gigs of ram so I don't think it is related to that either. (Plus my swap is at 0 right now)

Everything has been more or less fine for a while, i really don't know why this just started happening out of the blue.

---

### Post by atlfalcons866 on 2007-12-02
do you have tracker installed? that writes to the hard drive a lot when it is indexing your files.

---

### Post by emid on 2007-12-02
> **atlfalcons866 said:**
> do you have tracker installed? that writes to the hard drive a lot when it is indexing your files.

I do have tracker installed, but 100% of the time?  The light is constantly engaged until the computer eventually freezes.  Is there a way for me to see what is currently accessing the drive?

---

### Post by atlfalcons866 on 2007-12-02
post your top

> top

---

### Post by emid on 2007-12-02
I don't know why I didn't think of this, it is probably related to my software RAID 5 that i have set up.

---

### Post by emid on 2007-12-02
My RAID setup is resyncing, that is probably it.  The question now is why my computer was freezing as a result?

---

### Post by jaakan on 2007-12-02
Why are you using software RAID 5?, thats alot of I/O + CPU overhead vs hardware raid 5

What does kern.log have in it?

---

### Post by emid on 2007-12-02
> **jaakan said:**
> Why are you using software RAID 5?, thats alot of I/O + CPU overhead vs hardware raid 5

What does kern.log have in it?

kern.log has a lot in it, this is a sample:
```

Dec  2 16:03:21 d-desktop kernel: [ 3443.388968] Unknown OutputIN= OUT=vmnet8 SRC=172.16.227.1 DST=172.16.227.255 LEN=261 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=241 
Dec  2 16:03:21 d-desktop kernel: [ 3443.389057] Unknown OutputIN= OUT=vmnet1 SRC=192.168.169.1 DST=192.168.169.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Dec  2 16:03:21 d-desktop kernel: [ 3443.389141] Unknown OutputIN= OUT=vmnet8 SRC=172.16.227.1 DST=172.16.227.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Dec  2 16:08:25 d-desktop kernel: [ 3747.176268] Unknown OutputIN= OUT=vmnet1 SRC=192.168.169.1 DST=192.168.169.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Dec  2 16:08:25 d-desktop kernel: [ 3747.176430] Unknown OutputIN= OUT=vmnet8 SRC=172.16.227.1 DST=172.16.227.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Dec  2 16:13:27 d-desktop kernel: [ 4049.052262] Unknown OutputIN= OUT=vmnet1 SRC=192.168.169.1 DST=192.168.169.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Dec  2 16:13:27 d-desktop kernel: [ 4049.052429] Unknown OutputIN= OUT=vmnet8 SRC=172.16.227.1 DST=172.16.227.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Dec  2 16:14:21 d-desktop kernel: [ 4103.017122] Unknown OutputIN= OUT=vmnet1 SRC=192.168.169.1 DST=192.168.169.255 LEN=261 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=241 
Dec  2 16:14:21 d-desktop kernel: [ 4103.017255] Unknown OutputIN= OUT=vmnet8 SRC=172.16.227.1 DST=172.16.227.255 LEN=261 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=241 

```

I used software RAID because it was cheap :).  I've never really had any performance problems with it, it has been pretty good.

---

### Post by jaakan on 2007-12-02
if you can figure out what time it locked up there should be some odd stuff in that log round the same time.

look above "kernel: [    0.000000]" where the last boot started around th etime of when you first rebooted your PC after it locked up.

then look at syslog and messages around the same time

have you posted a bug reboot on this


if not you should include the following files in your bug report on launchpad

sudo lshw > lshw.txt
sudo dmidecode > dmidecode.txt
sudo lspci -vvnn > lspci.txt
sudo cp /var/log/kern.log > kern.log.txt
sudo cp /var/log/syslog > syslog.txt
sudo cp /var/log/messages > messages.txt
sudo uname -a > uname.txt

---

