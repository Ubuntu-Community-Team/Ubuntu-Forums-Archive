---
title: "woke up computer and can't get anywhere"
date: 2017-12-19
forum: General Help
---

### Post by Buntu Bunny on 2017-12-19
After several hours in hibernation I woke up my computer to go online. Firefox wouldn't open. After several tries I restarted the computer but at restart I got 

```
>> Checking Media Presence......
>> Media Present.....
>> Start PXE over IPv4.
```

It froze on that. Restarted (hard) several more times - same thing.

Next restart I went to boot options but Ubuntu wouldn't boot. I got

```
13.686277] ati1: COMRESET failed (errno 16)
23.702352] ati1: COMRESET failed (errno 16)
```

After a few more lines of similar

```

Reset failed. Giving up.
```

I was able to boot from my live DVD and get online from there to come here for help. So HELP!

First question - can I fix this and how?
2nd question - can I recover anything from the live DVD? I have most of what I need backed up but usually do my back ups last thing, so today's work didn't get backed up.

---

### Post by Buntu Bunny on 2017-12-19
I'm finding partial answers to my dilemma by searching Ubuntu Forums and AskUbuntu. Hopefully the information is still current for 16.04. 

I understand that my first step is to find and mount my Xubuntu partition from live dvd to access it. 

```
xubuntu@xubuntu:~$ sudo fdisk -l

Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/loop0: 1.1 GiB, 1213882368 bytes, 2370864 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

This is not what I expected to see based on the threads I've read (ram0 - ram15???). It looks like I've got only one partition and swap(?). Should be Windows on there somewhere too and one for home. 

So I'm stumped again. Can anyone give me a clue?

ADD - just tried

```
xubuntu@xubuntu:~$ sudo fdisk -l /dev/sda
fdisk: cannot open /dev/sda: No such file or directory

```

Getting that sinking feeling ............

ADD - and this

[ATTACH=CONFIG]277889[/ATTACH]

So my entire hard drive just disappeared??

---

### Post by Buntu Bunny on 2017-12-20
Suspicions confirmed, hard drive dead. I ran Dell's diagnostic tool first thing this morning and it could not detect a hard drive. So that's that. What really sucks is that the computer was new in Aug. 2016. This is only the second Dell I've had, and both had hardware failures in less than 18 months. First one was ethernet card at about 11 months, but Dell support just gave me the wild goose chase until after 12-month warranty was up. I swore off Dell then, but fell for a good deal. They say we learn from our mistakes but looks like I haven't learned enough! Maybe I can just replace the hard drive? Can anyone recommend some good resources for that?

---

### Post by vasa1 on 2017-12-20
> **Buntu Bunny said:**
> Suspicions confirmed, hard drive dead. I ran Dell's diagnostic tool first thing this morning and it could not detect a hard drive. So that's that. ...
Sorry to read that! I hope you'll get some useful suggestions from people who know about hardware and stuff!

---

### Post by dragonfly41 on 2017-12-20
Before writing off your drive I found this thread .. based on the log you posted ..

[https://askubuntu.com/questions/62295/how-to-fix-a-comreset-failed-error](https://askubuntu.com/questions/62295/how-to-fix-a-comreset-failed-error)

and can you run .. [COLOR=#242729][FONT=Consolas]smartctl -t long [/FONT][/COLOR]

---

### Post by Buntu Bunny on 2017-12-20
vasa1 and dragonfly41, thank you! This morning I was thinking, if it can't detect the hard drive, then maybe it's some sort of communication problem. 

> **dragonfly41 said:**
> Before writing off your drive I found this thread .. based on the log you posted ..

[https://askubuntu.com/questions/62295/how-to-fix-a-comreset-failed-error](https://askubuntu.com/questions/62295/how-to-fix-a-comreset-failed-error)

and can you run .. [COLOR=#242729][FONT=Consolas]smartctl -t long [/FONT][/COLOR]

dragonfly41, thank you for the link. I also found [this page]("https://www.dell.com/support/article/us/en/19/sln155163/how-to-troubleshoot-a-hard-drive-not-detected-error-on-a-dell-pc?lang=en") in Dell's Knowledge Base, so obviously this isn't an uncommon problem. But of course their instructions are for Windows. Still, I'll follow as many of the steps as I can and see what happens. 

I had to install smartmontools, but it did install. This is what I got.

```
xubuntu@xubuntu:~$ smartctl -t long
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-31-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

ERROR: smartctl requires a device name as the final command-line argument.

Use smartctl -h to get a usage summary
```

---

### Post by dragonfly41 on 2017-12-20
Run command

```
smartctl --help
```

to read options. Read the SMARTCTL EXAMPLES in the printout from above command.

e.g. a command line like

```
smartctl --all /dev/sda
```

---

### Post by Buntu Bunny on 2017-12-20
```
xubuntu@xubuntu:~$ smartctl --all /dev/sda
smartctl 6.5 2016-01-24 r4214 [x86_64-linux-4.4.0-31-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

Smartctl open device: /dev/sda failed: No such device
```

Not very hopeful, is it?

I've been taking notes and am going to try the suggestions from Dell next and see if that helps.

---

### Post by Buntu Bunny on 2017-12-20
So far: 
- Have reset power and data cables.
- have reset hard drive
- BIOS appears to be up to date

Result: no joy

What's worked for others hasn't worked either:
 - can't boot to safe mode because no GRUB
- fsck returns "no such file or directory ... Possibly non-existent device?"

So I reckon that's that. The next recommended step is to replace the hard drive.

Anyway, thanks to all for the help and moral support.

---

### Post by Bashing-om on 2017-12-20
Buntu Bunny; Hey !

Been there too, doing that - hard drive failure .

If bios does not see that drive there is no hope for an operating system to see it. So, what do you see when booting the computer ?

Not seen ? then next up is to pull that drive and install in in another box . See if it is seen in this new environment .

my thoughts -
[INDENT][INDENT]on the matter[/INDENT][/INDENT]

---

### Post by Buntu Bunny on 2017-12-20
> **Bashing-om said:**
> Buntu Bunny; Hey !

Been there too, doing that - hard drive failure .

If bios does not see that drive there is no hope for an operating system to see it. So, what do you see when booting the computer ?

Not seen ? then next up is to pull that drive and install in in another box . See if it is seen in this new environment .

my thoughts -
[INDENT][INDENT]on the matter[/INDENT][/INDENT]

Hey Bashing-om! Good to hear from you. When I boot the computer I get
```

>> Checking Media Presence......
>> Media Present.....
>> Start PXE over IPv4.
```

No other machine to try the HD on, unfortunately. So I reckon I'm looking at replacing it. 

If it isn't chickens, it's feathers.

---

### Post by Bashing-om on 2017-12-20
Buntu Bunny; Well -

Looks to me like a bios thing . does bios see the hard drive ?

If bios sees that drive -
Were me I would revert bios to default ( pull the main power and hold the power button for 10 seconds) .
Connect the power and boot the system. Make sure the boot priority is set to the hard drive as 1st on the boot list . Now what does bios report ?

[INDENT][INDENT]still, just a thought
[/INDENT][/INDENT]

---

### Post by Buntu Bunny on 2017-12-20
Bashing-om, no, bios does not see the hard drive. :(

---

### Post by Bashing-om on 2017-12-20
Buntu Bunny; Well ...

All I can suggest is to swap out the hard drive . But the problem may lie deeper . Say like the power supply has failed ?
You handy with a multi-meter ? Verify the voltage levels at the pin outs .

[INDENT][INDENT]could be this
[INDENT][INDENT][INDENT]might be that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Buntu Bunny on 2017-12-20
> **Bashing-om said:**
> Buntu Bunny; Well ...

All I can suggest is to swap out the hard drive . But the problem may lie deeper . Say like the power supply has failed ?
You handy with a multi-meter ? Verify the voltage levels at the pin outs .

That's what my husband thought we should do. And it does make sense before investing in a new hard drive. The computer is only 16 months old, so I'm not real happy with the idea of replacing anything. I've had two Dells and both had hardware failures in less than a year and a half. I can't help but wonder, what next?

---

### Post by timothylegg on 2017-12-21
Before dragging your machine to the recycle bin, here is a last ditch step.  It's possible that the drive itself is still good, but that something got whacked in the BIOS (like a Lenovo running 17.10) or that the controller failed from a bad capacitor. 

Open the machine, remove the hard disk and install it in an external caddy.  Any machine running Ubuntu, perhaps this very machine, might be able to mount it as a USB device and grant you access to your data.

Poor quality components in Dell machines is no surprise.  I have contacts in the industry that have told me that Michael Dell has a very poor reputation in the view of his Asian suppliers.  They have little incentive or reason to provide the favor of specifying a superior quality component on devices that he contracts for them to assemble.  The scale of manufacturing discrete components is so massive that the Weibull curves can be very well understood; they can determine a cheaper component with an MTBF that is likely to fail at the tail end of the prescribed warranty period.

---

### Post by Buntu Bunny on 2017-12-21
Timothylegg, that's definitely worth a try! Thanks!

I have long suspected that choices are often made at the manufacturing end of products that has a knowing impact on the life of the product. And I have to say I've not been impressed with Dell's customer service. My first Dell had an ethernet card fail right before the warranty expired. They managed to hold off doing anything until I would have to pay for it myself.

---

