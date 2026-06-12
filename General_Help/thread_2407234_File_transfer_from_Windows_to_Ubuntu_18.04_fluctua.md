---
title: "File transfer from Windows to Ubuntu 18.04 fluctuates from 110MB/S to 0"
date: 2018-12-01
forum: General Help
---

### Post by pechius on 2018-12-01
So basically that's the problem. File transfer takes much longer than it should because for some reason the transfer rate fluctuates wildly. It seems like it only started recently because I don't remember seeing anything like this before. Maybe it's an update that broke it. 

This is not a samba issue. Same behavior can be observed when transferring with NoMachine. Interestingly, if I'm transferring from Ubuntu to Windows, there's no problem. I see a straight line with no fluctutation.
You can see from my network activity that something is very wrong when trasnferring TO Ubuntu machine.
[https://imgur.com/7ABg7Qs](https://imgur.com/7ABg7Qs)

And here's how the transfer looks from Windows:
[URL="https://imgur.com/6Wkn4xr"]https://imgur.com/6Wkn4xr

[/URL]

---

### Post by TheFu on 2018-12-01
18.04 changed a few things.  Did the problem exist before?
Also, many things can screw up transfer performance. 
* networking
* network drivers
* file systems used
* mount options
* how the transfers are being performed - is gvfs being used or samba or cifs or nfs or something else?
* the programs used to cause the xfers.  GUI tools often have overhead that CLI tools do not.

---

### Post by pechius on 2018-12-01
> **TheFu said:**
> 18.04 changed a few things.  Did the problem exist before?
Also, many things can screw up transfer performance. 
* networking
* network drivers
* file systems used
* mount options
* how the transfers are being performed - is gvfs being used or samba or cifs or nfs or something else?
* the programs used to cause the xfers.  GUI tools often have overhead that CLI tools do not.

I'm only experimenting with 18.04.1. I've never head any othee version. I'm transferring files to the boot drive. Network drivers are definitely buggy in 18.04, but the strange thing that I didn't see this problem a few weeks before.

---

### Post by SeijiSensei on 2018-12-01
Give [WinSCP]("https://winscp.net/eng/download.php") a try.  It uses the SSH protocol rather than Samba/CIFS.

Situations where the speed drops to zero usually indicate that the receiving end is buffering the transaction, and the buffer is full.  The sender waits until told it can resume the transfer.

---

### Post by TheFu on 2018-12-01
Do you have write permissions to where the transfer is going?
Answers to the other questions would be helpful.

---

### Post by HermanAB on 2018-12-01
Try copying a file over the network to a RAM disk.  If it runs at a constant speed, then the trouble is a slow disk drive.

BTW, /tmp is a RAM disk.

---

### Post by TheFu on 2018-12-01
Not always a RAM disk, at least not here. I checked 3 other systems and none are using a RAM disk.
```
$ df -h /tmp/
Filesystem                         Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root   51G   37G   11G  78% /
```

---

### Post by HermanAB on 2018-12-01
Well, it is quite trivial to use tmpfs to make a RAM disk for the speed test

---

### Post by pechius on 2018-12-02
> **TheFu said:**
> Do you have write permissions to where the transfer is going?
Answers to the other questions would be helpful.
> **TheFu said:**
> 18.04 changed a few things.  Did the problem exist before?
Also, many things can screw up transfer performance. 
* networking
* network drivers
* file systems used
* mount options
* how the transfers are being performed - is gvfs being used or samba or cifs or nfs or something else?
* the programs used to cause the xfers.  GUI tools often have overhead that CLI tools do not.
First, thanks to all of you for your help.
I do have permissions. Iperf3 shows steady 940mbps from windows to Ubuntu, so it's probably not a network problem. I'm using samba, but I've also tried NoMachine transfer (which afaik doesn't use samba) and result is the same. That's why I think SeijiSensei's explanation is the most likely, the only question is why?? And why did the problem only start recently, even though I haven't really changed anything, except for maybe increasing swap file from 2gb to 4gb..

---

### Post by TheFu on 2018-12-02
NoMachine implements the NX protocol. I use NX daily, constantly, right now, and have for about 8 yrs.  NX uses ssh tunnels.  I don't use NoMachine, preferring to use x2go instead. I've used it from 5 continents from minimal laptops to continue working when on travel, but not bring any data with me.

With every different release, the versions of packages change.  That can impact defaults and some new features on the server-side can alter the way that clients communicate.

BTW, thanks for being on the bleeding edge with 18.04.  I've left my servers on 16.04 to avoid these sorts of issues until they are all figured out.  In my world, new is the enemy of stable.  16.04 support lasts until 2021, so I'm not in any hurry.

The replies here have merit. These are very experienced people.  

Some of my questions were to avoid guessing and heading down the wrong path towards the root problem.  For example, different file systems have known performance issues when the defaults are used.  There are solutions.
Using wifi instead of wired ethernet can cause huge fluctuations in network bandwidth due to external devices like portable phones or doorbells or microwaves. An older wifi device connected to the same network can cause huge drops in bandwidth, even when not in active use.  In a crowded wifi area, neighbors can drastically impact performance. 

But if you are happy with the current guesses, great.  Please mark the thread as solved using the "thread tools" button near the top.

---

### Post by pechius on 2018-12-02
Well, I would like to find a solution, but I don't know where to look anymore. I have no doubt that people here have experience and your suggestions have merit. I thought I about going with 16.04, but then again, that wouldn't stop all the issues because there is an issue with network drivers on 18.04 (send speed is reduced to 750mbps) and the newest 16.04.5 has the same kernel as 18.04 so some of the problems would still be there, I guess. At the moment, all I have is a 120GB ssd, msi b250m board and intel cpu. That's it. I'm waiting for my hard drives. I was simply testing how the file transfer performs, turns out it doesn't. I have tried transferring files a few backs and as far as I remember there were no issues. So I think the most likely thing is that there was a regression.

---

### Post by TheFu on 2018-12-02
> **pechius said:**
> Well, I would like to find a solution, but I don't know where to look anymore.

Call me crazy, but perhaps if you answered our questions, then a path to the root cause would become clear?
Keeping them secret isn't leveraging our knowledge.  If you don't actually post the answers, we'll cannot help.

---

### Post by HermanAB on 2018-12-03
The problem could be a bad filesystem.  The network transfer will stop if the HDD cannot read/write the data fast enough.  You can confirm that by setting up RAM disk and doing a test transfer.  If the disk filesystem is bad scheduling a fsck and rebooting to execute it may help.

---

### Post by pechius on 2018-12-03
I'm sorry I'm not sure what questions you have in mind. If you're talking anout this then I don't know if I have anything to add, but I'll try. 
> **TheFu said:**
> 18.04 changed a few things.  Did the problem exist before?
Also, many things can screw up transfer performance. 
* networking
* network drivers
* file systems used
* mount options
* how the transfers are being performed - is gvfs being used or samba or cifs or nfs or something else?
* the programs used to cause the xfers.  GUI tools often have overhead that CLI tools do not.
My network is fine. 
As for the drivers, my Windows pc works fine and has no problems transferring files to another windows pc and Ubuntu has no additional drivers instslled by me. Both machines have I219V as a network adapter.
I have a single ssd 120gb formatted with ext4
Can't say anything about the mount options. It's just a boot drive right now with Ubuntu installed on it.
As I've already said, both samba and nomachine give the same results, thus eliminating samba as the culprit.

> **HermanAB said:**
> Try copying a file over the network to a RAM disk.  If it runs at a constant speed, then the trouble is a slow disk drive.

BTW, /tmp is a RAM disk.

> **HermanAB said:**
> Well, it is quite trivial to use tmpfs to make a RAM disk for the speed test

> **HermanAB said:**
> The problem could be a bad filesystem.  The network transfer will stop if the HDD cannot read/write the data fast enough.  You can confirm that by setting up RAM disk and doing a test transfer.  If the disk filesystem is bad scheduling a fsck and rebooting to execute it may help.

Unfortunately I don't really know how to do any of that, but I'll try to find out.

---

### Post by Holger_Gehrke on 2018-12-03
Use```
mount -t tmpfs YouDoNotNeedADeviceButThereMustBeSomethingHere /path/to/an/empty/directory
```to create a RAM-disk and make it accessible in the given directory.

Holger

---

### Post by pechius on 2018-12-04
I'm happy to report that it fixed itself. Hopefully for good... I updated the system (as I always do) and also removed some unused kernels and now my transfer speed is steady 110MB/s. Thanks to all of you who tried to help me.

ETA: the most frustrating thing is while this problem appears to be gone there's a new one now, lol. The keypad isn't working correctly, even though it did a week ago. If I press 4 I see for on the screen, but if I press it again, it acts as a left arrow key. Oh well..

---

