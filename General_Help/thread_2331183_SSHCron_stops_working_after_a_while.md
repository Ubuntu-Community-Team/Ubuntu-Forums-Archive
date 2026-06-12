---
title: "SSH/Cron stops working after a while"
date: 2016-07-19
forum: General Help
---

### Post by ironitech on 2016-07-19
I have a ubuntu 16.04 server that is used for backups, gitlab, zoneminder and a couple of other tasks. 
Every now and then I'm unable to connect to the server by SSH. When I use ssh -vvv it hangs at: "debug1 local version string...". 
When this happens, gitlab also stops working, the webserver handles the request but I get a 502 error after a while, Zoneminder and all Cronjobs are halted. The only thing that seems to work is apache and gitlabs webserver (i don't remember it's name).

I can't login locally either, I tried to open a new console but that didn't work. Hard reset is the only solution and then the system can run for days or weeks without problem.

The last event in syslog is:
Jul 19 01:06:22 zmc_m2[9529]: ERR [Error while decoding frame 1800]
But they appear frequently and should not be causing any problems.

Any idea where to begin?  What log files should I investigate?

---

### Post by TheFu on 2016-07-19
Welcome to the forums.  

Sounds like some hardware issue or a misconfigured hostname/domainname or something wrong in the networking layers - NIC perhaps?  

Might be 2 separate issues.  Check all the logs and dmesg files for the console lockup issue. 

For the ssh issue, check that name resolution isn't the issue by using the IP and ping by IP.  Do all the machines involved "know" each other's names by the exact same name?  that is important depending on ssh settings. How is the name resolution handled? /etc/hosts, a DNS server, zeroconf?

---

### Post by ironitech on 2016-07-19
Hi and thanks! :-)

Ok, I haven't even thought about the possibility that they are separate issues as they almost always occur at the same time. 

Regarding host name I've tried to access by hostname and by IP and the result is the same so that doesn't seem to be the case. And while SSH is not working I can access the webservers on the server so I guess the hostname is ok?

Regarding dmesg, I can't seem to find logs from previous sessions, is there a way to read those?

---

### Post by ironitech on 2016-07-20
By the way, if it should be a hardware issue, what is the most likely part? Is it the NIC?

---

### Post by ironitech on 2016-07-20
And one more thing, I have a lot of this in the kern.log:

kernel: [154580.947724]  sdf: sdf1 sdf2 < sdf5 >
kernel: [154580.998044] device-mapper: table: 252:4: linear: Device lookup failed
kernel: [154580.998208] device-mapper: ioctl: error adding target to table
kernel: [154580.998407] device-mapper: table: 252:5: linear: Device lookup failed
kernel: [154580.998557] device-mapper: ioctl: error adding target to table




kernel: [164439.236102]  sde: sde1 sde2 < sde5 >
kernel: [164439.690158] device-mapper: table: 252:4: linear: Device lookup failed
kernel: [164439.690333] device-mapper: ioctl: error adding target to table
kernel: [164439.690505] device-mapper: table: 252:5: linear: Device lookup failed
kernel: [164439.690699] device-mapper: ioctl: error adding target to table

Might they be of interest? sde and sdf are the OS-disks in raid1.

---

### Post by TheFu on 2016-07-20
> **ironitech said:**
> By the way, if it should be a hardware issue, what is the most likely part? Is it the NIC?

Hard to say. I've seen overheating video cards cause unrelated lockups. Electrical issues can show up in very strange ways.

If there are any issues in the logs, fix them. All of them.  

See there's an issue with some RAID disks. Fix those.  Corrupted data on disk can cause all sorts of issues.

---

### Post by ironitech on 2016-07-21
It's funny you mention video card as that is one of the problems I've seen during boot. Thanks for the advice! I will look into this!

---

### Post by TheFu on 2016-07-21
This thinking a little here .... sometimes the disks haven't spun up when the kernel looks for them, but eventually the disks are ready and working fine. Look for "found disks" below those issues. Could just be that they weren't ready when the kernel looked for them, but did get there and all is fine.

And it could be the NIC, but NICs really don't _fail_ that often in the last 15 yrs. NIC issues tend to be having the wrong driver loaded (v-E instead of v-F or v-E1) - since I've switched to Intel NICs, just don't see those issues anymore. Makes life much easier to avoid non-Intel NICs, IMHO.

---

### Post by ironitech on 2016-07-21
These messages appears continuously, not just during boot, so I guess there might be a problem with them? 
I know the disks have been online for quite some time (I've been forced to change 2 disks in the other raid-set on this server so they might be in the end of there lifetime) so changing them might be a good idea anyway. But should I reinstall as there might be corrupt data on the disks? I guess that would be a good idea, however, this is not something I look forward to.

Edit: Around 35000 hours on the disks, that is almost 4 years.

---

### Post by TheFu on 2016-07-21
There can always be corrupt data on disks.  The only file system which does anything about that is ZFS.  If I was worried about data corruption, I'd compare the current files against my backups from 7, 30, 45, 60 , 90 days ago (My min backup versioning is 60 days).

Most of my disks are over 4 yrs old.  Just depends on the disk (avoid consumer Seagate disks).  Time isn't necessarily bad for disks. Look at the SMART data and watch how it changes over time. Because SMART isn't standardized, it really isn't very useful for point-in-time knowledge. Only watching how the data changed over time is helpful.  Plus, it could be a failing cable or controller.

Why do you use RAID?  Just curious.

Did you fix the name resolution stuff yet?

---

### Post by ironitech on 2016-07-21
The reason for using raid for the OS is that the server was configured this way when I got it. I got it from my old employer when they got new servers. I use raid5 for all the data, and raid1 for the OS. 

The reason why I've changed disks (this was in the raid5-set) was because the mdadm started reporting about a lot of bad sectors on one disk, I changed that disk and everything was fine for a couple of weeks and then I received warnings about another disk. I'm installing larger disks at the same time, so I will probably replace the remaining two pretty soon. 

Regarding name resolution, I'm not sure I understand exactly what you mean? When the server starts to behave like this, I can't access SSH through it's name or it's IP, but apache-server is still accessable, please explain what I should try to do.

---

### Post by TheFu on 2016-07-22
> **ironitech said:**
> Regarding name resolution, I'm not sure I understand exactly what you mean? When the server starts to behave like this, I can't access SSH through it's name or it's IP, but apache-server is still accessable, please explain what I should try to do.


Both machines should be able to ping each other using the same names. a-->b, b-->a, a-->a, b-->b
If the ping returns a name, it should match the name exactly used in the ping command, not some other name. Just something to check. Might not be anything, but ssh does have settings which can make it really picky.

---

### Post by TheFu on 2016-07-22
dup

---

### Post by ironitech on 2016-07-25
> **TheFu said:**
> Both machines should be able to ping each other using the same names. a-->b, b-->a, a-->a, b-->b
If the ping returns a name, it should match the name exactly used in the ping command, not some other name. Just something to check. Might not be anything, but ssh does have settings which can make it really picky.

Ah, ok!

Well, I will not be able to test this as I can't connect to the server when this problem occurs. As for now, the above is correct, the names are correct. But when the problem mentioned in the first post occurs, I can't even log in at the physical terminal, so pings wont be possible I'm afraid.

The server sometimes work for weeks before this happens...it's really annoying! I just remembered that the CPU was overheated once, the fan broke down so the CPU went into some low power mode to protect itself. Is it possible that it was damaged and this i why I get these problems?

My plan now is to change video card and the two OS-disks and reinstall ubuntu, and hope for the best.

---

