---
title: "[SOLVED] Cannot boot from neither CD-ROM drive nor hard disk!"
date: 2007-04-28
forum: General Help
---

### Post by bcasanov on 2007-04-28
I cannot boot from my CD-ROM drive nor my hard drive, when just a few hours ago, I was able to boot up into Linspire.  Then, the next time I turned on my computer, it was not able to boot up.  That is when I decided to try the live CD of Ubuntu 7.04 that I had recently burnt, in the hopes of someday replacing Linspire, as it has caused me numerous problems before.  

Well, I inserted my Ubuntu CD, made sure in the BIOS boot sequence to boot from the CD-ROM drive, but then, it did not boot up and displayed the message to press F1 to reboot or F2 to configure my BIOS.  I tried rebooting several times, but to no avail.  Investigating the matter further, I looked in the BIOS and found to my surprise that in the boot sequence, my CD-ROM drive (listed as the first item) and my hard disk drive (as the second item) were both listed as uninstalled!  I absolutely do not know how that happened.  I do not know how to solve the problem either; I am utterly clueless.  

Here are my specs obtained from my BIOS (this is a relatively old computer): 
Dell Optiplex GX150 computer- BIOS version: A09
SDRam: 256 Megabytes 
System memory speed: 133 MHz
Video memory: 1 MB
Processor: Intel Pentium III&#8212;1 GHz
Level 2 Cache:  256 KB integrated

Any time you need any further information on my computer in order to fully understand the problem and provide a solution, I will gladly furnish it.

---

### Post by sharke on 2007-04-28
Go into your bios somwhere there should be something like default settings or safe settings or optimal settings select this .and save and reboot Your problem is definetly computer related not the operating system.
Regards
Sharke

---

### Post by honeydew on 2007-04-28
If that dosnt work.. you may be having bios issues.. possibly reset the bios(pull the battery)

---

### Post by bcasanov on 2007-04-29
> **sharke said:**
> Go into your bios somwhere there should be something like default settings or safe settings or optimal settings select this .and save and reboot Your problem is definetly computer related not the operating system.
Regards
Sharke

Thank you Sharke for your kind and prompt response!  This goes to show how marvelous and friendly the community in this forum is.  Well, in response to your advice, I do agree with you that the problem is in my computer.  I really am not sure I can see an option in my particular BIOS to go back to default or optimal settings.  Here is the list of options I am directly presented with when I enter BIOS; perhaps you or someone else could show me one that could work as you stated, although I did try quite a few of those options, if not most of them:

System Time
System Date
Diskette Drive A 
" " B
Zip Floppy Support
Primary Drive 0
" " 1
Secondary Drive 0
" " 1
Boot Sequence
Memory Information
CPU Information
Integrated Devices
PCI IRQ Assignment
IRQ Reservations
System Security
Keyboard NumLock
Report Keyboard Errors
Auto Power On
Remote Wake Up 
AC Power Recovery
Fast Boot
Suspend Mode
System Event Log
Asset Tag

Regards, 
bcasanov

---

### Post by bcasanov on 2007-04-29
> **honeydew said:**
> If that dosnt work.. you may be having bios issues.. possibly reset the bios(pull the battery)

Thank you honeydew for your response; I am grateful that people in this forum can respond relatively quickly to concerns in a caring, considerate way!  In regard to your advice, my computer is not a laptop wherein I could reset the BIOS through taking out the battery.  I do not know how resetting the BIOS can be accomplished on my computer.  It is a rather old computer, I would have to say.  :)  

Regards, 
bcasanov

---

### Post by sharke on 2007-04-29
The battery refered to is the cmos battery you have to open rhe case to find it. i dont reccomend you do this. Go back into the bios and have agood look i think you may have missed something it should have somewhere to configure your drives, As your computer boots it may list your bios type if so please post it here
Regards Sharke

---

### Post by bcasanov on 2007-04-29
> **sharke said:**
> The battery refered to is the cmos battery you have to open rhe case to find it. i dont reccomend you do this. Go back into the bios and have agood look i think you may have missed something it should have somewhere to configure your drives, As your computer boots it may list your bios type if so please post it here
Regards Sharke

Thank you Sharke for your clarification about the battery honeydew referred to.  When my computer boots up, it displays the following:
Optiplex GX 150
Bios Revision A09

That did not seem like it showed my bios type, so I investigated online on my other computer and found on this website, [http://support.dell.com/support/edocs/systems/opgx150/en/ug/specs.htm#system_information](http://support.dell.com/support/edocs/systems/opgx150/en/ug/specs.htm#system_information), that my bios type seems to be: 

Desktop Management Interface (DMI) 2.0s- and system management BIOS 2.3-compliant BIOS in 4-megabit (Mb) flash chip

I hope that information is more helpful. 

Regards,
bcasanov

---

### Post by bcasanov on 2007-04-29
I found from this Dell forum, [http://www.dellcommunity.com/supportforums/board/message?board.id=oplex_bios&message.id=9597](http://www.dellcommunity.com/supportforums/board/message?board.id=oplex_bios&message.id=9597), that I could reset my specific bios to default settings by pressing alt-f.  I booted into the bios, reset it, and then, when I looked up the boot sequence, my cd-rom drive and hard disk drive do not show up!

The only options that are displayed in the boot sequence are:

1. Diskette drive
2. Integrated NIC

If by "Diskette drive," it means floppy disk drive, then that seems to be my only bootable option for right now, as I do not know how to boot from my NIC (Network Interface Card, I think).    :(

---

### Post by GuitarRocker2562 on 2007-04-29
you may want to try opening your computer, spay it with dust-off (there will be dust) and re-connect the HDD and CD drive.

---

### Post by bcasanov on 2007-04-29
> **GuitarRocker2562 said:**
> you may want to try opening your computer, spay it with dust-off (there will be dust) and re-connect the HDD and CD drive.

Thank you GuitarRocker2562 for your advice.  The thing is that I am an almost complete noob when it comes to going inside the gut of my computer hardware iin order to solve the problem of reconnecting the HDD and CD drive.  Perhaps if that is my last and only option, I would be absolutely willing to learn to do it with your help and the aid of other community forum members.  But is there still hope that I could, for example, boot from a floppy disk with a Linux distribution like Puppy Linux or other relatively small distro, and determine and solve the problem that way?

Regards,
bcasanov

---

### Post by ashz on 2007-04-29
The problem is a BIOS problem, that has already been established.

I suggest to either... 

1. Take to a computer service person
2. Attempt to do it yourself....which if ur a complete noob I would not recommend....because it could be something reasonably easy like replacing a cmos battery (which i doubt) or a new motherboard...in which case i would recommend taking it tobe serviced!!

Cheers
Ash

---

### Post by bcasanov on 2007-04-29
> **ashz said:**
> The problem is a BIOS problem, that has already been established.

I suggest to either... 

1. Take to a computer service person
2. Attempt to do it yourself....which if ur a complete noob I would not recommend....because it could be something reasonably easy like replacing a cmos battery (which i doubt) or a new motherboard...in which case i would recommend taking it tobe serviced!!

Cheers
Ash

Hello, Ashz, and thank you for your kindly advice.  I just have the question: Because the problem is a BIOS problem, then would there be no possible hope to solve it through booting from a floppy bootdisk and trying to reconnect the CD-ROM drive and HDD from the software?  If there exists that hope, then what software (like MS-DOS, Puppy Linux, Damn Small Linux, or any small Linux distro) would you recommend I should choose to boot from?  If the BIOS problem can only be solved by going through the hardware, then I will probably have to take my computer to a support person, but I want to exhaust all my other options before going that route.

Regards,
bcasanov

---

### Post by bcasanov on 2007-04-30
Could the problem also be solved by updating my BIOS?  I do not know how to do that, though.

---

### Post by JTux on 2007-04-30
I don't think is is possible to update a BIOS without booting in to an OS

You can boot Damn Small Linux from a floppy but you will need a DSL cd during the boot process

The DSL wiki describes how to boot DSL from a floppy:
[(http://www.damnsmalllinux.org/wiki/index.php/Boot_Floppies)]("http://www.damnsmalllinux.org/wiki/index.php/Boot_Floppies")

You will need another linux machine,  or 
a windows machine where you can install apps.

---

### Post by sharke on 2007-04-30
yes i think it is a problem with your mother board. But it is worth trying to restore the bios go herehttp://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R47131&formatcnt=3&libid=0&fileid=55571 and follow instructions carefully.
Regards
Sharke

---

### Post by bcasanov on 2007-04-30
> **sharke said:**
> yes i think it is a problem with your mother board. But it is worth trying to restore the bios go herehttp://support.us.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R47131&formatcnt=3&libid=0&fileid=55571 and follow instructions carefully.
Regards
Sharke

Sharke, I sincerely thank you as well as the other posters in this thread who have helped me enourmously!  I am extremely grateful to all of you who have taken the time to help me with the problem.  I will be sure to refer others to this friendly, superb forum community of Ubuntu.  

I have followed your advice, and lo and behold, I have successfully updated to the A10 version of the BIOS, looked in the boot sequence, and my cd-rom drive finally appears!  Yesss!  :)   

However, the damper to this positive experience is that my hard disk drive still seems to not be installed or recognized, because when I booted up, the computer stated: "Primary hard disk drive 0 not found.  Strike the F1 key to continue, F2 to run the setup utility."  Striking the F1 key just gives me the same message again.  Pressing the F2 key took me to the BIOS configuration screen.  There, the primary drive 0 is listed as "Unknown Device."    Perhaps the problem could be solved if I boot into the Ubuntu live CD and try to fix it from there somehow, but I do not really know the procedure in Ubuntu to recover or "rediscover" the HDD.

Again, I appreciate the genuine, helpful efforts of everyone who has helped me.

Regards,
bcasanov

---

### Post by aldenhg on 2007-04-30
It really sounds like you might just have a cable or two loose on the inside. If you have even a faint idea of what your hard drive might look like, I'd bet you could fix it just by making sure the cable is all the way in. Also, if this is an older computer that has never been opened up chances are there's an awful lot of dust in there. If that's the case, go pick up a can of compressed air (you can find them at computer or photo stores), open the computer up, take it outside and blast that dust out until it's all gone. Dust can cause a lot of funky problems in a computer, so it just might take care of your problems.
If you're scared of tinkering with anything on the inside, take it to a repair shop. Be prepared for them to charge you an arm and a leg, but they can at least take a look under the hood and tell you if it's something simple.

---

### Post by sharke on 2007-04-30
[http://www.austincc.edu/cloud/manuals/Dell/GX150/advfeat.htm#additional_setup_opts](http://www.austincc.edu/cloud/manuals/Dell/GX150/advfeat.htm#additional_setup_opts)
take a look explains howto use your bios setup utility.
Regards
Sharke

---

### Post by bcasanov on 2007-04-30
> **sharke said:**
> [http://www.austincc.edu/cloud/manuals/Dell/GX150/advfeat.htm#additional_setup_opts](http://www.austincc.edu/cloud/manuals/Dell/GX150/advfeat.htm#additional_setup_opts)
take a look explains howto use your bios setup utility.
Regards
Sharke

Now I understand that my hard disk drive probably is not automatically detected, because when I look into the primary drive 0, the drive type shows up as automatic, but it still displays the "unknown device" error. I would have to manually configure the HDD, but I do not know the specific drive type number that would fit it; I do not have the manual that came with my Dell that could possibly have that information. 

Regards, 
bcasanov

---

### Post by bcasanov on 2007-04-30
Now that I can boot from the CD-ROM drive, I went ahead and used the live CD to go into Ubuntu. The only thing during the command list of loading items that did not display an ok to the right was the one that stated something like "loading filesystems."  Because the lines moved relatively fast, I did not have time to jot down the particular error.  However, the error was not so grave, as it did not prevent me from booting into Ubuntu.  

Is it possible that the problem of the HDD not being detected could be solved by mounting the HDD into Ubuntu root or something similar?  I tried to install Ubuntu, but when it came to the part about partitioning the disk, it did not show any partition or HDD, so I gathered that perhaps the HDD was not mounted.  From some of the advice gathered on the forums, I checked etc/fstab, having heard that it displays some of the not-yet-mounted partitions, filesystems, and drives.  My etc/fdisk states this: 

unionfs / unionfs rw O O
tmpfs /tmp tmpfs nosuid,nodev O O

This seems cryptic to me, and I do not really know how to gather from this information what/where/how to mount the internal HDD.

---

### Post by sharke on 2007-04-30
I discussed your problem with my computer support team at my work and he tells me a common complaint with this computer of yours is over time the heatsinks on the CPUs work loose and the CPUs go   into thermal off mode while in Setup. The CPUs and heatsinks are under a large fan shroud. You will have to open the case to see if this is the problem.
Regards
Sharke

---

### Post by sandman55 on 2007-04-30
Hi bcasanov the guys have given you some good advice but the problem could still be from your motherboard there has been a problem sometime before 2000 when a Tiwan company pirated the formulas for making electrolytic capacitors but they didnt get it right and these faulty caps were used in many motherboards before it was realised.
If you look inside your computer after you unplug it from the wall socket you will see many capacitors on the motherboard they look like little cans mounted on their ends (you cant miss them) and the end that faces you has a X scored into the aluminium to provide a weakness in the can so that if it develops an internal short it will pop out the X weakness. Now the thing to look for is if the X is bulging and perhaps leaking you will see a dark discolouring on the shiny aluminium end. If this is the case its a good sign that your motherboard has either had it, or is on the way out, this is also something to check when buying a secondhand computer.

Be careful when your working inside your computer if you touch anything you could do damage by discharging static electricity. Ways to prevent this are to frequently touch the metal of the case to discharge any static, try not to work on carpet and some people even work barefooted :) Professionals wear a strap on their wrist with a flexible wire to the case.

---

### Post by bcasanov on 2007-04-30
I have opened the case of my computer, and here is how the inside looks:

[ATTACH]31345[/ATTACH] [ATTACH]31346[/ATTACH] [ATTACH]31347[/ATTACH] [ATTACH]31348[/ATTACH]

It seems as though there might be no damage to the wires, cables; I touched some of the them to see if they were loose, and they seem to be firmly attached.  I think everything looks sound in terms of the various devices positioned in the motherboard, which I think is the long green thing with lots of numbers on the bottom of the case.  

However, there were cobwebs entangled in the lower right part of the case (not noticeable from the pictures), and there was lots of dust situated in the big tower structure (I might assume that is the CPU or a part of it).  I took out the cobwebs as well as the dust in the tower.

I can see where the CD-ROM drive and floppy disk drive are situated inside the case, but I wonder where the hard drive might be.  Perhaps it has a serial number or identification that could help me know exactly what type of HDD it is, whether it is SATA, ATA, etc.  I would need to know exactly what type of HDD I have so that I could boot up diagnostic software, such as [http://www.hitachigst.com/hdd/support/download.htm#DFT](http://www.hitachigst.com/hdd/support/download.htm#DFT), to help me bring the HDD back to life.  

I hope the pictures are clear enough; if you need a better close-up, I'll gladly furnish it.

---

### Post by bcasanov on 2007-04-30
Strangely, in my BIOS, when I go through the various possible configurations for the primary device 0, the maximum capacity that is available in the device configuration is something like 528 MB.  My hard disk drive has more like 20 GB.  I do not know the HDD's cylinders, heads or sectors per track, but in this website, [http://www.csgnetwork.com/harddisk.html](http://www.csgnetwork.com/harddisk.html), I found that  cylinders x heads x sectors per track x 512 (bytes per sector) = capacity.  

On that website, I also found the following information perhaps relevant to my case: 

> IDE hard disks larger than 504 MB require more than 1024 cylinders in the CMOS memory (or they could instead use more than 63 sectors per track, but this is very rare). As a result, drives of this size are not compatible with the system BIOS INT13h interface and the entire drive cannot be used unless geometry translation is being employed by the hard disk controller. Because most IDE controllers do not use geometry translation, IDE hard disks are almost always subject to the 1024-cylinder limit as imposed by the system AT ROM BIOS.

So, perhaps the problem with the HDD not being correctly detected could be a result of the hard disk controller not using geometry translation.  Among the suggestions to solve this problem is the advice to update the BIOS.  I had already updated to version A10 of the BIOS, so I decided to flash the Bios to A11. This version did not solve the problem either.  

The next tip that is suggested is to see if my CMOS memory has enabled LBA (logical block addressing) support .  I do not know how to enable LBA, because I have looked at all the options available in my BIOS and found that none of them mention LBA.

---

### Post by bcasanov on 2007-04-30
In answer to my own question, I learned from this website, [http://www-pc.uni-regensburg.de/hardware/PC/DELL/GX150/manual/gx150sg/smdsktp.htm](http://www-pc.uni-regensburg.de/hardware/PC/DELL/GX150/manual/gx150sg/smdsktp.htm), that the hard disk is located on the top cover (my computer is a small desktop chassis) to the right of the floppy and CD-ROM drives, and that the tower structure thing is actually the microprocessor and heat sink.

---

### Post by bcasanov on 2007-05-01
Hey folks, great news!  I finally got the HDD to be recognized!  :KS  What I did was remove the hard-drive shroud, remove the hard disk, and reinsert it, making sure the cables were firmly attached.  When I booted up, voila!, the BIOS detected my hard disk as the primary device 0.  It seems that removing the hard disk drive and reinserting it reset the controller or something.  From there, I booted into Kubuntu live CD, which I also burned along with Ubuntu, and installed it onto my hard drive without any problems.  

You all have given me invaluable advice, and I have learned quite a bit about my computer in the process.  Thank you again for your kind support!

---

### Post by sandman55 on 2007-05-01
Good for you and as you say you have learned something on the way, also you wondered where the battery was, its the shiny disk that has the red corner of the tab of one of your ribbon cables on it also the long narrow cards directly to the left of your CPU are the ram, you can also see the electrolytic capacitors either side of your CPU heat sink and scattered around the motherboard.
What you did by removing and reinserting the HDD cable was to wipe the connections clean that is a fault that can happen and not just on an old system I fixed my sisters computer by removing and reinserting the ram and hers is 3 or 4 years old reading back I see aldenhg suggested it might be this :)

---

