---
title: "Unable to boot PCIe SSD"
date: 2023-04-03
forum: General Help
---

### Post by satimis on 2023-04-03
Hi all,

Hard drives connected in PC:-

2TB PCIe SSD - Ubuntu 22.04 VBox
1TB PCIe SSD - Ubuntu 22.04 VBox
500M SATA3 SSD - Ubuntu 22.04 KVM
1TB SATA3 SSD - Windows 10
4TB SATA3 WD - solely for storage without OS installed.

BIOS detects 1TB PCIe SSD but unable to boot it, always booting 2TB PCIe SSD.  If removing the 2TB PCIe SSD, it boots the 500M SATA3 SSD.

This 1TB PCIe SSD is seldom used.  I just found this problem 2 days before.  Please advise how to fix the problem.  Thanks

Regards

---

### Post by Dennis N on 2023-04-04
Do you mean you are unable to boot an OS on the 1TB PCIe SSD drive? I don't see anything there that would be bootable at startup - only a VM (which would not be).

---

### Post by satimis on 2023-04-04
> **Dennis N said:**
> Do you mean you are unable to boot an OS on the 1TB PCIe SSD drive? I don't see anything there that would be bootable at startup - only a VM (which would not be).
Yes.

OS - Ubuntu 22.04
Host of VBox

Regards

---

### Post by MAFoElffen on 2023-04-04
> **satimis said:**
> Hi all,

Hard drives connected in PC:-

2TB PCIe SSD - Ubuntu 22.04 VBox
1TB PCIe SSD - Ubuntu 22.04 VBox
500M SATA3 SSD - Ubuntu 22.04 KVM
1TB SATA3 SSD - Windows 10
4TB SATA3 WD - solely for storage without OS installed.

BIOS detects 1TB PCIe SSD but unable to boot it, always booting 2TB PCIe SSD.  If removing the 2TB PCIe SSD, it boots the 500M SATA3 SSD.

This 1TB PCIe SSD is seldom used.  I just found this problem 2 days before.  Please advise how to fix the problem.  Thanks

Regards
Please provide us with information we can see... Such as either the 'boot-info' report from ['boot-repair']("https://help.ubuntu.com/community/Boot-Repair") or the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") Report. Both of those generate reports, where we can see what is there, and what you are referring to. both generate reports that upload to a PasteBin, where we can review them.

Just looking at a list of drives, does not tell us what is there, and where things are located. There are many blanks of information that is missing to make any recommendations yet. It is very confusing to me that you refer to things as VBox, which to me means VirtualBox, which would need a VirtualBox Host to be able to boot VM Guests... and talk about that it does not boot.

In the list, I can interpret that as that you might mean that you have Ubuntu installed more than once, or not. That you use 2 drive for VBox, and one for KVM... But unclear of where your Ubuntu OS is installed, or how it is setup. You see how that can be confusing to us, right? I cannot see what any of those missing details are. I am not looking over your shoulder there, seeing what is there.

That then begs to me, exactly what does not boot? I am sorry, but... I am confused at the moment and need to get a clear picture of what is there, and what you are asking about as a problem. 

I am asking you to submit more information, and to paint us a good picture of the problem. Probably the best, with so much going on, is to submit "both" reports.

---

### Post by satimis on 2023-04-04
> **MAFoElffen said:**
> Please provide us with information we can see... Such as either the 'boot-info' report from ['boot-repair']("https://help.ubuntu.com/community/Boot-Repair") or the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") Report. Both of those generate reports, where we can see what is there, and what you are referring to. both generate reports that upload to a PasteBin, where we can review them.

Just looking at a list of drives, does not tell us what is there, and where things are located. There are many blanks of information that is missing to make any recommendations yet. It is very confusing to me that you refer to things as VBox, which to me means VirtualBox, which would need a VirtualBox Host to be able to boot VM Guests... and talk about that it does not boot.

In the list, I can interpret that as that you might mean that you have Ubuntu installed more than once, or not. That you use 2 drive for VBox, and one for KVM... But unclear of where your Ubuntu OS is installed, or how it is setup. You see how that can be confusing to us, right? I cannot see what any of those missing details are. I am not looking over your shoulder there, seeing what is there.

That then begs to me, exactly what does not boot? I am sorry, but... I am confused at the moment and need to get a clear picture of what is there, and what you are asking about as a problem. 

I am asking you to submit more information, and to paint us a good picture of the problem. Probably the best, with so much going on, is to submit "both" reports.
Sorry, I'm not quite clear "how to run those commands".  I can't start 1TB drive.

Regards

---

### Post by ajgreeny on 2023-04-04
What exactly is this disk and what is on it?
*500M SATA3 SSD - Ubuntu 22.04 KVM*

500M is nowhere near large enough to have a KVM installation of Ubuntu 22.04, so either you meant 500G or something is very wrong.
And do you really have two different VBox VMs of Ubuntu, one of which is 2TB and the other 1TB in size?

---

### Post by satimis on 2023-04-04
> **ajgreeny said:**
> What exactly is this disk and what is on it?
*500M SATA3 SSD - Ubuntu 22.04 KVM*
Only the OS-Ubuntu 22.04 as host and KVM.  I only use this drive testing KVM not for daily work nor for production.

> 
And do you really have two different VBox VMs of Ubuntu, one of which is 2TB and the other 1TB in size?
Yes.  1TB is the original drive on this PC.  Late I found not sufficient storage space.  Then I add the 2TB to replace it for daily working.  I just leave the 1TB drive in the PC without disconnecting it.  It was still working without problem but I didn't use it daily until 2 days ago.  I tried to test my old Epson 3490 photo scanner on it and I found it unable to start.

---

### Post by MAFoElffen on 2023-04-04
So... Let me add this to this thread, that I collected from one of your other threads... So that others can see what you have (recently)... I ignored looking at it in that thread, because in that thread, which was about a graphics issue, it was not relevant to that problem... But it is relevant in this thread. I edited out the loop devices for you.
```

Disk /dev/nvme0n1: 953.87 GiB, 1024209543168 bytes, 2000409264 sectors
Disk model: INTEL SSDPEKNW010T8                     
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 271E9246-CC54-4368-8693-FDCC3EE8AB23

Device           Start        End    Sectors   Size Type
/dev/nvme0n1p1    2048    1050623    1048576   512M EFI System
/dev/nvme0n1p2 1050624 2000408575 1999357952 953.4G Linux LVM

Disk /dev/nvme1n1: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: Samsung SSD 970 EVO Plus 2TB            
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 6F56F295-23AB-4B8D-9CCA-CD9FA6D59C83

Device           Start        End    Sectors  Size Type
/dev/nvme1n1p1    2048    1050623    1048576  512M EFI System
/dev/nvme1n1p2 1050624 3907028991 3905978368  1.8T Linux LVM

Disk /dev/sda: 3.64 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: HGST HUS726T4TAL
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 343B80D3-E9CF-4B72-B4FF-2D311BA603E3

Device     Start        End    Sectors  Size Type
/dev/sda1   2048 7814035455 7814033408  3.6T Linux filesystem

Disk /dev/sdb: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: Samsung SSD 870 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: FC5FA10F-029D-4101-995A-0582344A4DA7

Device          Start        End    Sectors   Size Type
/dev/sdb1        2048     923647     921600   450M Windows recovery environment
/dev/sdb2      923648    1126399     202752    99M EFI System
/dev/sdb3     1126400    1159167      32768    16M Microsoft reserved
/dev/sdb4     1159168 1951400313 1950241146 929.9G Microsoft basic data
/dev/sdb5  1951401984 1952462847    1060864   518M Windows recovery environment
/dev/sdb6  1952464896 1953521663    1056768   516M Windows recovery environment

Disk /dev/sdc: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk model: CT500MX500SSD1  
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: A771E156-93A7-480A-8B12-99A686A3E405

Device       Start       End   Sectors   Size Type
/dev/sdc1     2048   1050623   1048576   512M EFI System
/dev/sdc2  1050624 976771071 975720448 465.3G Linux filesystem

Disk /dev/mapper/ubuntu--vg-root: 930.37 GiB, 998974160896 bytes, 1951121408 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/mapper/ubuntu--vg-swap_1: 976 MiB, 1023410176 bytes, 1998848 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/mapper/vgubuntu-root: 1.82 TiB, 1997809909760 bytes, 3901972480 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/mapper/vgubuntu-swap_1: 1.91 GiB, 2046820352 bytes, 3997696 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```
Now I see.

You have multiple disks, with multiple OS'es installed, all with EFI partitions. The UEFI BIOS on your computer is going to look at and boot to whatever the first EFI partition on the first disk it sees in the boot order... I am sorry, but I don't remember off the top of my head what computer you have... Please remind me.

If you just pressed key <F10> while booting, it will bring up the UEFI boot menu, where you could choose what to boot from... When you decide what you want your configuration to grow up to be, then I can suggest how to integrate things into one system configuration, that can boot all your OS'es... From one to another. Even if that is with multiple installations of Ubuntu.

---

### Post by satimis on 2023-04-04
> **MAFoElffen said:**
>  - snip -
Now I see.

You have multiple disks, with multiple OS'es installed, all with EFI partitions. The UEFI BIOS on your computer is going to look at and boot to whatever the first EFI partition on the first disk it sees in the boot order... I am sorry, but I don't remember off the top of my head what computer you have... Please remind me.
This AMD PC was built by me about 4~5 years ago

$ hwinfo > hwinfo.txt
$ gzip hwinfo.txt 

hwinfo.txt.gz is attached here.

> 
If you just pressed key <F10> while booting, it will bring up the UEFI boot menu, where you could choose what to boot from... When you decide what you want your configuration to grow up to be, then I can suggest how to integrate things into one system configuration, that can boot all your OS'es... From one to another. Even if that is with multiple installations of Ubuntu.

I'm using MS keyboard without <F10> key

Regards

---

### Post by MAFoElffen on 2023-04-04
@satimis --
Please do not take offense to this or take it as criticism. I am just trying to make it easier for you to get help here.

Please quit tap dancing around what you are asked. If someone asks you for something in an accepted format, that "is" what they are asking for.

Several times, in several different threads, you have been asked for information, that seems to the Member as straight-forward and clear. Instead of just answering or providing that information "in that form and format", you go off and do something else, in another direction. What is provided by you in the way of information is round-about.

I know where this comes from. You had posted raw output in a post, and I asked you if you could please post that within CODE Tags. Instead of doing that, you now provide that output in attached text files, rather post them in your posts "within" Codes Tags. Using CODE Tags is simple once you learn how to do that. It is simple for members to read and scan through. It also prevents any problems the Forum's software might have for that. 

What continually posting output as file attachments causes people more work to help you as they have to is to download that text file to be able to see it. Most members here do not want to have to download something that they will only look at once. That downloads things to their computer, that they do not need. Would you want to have to do that to help someone?

Posting screenshots are sometimes needed, but are provided in a more useful format as some kind of text. That is where and what CODE tags come in handy for. That is easy to do and to read.

A prime example of an unneeded format, is what you just provided in response to me asking you about running the boot-info and system-info reports and posting the URL's to where they get uploaded to. Those report formats are easy to read and members here are used to that format. We are all just volunteers, common folk, that have used Ubuntu for a while and have a desire to help other Users, in sharing our experience to solve their problems or questions. Only some of us here have detailed enough experience to read hex dumps and system traces, like is in the hwinfo report.

The hwinfo report is above the heads of most members here. As a new User, how much of that hwinfo report do you understand? There is a lot of information there that has nothing to do with what I need to know to help you. I understand it, but I have over 30 years of professional IT experience. Once I weed through the extra cruft, I would then have to figure out how to explain what I found, and what it means in common, simple terms.

That is why I wrote the UbuntuForums 'system-info' script and am a collaborator for 'boot-repair'/'boot-info' scripts. To give back to the community here. To help people to be able to help others, in a simple, understandable manner. Tools are only helpful if they are used.

I do not want to be the only one that can help you here. I am just one person. And you are not making that easy.

If you tried to make it easy to get help, in a form that is easily understandable, and human readable, then more people here might be willing to help you. We are trying to help you. Though you do need to try to help us, to be able to help you.

I applaud your enthusiasm, and curiosity in your new journey into Linux. You have come a long while, diving into things and exploring what it possible for you. You have come a very long way, in a very, very short time. When I first came to this Forum there were people here that helped me. I still learn new things every day. I hope that someday that you decide to help others and share your experiences to help them. This is how it works here.

I hope I have not said anything that you interpret wrong. I truly, honestly, sincerely just want to help you, and others here.

EDIT: A note of concern for the hwinfo report... I got with my team to  decide, between ourselves, what was acceptable, security wise, about  what should be included in the system-info report to be seen 'publicly' /  online. We spent a lot of time going through serial numbers, MAC  addresses, etc., to allow a User the ability to see those things, as a sort of "For Your Eyes Only" kind of thing, but to  add filters to sanitize those items to before being shared publicly. The hwinfo  report does not do that. All your details, in those items, are now out on  the web. You might want to think about what is acceptable risk to you... It matters more to some people than others. That decision is up to you, but you should be aware and informed, so you can make that decision on your own.

---

### Post by ajgreeny on 2023-04-05
Is this computer the same one as in your other thread at [https://ubuntuforums.org/showthread.php?t=2485575](https://ubuntuforums.org/showthread.php?t=2485575) where you're having difficulties at boot?

Can You also confirm that you are **NOT USING GRUB-CUSTOMIZER** which can result in many problems using grub, for example, the thread at [https://ubuntuforums.org/showthread.php?t=2485577](https://ubuntuforums.org/showthread.php?t=2485577)

I am not suggesting these are the same problem but simply trying to get all the information we need to be able to help you.

---

### Post by satimis on 2023-04-05
> **ajgreeny said:**
> Is this computer the same one as in your other thread at [https://ubuntuforums.org/showthread.php?t=2485575](https://ubuntuforums.org/showthread.php?t=2485575) where you're having difficulties at boot?

Yes, correct.

> 
Can You also confirm that you are **NOT USING GRUB-CUSTOMIZER** which can result in many problems using grub, for example, the thread at [https://ubuntuforums.org/showthread.php?t=2485577](https://ubuntuforums.org/showthread.php?t=2485577)

No.

> 
I am not suggesting these are the same problem but simply trying to get all the information we need to be able to help you.
Noted and thanks

Regards

[B][COLOR="#FF0000"]Edit
====[/COLOR][/B]
Just re-check MAFoElffen's suggestion on post #20 of that thread;
[https://ubuntuforums.org/showthread.php?t=2485575&page=2](https://ubuntuforums.org/showthread.php?t=2485575&page=2)

There is something similar. But now GRUB menu doesn't start at boot.

I can change /etc/default/grub back to its original file.  I have it saved as"grub_orig_20230305" before editing.

$ ls /etc/default/```

acpid            console-setup       im-config            openvpn
acpi-support     cron                intel-microcode      rsync
alsa             dbus                irqbalance           saned
amd64-microcode  google-chrome       kerneloops           ufw
anacron          grub                keyboard             useradd
apport           grub.d              locale
avahi-daemon     **[COLOR="#FF0000"]grub_orig_20230305[/COLOR]**  networkd-dispatcher

```

---

### Post by ajgreeny on 2023-04-05
> Can You also confirm that you are NOT USING GRUB-CUSTOMIZER which can result in many problems using grub, for example, the thread at [https://ubuntuforums.org/showthread.php?t=2485577](https://ubuntuforums.org/showthread.php?t=2485577)

No.Just to avoid confusion, do you mean you can not confirm that you are not using it, or do you mean that you are not using grub-customizer?

Sorry, it was a question that should have been better put to avoid such a double negative option in your reply.

---

### Post by satimis on 2023-04-05
> **ajgreeny said:**
> Just to avoid confusion, do you mean you can not confirm that you are not using it, or do you mean that you are not using grub-customizer?
I can't confirm it.  I just follow MAFoElffen's suggestion to test.

---

### Post by MAFoElffen on 2023-04-06
satimis... I think ajgreeny is trying to tell you that having grub customizer installed, and trying to make changes manually have some conflicts. If I knew that you were using Grub Customizer, I would have had you uninstall it "before" attempting to making manual changes.

That may be the whole problems. Too many conflicting things going on at once, and them fighting with each other. LOL

I have no idea how many changes you have going on at once, what they are, and how they are conflicting with each other. That makes thing entertaining, but rather very complicated. That may also be why changes we recommend are doing "nothing", when in normal circumstances, they should have some kind of affect.

---

### Post by satimis on 2023-04-06
> **MAFoElffen said:**
> satimis... I think ajgreeny is trying to tell you that having grub customizer installed, and trying to make changes manually have some conflicts. If I knew that you were using Grub Customizer, I would have had you uninstall it "before" attempting to making manual changes.

That may be the whole problems. Too many conflicting things going on at once, and them fighting with each other. LOL

I have no idea how many changes you have going on at once, what they are, and how they are conflicting with each other. That makes thing entertaining, but rather very complicated. That may also be why changes we recommend are doing "nothing", when in normal circumstances, they should have some kind of affect.
I haven't installed Grub Customizer in the past, except following your instruction on another posting-"Dark screen at booting" making change on /etc/default/greb.

I think it would be better pending to solve the problem on this thread until the problem on "Dark screen at booting" solved

---

### Post by MAFoElffen on 2023-04-06
> **satimis said:**
> I haven't installed Grub Customizer in the past, except following your instruction on another posting-"Dark screen at booting" making change on /etc/default/greb.

"***I haven't.. except when...***" Does that mean "Grub Customizer" is installed or not? There is that 'escape' again, but may just be a *translation* difference.

I gave you very detailed instructions on how to edit the grub default file manually. That has nothing to do with Grub Customizer... I did not, in any way instruct you to, or recommend that you install "Grub Customizer". I have not recommended it "ever."

Are we talking about the same thing? Wait, do you know what Grub Customizer is?
RE: [https://itsfoss.com/customize-grub-linux/](https://itsfoss.com/customize-grub-linux/)

Many users from many different distributions are having problems with Grub Customizer breaking Grub.

If it is or not installed makes a difference here, as it does in your other threads.

---

### Post by satimis on 2023-04-06
> **MAFoElffen said:**
> I gave you very detailed instructions on how to edit the grub default file manually. That has nothing to do with Grub Customizer... I did not, in any way instruct you to, or recommend that you install "Grub Customizer". I have not recommended it "ever."

Are we talking about the same thing? Wait, do you know what Grub Customizer is?
RE: [https://itsfoss.com/customize-grub-linux/](https://itsfoss.com/customize-grub-linux/)

Many users from many different distributions are having problems with Grub Customizer breaking Grub.
I just followed your instruction to perform the test on "Dark screen at booting".  Neither I know Grub Customizer as I replied to ajgreeny above

$ apt policy grub-customizer```

N: Unable to locate package grub-customizer

```
It is NOT Ubuntu 22.04 repo

Regards

---

### Post by MAFoElffen on 2023-04-06
Okay. I think that was just a language translation misunderstanding.

1:30a.m. here. Getting some sleep and we will attack this again, freshly, tomorrow.

---

### Post by satimis on 2023-04-06
> **MAFoElffen said:**
> Okay. I think that was just a language translation misunderstanding.

1:30a.m. here. Getting some sleep and we will attack this again, freshly, tomorrow.
Thanks for your help.

Regards

---

### Post by MAFoElffen on 2023-04-06
Okay... 

How many instances of Ubuntu do you have installed? 

I think I remember you also saying that you have Window installed right?

Which drive with with instance of Ubuntu do you want to be the primary?

(I asked you to run the 'system-info' script and post the URL, that would answer a lot of questions that we have to go back and forth on... LOL)

---

### Post by satimis on 2023-04-06
> **MAFoElffen said:**
> Okay... 

How many instances of Ubuntu do you have installed? 
Ubuntu 22.04 as host and VirtualBox - 2TB PCIe SSD
Ubuntu 22.04 as host and VirtualBox - 1TB PCIe SSD
(unable to start)
Ubuntu 22.04 as host and KVM - 500G SATA3 SSD
(It starts without problem and no warning
OpenShot and GIMP installed on their AppImage and work without problem.  They can be started clicking their icons)

> 
I think I remember you also saying that you have Window installed right?

Yes, on a 1TB SATA3 SSD. It starts and works without problem.  No warning popup at starting it.

> 
Which drive with with instance of Ubuntu do you want to be the primary?
Ubuntu 22.04 as host and VirtualBox on 2TB PCIe SSD

> 
(I asked you to run the 'system-info' script and post the URL, that would answer a lot of questions that we have to go back and forth on... LOL)
Pls advise where to run 'system-info' ?  Thanks

Regards

---

### Post by ajgreeny on 2023-04-07
Post #4 shows you a link for the system- info script which tells you how to run it and report.

---

### Post by satimis on 2023-04-07
> **ajgreeny said:**
> Post #4 shows you a link for the system- info script which tells you how to run it and report.
Thanks

I download the script as system-info on following URL
Run from GUI
[https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)

$ sudo add-apt-repository ppa:mafoelffen/system-info
[sudo] password for satimis: ```

Repository: 'deb https://ppa.launchpadcontent.net/mafoelffen/system-info/ubuntu/
                   
Get:14 http://hk.archive.ubuntu.com/ubuntu jammy-updates/restricted i386 Packages [27.2 kB]
Get:15 http://hk.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages [744 kB]
....
....
Get:19 http://hk.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 Packages [24.1 kB]
Get:20 https://ppa.launchpadcontent.net/mafoelffen/system-info/ubuntu jammy/main i386 Packages [460 B]
Get:21 http://hk.archive.ubuntu.com/ubuntu jammy-updates/multiverse amd64 DEP-11 Metadata [940 B]
Get:22 http://hk.archive.ubuntu.com/ubuntu jammy-backports/main amd64 DEP-11 Metadata [8,000 B]
Get:23 http://hk.archive.ubuntu.com/ubuntu jammy-backports/universe amd64 DEP-11 Metadata [12.5 kB]
Get:24 https://ppa.launchpadcontent.net/mafoelffen/system-info/ubuntu jammy/main Translation-en [256 B]
Fetched 4,589 kB in 6s (820 kB/s)                            
Reading package lists... Done

```

$ sudo apt update
```

Hit:1 http://security.ubuntu.com/ubuntu jammy-security InRelease
Hit:2 http://hk.archive.ubuntu.com/ubuntu jammy InRelease                      
Hit:3 http://hk.archive.ubuntu.com/ubuntu jammy-updates InRelease              
Hit:4 http://hk.archive.ubuntu.com/ubuntu jammy-backports InRelease            
Hit:5 https://ppa.launchpadcontent.net/mafoelffen/system-info/ubuntu jammy InRelease
Hit:6 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy InRelease
Hit:7 https://dl.google.com/linux/chrome/deb stable InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.

```

$ sudo apt upgrade```

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  libimage-magick-perl libavcodec-extra libavdevice58 ffmpeg libopenexr25
  libmagick++-6.q16-8 libpostproc55 libmagickcore-6.q16-6-extra
  libimage-magick-q16-perl libmagickwand-6.q16-6 libavcodec-extra58
  libavutil56 imagemagick-6.q16 libswscale5 libmagickcore-6.q16-6
  libswresample3 imagemagick-6-common libavformat58 libavfilter7
Learn more about Ubuntu Pro at https://ubuntu.com/pro
The following packages have been kept back:
  grub-efi-amd64-bin grub-efi-amd64-signed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

$ sudo apt install system-info```

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  system-info
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 33.3 kB of archives.
After this operation, 128 kB of additional disk space will be used.
Get:1 https://ppa.launchpadcontent.net/mafoelffen/system-info/ubuntu jammy/main amd64 system-info all 02.00.07 [33.3 kB]
Fetched 33.3 kB in 1s (22.3 kB/s)                          
Selecting previously unselected package system-info.
(Reading database ... 259491 files and directories currently installed.)
Preparing to unpack .../system-info_02.00.07_all.deb ...
Unpacking system-info (02.00.07) ...
Setting up system-info (02.00.07) ...

```

$ which system-info```

/usr/bin/system-info

```

$ system-info > system-info-output.txt```

[sudo] password for satimis: 
<E>xit and install the program(s) or <C>ontinue anyway? <E/C> c
What is the Main Complaint (summarized)? 

```

I'm stuck here. Pls advise how to proceed?  Thanks

Regards

---

### Post by Dennis N on 2023-04-07
> I'm stuck here. Pls advise how to proceed? Thanks

You should exit and install the needed programs. After that's done, start it again. When you get to this point, answer the questions that are asked.  You don't need the redirect to file - a file is automatically created.

---

### Post by MAFoElffen on 2023-04-07
You didn't show the whole screen, which at the top of the screen would have listed any missing util's (LOL), but I am suspecting that it say that 'pastebinit' is not installed. (Not a default installed app). But that is okay... I wrote 4 fallback routines to different Linux basic util's to do that upload, so that it would work with most all Linux Distro's.

From there, press <C> <Enter>

If there is any important util's, that are somehow missing, the end of the report has a section that lists missing programs. We wanted that there, so that Members here could see what might have been missing that could have affected the results. 

### PLEASE READ
To other's here. I wrote that script for the Member's here, targeting it to Ubuntu and it's flavors. To help Member's gather information from a User in need, so that we can make informed recommendations, without having to repost the same commands to them over and over again. I gave this script to the Ubuntu Forum, and it was adopted by the Admin Council. It is free to use for all. It is supposed to help the Member's here and make things easier for us all. This is my legacy to leave to you all here.

I appreciate all the Members here, who spend countless hours helping others, sharing their experience and skills. You all are invaluable to the Community here.

*** One thing we are trying to focus on right now, is to make the instructions on how to get it installed and to use it, more clear to new users. If you have any ideas on this, or have any recommendations... Please, please, please post them in the Dev thread at: [https://ubuntuforums.org/showthread.php?t=2465764](https://ubuntuforums.org/showthread.php?t=2465764) I am truly wanting feedback on this, so we can make this process easier for new users. This is truly a community supported effort. The Forum Admins and I are currently working on this.

(Also) I am working on the man pages, which after that will be a Wiki on how to use, and how to interpret the report for diagnostics... So that Members know how to look it and identify what they need to know to help diagnose or make their recommendations. At the least, it tells you what you are making recommendations for. A tool is effective if it is understood and used well.

---

### Post by satimis on 2023-04-07
> **Dennis N said:**
> You should exit and install the needed programs. After that's done, start it again. When you get to this point, answer the questions that are asked.  You don't need the redirect to file - a file is automatically created.
Thanks for your advice.

Performed following steps;
$ system-info```

....
Running Script: system-info Version: 02.00-06, Script Date: 2023.03.20
related question.

Program(s) curl,  is/are missing, 
but can be ignored as there still are installed utilities present to 
to be able to upload the report to an online PasteBin.

Some of these utilities are not default installed utilities to all Editions, 
versions, and flavors of Ubuntu... So may be considered as optional. 

<E>xit and install the program(s) or <C>ontinue anyway? <E/C> E
Please install the missing programs listed above before rerunning script.
......
<E>xit and install the program(s) or <C>ontinue anyway? <E/C> E

```

$ apt policy curl```

curl:
  Installed: (none)
  Candidate: 7.81.0-1ubuntu1.10
  Version table:
     7.81.0-1ubuntu1.10 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
     7.81.0-1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```
$ sudo apt install curl

$ system-info```

(enter password0
........
This script needs some parts of it to run with elevated permissions.

Please enter your password for that to happen.
[sudo] password for satimis: 
Running Script: system-info Version: 02.00-06, Script Date: 2023.03.20
All required programs installed...

Please provide some "Basic Information"...
What is the Main Complaint (summarized)? Unable to boot PCIe SSD [Enter}
Describe the Problem: 1TB PCIe fails to start [Enter]
.....
.....
You are using the viewer 'less'.
Advance to a next page with the <SpaceBar> key.
Navigate what has been displayed with the
Left/Right/Up/Down Arrow, PageUp, PageDown, Home, or End keys.
If you are running within a graphical terminal session,

you can also navigate with the mouse or touchpad.
Get more built-in help within 'less' with the <H> key.
At any point while in 'less' or if you see this '(END)' prompt
at the lower left of your screen,
 quit from 'less' to continue the script with the <q> key. 

 --- SENSITIVE DATA WARNING ---  

This Report is prepared in two versions- 

The 'Your Eyes Only' version, only exists temporarily in memory, and is 
viewed onscreen by 'less'. The report that is viewed by 'less' onscreen 
contains 'sensitive data' that should NOT be posted publicly. 

[press Space-Key]
....
....
....
 --- SENSITIVE DATA WARNING ---  

This Report is prepared in two versions- 

The 'Your Eyes Only' version, only exists temporarily in memory, and is 
viewed onscreen by 'less'. The report that is viewed by 'less' onscreen 
contains 'sensitive data' that should NOT be posted publicly. 

The Final Report 'file' is saved to disk as a file. The Final Report is 
sanitized, filtered, with the sensitive data removed. It is safe to post 
online publicly. 

(END)

```

The file  system-info.txt.gz is attached here

Regards

---

### Post by satimis on 2023-04-07
> **MAFoElffen said:**
> You didn't show the whole screen, which at the top of the screen would have listed any missing util's (LOL), but I am suspecting that it say that 'pastebinit' is not installed. (Not a default installed app). But that is okay... I wrote 4 fallback routines to different Linux basic util's to do that upload, so that it would work with most all Linux Distro's.

- snip -
Sorry, I don't follow.

Which "whole screen" you need?

---

### Post by MAFoElffen on 2023-04-08
That is okay. Past tense now. I can see the report and go through it. About 2:30 am. here now. Will look at it in the morning.

Thank you.

---

### Post by satimis on 2023-04-08
> **MAFoElffen said:**
> That is okay. Past tense now. I can see the report and go through it. About 2:30 am. here now. Will look at it in the morning.

Thank you.
Noted and thanks, waiting for your reply.

---

### Post by MAFoElffen on 2023-04-08
I think this information is where to start explaining things about what is going on. It has the best visualization to explain on:
```

---------- Disk/Partition Information From 'lsblk':
NAME                    SIZE FSTYPE      LABEL    MOUNTPOINT                         MODEL
sda                     3.6T                                                         HGST HUS726T4TALE6L4 # WD Ultrastar HDD
|_sda1                  3.6T ext4                                                    
sdb                   931.5G                                                         Samsung SSD 870 EVO 1TB
|_sdb1                  450M ntfs        Recovery                                    
|_sdb2                   99M vfat                                                    
|_sdb3                   16M                                                         
|_sdb4                929.9G ntfs                                                    
|_sdb5                  518M ntfs                                                    
|_sdb6                  516M ntfs                                                    
sdc                   465.8G                                                         CT500MX500SSD1  # Crucial MX500 SSD 
|_sdc1                  512M vfat                                                    
|_sdc2                465.3G ext4                                                    
sr0                    1024M                                                         SONY DVD RW AW-G170S
nvme0n1               953.9G                                                         INTEL SSDPEKNW010T8
|_nvme0n1p1             512M vfat                 /boot/efi                          
|_nvme0n1p2           953.4G LVM2_member                                             
  |-ubuntu--vg-root   930.4G ext4                                                    
  `-ubuntu--vg-swap_1   976M swap                                                    
nvme1n1                 1.8T                                                         Samsung SSD 970 EVO Plus 2TB
|_nvme1n1p1             512M vfat                                                    
|_nvme1n1p2             1.8T LVM2_member                                             
  |-vgubuntu-root       1.8T ext4                 /                                  
  `-vgubuntu-swap_1     1.9G swap                 [SWAP]                             

```
There shows 5 disks, with 4 OS'es installed, each with their own EFI directories. Of those 4, one is Windows, and 3 are Linux (You say they are all Ubuntu). Two of the Linux are on NVMe (1TB & 2TB), and One Linux on a 500GB SSD.

The NVMe that is set to the first drive in the boot order in BIOS is the 1TB NVMe (NVMe slot 0). The Drive that seen second in BIOS is the 2TB NVMe (NVMe slot 1).

On the SATA bus, the Drives set in order are the 4TB HHD (No OS installed), a Windows OS on  a Samsung 1TB, and Linux on a Crucial 500GB SSD... 

In that order. I am assuming they are probably plumbed physically in your box as:
```

NVMe slot0   1TB NVMe
NVME slot1   2TB NVme
SATA1        4TB HHD
SATA2        1TB SSD
SATA3        500GB SSD

```
Of the two NVMe drives, the booted system that the report was run from was on the second drive (nvme1n1, 2TB), but since the other drive (nvme0n1, 1TB) is seen first, it is using the EFI partition from it to boot from. See above where the mount of /boot/efi was indicated?

With me so far?

You say want to boot from the 2TB OS as the primary OS. Your thread title says you want to boot from the 500GB SSD OS... I'm thinking that is not what you meant, by the title right? Because you said differently later. (But NVMe are also referred to as being SSD also, but for this explanation we will just refer the NVMe drives as NVMe...)

The easiest fix would be to unplug your box, take the cover off, touch the metal frame with your hand to discharge any static, and then swap the NVMe drive cards in their slots... Putting the 2TB NVMe in NVMe slot0, and the 1TB NVMe in slot1. That way, without having to make any confusing changes in the BIOS, the 2TB NVMe is going to be seen first, and will use it's EFI partiton for the OS on it's drive...

But that is only step 1.

Step 2 would be to boot the system up, and get into the BIOS on boot, then save. That way the BIOS sees the changes in hardware and you save it. 

Step 3 would be to boot the OS on the 2TB drive and add something to your /etc/default/file
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=5
GRUB_RECORDFAIL_TIMEOUT=5
# GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="-- splash video=3840x2160-32"
GRUB_CMDLINE_LINUX=""
[COLOR=#ff0000]GRUB_OS_PROBER_DISABLE=false
[/COLOR]
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
#GRUB_TERMINAL=console

# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXMODE=3840x2160

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

#GRUB_DISABLE_RECOVERY="true"
#GRUB_INIT_TUNE="480 440 1"

```
Save and exit... Then 
```

sudo update-grub

```
At that point, grub should find the current Ubuntu instance, the other 2 instances of installed Ubuntu, and the installed Windows OS.

When you reboot the Grub2 menu is going to have 3 lines for Ubuntu and one for Windows.

Is that clear enough instructions? If you have any question, please ask.

EDIT: If may not work that way, because at the moment, we don't know what the drive order that is set in UEFI in the EFI partition of the 2TB NVMe drive. Don't panic if it boots another drive first. I am pretty sure that when you installed Ubuntu on that drive, that it set that same drive as the first boot in that drive's EFI partition. But if for some reason it didn't, I will talk you though resetting that order.

EDIT2: You have a very complex multi-boot setup. After this is worked out, I will explain what you should do for care-and-feeding to keep it healthy during/after updates that involve Grub2. But we should also talk about why you decided to install Ubuntu 3 times... and have 3 of the same versions of the same OS... It just seems that you are making this a lot harder than it needs to be. Than what it could be. It could be simplified quite a lot, and be going great on just one install of Ubuntu.

---

### Post by satimis on 2023-04-09
> **MAFoElffen said:**
> I think this information is where to start explaining things about what is going on. It has the best visualization to explain on:
```

---------- Disk/Partition Information From 'lsblk':
NAME                    SIZE FSTYPE      LABEL    MOUNTPOINT                         MODEL
sda                     3.6T                                                         HGST HUS726T4TALE6L4 # WD Ultrastar HDD
|_sda1                  3.6T ext4                                                    
sdb                   931.5G                                                         Samsung SSD 870 EVO 1TB
|_sdb1                  450M ntfs        Recovery                                    
|_sdb2                   99M vfat                                                    
|_sdb3                   16M                                                         
|_sdb4                929.9G ntfs                                                    
|_sdb5                  518M ntfs                                                    
|_sdb6                  516M ntfs                                                    
sdc                   465.8G                                                         CT500MX500SSD1  # Crucial MX500 SSD 
|_sdc1                  512M vfat                                                    
|_sdc2                465.3G ext4                                                    
sr0                    1024M                                                         SONY DVD RW AW-G170S
nvme0n1               953.9G                                                         INTEL SSDPEKNW010T8
|_nvme0n1p1             512M vfat                 /boot/efi                          
|_nvme0n1p2           953.4G LVM2_member                                             
  |-ubuntu--vg-root   930.4G ext4                                                    
  `-ubuntu--vg-swap_1   976M swap                                                    
nvme1n1                 1.8T                                                         Samsung SSD 970 EVO Plus 2TB
|_nvme1n1p1             512M vfat                                                    
|_nvme1n1p2             1.8T LVM2_member                                             
  |-vgubuntu-root       1.8T ext4                 /                                  
  `-vgubuntu-swap_1     1.9G swap                 [SWAP]                             

```
There shows 5 disks, with 4 OS'es installed, each with their own EFI directories. Of those 4, one is Windows, and 3 are Linux (You say they are all Ubuntu). Two of the Linux are on NVMe (1TB & 2TB), and One Linux on a 500GB SSD.

The NVMe that is set to the first drive in the boot order in BIOS is the 1TB NVMe (NVMe slot 0). The Drive that seen second in BIOS is the 2TB NVMe (NVMe slot 1).

On the SATA bus, the Drives set in order are the 4TB HHD (No OS installed), a Windows OS on  a Samsung 1TB, and Linux on a Crucial 500GB SSD... 

In that order. I am assuming they are probably plumbed physically in your box as:
```

NVMe slot0   1TB NVMe
NVME slot1   2TB NVme
SATA1        4TB HHD
SATA2        1TB SSD
SATA3        500GB SSD

```
Of the two NVMe drives, the booted system that the report was run from was on the second drive (nvme1n1, 2TB), but since the other drive (nvme0n1, 1TB) is seen first, it is using the EFI partition from it to boot from. See above where the mount of /boot/efi was indicated?

With me so far?

You say want to boot from the 2TB OS as the primary OS. Your thread title says you want to boot from the 500GB SSD OS... I'm thinking that is not what you meant, by the title right? Because you said differently later. (But NVMe are also referred to as being SSD also, but for this explanation we will just refer the NVMe drives as NVMe...)

The easiest fix would be to unplug your box, take the cover off, touch the metal frame with your hand to discharge any static, and then swap the NVMe drive cards in their slots... Putting the 2TB NVMe in NVMe slot0, and the 1TB NVMe in slot1. That way, without having to make any confusing changes in the BIOS, the 2TB NVMe is going to be seen first, and will use it's EFI partiton for the OS on it's drive...

But that is only step 1.

Step 2 would be to boot the system up, and get into the BIOS on boot, then save. That way the BIOS sees the changes in hardware and you save it. 

Step 3 would be to boot the OS on the 2TB drive and add something to your /etc/default/file
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=5
GRUB_RECORDFAIL_TIMEOUT=5
# GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="-- splash video=3840x2160-32"
GRUB_CMDLINE_LINUX=""
[COLOR=#ff0000]GRUB_OS_PROBER_DISABLE=false
[/COLOR]
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
#GRUB_TERMINAL=console

# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXMODE=3840x2160

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

#GRUB_DISABLE_RECOVERY="true"
#GRUB_INIT_TUNE="480 440 1"

```
Save and exit... Then 
```

sudo update-grub

```
At that point, grub should find the current Ubuntu instance, the other 2 instances of installed Ubuntu, and the installed Windows OS.

When you reboot the Grub2 menu is going to have 3 lines for Ubuntu and one for Windows.

Is that clear enough instructions? If you have any question, please ask.

EDIT: If may not work that way, because at the moment, we don't know what the drive order that is set in UEFI in the EFI partition of the 2TB NVMe drive. Don't panic if it boots another drive first. I am pretty sure that when you installed Ubuntu on that drive, that it set that same drive as the first boot in that drive's EFI partition. But if for some reason it didn't, I will talk you though resetting that order.

EDIT2: You have a very complex multi-boot setup. After this is worked out, I will explain what you should do for care-and-feeding to keep it healthy during/after updates that involve Grub2. But we should also talk about why you decided to install Ubuntu 3 times... and have 3 of the same versions of the same OS... It just seems that you are making this a lot harder than it needs to be. Than what it could be. It could be simplified quite a lot, and be going great on just one install of Ubuntu.
Hi,

First, to answer your question why installing Ubuntu 22.04 desktop 3 times on this PC

1) This PC was built by me 4~5 years ago
2) Initial setup
One 1TB PCIe SSD running Ubuntu 22.04 as Host and VirtualBox
One SATA3 1TB SSD running Windows
One 4TB WD drive for storage without OS installed.
3) Later I found insufficient space on 1TB PCIe SSD.  Then I added a 2TB PCIe SSD to replace the 1TB PCIe SSD, also running Ubuntu 22.04 as Host and VirtualBox.

I haven't disconnected the 1TB PCIe SSD, just leaving it there.  Both 1TB PCIe SSD and 2TB PCIe SSD could boot without problem in the past.  Until last week I found 1TB PCIe SSD unable to boot.

4) Later I added a 500G SATA3 SSD, installing Ubuntu 22.04 as Host to test KVM and Docker

I can install one of following Linux Distributions as Host of KVM to test Docker:-
RedHat
Linux Mint
Debian
Fedora
Gentoo
etc.

I have run all of them in the past without problem.  Just for convenience having an Ubuntu 22.04 ISO on my database.  I installed it as Host of KVM.  

I can disconnected the 1TB PCIe SSD and 500G SATA3 SSD.  I don't use them.

Now I just reconfigued the BIOS booting

1st boot - 2TB PCIe SSD
2nd boot - 1TB PCIe SSD
3rd boot - 500G SATA3 SSD
4th boot - 1TB SATA3 Windows

and re-ran "system-info"

The output file is attached here.

Also I made following test:
Disconnected the 2TB PCIe SSD, 1TB SATA3 SSD (Windows) and 500G SATA3 SSD, leaving only 1TB PCIe SSD and 4TH WD drive behind.  I found unable to boot the 1TB PCIe SSD, dropping to GRUB screen.  Ubuntu 22.04 failed to boot.

For your information.  Thanks.

Regards

---

### Post by MAFoElffen on 2023-04-09
Why are you not unloading the Reports to a pastebin? A lot easier for you to submit, and easier for all of us to read...

*** ===> I will not make a recommendation for anything until you paint me a clear picture of what you want to do. It is many post into this thread and what you say and what you do are completely different things. 

In how you do things, instead of integrating things into one system, you treat each disk as a separate computer, and are causing yourself to do 4 times the work. Is that what you really want to do? You want each drive to be able to boot on it's own, if, you select that drive as the boot order. You keep changing the boot order, to do that...

If so and want the 1TB NVME to be able to boot by itself... Then fix the EFI partition on that drive. Trying to figure out "HOW" to word this, so you understand what is going on...

The BIOS, if you point to the EFI partition of that drive... The EFI partition of that drive has it's own boot order in it.From the first system-info report, that EFI's boot order had the 2TB drive as it's primary (first in the order)... So, like I said in my previous post, the 2TB NVMe drive was booted from the EFI partition of the  1TB NVMe drive.

So, before we make any changes, lets get a clear idea of exactly what you want to do, and how you do things... It would be easier if I knew what you do and why you do it that way.

Because I see three different paths there, Each path has Windows untouched, on it's own disk.

1. Make changes so that you have 1 instance of Ubuntu, where everything is install on it, and you only have to maintain 1 Linux System. This would save you time, effort, and space.

2. Make changes to i\have your 3 separate Linux systems (even though replicated 3 times), that can work, no matter which disk is selected as the first in the boot order. This would require the most work to set up, but is possible. Would mean that you had to be on top of everything and understand what changes you do, how they affect the whole.

3. Make the system work, so you do not change the BIOS boot order, and integrate the system with one Grub2 menu, where you just go to your different system by choosing different options from that menu. Least amount of work to setup, and maintain. Least amount of work to do for use.

You tell me what you want to do, in how you want to do things, and why you want to do them that way.

---

### Post by satimis on 2023-04-09
> **MAFoElffen said:**
> Why are you not unloading the Reports to a pastebin? A lot easier for you to submit, and easier for all of us to read...

*** ===> I will not make a recommendation for anything until you paint me a clear picture of what you want to do. It is many post into this thread and what you say and what you do are completely different things. 

In how you do things, instead of integrating things into one system, you treat each disk as a separate computer, and are causing yourself to do 4 times the work. Is that what you really want to do? You want each drive to be able to boot on it's own, if, you select that drive as the boot order. You keep changing the boot order, to do that...

If so and want the 1TB NVME to be able to boot by itself... Then fix the EFI partition on that drive. Trying to figure out "HOW" to word this, so you understand what is going on...

The BIOS, if you point to the EFI partition of that drive... The EFI partition of that drive has it's own boot order in it.From the first system-info report, that EFI's boot order had the 2TB drive as it's primary (first in the order)... So, like I said in my previous post, the 2TB NVMe drive was booted from the EFI partition of the  1TB NVMe drive.

So, before we make any changes, lets get a clear idea of exactly what you want to do, and how you do things... It would be easier if I knew what you do and why you do it that way.

Because I see three different paths there, Each path has Windows untouched, on it's own disk.

1. Make changes so that you have 1 instance of Ubuntu, where everything is install on it, and you only have to maintain 1 Linux System. This would save you time, effort, and space.

2. Make changes to i\have your 3 separate Linux systems (even though replicated 3 times), that can work, no matter which disk is selected as the first in the boot order. This would require the most work to set up, but is possible. Would mean that you had to be on top of everything and understand what changes you do, how they affect the whole.

3. Make the system work, so you do not change the BIOS boot order, and integrate the system with one Grub2 menu, where you just go to your different system by choosing different options from that menu. Least amount of work to setup, and maintain. Least amount of work to do for use.

You tell me what you want to do, in how you want to do things, and why you want to do them that way.
My posting on #32 above was to answer your questions on #31, adding new discovery.  My expectation is to recover the previous state in this PC, if possible:

Boot options:
1st boot: 2TB PCIe SSD (Ubuntu 22.04 as Host and VirtualBox)
2nd boot: 1TB PCIe SSD (Ubuntu 22.04 as Host and VirtualBox)
3rd boot: 1TB SATA3 SSD (MS Windows)
4th boot: 500G SATA3 SSD (Ubuntu 22.04 as Host and KVM)

The problem of unable to start OpenShot AppImage and GIMP AppImage on 2TB PCIe SSD would be a different issue.  I think it should be treated separately OR to start a new posting?

Thanks

Regards

---

### Post by MAFoElffen on 2023-04-09
No. Not a new thread. Lets deal with everything here, and get it done with.  Lets get you drive as static so you aren't removing your drives so often. For most people, if they put a drive in, once it is set up, that's where they stay and that is the drive order that stays.

I say we take care of "everything" drive and boot wise "here".

First, when you opened this thread and the title of this thread, by 34 posts later, has evolved, but I think I have an idea of what you do and the problems you cause yourself by doing those things...

Here is my plan to take care of you.

1. We take care of the EFI directories in each drive (except the Windows drive), so that each drive primarily points to the OS on that drive as the default boot (first in the boot order of the EFI preference in the EFI partition). One drive at a time, as if it was the only drive in the computer. As if it was the only installation of Ubuntu.

2. The last drive we will set up is the 2TB NVMe drive, so that "that" drive will the one that stays as the drive the BIOS stays pointing to as first in the drive order. First as if it where alone, with no other OS'es

3. After we set up that drive to point to the OS on that drive, then we will put all the drives back in and "discover" the OS'es on the other drives, and let Grub add them to the Boot Menu. So that when you turn on your computer, it boots to the Ubuntu on that drive, and you have access during the boot process to get to the other OS'es if you choose.

Do you understand and does that match your vision of what you want? That way, if something ever goes wrong, all the other drives can be booted, as if they were the primary... You have fall-backs.

Once we get that all done, then we will jump back over to your Dislpay error problem thread and take care of that... Then after that on to your two new issues, on OpenShot and Gimp.

***
Sidenote: If it were me, I would keep the Ubuntu on the 2TB drive, where you have KVM and Docker installed, and additionally install VirtualBox. They can co-exist on the same instance. Then you could learn and play with Docker Desktop, which uses VBox. The VBox VM's can stay on other drives, and you can recover the space, where you have those two extra duplicated Ubuntu installs. You would also only have to maintain 1 Operating System with updates, maintenance and tweaking. But that is me.

I sued to use VBox, VMware Player, Xen and KVM, Docker, LXC. I had to support people with all, so had all installed. I had Multi-boot with Windows, Ubuntu, RedHat and Solaris. I had 7 desktops, 14 servers and 2 laptops. 

Now I just have 5 machines. 1 sever, a workstation, 3 laptops and a RaspberryPi. Most all are dual-boot with Windows and Ubuntu. Now I just mostly concentrate my efforts in KVM and LXD. I can do everything I need to do in those two. The workstation has drive docks where I can just swap drives easily to bring it up as a vSphere Server just by powering it up with that drive, to do my tests and verification's.

I am telling you that life is simpler if you set things up simpler... With a plan in what you want as a goal, and know how to adapt to what you want to do.

---

### Post by satimis on 2023-04-10
> **MAFoElffen said:**
> No. Not a new thread. Lets deal with everything here, and get it done with.  Lets get you drive as static so you aren't removing your drives so often. For most people, if they put a drive in, once it is set up, that's where they stay and that is the drive order that stays.

I say we take care of "everything" drive and boot wise "here".

First, when you opened this thread and the title of this thread, by 34 posts later, has evolved, but I think I have an idea of what you do and the problems you cause yourself by doing those things...

OK, understand

> 
Here is my plan to take care of you.

1. We take care of the EFI directories in each drive (except the Windows drive), so that each drive primarily points to the OS on that drive as the default boot (first in the boot order of the EFI preference in the EFI partition). One drive at a time, as if it was the only drive in the computer. As if it was the only installation of Ubuntu.

2. The last drive we will set up is the 2TB NVMe drive, so that "that" drive will the one that stays as the drive the BIOS stays pointing to as first in the drive order. First as if it where alone, with no other OS'es

3. After we set up that drive to point to the OS on that drive, then we will put all the drives back in and "discover" the OS'es on the other drives, and let Grub add them to the Boot Menu. So that when you turn on your computer, it boots to the Ubuntu on that drive, and you have access during the boot process to get to the other OS'es if you choose.

Do you understand and does that match your vision of what you want? That way, if something ever goes wrong, all the other drives can be booted, as if they were the primary... You have fall-backs.

OK.  Now all drives can boot without problem except the 1TB PCIe SSD running Ubuntu 22.04 as Host of VirtualBox.

> 
Once we get that all done, then we will jump back over to your Dislpay error problem thread and take care of that... Then after that on to your two new issues, on OpenShot and Gimp.
 Understand.

> 
***
Sidenote: If it were me, I would keep the Ubuntu on the 2TB drive, where you have KVM and Docker installed, and additionally install VirtualBox. They can co-exist on the same instance. Then you could learn and play with Docker Desktop, which uses VBox. The VBox VM's can stay on other drives, and you can recover the space, where you have those two extra duplicated Ubuntu installs. You would also only have to maintain 1 Operating System with updates, maintenance and tweaking. But that is me.

KVM and Docker are NOT installed on the 2TB PCIe drive.  They are installed on the 500G SATA3 drive.  Actually the test has been finished.  I just keep the drive on the PC for further reference

Other advice noted and thanks.

Regards

---

### Post by satimis on 2023-04-12
Hi all,

Just ran boot-rescue on USB Ubuntu 22.04 installer to rescue the 1TB PCIe SSD, no error popup during processing.  But on reboot it still drops to GRUB shell.

The drive is still working.  Their storage data can be copied via File Manager when booting another drive

Any advice? Thanks in advance.

Regards

---

### Post by MAFoElffen on 2023-04-12
Sorry. Have worked (straight) the past 9 days. Last night, closing shift was brutal. Trying to get at least a bit of rest... Will get back to this a bit later today.

What I would do is take all the drives out, except that drive, the 2TB drive, and the 4TB drive. 

Like I told you, the EFI directory on the 1TB points to the 2TB drive.

Boot it. Then do
```

sudo lsblk

```
Post that, then also post the results of 
```

sudo efibootmgr -v

```

---

### Post by satimis on 2023-04-12
> **MAFoElffen said:**
> Sorry. Have worked (straight) the past 9 days. Last night, closing shift was brutal. Trying to get at least a bit of rest... Will get back to this a bit later today.

What I would do is take all the drives out, except that drive, the 2TB drive, and the 4TB drive. 

Like I told you, the EFI directory on the 1TB points to the 2TB drive.

Boot it. Then do
```

sudo lsblk

```
Post that, then also post the results of 
```

sudo efibootmgr -v

```
$ sudo lsblk
```

NAME            MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0             7:0    0     4K  1 loop /snap/bare/5
loop1             7:1    0  63.3M  1 loop /snap/core20/1828
loop2             7:2    0  63.3M  1 loop /snap/core20/1852
loop3             7:3    0    73M  1 loop /snap/core22/583
loop4             7:4    0    73M  1 loop /snap/core22/607
loop5             7:5    0 346.3M  1 loop /snap/gnome-3-38-2004/119
loop6             7:6    0 349.7M  1 loop /snap/gnome-3-38-2004/137
loop7             7:7    0 460.3M  1 loop /snap/gnome-42-2204/65
loop8             7:8    0 460.4M  1 loop /snap/gnome-42-2204/68
loop9             7:9    0  91.7M  1 loop /snap/gtk-common-themes/1535
loop10            7:10   0  45.9M  1 loop /snap/snap-store/582
loop11            7:11   0  45.9M  1 loop /snap/snap-store/638
loop12            7:12   0  49.8M  1 loop /snap/snapd/18357
loop13            7:13   0  49.8M  1 loop /snap/snapd/18596
loop14            7:14   0   304K  1 loop /snap/snapd-desktop-integration/49
loop15            7:15   0   428K  1 loop /snap/snapd-desktop-integration/57
sda               8:0    0   3.6T  0 disk 
&#9492;&#9472;sda1            8:1    0   3.6T  0 part 
sr0              11:0    1  1024M  0 rom  
nvme0n1         259:0    0   1.8T  0 disk 
&#9500;&#9472;nvme0n1p1     259:1    0   512M  0 part /boot/efi
&#9492;&#9472;nvme0n1p2     259:2    0   1.8T  0 part 
  &#9500;&#9472;vgubuntu-root
  &#9474;             253:0    0   1.8T  0 lvm  /var/snap/firefox/common/host-hunspell
  &#9474;                                       /
  &#9492;&#9472;vgubuntu-swap_1
                253:1    0   1.9G  0 lvm  [SWAP]

```

$ sudo efibootmgr -v```

BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001
Boot0001* ubuntu        HD(1,GPT,9ba0e032-02d6-4dd7-8e08-8fc19e9ab185,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)..BO

```

---

### Post by MAFoElffen on 2023-04-12
> **satimis said:**
> $ sudo lsblk
```

NAME            MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda               8:0    0   3.6T  0 disk 
&#9492;&#9472;sda1            8:1    0   3.6T  0 part 
sr0              11:0    1  1024M  0 rom  
nvme0n1         259:0    0   1.8T  0 disk 
&#9500;&#9472;nvme0n1p1     259:1    0   512M  0 part /boot/efi
&#9492;&#9472;nvme0n1p2     259:2    0   1.8T  0 part 
  &#9500;&#9472;vgubuntu-root
  &#9474;             253:0    0   1.8T  0 lvm  /var/snap/firefox/common/host-hunspell
  &#9474;                                       /
  &#9492;&#9472;vgubuntu-swap_1
                253:1    0   1.9G  0 lvm  [SWAP]

```

$ sudo efibootmgr -v```

BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001
Boot0001* ubuntu        HD(1,GPT,9ba0e032-02d6-4dd7-8e08-8fc19e9ab185,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)..BO

```

And where is the 1TB Drive? Not present at all there.

Remove the 2TB drive and put in the 1TB NVMe drive. Boot it from a Boot-Repair LiveUSB and upload a report (Do not choose repair).

---

### Post by satimis on 2023-04-14
> **MAFoElffen said:**
> And where is the 1TB Drive? Not present at all there.

Remove the 2TB drive and put in the 1TB NVMe drive. Boot it from a Boot-Repair LiveUSB and upload a report (Do not choose repair).
Hi MAFoElffen,

It is very strange that my reply to your posting #40 disappears.  I'll do it again later because now both Windows drive and the 500G SATA3 SSD drive are connected.

The report running Boot-Repair LiveUSB before is now attached.  It was generated before repair.

Now the situation of Ubuntu 22.04 running on the 2TB PCIe NVMe SSD drive is becoming worse.  Additional to GIMP and OpenShot unable to start, the 4TB SATA3 WD Drive mounted on an external USB docking is now unable to be connected.  Please refers to the attached screenshot.  This drive is for sharing data amongst PCs.

The above-mentioned external drive still works on the Ubuntu 22.04 running on 500G SATA3 SSD drive without problem.  It can be connected to retrieve its data and to add data on it.

Windows on the 1TB SATA3 SSD drive still works without problem.

I don't think the 1TB and 2TB PCIe NVMe drives are corrupted.  Their data can still be retrieved while running Ubuntu 22.04 on the 500G SATA3 SSD drive.

Regards

---

### Post by satimis on 2023-04-14
> **MAFoElffen said:**
> And where is the 1TB Drive? Not present at all there.

- snip- 
Tried it again.

$ sudo lsblk
```

NAME            MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0             7:0    0     4K  1 loop /snap/bare/5
loop1             7:1    0  63.3M  1 loop /snap/core20/1828
loop2             7:2    0  63.3M  1 loop /snap/core20/1852
loop3             7:3    0    73M  1 loop /snap/core22/583
loop4             7:4    0    73M  1 loop /snap/core22/607
loop5             7:5    0 346.3M  1 loop /snap/gnome-3-38-2004/119
loop6             7:6    0 349.7M  1 loop /snap/gnome-3-38-2004/137
loop7             7:7    0 460.3M  1 loop /snap/gnome-42-2204/65
loop8             7:8    0 460.4M  1 loop /snap/gnome-42-2204/68
loop9             7:9    0  91.7M  1 loop /snap/gtk-common-themes/1535
loop10            7:10   0  45.9M  1 loop /snap/snap-store/582
loop11            7:11   0  45.9M  1 loop /snap/snap-store/638
loop12            7:12   0  49.8M  1 loop /snap/snapd/18357
loop13            7:13   0  49.8M  1 loop /snap/snapd/18596
loop14            7:14   0   304K  1 loop /snap/snapd-desktop-integration/49
loop15            7:15   0   428K  1 loop /snap/snapd-desktop-integration/57
sda               8:0    0   3.6T  0 disk 
&#9492;&#9472;sda1            8:1    0   3.6T  0 part 
sdb               8:16   1     0B  0 disk 
sr0              11:0    1  1024M  0 rom  
nvme0n1         259:0    0 953.9G  0 disk 
&#9500;&#9472;nvme0n1p1     259:1    0   512M  0 part /boot/efi
&#9492;&#9472;nvme0n1p2     259:2    0 953.4G  0 part 
  &#9500;&#9472;ubuntu--vg-root
  &#9474;             253:0    0 930.4G  0 lvm  
  &#9492;&#9472;ubuntu--vg-swap_1
                253:1    0   976M  0 lvm  
nvme1n1         259:3    0   1.8T  0 disk 
&#9500;&#9472;nvme1n1p1     259:4    0   512M  0 part 
&#9492;&#9472;nvme1n1p2     259:5    0   1.8T  0 part 
  &#9500;&#9472;vgubuntu-root
  &#9474;             253:2    0   1.8T  0 lvm  /var/snap/firefox/common/host-hunspell
  &#9474;                                       /
  &#9492;&#9472;vgubuntu-swap_1
                253:3    0   1.9G  0 lvm  [SWAP]
                
```

$ sudo efibootmgr -v```

BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0004,0005
Boot0004* ubuntu        HD(1,GPT,9ba0e032-02d6-4dd7-8e08-8fc19e9ab185,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO
Boot0005* ubuntu        HD(1,GPT,925d583f-d383-49d0-9a23-7efb9ffdc926,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO

```

Regards

---

