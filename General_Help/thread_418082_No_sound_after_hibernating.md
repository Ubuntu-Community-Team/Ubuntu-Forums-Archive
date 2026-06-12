---
title: "No sound after hibernating"
date: 2007-04-22
forum: General Help
---

### Post by vidak on 2007-04-22
I have a HDA Intel integrated sound card on my laptom, and after installing feisty, I'm experiencing the following problem: when sending the machine to hibernating, and coming back, the sound disappears (it's OK after a reboot). This is something new after dapper/edgy... 
Has anybody a similar problem/solution?

---

### Post by Brucevdk on 2007-04-27
I'm using an IBM ThinkPad R51 (2887AVG) and I am experiencing the same symptons. This is what *aplay -l* and *lspci* report:
```

card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

```

When I remove or insert the power cable from the battery I can hear the sound for less than a second but shortly thereafter it is once again gone. 

There are multiple bug reports concerning this issue over at LaunchPad, two of them are [Bug #96230]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96230") and [Bug #98605]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/98605"). As is mentioned description, rebooting the machine does not resolve the issue, you have to power down completely to regain sound. Also, there are plenty of other threads discussing this issue in this forum.

---

### Post by stmiller on 2007-04-27
This is an alsa bug. The alsa driver must be compiled as able to hibernate/suspend and reload. So apparently this is not happening. For the time being you can do:

$ sudo /etc/init.d/alsa-utils restart

when getting back from sleep to get sound working again. There is a sort of script of things that run to get reloaded when the computer wakes up. (Start network again, etc. ,etc.) So you could add a line to start alsa when the computer wakes up. Let me know if you need more details.

---

### Post by vidak on 2007-04-28
> **stmiller said:**
> 
$ sudo /etc/init.d/alsa-utils restart


I've tried this one already but it didn't help.alsa seems to be restarted, but that's all. Still no sound. The power led is flashing continuously - another interesting 'feature'...

---

### Post by energiya on 2007-04-28
Well, you could close any alsa-related service before calling hibernate, and after, start alsa and load the settings (alsactl restore)

---

### Post by vidak on 2007-05-02
I've tried to turn off alsa before hibernating, and restarting it when coming back. The PCM and Master mixers got muted, but after restoring, still no sound :confused: 
Any ideas?

---

### Post by emorphien on 2007-05-20
I'm having the same problem on my X31.

---

### Post by mbradlcu on 2007-05-20
before restarting alsa try:
```
sudo fuser -vk /dev/dsp
```

---

### Post by ardath on 2007-05-20
vidak,

have you tried changing volume after restore? 
i have the same problem. alsa is working but the sound seems to be muted. after i change volume of master & pcm the sound comes back (however, i have to change volume of _both_ channels).

---

### Post by daschmidty on 2007-05-22
this is a little weird but seems to work.
I read some post saying to use uswsusp instead of the default hibernate script, and that has magically worked for some people, though that alone did not work on my thinkpad X24. However if i hibernate using uswsusp, then restart alsa on wakeup, the sounds seems to work

to use uswsusp
```
sudo apt-get install uswsusp
sudo s2disk
```

---

### Post by tommie74 on 2007-06-17
I´ve had the same problem, no sound after waking from hibernate, and found a solution in launchpad. 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893)

The problem seems to be related to a change in the kernel. An updated kernel is available for download:

[http://rookery.ubuntu.com/~kyle/kernels/salgado/2007-04-25/linux-image-2.6.20-15-generic_2.6.20-15.28_i386.deb](http://rookery.ubuntu.com/~kyle/kernels/salgado/2007-04-25/linux-image-2.6.20-15-generic_2.6.20-15.28_i386.deb)

install using package manager or 

```
dpkg -i /home/***your user name***/Desktop/linux-image-2.6.20-15-generic_2.6.20-15.28_i386.deb
```

hope this works for you too, as it did for many others,
Thomas.

---

### Post by Brucevdk on 2007-06-17
Thanks for pointing me to [that bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893") Thomas, in the commentary section somebody mentions changing *HIBERNATE_MODE* in */etc/default/acpi-support* to *platform*. This works for me on my ThinkPad R51 with the stock Debian/Ubuntu 2.6.20-16 kernel, no need for a custom kernel at all.

---

### Post by tommie74 on 2007-06-18
Good! I´ve tried that too, but on my compaq presario that didn´t work.

---

