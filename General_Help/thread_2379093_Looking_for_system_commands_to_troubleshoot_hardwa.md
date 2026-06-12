---
title: "Looking for system commands to troubleshoot hardware"
date: 2017-11-30
forum: General Help
---

### Post by cowboy.bebop on 2017-11-30
I am specifically looking for commands used from a Live ISO ran from memory or an unmodified version of Ubuntu (such as apt-get install) installed on a HDD, to troubleshoot hardware. I am trying to troubleshoot HW issues in terminal, and avoid using GUI based applications. Something someone could see in TTY, if terminal in GUI was inaccessible. I originally posted in Reddit, but due to the lack of responses I would try my luck here.

Initially posted in [Hardware]("https://ubuntuforums.org/showthread.php?t=2377805"), and had my thread transferred to virtualization, which is not relevant to the title of the question, so I will neglect the notion of using virtualization for the sake of this thread. Also, some responses seem to veer off the topic at hand, and doesn't really answer or provide detail to the question I asked, so I figured I would try here. 

I am familiar with the commands:

        dmidecode
        grep
        hdparm
        lscpu
        lshw
        lspci
        upower

But I would really like to know if there is a command to detect failures or errors, within a log of course, with the sensors on a motherboard, to determine if a motherboard is failing. Of course not only the motherboard, but with other hardware as well. Anyone familiar with such a commands without installing third party add-ons using package manager or apt-get. You must limit yourself with TTY, whether there is a hardwired connection or not, apt-get and package manager are off limits. How would you determine a hardware failure from within TTY or terminal, aside from using BIOS? The commands I provided above do help, but unfortunately only report mostly configurations and less of errors/failures. I have sabotaged a personal laptop of mine, and cannot determine where the best place to look to determine what has failed, warning'ed or error to coin the hardware defective.

---

### Post by him610 on 2017-12-02
Whenever I suspect a hardware problem (almost never), I normally use a couple of different diagnostic tools...
```
journalctl | grep warn && journalctl | grep fail
```
or
```
dmesg | grep fail
```

There may be better diagnostic tools available that I am unfamiliar with. One of the hardware masters may have [better | best] suggestion.

---

### Post by Yellow Pasque on 2017-12-03
It seems like you're looking for a "smoking gun" error message to pinpoint a bad mobo. I don't think you're going to find one. It's like Memtest - If you get errors, you likely have a bad memory stick(s), but it could be a memory controller issue (i.e a bad CPU or mobo) or even a bad power supply with a bit of voltage droop. It's hard to pinpoint without spare hardware.

> if there is a command to detect failures or errors, within a log of course, with the sensors on a motherboard, to determine if a motherboard is failing

Well, with the 'sensors' command you've (usually) got the CPU temp sensor. If you're lucky, and the Super I/O chip is supported in linux (and appropriate kernel module is loaded), you may also see other temps, fan speeds, and voltages. You basically have the Linux equivalent of "Speedfan" in terminal form.
Probably the only hardware failure you're going to be able to determine is if a fan went out and is causing overheating. I don't think I would trust output of sensors to diagnose a bad PSU, even if there are voltage readings.

About the only other thing I suggest is 'smartctl' command to look at hard disks. I used to work at a giant tech company too, and bad hard disks were one of the easier things to troubleshoot because SMART logs were fairly straightforward and certain critical values meant automatic replacement of the disk.

---

