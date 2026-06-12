---
title: "Grub Error"
date: 2008-04-16
forum: General Help
---

### Post by Pandab34R on 2008-04-16
I installed Unbuntu studio on a seperate hard disk. So I had a disk a: with windows and a disk b:with ubuntu studio. All the sudden while operating in windows my computer shuts off and restarts. It reboots and I find myself looking at a grub error about 2 seconds after it goes post. "Unable to load grub". I cant remember the error code but I have tried reinstalling grub from a knoppix cd and an ubuntu cd. Neither worked. I really need to be able to get back to that first drive and reinstalling windows is not an option.

---

### Post by silvagroup on 2008-04-16
When you say you tired to install from the cd's what exactly did you do.

---

### Post by Pandab34R on 2008-04-17
I followed the instructions given on these forums for installing grub. They told me to run a few commands in the terminal which I did, and it seemed to install properly. I installed it to the device which I believe has grub on it already, and then when that didn't work I installed it to the other device. Neither fixed the issue.

---

### Post by danwood76 on 2008-04-17
It sounds like you may have a hard disk error.
It would be very useful to know the grub error, could you boot up without the live CD and find out what the grub error is?

Check that your disks are plugged in correctly, sometimes the power leads fall out with vibration if they havent been pushed in all the way.

---

### Post by Pandab34R on 2008-04-17
I'll try that this evening when i get home. For now, I've gotta run. But just so you know - the ubuntu studio partition is not a priority at all. I could care less about booting back up into it because it was just something I was playing around with. So even if I could just get  RID of grub alltogether and go back to what windows was using would be fine.

---

### Post by Pandab34R on 2008-04-17
Okay here is what it is saying:

Grub Loading Stage1.5.

Grub Loading, Please Wait...
Error 21

---

### Post by zvacet on 2008-04-17
[Here]("http://users.bigpond.net.au/hermanzone/p15.htm#21")

To fins out where your Ubuntu is 

```
sudo fdisk -lu
```

---

### Post by Pandab34R on 2008-04-17
```

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   488392064   244196001   42  SFS

```

---

### Post by danwood76 on 2008-04-18
Well it looks like you only have 1 hard disk with one partition, which is neither linux nor windows.
Check that your hard disks are plugged in correctly.

Otherwise I would suspect a dead hard disk.

---

### Post by Pandab34R on 2008-04-18
I do not think that is the case because I have a volume, hda1 mounted and that is my windows volume. I am looking at all of my files on that hard disk right now... Perhaps the other hard disk got messed up and that is why grub wont load? 

Is there any possibility of repairing this problem? Obviously it thinks it needs to be loading grub, but what is telling it to load grub? Can we just get rid of that factor or something? Im not a very experienced linux user and a pretty average user at that so I dont really know what to do right now.

---

### Post by danwood76 on 2008-04-18
On the MBR of your first disk (hda) it will be instructed to load grub from the linux drive, obviously that drive is inaccesable and it gives up.

You can get windows back by reloading the windows MBR from within the live session.

First you need to install ms-sys:
```

sudo apt-get install ms-sys

```
Then to restore the MBR do
```

ms-sys -w /dev/hda

```

When you reboot you should then get windows up, grub wont load and so you wont get ubuntu but maybe that drive has died so I dont suppose that matters.

---

### Post by Pandab34R on 2008-04-18
```

knoppix@Knoppix:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree... Done
ms-sys is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```
Then Proceeeded to run this:
```

knoppix@Knoppix:~$ sudo ms-sys -w /dev/hda
DOS/Windows NT master boot record successfully written to /dev/hda

```

---

### Post by Pandab34R on 2008-04-18
Great, it worked! Thank you very much!!

---

### Post by Black-Diamond on 2008-05-02
I almost have the same problem but when i tried your solution
see what it respond to me


ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ms-sys
ubuntu@ubuntu:~$ sudo ms-sys -w /dev/hda
sudo: ms-sys: command not found
ubuntu@ubuntu:~$
ubuntu@ubuntu:~$

---

