---
title: "Ubuntu won't finish loading and start"
date: 2007-06-07
forum: General Help
---

### Post by billybag on 2007-06-07
i can select ubuntu from my grub menu. After i do, the loading screen shows up, but barely loads anything. The loading bar shows some progress, but very little and then i just get a blank screen with a blinking underscore :(

the last thing i did that may have caused this, is i had azureus running last night. I closed down my system, and it just never worked afterward.

any ideas?

---

### Post by Herman on 2007-06-08
Hello billybag,
Try booting your Ubuntu Live CD and run a file system check on your Ubuntu partition.

First you will need to do 'sudo fdisk -lu' or take a look with GParted to see which partition is your Ubuntu partition, lets say it is 'dev/hda2', and it is formatted with the ext3 file system okay? Then you would use a command like this to fix your file system, ```
sudo e2fsck -y -p -f /dev/hda2
``` Try that and see if it helps you. It's just a guess, we have no way of knowing if it's even a file system problem or not, but it won't hurt except maybe being a waste of time.

Another idea is to try booting up from  [Grub's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and you may get some clues that way. Grub's Command Line interface is more interactive and you may get some useful feedback. You will be booting without the splash screen so you should be able to read  the text as Ubuntu boots so you 'll be able to see what's going on better, (where it has the problem). You could try a few different things like booting with an older kernel too.

Regards, Herman :D

---

### Post by billybag on 2007-06-08
thank you Herman. Unfortunately i dont have my ubuntu CD and i need to burn another one. I also can't do that currently, because i am away from my house for the next few days. I will experiment with the grub menu though. If it helps any, i am able to view the partition with partition magic when i boot to windows. Everything appears normal when i browse it.. but who know...

thanks again

-b

---

### Post by billybag on 2007-06-08
i desided to edit the grub so that it would not show the image splash, that way i could see what happens when ubuntu attempts to load. It stops loading when it gets to:

[78.516273] H-B 5-0:1.0:over-crrent change on port 4

I am guessing this is my USB port? Like i said, i am away from my house and brought my computer with me and only boright the essentials (moniter, keyboard, and mouse) maybe that has something to dow ith it although it had been working perfectly fine up until i restarted it that morning...

---

### Post by Herman on 2007-06-08
Well I have had a careful look over the 'dmesg' logs of three computers here, and copied each one to a file and named it 'bootmessages'. Then I tried 'grep --color 'port' bootmessages' but I can't find anywhere in any of mine where it says anything about 'over-current change'.
It does seems as if this has something to do with your USB ports, but I don't know what exactly.
Here's an example I snipped out from the middle of one of mine,
> [    3.379332] hub 1-0:1.0: USB hub found
[    3.379346] hub 1-0:1.0: 3 ports detected
[    3.481182] ACPI: PCI Interrupt 0000:00:03.1[b] -> GSI 21 (level, low) -> IRQ 17
[    3.481204] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    3.481240] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[    3.481262] ohci_hcd 0000:00:03.1: irq 17, io mem 0xea010000
[    3.539073] usb usb2: configuration #1 chosen from 1 choice
[    3.539124] hub 2-0:1.0: USB hub found
[    3.539136] hub 2-0:1.0: 3 ports detected
[    3.641023] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 18
[    3.641044] ohci_hcd 0000:00:03.2: OHCI Host Controller
[    3.641079] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[    3.641098] ohci_hcd 0000:00:03.2: irq 18, io mem 0xea011000
[    3.698947] usb usb3: configuration #1 chosen from 1 choice
[    3.698999] hub 3-0:1.0: USB hub found
[    3.699014] hub 3-0:1.0: 2 ports detected
[    3.784755] usb 1-2: new full speed USB device using ohci_hcd and address 2
[    3.801336] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 19
[    3.801360] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    3.801407] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[    3.801457] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[    3.801471] ehci_hcd 0000:00:03.3: irq 19, io mem 0xea012000
[    3.801484] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.801601] usb usb4: configuration #1 chosen from 1 choice
[    3.801653] hub 4-0:1.0: USB hub found
[    3.801664] hub 4-0:1.0: 8 ports detected I don't know, maybe try booting without anything plugged into any USB ports and then if it boots, try booting again with just your keyboard or just your mouse and see if you can tell what it is that's causing the trouble.
Unless it's detecting that too much current from your power supply can go to your USB port for some reason, you try looking in your BIOS before you boot up and check your voltages there. I'm pretty sure some of your 5.0 V goes to your USB ports. Here's an example of that, [    System Health Check]("http://www.users.bigpond.net.au/hermanzone/p1.htm#System_Health_Check")
I'm not too sure what else to suggest. If Windows boots up okay then chances are your hardware is okay, unless Windows is not sophisticated enough to care if you burn out a USB device. Or it could be some kind of a glitch in Ubuntu, I don't know.  Maybe a cheat code can get you past it, I'll look into that for you directly.
Regards, Herman :D

---

### Post by Herman on 2007-06-09
I have googled 'over-current change' and done some reading on the subject.

Here's a link about the voltage and   pin-out arrangement USB devices, [URL="http://www.hardwarebook.info/Universal_Serial_Bus_%28USB%29"]http://www.hardwarebook.info/Universal_Serial_Bus_(USB)
[/URL]
From what I can gather, there are measures in place to protect your motherboard and your USB devices from further damage if an item of hardware has a problem that causes the USB port to draw too much current.  A problem like that could be caused by a damaged motherbord or the USB ports themselves, a damaged USB cable or some kind of a problem inside the USB device.
The BIOS detects the over-current condition and the kernel is able to communicate with the BIOS. It can happen that the BIOS can give a false alarm, or the kernel can mis-read the BIOS and give a false alarm.

Just in case it is really a hardware problem, check your cables, ports and plugs and devices visually, and try to remember if anything has been dropped, exposed to moisture or received a violent impact recently. Try booting with a different mouse and also a different keyboard if those are USB devices.

If you have older kernels listed in your grub menu when you boot up, try selecting an older kernel and boot from that and see what happens. Windows isn't complaining about it, so maybe it's a glitch in your kernel if you got a new kernel recently in an update.

---

### Post by billybag on 2007-06-09
Hey. thank you so much for the advice. I still dont know what it can be though. I have tried booting with nothing plugged in and i have tried different kernals. I have the same problems.

---

### Post by billybag on 2007-06-09
OKAY so i took out my USB card and now i get this! (and now thinking back, i got this message once or twice before instead of the previous posted message)
[36.155508] kjournald starting commit interval 5 seconds
[36.155592 EXT3-F3:hdb1 orphan cleanup readonly fs

??hopefully you are still keeping up on this ;)

---

### Post by Herman on 2007-06-09
Okay, it sounds like you didn't get much further, rats! Nice try too, I like your idea of removimg your USB card, that *should* have fixed it!  :D (If your USB port had any problem). No USB card- no problem right? makes sense to me!, but no, I guess we'll need to look at a different approach now.

I'm looking up some kernel parameters to try out. I have never needed any of these myself, so they are a new subject for me.  I'm looking in this link here, for lack of a better source of information, [http://www.knoppix.net/wiki/Kernel-parameters-2.6.11  ]("http://www.knoppix.net/wiki/Kernel-parameters-2.6.11")

You mentioned earlier how you were able to edit your Grub menu remove the usplash, did you do that by pressing your 'e' key and editing it? You should be add a kernel option on the same line. 

I'm testing booting up with the option 'nousb', but that doesn't seem to have made any difference that I can see in  dmesg. I still see the same lines about USB hub found and 4 ports detected, and so on. You could try it and see if it does anything for you though.
I tried plugging in a USB external disk and it still detected it and automounted it as normal.

I have heard of people needing to boot with kernel parameters like 'noacpi', or  'nodma', or 'noapic' and others like that.

Here's the Wikipedia link about acpi, [http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface) I don't imagine using that parameter would help any. 

Here's the Wikipedia link about dma, I wouldn't think booting with 'nodma' would be useful either, [http://en.wikipedia.org/wiki/Direct_memory_access](http://en.wikipedia.org/wiki/Direct_memory_access)

Here's the Wikipedia link about apic, [http://en.wikipedia.org/wiki/Intel_APIC_Architecture.]("http://en.wikipedia.org/wiki/Intel_APIC_Architecture")
Maybe that one would be worth a try. I'll try booting with that and see what it does in one of my computers here. Mind you, I'm not the one with the problem, but at least I can experiment and look at dmesg and see how it affects that.
Regards, Herman

---

### Post by billybag on 2007-06-09
probably doesnt matter but i copied that error message a little wrong

[36.155508] kjournald starting commit interval 5 seconds
[36.155592] EXT3-fs:hdb1 orphan cleanup readonly fs

F3 should have been fs. i will try that nousb option now though

---

### Post by Herman on 2007-06-09
Here's a nice link I thought could be relevant to this subject, 
**[grumpymole: [B]Ubuntu** - How To Edit Grub **Boot** Parameters]("http://www.google.com.au/url?sa=t&ct=res&cd=2&url=http%3A%2F%2Fgrumpymole.blogspot.com%2F2007%2F05%2Fubuntu-how-to-edit-grub-boot-parameters.html&ei=PmhrRsoPh9iDA9XFod4C&usg=AFQjCNFojVbuMBDWPKytAslePTzfVc-dFQ&sig2=6qif5XMH6CE3wDQS3ebcLw")

[/B]Sub-links off that first link are good, "[This site]("http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO-3.html") is quite good.  Also, [this page]("http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html")"

---

### Post by billybag on 2007-06-10
i used the command RW since it seemed pertinent to my previous msg. this time i got:

EXT3 FS on hdb1, internal journal

what is this journal thing that it keeps mentioning? Does this sound like a RAID issue to you? This just seems so random because like i said, it was working fine one minute, then this happened the next.

---

### Post by billybag on 2007-06-10
okay... that last message i got seems to be a normal thing. I googled it and it seems to show up anyway, even if their is not problem... at least that is what i have concluded. So i am wondering why it is the last message it shows before it stops attempting to load ubuntu. the orphan cleanup message i got may even be normal as well.But deffintely the USB thing was an issue... but now what is the issue?

---

### Post by billybag on 2007-06-10
Okay so what if those message aren't even pertinent to my problem, i am thinking... I have never loaded ubuntu without that splash screen, so for all i know... i could have always been getting those messages and i am willing to bet that i have. So this kind of brings us back to square one, eh?

i mentioned before that i have partition magic 8 on windows. Do you think their may be anything i can do with that. I have already browsed the harddrive that my ubuntu is on and deleted music and video files that i dont need anymore, thinking maybe my harddrive was just too full... but that didnt seem to do anything.

---

okay so i booted in recovery on the oldest kernal i had in my grub menu and i got this for the last 4 lines:

INFO: recovery required on readonly filesystem
write access will be enabled after recovery
orphan cleanup readonly
kjournal starting commit interval 5 seconds

still, it is possible i have always gotten this... but i believe this means things did not shut down properly/tidely. the only thing is i  have ext3... so i am not sure how to go about recovering :(

---

### Post by Herman on 2007-06-10
Yeah, you're right, those boot up messages could be indicating a file system problem now.
Yesterday one of the first things I did was try and experiment with a USB port and I deliberately shorted one out with a paper clip. The computer (my amd64 desktop box), didn't even get as far as Grub, but I got the following message from the BIOS, "USB Device Over Current Status Detected!! System Will Shut Down After 15 Seconds~".
When I tried shorting a USB port in my laptop, it just made it freeze, that's all. So a real problem with a USB port can make the machine fail to boot, or a false alarm from the BIOS and likely from the kernel too. 
Okay so we're over that problem of course but the machine still isn't booting up all the way. 
I agree with you, a file system check is always a good idea, it always does some good and  I have seen a few puzzling problems solved instanly and 'miraculously' by file system checks. 
The Ubuntu Live CD is great for running a file system check from, and so is GParted LiveCD, Knoppix, or almost any Live CD.
You boot your Live CD and open a terminal and use 'sudo fdisk -lu' or check with a graphical partition editor to see what partitions you have if you don't already know for sure.
Then presuming you have the ext3 file system you would run something like,
```
sudo e2fsck -f -y -v /dev/hda2
``` and
```
sudo e2fsck -C0 -f -p -v /dev/hda2
``` Where: your Ubuntu partition is /dev/hda2, or partition 2 in your first hard disk, please alter the command if it's some other disk and partition number.
The first one should fix most bad file system problems and the second one should just tidy it up a little bit more. Those won't hurt and they may help.
Your orphaned file should turn up in your lost+found directory. If it's not a vital part of your operating system your system should boot and we can look at ways of recovering the file from the lost+found then.

---

### Post by billybag on 2007-06-10
Is the ubuntu live cd available to download, because i dont have the disk :(

and also, i said before that i was away from my home. I will be at my home monday night and that is when i will burn a live cd, if i can, and try this.

---

### Post by Herman on 2007-06-10
I remember you said you were away from home already, but obviously you at least have internet access wherever you are. If you can get a blank CD or USB disk somehow the smallest download I can think of (and most useful) would be here, [GParted -- Welcome]("http://gparted.sourceforge.net/").
You could download the latest GParted LiveCD for CD or for USB disk. The latest release is gparted-livecd-0.3.4-7.iso and it's only 48.6 MB (50944000 bytes) to download, and it's free. I just downloaded a copy myself right now, I'm going to try to install it in an external USB drive just for fun. I don't know if you can install GParted to USB in Windows, but you should be able to burn an .iso file to a CD in Windows at least.

If you can burn that to a CD or turn it into a USB disk you should be all set!  All you need to do is boot GParted and right-click on your partition and click 'check'. 
I just hope that's your problem and a file system check will fix it for you. If you end up with that orphaned file in lost+found, here is the best link I have so far about how to get a file back out of the lost+found, [http://www.linuxjournal.com/article/193](http://www.linuxjournal.com/article/193), and scroll down to the paragraph titled 'The Lost+Found Directories'.

At worst this could be just a waste of time, but it might fix it. I don't want to be wasting anyone's time, but I can only go by the clues we can gather, and so far the boot-up messages are the best way I can think of to try to diagnose what's wrong. They could be entirely misleading for all we know, or we could be making the wrong assumptions about them, but they're the best way I can think of so far to approach your problem. So I appologize in advance if this doesn't solve your problem. I'll be keeping my fingers crossed for you.

UPDATE: I happened to find this thread, 			 			 			 			[ext3 journal problems]("http://ubuntuforums.org/showthread.php?t=469765&highlight=lost+found"), else where here in the forums. When I read post #5 it made me feel better, it tends to confirm that we're on the right track here thinking that a file system check will be the best thing to try. :)
 			  		


---

### Post by billybag on 2007-06-11
Well, i did just what you said and my ubuntu started up :)

Now i have thre folders in LOST+FOUND. i am not sure if it is related. In one folder, it has a file called SOCKET,  Next folder contains AGENT.12641, and the third folder also contains AGENT.12641

I ran into some aptitude errors so i did dpkg --configure -a and got this:

```

root@Waffle:/home/billy # dpkg --configure -a
Setting up linux-libc-dev (2.6.20-16.29) ...
Setting up linux-image-2.6.20-16-386 (2.6.20-16.29) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-386
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.20-16.28 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.20-16.28 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Your /etc/kernel-img.conf needs to be updated. Read grub's NEWS.Debian[1]
file and follow its instructions.

 1. /usr/share/doc/grub/NEWS.Debian.gz


You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.20-16-386
Found kernel: /boot/vmlinuz-2.6.20-15-386
Found kernel: /boot/vmlinuz-2.6.20-14-386
Found kernel: /boot/vmlinuz-2.6.20-13-386
Found kernel: /boot/vmlinuz-2.6.20-12-386
Found kernel: /boot/vmlinuz-2.6.20-11-386
Found kernel: /boot/vmlinuz-2.6.20-10-386
Found kernel: /boot/vmlinuz-2.6.20-9-386
Found kernel: /boot/vmlinuz-2.6.20-8-386
Found kernel: /boot/vmlinuz-2.6.17-11-386
Found kernel: /boot/vmlinuz-2.6.17-10-386
Found kernel: /boot/vmlinuz-2.6.15-27-386
Found kernel: /boot/vmlinuz-2.6.12-10-386
Found kernel: /boot/vmlinuz-2.6.10-6-386
Found kernel: /boot/vmlinuz-2.6.10-5-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


Setting up mplayer (1.0~rc1-0ubuntu9.1) ...

root@Waffle:/home/billy # 

```

i did dpkg --configure -a again afterwards and got nothing... so i dont know if that whole mess was fixed or what it meant.

---

### Post by Herman on 2007-06-12
Hey there billybag! :)
I'm happy to see you got it to boot up! Well done! :D

It looks to me as if everything is probably okay if your system boots up and runs normally, but only time will tell. I haven't had any experience myself with restoring files from the /lost+found. That link I already gave you is probably the best I've seen on that subject, it didn't mention anything about finding files in there named 'SOCKET' or 'AGENT.####' did it? I don't know.  I'll try to find out a little more about that, but it may take time. It's something that doesn't happen very often. All I ever see in any of my /lost+found directories when I do 'sudo ls -a /lost+found' is:  . ..
Hopefully they'll just be some unimportant obscure files you'll never ever need or miss, or maybe they'll be replaced anyway in an update. If I learn any anything more about restoring files from the /lost and found I'll tell you right away.

Here are a few of my favorite links on the Ext3 file system, 
[5.10. ]("http://www.tldp.org/LDP/sag/html/disk-usage.html")[Filesystems]("http://www.tldp.org/LDP/sag/html/filesystems.html")[SIZE=-1]**  Linux System Administrators Guide**[/SIZE]
                              
                              [Design and Implementation of the Second Extended Filesystem]("http://web.mit.edu/tytso/www/linux/ext2intro.html")

**[EXT3, Journaling Filesystem]("http://olstrans.sourceforge.net/release/OLS2000-ext3/OLS2000-ext3.html")**

                               [B][Linux ext3 FAQ]("http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html")
[/B]

You got a new kernel too eh? :D (That what it looks like to me form your  dpkg --configure -a report there.

Well bye for now, and all the best,
Regards, form Herman :D

UPDATE: Here are some more links on /lost+found,
[http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html)

[http://www.sunmanagers.org/pipermail/summaries/2004-November/005866.html](http://www.sunmanagers.org/pipermail/summaries/2004-November/005866.html)

[http://archives.free.net.ph/message/20050811.104345.e1c72f03.en.html](http://archives.free.net.ph/message/20050811.104345.e1c72f03.en.html)

[http://ubuntuforums.org/archive/index.php/t-229143.html](http://ubuntuforums.org/archive/index.php/t-229143.html)

---

### Post by Herman on 2007-06-12
Hello billybag,
This link I found for a .pdf doc seems to very really great! It goes into explaining the problem of having files in the lost+found and how to recover them in quite a bit of detail. I'm finding it extremely interesting. Hopefully it will help you.
> [SIZE=-2]**[PDF]**[/SIZE] **[Untitled]("http://www.oreilly.com/catalog/morelnxsvrhks/chapter/hack96.pdf")**
[SIZE=-1]File Format: PDF/Adobe Acrobat - [View as HTML]("http://72.14.253.104/search?q=cache:oualAZD4w_UJ:www.oreilly.com/catalog/morelnxsvrhks/chapter/hack96.pdf+ext3+lost%2Bfound+directory&hl=en&ct=clnk&cd=2&gl=au")
The first thing to do when exploring an ext2 or **ext3 lost**+**found directory** is. to prepare an area on another disk to which you can temporarily copy files **...**
[www.oreilly.com/catalog/morelnxsvrhks/chapter/hack96.pdf]("http://www.oreilly.com/catalog/morelnxsvrhks/chapter/hack96.pdf") - [Similar pages]("http://www.google.com.au/search?hl=en&q=related:www.oreilly.com/catalog/morelnxsvrhks/chapter/hack96.pdf")[/SIZE]  That looks like really great info and I believe it will probably turn out to be the best link I'll ever find on this subject for years. 

Regards, Herman :)

---

### Post by billybag on 2007-06-12
thanks for al the help

-b

---

### Post by Herman on 2007-06-13
:D Okay, thanks for sticking with me through all that! I benefitted a great deal also, you helped me learn more too, it's been great working with you. All the best with it and see you around the Ubuntu Web Forums! :D
Regards, Herman

---

