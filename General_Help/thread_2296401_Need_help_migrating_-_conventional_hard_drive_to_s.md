---
title: "Need help migrating - conventional hard drive to solid state drive - dual boot laptop"
date: 2015-09-25
forum: General Help
---

### Post by ask_ on 2015-09-25
Hello,

I have a Lenovo Laptop :- 
[COLOR=#000000]Lenovo Essential G Series G560-(59-304299) Laptop 

[/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]PROCESSOR[/FONT][/COLOR]
Processor    Core i3
Variant    370M
Chipset    Mobile Intel HM 55 Express
Brand    Intel
Clock Speed    2.4 GHz
Cache    3 MB
MEMORY
Expandable Memory    Upto 8 GB
Memory Slots    2 (Unused Slot - 1)
System Memory    2 GB DDR3
STORAGE
Hardware Interface    SATA
RPM    5400
HDD Capacity    500 GB
OPTICAL DISK DRIVE
Optical Drive    Tray-in Rambo drive
PLATFORM
Operating System    Free DOS
DISPLAY
Screen Size    15.6 Inch
Resolution    1366 X 768 Pixels
Screen Type    HD LED Glare Display
INPUT
Web Camera    0.3 Megapixel
Pointer Device    Touchpad
Keyboard    Standard Keyboard
AUDIO
Internal Mic    Yes
Speakers    Yes
COMMUNICATION
Ethernet    10/100/1000M LAN
Wireless LAN    802.11 b/g/n
Bluetooth    v2.1
POWER
Battery Backup    Up to 3 hours
Power Supply    65 W AC Adapter
Battery Cell    6 Cell Lithium-ion
PORTS/SLOTS
USB Port    Yes
Mic In    Yes
RJ45 LAN    Yes
VGA Port    Yes
Multi Card Slot    Yes
MACHINE DIMENSIONS
Weight    2.24 kg
Dimension    376 x 250 x 20-35.5 mm [COLOR=#000000][FONT=Ubuntu Mono]Color    Black[/FONT][/COLOR]
```[COLOR=#000000]


On this laptop I have a dual boot going on. One OS is Ubuntu 14.04 and the other is Windows 7. I am thinking of buying this hard drive :-
[/COLOR]http://www.amazon.com/Samsung-2-5-Inch-Internal-MZ-75E500B-AM/dp/B00OBRE5UE/ref=sr_1_2?s=pc&ie=UTF8&qid=1443198433&sr=1-2&keywords=solid+state+drive 

[COLOR=#000000]My goal is to shift from my hard drive in the laptop to this one, and use the system as it is. 
1) A  question I have , in context of my particular laptop, can I install an SSD into it ?


2) As I understand this, I must clone my hard drive into the solid state drive. But I have heard that the software which accompanies these ssds does not recognise Ubuntu partitions. Hence I am looking for a software which allows me to do this . (can you also suggest an accompanying tutorial webpage for it).

3) Do the physical sizes of the two hard drives have to be the same. Or will it suffice that the solid state drive has enough free space.

I wish to use my current system for at least 2 more years hence I am thinking of shifting to an SSD. The reason is that my hard drive is already 3.5 years old , and I wish to avoid hard disk crash.

Here's the current statistics on the same :- 

[/COLOR]```
Lenovo-G560:~$ sudo smartctl -a /dev/sda | egrep '(Load_Cycle_Count|Temperature)'
193 Load_Cycle_Count        0x0032   168   168   000    Old_age   Always       -       98796
194 Temperature_Celsius     0x0022   103   092   000    Old_age   Always       -       44



```

[COLOR=#000000]I like my system in it's current state, I don't wish to go through the hassle of installing a new ubuntu on another laptop if the need arises, and install all my favorite software again.



Thanks.
[/COLOR]

---

### Post by leepe on 2015-09-25
If you have a SATA hard drive currently installed, then yes you can put an SSD in your system. Be careful though: you might need an adapter sled to make it mount properly. Most laptops have 2.5" drive bays for their hard drives, but they come in different thicknesses. Chances are you don't need one, but it's up to you to determine that for good. Poke around on some forums to see if anybody has done it et and shared their experience. This article [http://www.pcadvisor.co.uk/how-to/laptop/how-upgrade-your-laptop-hard-disk-ssd-3366618/](http://www.pcadvisor.co.uk/how-to/laptop/how-upgrade-your-laptop-hard-disk-ssd-3366618/) has been a great resource for some of my friends in the past. It won't tell you exactly what you need, but it will at least point you in the right direction.
As far software, Clonezilla (clonezilla.org) seems like a good choice. I've never user it before, but I hear it is very good, and has all the functionality you are looking for. The disk doesn't have to be the same size, but it seems like you might have to do some extra configuration it it isn't.
Here's a guy who had a similar problem (for reference): [http://askubuntu.com/questions/222193/cloning-a-dual-boot-system-from-hdd-to-ssd](http://askubuntu.com/questions/222193/cloning-a-dual-boot-system-from-hdd-to-ssd)
Good luck!

---

### Post by grahammechanical on 2015-09-25
Ubuntu partitions are no different from the partitions used by any other Linux Distributions. In fact the default partition file system is not a Ubuntu file system at all but a Linux file system called Ext4. If my understanding is correct, then the complete partitioning scheme on the old hard disk is replicated on the new hard disk. The new disk must be the same size of the old disk or greater. As an interim step you will need somewhere to store the compressed image that is created. You may find that extra space on the new hard disk is not used.

You have a 500 GB hard drive. So, you will need a 500 GB SSD. If you use drive cloning.

[https://help.ubuntu.com/community/DriveImaging](https://help.ubuntu.com/community/DriveImaging)

Regards

---

### Post by ask_ on 2015-09-25
Thanks all. For the replies. Will try the stuff.  By the way , what is usual load cycle count after which hard disks become unreliable. Currently mine is a little bit below 100,000

---

### Post by ask_ on 2015-09-26
> **grahammechanical said:**
>  As an interim step you will need somewhere to store the compressed image that is created. You may find that extra space on the new hard disk is not used.




I did not understand what is meant by compressed image in this case. 
Do you mean if I buy a 500 GB SSD, I will need additional space to store the image in the interim step ? Kind of like an external hard drive in addition to the SSD ?

Or do you simply refer to the image of the original hard drive which will be cloned on to the SSD ?

I am confused by what is referred to as compressed image in the interim step.

Thanks.

---

### Post by ask_ on 2015-09-30
Guys, I am done with the migration . 
Now my system has a 500 GB Samsung SSD. :D 

I used Clonezilla to do the cloning. Thanks for suggesting that software. The dual boot system was cloned quite nicely using it. And putting the drive in the laptop bay also did not give me much trouble.

Thanks.

---

