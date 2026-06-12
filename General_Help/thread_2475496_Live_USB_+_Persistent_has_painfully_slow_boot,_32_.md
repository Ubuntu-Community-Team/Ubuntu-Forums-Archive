---
title: "Live USB + Persistent has painfully slow boot, 32 minutes vs. 2 min. w/o Persistent"
date: 2022-05-29
forum: General Help
---

### Post by flabbers on 2022-05-29
[LIST]
[*]Ubuntu 20.04.3 64-bit
[*]8GB flash drive, written via Rufus
[*]Legacy BIOS, old dual core processor, USB 2.0, 8GB RAM
[/LIST]

Hello:

Ubuntu Live USB without Persistent partition boots quickly. With a 3GB Persistent partition, it is painfully slow, taking over 32 minutes to functional desktop vs. 2 minutes when booting from Live USB without Persistent partition.

I recognize that, during use, a Live USB with Persistent partition will be slower due to slow writes to flash drive. But, I see huge difference in boot time, during which isn't it just reading?

Without Persistent partition:

[LIST=1]
[*]30 seconds, Disk check message appears, I cancel it.
[*]1 min.35, "Install" window, the Try vs. Install choice appears
[*]2 min.10, Desktop and apps functional
[/LIST]

With 3GB Persistent partition:

[LIST=1]
[*]50 seconds, Disk check message appears, I cancel it.
[*]18 min., "Install" window, the Try vs. Install choice appears
[*]32 min., Desktop and apps functional, though slow to respond
[/LIST]

---

### Post by sudodus on 2022-05-29
There can be several reasons why your persistent live drive is slow.

- 8 GB flash drive: usually very slow memory hardware (particularly for writing). You can get a fast USB 3 pendrive (with at least 16 GB). Even better is an SSD connected via an USB 3 to SATA adapter.

- USB 2: slow interface. This is difficult to fix, if the computer lacks a USB 3 system. But some old computers have eSATA, and you can run your system in an SSD that way. Anyway, even with a USB 2 interface, a fast USB 3 drive will be faster because in USB 2 flash drives, the memory hardware is almost always limiting the speed (bottleneck).

- old flash drive: the speed of USB drives are gradually getting slower (particularly for writing).

[hr][/hr]
- If you turn off some write operations, you get a faster system. Example 1, turn off journaling (but the system will be more difficult to fix after corruption). Example 2, set 'noatime' mount option. This will also reduce wear of the memory cells due to repeated writing.

- There might also be some 'extra' problems because of 'bad configuration', or 'too much' persistent live tweaking of the system. You can start all over with a fresh persistent live system.

- You can also start all over with a light-weight flavour of Ubuntu, for example Lubuntu or Xubuntu. These flavours will need less drive space, so less reading, but the graphics system and selected software are faster too, so the speed can increase significantly.

See more details at [this link](https://help.ubuntu.com/community/Installation/FromUSBStick/pre) and links from it.

---

### Post by flabbers on 2022-05-29
Thanks for the reply

 Most of what you wrote is about improving the speed of the flash drive, USB interface, etc. But, during boot, is there any writing being done to the flash drive? My point primarily is the comparison between a live USB boot without persistence and a live USB boot with persistence. 

Without persistence, I can reach functional desktop in two minutes. As soon as persistence is added, on the identical flash drive on the identical computer, it takes over 32 minutes. 

 My primary question is, why does it take 32 minutes longer to boot from the same equipment when there is persistence versus very quick boot without persistence?

---

### Post by sudodus on 2022-05-29
You can run the command
```

dmesg

```
or may better pipe the output to less,
```

dmesg | less

```
and look at its output in detail. You may find one or two processes that need 'too much' time. See **[FONT=Courier New] man dmesg [/FONT]** for details.

---

### Post by flabbers on 2022-05-29
Sorry, folks. I am a newbie to Linux. I just want to use  Ubuntu. I wouldn’t know what I’m looking at when trying to see what processes take too long. 

 I just thought that somebody might know why adding persistence causes the same USB to take 30 minutes  longer to boot.

---

### Post by GhX6GZMB on 2022-05-29
Nothing strange about your USB behaviour.
1: USB reading: very fast
2: USB writing: very fast until the built-in RAM buffer is full. The buffer is perhaps 4...16 MB, not much more. Then it gets REAL slow.

ad1: Live boot: only reading from USB necessary: fast.
ad2: persistent boot: installed OS is written back to the USB: very slow.

Simple hardware limitations. BTW: going to USB3 will NOT help. The limitation is the write speed to the core memory array.

---

### Post by flabbers on 2022-05-29
> **ml9104 said:**
> Nothing strange about your USB behaviour.
1: USB reading: very fast
2: USB writing: very fast until the built-in RAM buffer is full.  I understand that. But, does it write to the flash drive even during the boot process?

---

### Post by GhX6GZMB on 2022-05-29
Unless you do a full install to your USB, the OS will be extracted and written to the USB on every session. BTW, 3 GB is painfully little and probably useless.
[https://askubuntu.com/questions/1330368/live-usb-with-persistence-vs-full-install-on-usb](https://askubuntu.com/questions/1330368/live-usb-with-persistence-vs-full-install-on-usb)

---

### Post by flabbers on 2022-05-29
> **ml9104 said:**
> Unless you do a full install to your USB, the OS will be extracted and written to the USB on every session.   And that doesn't happen if it's a Live USB without persistence? 

> **ml9104 said:**
> BTW, 3 GB is painfully little and probably useless.  Perhaps I misunderstood the uses of persistence. All I want is to be able to have some simple settings to be persistent, such as setting mouse speed and scrolling behaviour, WiFi network, and zoom level in Firefox. I thought that such settings changes might be written as simple config files to the persistent partition. Is that not correct?

---

### Post by GhX6GZMB on 2022-05-29
I'm not certain you read the link I posted. The point is this one:
"A Persistent install extracts the OS from a compressed file and saves data to an overlay file or partition each session"

If your computer does not have a disk system that's useable for Ubuntu, it will use the USB drive.

---

### Post by flabbers on 2022-05-29
Thanks.

I read it. Most of that post deals with differences between a persistent live usb and a full install to usb. I read what it said about a persistent live usb extracting the OS and saving data each session. If it's a live usb without persistence, does none of that happen?

Is there a way to save simple settings such as I described, without making the live usb so painfully slow to boot?

---

### Post by sudodus on 2022-05-30
You can start improving the speed by getting a new and fast USB 3 pendrive (which should have faster memory hardware), and create the persistent live system on that drive. Make your simple tweaked settings persistent and test how fast the system will boot for you.

I make a lot of persistent live systems and test them with various hardware because I make a tool for it, [mkusb](https://help.ubuntu.com/community/mkusb). According to my experience, the hardware (particularly the USB drive) makes a big difference in speed.

Links:

- [when old pendrives get slower](https://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)
- [link about drive speed](https://help.ubuntu.com/community/Installation/FromUSBStick/pre)

Final comment:

You can also have the partition for persistence on an internal drive (instead of on the USB drive), and that may give you a much faster system. (But then it will not be portable between computers.)

---

### Post by dragonfly41 on 2022-05-30
There are workarounds you could consider.
  
  You could open a free DropBox account and have a script in the LiveUSB (non persistent) to pull settings from DropBox into your Live USB session.
  
  You could use Cubic to create a custom Ubuntu (or other distro) ISO which is then used to create your Live USB.
  
  You could use both above thus emulating a persistent Live USB.
  
  If you use Cubic to create a custom ISO I would add a custom script to automatically access DropBox at startup. A simple but very useful automation tool I use is Actiona. In fact you will probably find that Actiona is already installed but if not use Cubic to create a pre-installed toolset in your ISO which creates Live USB.
  
  These ideas are theoretical. I use Ubuntu in an external SSD via USB 3.0 port. Also you might consider installing [rEFInd]("https://ubuntuforums.org/ROOT--rEFInd.html") during use of Cubic.
  
  I also read in post #1 ..
  &#8226; Legacy BIOS, old dual core processor, USB 2.0, 8GB RAM

This should be EFI mode.

---

### Post by flabbers on 2022-05-30
> **dragonfly41 said:**
> There are workarounds you could consider... <snip>
These ideas are theoretical... <snip> Thanks. Those ideas sound interesting, though I have no experience of any of them so would require research and work. I hoped to just find a turnkey solution, writing an ISO to the USB and then using it. I 


> **dragonfly41 said:**
> &#8226; Legacy BIOS, old dual core processor, USB 2.0, 8GB RAM


This should be EFI mode. I don't believe the motherboard supports EFI, it's 11-years old.

> **sudodus said:**
> I make a tool for it, [mkusb]("https://help.ubuntu.com/community/mkusb").  I've read good things about your tool. I used Rufus simply because I was already familiar with it.

> **sudodus said:**
> According to my experience, the hardware (particularly the USB drive) makes a big difference in speed. Thanks for the reply. Yes, I believe you. But, when booting a Live USB without persistence, the speed is acceptable. It boots in 2 minutes and when using apps the speed is okay. However, when booting the identical equipment from Live USB with persistence, boot takes more than 30 minutes.


Another poster shared a link that said that persistent live usb extracts the OS and saves data each session, which takes time. What he didn't say is whether a live usb without persistence does that or not.


What happens during boot when there is persistence that doesn't happen without persistence? Why does a Live USB with persistence take 32 minutes to boot when the identical USB without persistence takes only 2 minutes?

---

### Post by dragonfly41 on 2022-05-30
Search around for more clues ..


[https://askubuntu.com/questions/1175880/usb-persistence-not-working](https://askubuntu.com/questions/1175880/usb-persistence-not-working)

[https://ubuntuforums.org/showthread.php?t=1453690](https://ubuntuforums.org/showthread.php?t=1453690)

---

### Post by sudodus on 2022-05-30
In a persistent live system the computer reads modified or additional system tools and settings written in the partition for persistence and overlays it onto the original system of the live system. Depending on the tools and settings something might be written to the partition for persistence. Typically the time to boot may increase to the double.

We cannot answer you questions in a detailed way because we don't know enough about your hardware and not enough about the software (exactly what there is in your partition for persistence and how it interacts with the hardware).

Instead several posts by me and others describe different things that can make the operation slow, but ***you*** must test which are the main causes of the extremely slow operation with persistence in this particular case.

An alternative to doing it yourself is to get hands on help by somebody who sits together with you at your computer, maybe a member of a local linux user group.

Final tip:

If you are not prepared to test any new hardware, not even a new USB flash drive, I suggest that you try with an extremely light-weight Linux distro, for example Puppy Linux or Tiny Core Linux. There are 32-bit as well as 64-bit versions of Puppy Linux. I use Puppy (bionicpup32) in an IBM Thinkpad T42, that is 18 years old (released May 2004). The normal operation is persistent live (or frugal which is similar). With light-weight software a persistent live system can run well with very old hardware.

As I wrote earlier, persistent live Lubuntu or Xubuntu might work much faster in your computer compared to your current system, but you should test Puppy or Tiny Core too.

---

### Post by flabbers on 2022-05-30
> **dragonfly41 said:**
> Search around for more clues ..
[https://askubuntu.com/questions/1175880/usb-persistence-not-working](https://askubuntu.com/questions/1175880/usb-persistence-not-working)
[https://ubuntuforums.org/showthread.php?t=1453690](https://ubuntuforums.org/showthread.php?t=1453690) I did many searches and lots of reading before I posted here. I saw many folks saying to get faster hardware. I saw no specific details of why a persistent boot is so much slower than a regular live usb. And, I gained no understanding of why the boot process is so much slower.


> **sudodus said:**
> ... Thank you for the replies. I am a linux newbie. I'm a Windows user, and I just want to occationally use linux when I need to solve problems on my PC or friends' PCs.


> **sudodus said:**
> In a persistent live system the computer reads modified or additional system tools and settings written in the partition for persistence and overlays it onto the original system of the live system. Depending on the tools and settings something might be written to the partition for persistence. Typically the time to boot may increase to the double. Would that be the case even for a brand-new live usb with persistence that has not yet been used?  I haven't yet written anything to the persistence partition.


> **sudodus said:**
> We cannot answer you questions in a detailed way because we don't know enough about your hardware and not enough about the software (exactly what there is in your partition for persistence and how it interacts with the hardware). I can provide full hardware details if you think it would be useful. As for the software, it's whatever Rufus created when writing the Ubuntu ISO to the usb flash drive. I'm a Windows user, so I use a Windows application to create the live usb.


> **sudodus said:**
> If you are not prepared to test any new hardware, not even a new USB flash drive,  I don't see how you conclude that. I opened this thread only yesterday, so not surprising that I haven't yet rushed out to buy a new flash drive.
I tested with other flash drives, and tested on multiple PCs. I can get a new flash if it would make a difference. 


> **sudodus said:**
> I suggest that you try with an extremely light-weight Linux distro, for example Puppy Linux or Tiny Core Linux. There are 32-bit as well as 64-bit versions of Puppy Linux. I use Puppy (bionicpup32) in an IBM Thinkpad T42, that is around 20 years old. The normal operation is persistent live (or frugal which is similar). With light-weight software a persistent live system can run well with very old hardware... persistent live Lubuntu or Xubuntu might work much faster in your computer compared to your current system, but you should test Puppy or Tiny Core too. Thanks. I'll try that.


I've seen many posts from users saying that persistence causes very slow boots, but no real solutions other than faster equipment. Still, that doesn't really explain why the identical equipment is fast when there is no persistent partition. I would have thought that a newly-created live usb with persistence would have similar boot time to a live usb without persistence. When booting a live usb without persistence, it's fast. Maybe I'm missing something.

---

### Post by sudodus on 2022-05-30
> **flabbers said:**
> ...

 Would that be the case even for a brand-new live usb with persistence that has not yet been used?  I haven't yet written anything to the persistence partition.

The more you write to the persistence partition the slower it should be. If you write nothing, the system itself will write some files, but nothing big, so it should not get very slow, not at all 10-15 times slower (in your case).
> 
 I can provide full hardware details if you think it would be useful. As for the software, it's whatever Rufus created when writing the Ubuntu ISO to the usb flash drive. I'm a Windows user, so I use a Windows application to create the live usb.

Good, try with the [Ubuntu Forums system-info script](https://github.com/UbuntuForums/system-info/): boot into your persistent live Ubuntu system, download system-info, run it, let it upload the result to a pastebin, and post the link to the pastebin in a new post here.
> 
 I don't see how you conclude that. I opened this thread only yesterday, so not surprising that I haven't yet rushed out to buy a new flash drive.
I tested with other flash drives, and tested on multiple PCs. I can get a new flash if it would make a difference. 

Sorry, I jumped to conclusions. If you wish, I can suggest suitable USB drives depending on your cost limit.

If your computer is a laptop, is there an eSATA port? If it is a desktop, you might add an eSATA card (if there is a free place to put a plug-in card). That will give you fast access to an external drive, just like an internal SATA drive. It is good for this purpose (to run persistent live), and will also provide a fast connection to a backup drive.
> 
I've seen many posts from users saying that persistence causes very slow boots, but no real solutions other than faster equipment. Still, that doesn't really explain why the identical equipment is fast when there is no persistent partition. I would have thought that a newly-created live usb with persistence would have similar boot time to a live usb without persistence. When booting a live usb without persistence, it's fast. Maybe I'm missing something.

It is possible that there is something wrong with the persistent live system. It is also possible that the computer has not got enough 'horsepower' or RAM to run well with your current version and flavour of operating system. [COLOR="#000080"]*The more I think about your problem the more I suspect that you have not got enough RAM, so the system needs the slow USB drive to write things that should normally reside in RAM.* This should be improved a lot with a light-weight flavour like Lubuntu or Xubuntu, and even more improved with ultra-light Puppy Linux or Tiny Core Linux.[/COLOR]

My experience of Rufus is good. It is a good tool to create both live-only and persistent live drives from Windows. If you have a current version of Rufus, it should not cause any major problem. (My mkusb is an alternative, but you need Ubuntu to use it, so until you have a good persistent live system or installed system, I suggest that you continue using Rufus.)

---

### Post by flabbers on 2022-05-31
> **sudodus said:**
> try with the Ubuntu Forums system-info script... <snip> post the link to the pastebin in a new post here. Good morning. Thank you for the assistance.

Report at [http://termbin.com/fa3u](http://termbin.com/fa3u)

> **sudodus said:**
> If your computer is a laptop, is there an eSATA port?  This particular laptop doesn't have eSATA. But, that's a good suggestion for other PCs, thanks. 

> **sudodus said:**
> I suspect that you have not got enough RAM, so the system needs the slow USB drive to write things that should normally reside in RAM. The laptop in question, 32-minute boot, has 8 GB RAM. I also ran the same Live USB on another laptop, also old but much faster CPU etc., that has 16 GB RAM. The Live USB with persistence was also very slow to boot on that laptop, 25 minutes.

---

### Post by sudodus on 2022-05-31
Thanks for the link to the pastebin :-)

The cpu is rather weak, the model was released during 2011, and has 2 cores (and 2 threads) according to details from ark.intel.com. But I don't think it is causing the extremely slow boot.

```

    Description: CPU
    Product: Intel(R) Pentium(R) CPU B950 @ 2.10GHz
    Vendor: Intel Corp.
    Physical id: 4
    Bus info: cpu@0
    Version: Intel(R) Pentium(R) CPU B950 @ 2.10GHz
    Serial: [REMOVED]
    Slot: CPU 1
    Size: 1042MHz
    Capacity: 2100MHz
    Width: 64 bits
    Clock: 100MHz

```

There seems to be enough RAM :-)

```

---------- Memory Information:
              total        used        free      shared  buff/cache   available
Mem:          7.7Gi       1.0Gi       5.0Gi       309Mi       1.7Gi       6.1Gi
Swap:            0B          0B          0B

```


I have a few questions about the USB devices:
```

---------- USB Information from 'lsusb -t -v':
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
        ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
        |__ Port 6: Dev 3, If 0, Class=Mass Storage, Driver=ums-realtek, 480M
            ID 0bda:0138 Realtek Semiconductor Corp. RTS5138 Card Reader Controller
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    ID 1d6b:0002 Linux Foundation 2.0 root hub
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M
        ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
        |__ Port 1: Dev 3, If 0, Class=Mass Storage, Driver=usb-storage, 480M
            ID 0011:7788 [COLOR="#cc0000"]**Unknown counterfeit flash drive**[/COLOR]                      # This drive might be really slow when writing
        |__ Port 4: Dev 4, If 2, Class=Vendor Specific Class, Driver=, 12M
            ID 0a5c:21bc Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR           # what if you turn off Bluetooth?
        |__ Port 4: Dev 4, If 0, Class=Wireless, Driver=btusb, 12M
            ID 0a5c:21bc Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR
        |__ Port 4: Dev 4, If 3, Class=Application Specific Interface, Driver=, 12M
            ID 0a5c:21bc Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR
        |__ Port 4: Dev 4, If 1, Class=Wireless, Driver=btusb, 12M
            ID 0a5c:21bc Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR
        |__ Port 5: Dev 5, If 0, Class=Video, Driver=uvcvideo, 480M            # what is this (video via USB 2)? Can it be turned off?
            ID 0c45:643e Microdia 
        |__ Port 5: Dev 5, If 1, Class=Video, Driver=uvcvideo, 480M
            ID 0c45:643e Microdia 

```

---

### Post by tea for one on 2022-05-31
This thread piqued my interest, especially:-
> The laptop in question, 32-minute boot, has 8 GB RAM. I also ran the same Live USB on another laptop, also old but much faster CPU etc., that has 16 GB RAM. The Live USB with persistence was also very slow to boot on that laptop, 25 minutes. 
> ID 0011:7788 Unknown counterfeit flash drive                      # This drive might be really slow when writing
Anyway, It encouraged me to conduct an unscientific experiment.

[COLOR="#0000FF"]USB device:[/COLOR]  Sandisk Ultra USB 3.00 16GB
[COLOR="#0000FF"]Target PC:[/COLOR]     2019 vintage, Intel NUC6AYH with 4GB RAM and Celeron J3455 processor
[COLOR="#0000FF"]USB Port:[/COLOR]   Front port version 2.0
[COLOR="#0000FF"]Iso:[/COLOR]               Lubuntu 22.04 (LXQT) with 4GB Persistent Storage
[COLOR="#0000FF"]Details:[/COLOR]	     UEFI and GPT on USB and target PC

[COLOR="#0000FF"]Using Rufus 3.18 in Windows 11[/COLOR] – Grub selection to Desktop [COLOR="#0000FF"]63 seconds[/COLOR]
[COLOR="#0000FF"]Using mkusb (dus 22.0.6) in Ubuntu 22.04[/COLOR] – Grub selection to Desktop [COLOR="#0000FF"]61 seconds[/COLOR]

@sudodus – 2 seconds quicker – Guinness Book of Records have been contacted ;)

---

### Post by dragonfly41 on 2022-05-31
[COLOR=#0000FF]> Details: [/COLOR]> [COLOR=#000000]UEFI and GPT on USB and target PC[/COLOR][COLOR=#000000]

One difference I read in post #1 and confirmed by OP ..
No UEFI.

It would be helpful to respondents if OP would give some hint of what the LiveUSB is to be used for.
Maths, Games, Coding ??[/COLOR]

---

### Post by flabbers on 2022-05-31
> **dragonfly41 said:**
> No UEFI. Yes, it's an old laptop that does not support UEFI.
> **dragonfly41 said:**
> It would be helpful to respondents if OP would give some hint of what the LiveUSB is to be used for.  To use when I work on friends'/family's PCs, to troubleshoot issues. Yesterday I used it to save user files from a friend's non-booting PC.


> **sudodus said:**
> Thanks for the link to the pastebin  Thanks for suggesting it and reviewing it.


> **sudodus said:**
> The cpu is rather weak, the model was released during 2011, and has 2 cores (and 2 threads) according to details from ark.intel.com.  Indeed, yes. I'm the guy that friends and family ask for PC help. I'm working on this PC for a friend's child.


> **sudodus said:**
>  ```
 <snip>
        |__ Port 1: Dev 3, If 0, Class=Mass Storage, Driver=usb-storage, 480M
            ID 0011:7788 Unknown counterfeit flash drive                      # This drive might be really slow when writing
        |__ Port 4: Dev 4, If 2, Class=Vendor Specific Class, Driver=, 12M
            ID 0a5c:21bc Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR           # what if you turn off Bluetooth?
<snip>
        |__ Port 5: Dev 5, If 0, Class=Video, Driver=uvcvideo, 480M            # what is this (video via USB 2)? Can it be turned off?
            ID 0c45:643e Microdia

```
Interesting. I wonder how it defines "counterfeit". This is a Duracell brand flash drive from a reputable major electronics chain.

Re. Bluetooth, I'll try that. Bluetooth must be enabled by default in the Ubuntu ISO.

Re. the video, I have no idea what that is. Maybe the built-in webcam?

I think you hit the nail on the head with the flash drive. A Sony flash drive boots much faster.

I still find it odd that Ubuntu needs to write to the persistent partition during boot, epecially when nothing has yet been written to persistence. I would have thought nothing would need to be written until I changed some settings.

---

### Post by sudodus on 2022-06-01
> **flabbers said:**
> 
I think you hit the nail on the head with the flash drive. A Sony flash drive boots much faster.


Please tell us your results (the time to boot a persistent live system)

- with a USB 3 pendrive (with at least 16 GB) and with explicit read and write speeds in the specification
- with a lighter Ubuntu flavour (Lubuntu or Xubuntu) or even an ultra-light Linux distro (Puppy or Tiny Core)  :-P

Good luck

---

### Post by KyleCF on 2023-01-24
Have you tried booting the same USB on another computer? It could be that your motherboard is garbage.

My USB flash disk is a Sandisk Extreme Pro 3.1 drive. It's faster than my internal disks. I have installed Ubuntu on the flash disk as though the USB is an HDD. On my ASUS gaming PC, and my wife's Gigabyte laptop, the USB boots in under a minute. On my MSI gaming laptop, an Alpha 15 A3DD (which, by spec, only has fast USB ports), it takes 30+ minutes to boot. I've tweaked every setting possible in the BIOS and get the same result. I then tested on another MSI laptop (a GS70 20OD Stealth) and got the same bad result, which tells me MSI laptops are simply designed to be this way.

---

### Post by flabbers on 2023-02-12
> **KyleCF said:**
> Have you tried booting the same USB on another computer? It could be that your motherboard is garbage. I have now tried on multiple PCs. The speed varies on different systems, as I would expect.

The point of this thread was not the specific speed to load/boot. The point is how much slower a Live disk is when persistence is added.

When persistence is present, the flash drive is accessed frequently. Even when the system is idle and I'm not doing anything, the flash drive is reading or writing. It seems that there is a lot of unnecessary activity when the drive has persistence. I think drive operations could be made more efficient under persistence to eliminate unnecessary writing that slows things down.

---

### Post by sudodus on 2023-02-12
The Ubuntu developers seldom visit this web-site. I think you have better luck when suggesting improved performance during persistent live operation at [https://discourse.ubuntu.com/](https://discourse.ubuntu.com/).

But be aware that persistent live operation has a rather low priority among the Ubuntu developers.

We are a few volunteers, that try to help people use what is available without modifying the Ubuntu code. (I develop and maintain [mkusb](https://help.ubuntu.com/community/mkusb), a tool to make live-only and persistent live USB boot drives.)

---

### Post by flabbers on 2023-02-13
> **sudodus said:**
> But be aware that persistent live operation has a rather low priority among the Ubuntu developers. Thanks, I appreciate your insights.

---

### Post by DuckHook on 2023-02-13
> **flabbers said:**
> …The point is how much slower a Live disk is when persistence is added.

When persistence is present, the flash drive is accessed frequently. Even when the system is idle and I'm not doing anything, the flash drive is reading or writing. It seems that there is a lot of unnecessary activity when the drive has persistence. I think drive operations could be made more efficient under persistence to eliminate unnecessary writing that slows things down.
I don't find this so surprising. A LiveUSB needs to do only one thing: read the data on the drive. It *never* has to write. Hence, the slowest part of disk access is eliminated. When a disk is tagged as read only, such as is the case with a LiveUSB, the system does not even try to write to it.

Depending on the USB stick, writes can be 10 times slower than reads. USB sticks have a microcontroller that determines where writes will go to. It does this in the interest of write balancing because USB sticks have a limited number of writes to any physical location. If it uses the same locations all the time, then the USB stick will quickly burn out and become unwritable. To prevent this, the microcontroller spreads writes all over the stick, keeping track of how often locations have been written to so that different locations can be rotated into use. All of this requires a lot of processing and the microcontroller on a USB stick is usually cheap and slow.

Since a persistent stick is by definition writable, this means that it must constantly hold open its inode table and run all sorts of invisible infrastructure like journaling. This hidden overhead is substantial. On a fast HDD or SSD, it isn't noticeable. On a slow USB stick it becomes very noticeable. Also, once writes are enabled, the OS treats it as a standard and typical disk, which means that write data will often be cached and written to disk only when the system feels like it. This will take the form of delayed disk access well after the time when you think there should be any activity.

---

