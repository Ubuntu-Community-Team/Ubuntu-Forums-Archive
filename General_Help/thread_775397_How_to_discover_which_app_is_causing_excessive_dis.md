---
title: "How to discover which app is causing excessive disk i/o"
date: 2008-04-30
forum: General Help
---

### Post by crispinb on 2008-04-30
Is there a tool which can monitor or otherwise show me what's doing lots of HD i/o at a given time?

I ask because on my newly-installed Xubuntu hardy, I get intermittent periods of a minute or two when the disk thrashes like billy-oh, killing everything dead for the duration (can't do a thing 'till it stops).

It's not the FF beta5 bug, because I rarely use FF. 

Note also that at the time there is *not* usually particularly high CPU usage, so no clues available there. So I really need to find which process is thrashing the disk.

---

### Post by crispinb on 2008-05-01
Anyone? I'm having real problems with the intermittent unresponsiveness of 8.04

---

### Post by mali2297 on 2008-05-01
See the answer in this [old thread]("http://ubuntuforums.org/showthread.php?t=396692"). It looks like one needs to recompile the kernel to enable this feature.

---

### Post by crispinb on 2008-05-01
> **mali2297 said:**
> See the answer in this [old thread]("http://ubuntuforums.org/showthread.php?t=396692"). It looks like one needs to recompile the kernel to enable this feature.

Nice, thank you.

Following up on your lead, I found iotop.py  [here]("http://guichaz.free.fr/misc/"). It runs without kernel modification on 8.04 with its default 2.6.24-16 kernel.

It's even quite fun to watch the disk IO of running processes. Sad though that might be.

---

### Post by mali2297 on 2008-05-01
Good to know that it has been enabled by default. Report back if you find out what's stalling your system.

---

### Post by crispinb on 2008-05-02
> **mali2297 said:**
>  Report back if you find out what's stalling your system.

Well, it's been a bit of a puzzle. When the hard drive spins and everything stalls, iotop shows little or no I/O happening. So probably not the fault of a particular application or xubuntu itself.

I thought it might be a HD hardware problem. I don't have much in the way of diagnostic stuff to check this, but ran what I could, looked at SMART output etc, ran fsck in case there was a filesystem problem. All seems fine.

But .. then I remembered that on my old install of 7.10 I had added some hdparm settings because of problems with the power management of my particular HD (a Toshiba MK4019GAX). So I've gone back to running hdparm to turn power-saving off. So far I haven't experienced the HD spinning and locking everything up ... but I'm still on tenterhooks half-expecting it to happen again.

---

### Post by timnils on 2008-05-07
Hi,
A fresh Xubuntu install and I am experiencing the same problem with HD spinning. I am certain that it has nothing to do with the hardware since I have a dual boot. My laptop is a HP, Omnibook 6000, 700mhz, 256mb.
Thanks in advance for your help.

---

### Post by crispinb on 2008-05-07
> **timnils said:**
> Hi,
A fresh Xubuntu install and I am experiencing the same problem with HD spinning. I am certain that it has nothing to do with the hardware since I have a dual boot. My laptop is a HP, Omnibook 6000, 700mhz, 256mb.
Thanks in advance for your help.

Why don't you try grabbing iotop (find link in post above) and leaving it running in a terminal? When the drive starts spinning, iotop might show you what's doing it.

---

### Post by mahousaru on 2008-05-07
Could it be the issue with atime?  I know that hardy now uses relatime by default, but my lappie which i upgraded didn't have that parameter.

if you type mount in the terminal it should show how your disks are mounted

---

### Post by timnils on 2008-05-07
> **crispinb said:**
> Why don't you try grabbing iotop (find link in post above) and leaving it running in a terminal? When the drive starts spinning, iotop might show you what's doing it.
Thank you for your suggestion. I have downloaded that file but I do not know what to do with it. I suppose it should be installed but how. Can you write which steps should i take?
Regards

---

### Post by mali2297 on 2008-05-08
> **timnils said:**
> Thank you for your suggestion. I have downloaded that file but I do not know what to do with it. I suppose it should be installed but how. Can you write which steps should i take?
Regards

Pass it to the python interpreter with
```

python iotop.py

```
*or* run it as an executable:
```

chmod +x iotop.py
./iotop.py

```

---

### Post by timnils on 2008-05-08
> **mali2297 said:**
> Pass it to the python interpreter with
```

python iotop.py

```
*or* run it as an executable:
```

chmod +x iotop.py
./iotop.py

```

Thanks,
If I understand correctly about iotop, it shows that spinning has to do with Firefox which writes and reads to and from the disk and it can take a couple of minutes. During this time the counter shows reading or writing numbers increase but suddenly they are back to zero and counting begins to increase again. Meanwhile my laptop is not responsive. I can move the mouse and click but nothing happens while HD is spinning.
I have not a clear idea what is going on. What is the next step?
Regards
Tim

---

### Post by mali2297 on 2008-05-08
> **timnils said:**
> Thanks,
If I understand correctly about iotop, it shows that spinning has to do with Firefox which writes and reads to and from the disk and it can take a couple of minutes. During this time the counter shows reading or writing numbers increase but suddenly they are back to zero and counting begins to increase again. Meanwhile my laptop is not responsive. I can move the mouse and click but nothing happens while HD is spinning.
I have not a clear idea what is going on. What is the next step?
Regards
Tim

You could try another browser, like Firefox 2 (if you are using 3 now) or Opera. See if it helps. Although, there  might be some underlying problem that has nothing to do with Firefox.

---

