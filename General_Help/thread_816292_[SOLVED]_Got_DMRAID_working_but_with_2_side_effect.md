---
title: "[SOLVED] Got DMRAID working but with 2 side effects"
date: 2008-06-02
forum: General Help
---

### Post by Jebtrix on 2008-06-02
Well after some time messing around with the FakeRaidHowto I got dmraid working under 8.04 Hardy. What I did different than the howto is I did a full install on one drive without raid first, tar'd it up. Then pretty much followed the howto except I restored my tar instead of creating a ubuntu installation from scratch. This way I had a working menu.lst and fstab file to work with. Now that its up and running I see 2 side effects that is mostly an annoyance but I can't help from asking.

1. When booting up I get the usual Ubuntu graphical progress bar but as soon as the bar goes from the back and forth to an actual progression it dumps into verbose boot. Now the menu.lst for Grub is still set to quite splash so I'm not sure why this happens..? Is it because when it tries to read sda (one of the raid drives) directly it gets block read errors?

2. Gnome still detects sda and sdb. Once my desktop is up I see a 499GB drive in my places. Of course it wont mount cause that is the RAID but how do I keep gnome from detecting the 'phantom' drive. Or more basically can I somehow blacklist sda and sdb from being detected and let dmraid do its job? :confused:

---

### Post by fjgaude on 2008-06-02
So many questions... why use dmraid and not mdadm? Ubuntu sees the drives as drives during boot up, and then you would use dmraid to assemble them into an array. The verbose mode takes over when a error is detecting by the OS.

Your raid is raid1 setup by the BIOS features?

Do you have a total of three drives or you are booting off the raid array?

Show us what 

```
sudo fdisk -l
```

looks like once you are at the desktop.

What program did you use to copy the entire original install of Ubuntu?

---

### Post by Jebtrix on 2008-06-02
Its RAID0 with 2 250G IDE drives (Promise TX2 IDE Raid Controller). Yes the RAID0 is my boot drive. Once I get it down pat I'll be doing it with Nvidia Sata RAID0 on my main machine. Ill give the output of that cmd once I get home to that machine. As for why dmraid, well that was the fakeraid howto so I'd thought I'd at least start there. Me only a 2 week n00b. :???:

All I did for backup was use a simple tar ball as found on another post:
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

Saved it on a usb stick. Then restored with:
tar xvpfz backup.tgz -C /target (target being the root of the mounted raid)

I was successful (mostly) doing it entirely the way the fakeraid howto showed with creating a ubuntu installation from scratch. Its when it came to doing fstab and menu.lst it became difficult because fstab was blank this way. Just seemed easier to tweak a working installation instead. I mean it works great except for these 2 issues so far.
 
Since it gets the read error on sda before dmraid is loaded you answered 'Why it happens' in my first question :)

---

### Post by fjgaude on 2008-06-03
Well, I can't say I've ever heard of anyone doing what you are doing... it is not possible in my opinion to boot from a software raid0. Consider each drive has a piece of the data, stripped it's called, and that when trying to boot you have to have the dmraid software make the array. So it seems impossible.

What likely you have is in copying from your USB you have placed all the data on one of the two drives.

When you get home, let's see the fdisk -l output to try to see what we have.

---

### Post by Jebtrix on 2008-06-03
Forums were down everytime I tried yesterday so I'll post that output tonite. I read about Grub only working on RAID1 (or installing it on all drives in an array). I can tell you for sure I extracted to the mapped array and not a particular physical drive. But I understand your skepticism. Guess we'll see tonite. Thanks for the interest in my escapade here :)

---

### Post by fjgaude on 2008-06-03
Yes, we would all like to know if you can do it with raid0. Maybe because we think it can't be done, logically, that you will succeed. <smile>

Somehow you have to have grub on one of the drives without it being spliced over to the other drive. You understand?

---

### Post by danwood76 on 2008-06-03
I boot ubuntu (and grub) off a fake RAID0 with no problems.
The fakeraid howto is a bit of an odd route to take, when I do it I install dmraid in the live session and then make it detect the arrays (sudo dmraid -ay) and then run the normal installer making sure to do a manual partition and hide all the normal drives/partitions.

Then you get a full working install which boots off a RAID0 (simple eh?)
there is one slight snag with my setup as I have 2 fake RAID0 arrays I have to manually patch the initramfs to make sure it initialises the correct array first otherwise my kernel gets confused.

This works as the RAID chipset (intel ICH) reads the boot sectors and boot files required from the striped array allowing you to load the drivers and so on up.
You cant do this with a purely software RAID due to this.

---

### Post by fjgaude on 2008-06-03
> **danwood76 said:**
> I boot ubuntu (and grub) off a fake RAID0 with no problems.
The fakeraid howto is a bit of an odd route to take, when I do it I install dmraid in the live session and then make it detect the arrays (sudo dmraid -ay) and then run the normal installer making sure to do a manual partition and hide all the normal drives/partitions.

Then you get a full working install which boots off a RAID0 (simple eh?)
there is one slight snag with my setup as I have 2 fake RAID0 arrays I have to manually patch the initramfs to make sure it initialises the correct array first otherwise my kernel gets confused.

This works as the RAID chipset (intel ICH) reads the boot sectors and boot files required from the striped array allowing you to load the drivers and so on up.
You cant do this with a purely software RAID due to this.

Thanks, very interesting... I'm not about to do this, but others may wish.

frank

---

### Post by Jebtrix on 2008-06-03
Ah so hiding is the missing ingredient. I'll have to check that out once I get home.. #-o

---

### Post by danwood76 on 2008-06-04
Sorry I didnt mean hide I meant ignore.

Then to stop gnome from displaying the drive you tell HAL to ignore it, I found this thread a few months ago on the subject:
[http://ubuntuforums.org/showpost.php?p=2605508&postcount=34](http://ubuntuforums.org/showpost.php?p=2605508&postcount=34)

BTW my splash screen doesnt work either I dont think, but I dont see the need to repair it, its only there for 20 seconds anyway.

---

### Post by Jebtrix on 2008-06-04
I tried that post to tell HAL to ignore but to no success. Since he doesn't specify explicitly I'm wondering if that works if Gnome is displaying individual drives of the array. In my situation its just displaying one drive, technically the built array in proper size. Maybe I'm missing something, I'll have to play around more.

---

### Post by Jebtrix on 2008-06-04
Nevermind it does work :) I edited out an xml tag by accident..duh

---

### Post by fjgaude on 2008-06-04
Okay, just to get this all straight and cap it off, at least for now: You do this to get the speed of two drives, raid0 stripped, which is just about double that of one drive. If one drive fails you lose everything?

---

### Post by danwood76 on 2008-06-04
Indeed you do, but to be honest I cant remember when a drive last failed on me and anything I really need is backed up anyhow.
I would say the risk is the same as having all your data on just one drive as if I had my 1TB as a single drive it would have cost me a lot more and would have been slower but still would loose it all, although statistically you are twice as likely to fail.
The chance of a drive failing is minimal though so I dont care.

---

### Post by Jebtrix on 2008-06-05
Honestly anything that is irreplaceable is burned to disc for safe keeping. For added measure any Delphi code I write is also rar'd up, password protected, and emailed to myself on 2 online webmail accounts I have in case my house or work goes up in smoke. I also sync a 32gb usb stick at the end of the day because I just like having an arsenal on hand. All I'm interested in is pure speed period. If your talking a server machine, thats a totally different story, but for desktop, speed is king! :mrgreen: imho

BTW danwood76 take a look at the solution here:
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/205990](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/205990)

It fixed the progress bar issue completely. So all in all this thread is solved! Thanks.

---

### Post by fjgaude on 2008-06-05
Happy you fellows got the raid0 to boot successfully. I too am into speed on the desktop being a graphic designer, but I can't afford a loss of data while editing, etc., thus I use raid5 with four drives. Boot from a Raptor for its speed, quickness, and if it fails it's not too difficult to re-install the OS.

How do you test for speed? I use hdparm:

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   19216 MB in  2.00 seconds = 9622.09 MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = 212.01 MB/sec

```

The md32 is the raid5, but you already knew this, eh? <smile>

---

### Post by Jebtrix on 2008-06-05
Nice numbers. Wondered how I was going to measure speed, thanks for the cmd. 

/dev/mapper/pdc_bgfbgeab:
 Timing cached reads:   482 MB in  2.01 seconds = 240.27 MB/sec
 Timing buffered disk reads:  132 MB in  3.00 seconds =  43.95 MB/sec

This is my ancient Athlon junker with 2 ATA100 WD 250Gb drives. Lol.. but hey, imagine how slow without RAID0! I got 6 sata ports on my new mobo, maybe Ill grab 6 drives from work and see if I can do a 6 drive stripe for kicks :twisted:

---

### Post by danwood76 on 2008-06-06
Nice speeds, just did mine

RAID0 set 1:
```

danny@danny-desktop:~/Desktop$ sudo hdparm -tT /dev/mapper/isw_bbbbfiiiih_HDb

/dev/mapper/isw_bbbbfiiiih_HDb:
 Timing cached reads:   9886 MB in  2.00 seconds = 4946.69 MB/sec
 Timing buffered disk reads:  322 MB in  3.02 seconds = 106.74 MB/sec

```
RAID0 set 2:
```

danny@danny-desktop:~/Desktop$ sudo hdparm -tT /dev/mapper/isw_cjfgejeghi_HDd

/dev/mapper/isw_cjfgejeghi_HDd:
 Timing cached reads:   10214 MB in  2.00 seconds = 5111.56 MB/sec
 Timing buffered disk reads:  470 MB in  3.00 seconds = 156.55 MB/sec

```

My first set is made of drives which are about 5 years old, they still arent doing too badly, second set is some cheap 500GB I bought last year.
Both sets are SATA (second set SATA2)

This threads now turned into a 'mine is bigger than yours' ;)

---

### Post by gdmix on 2008-06-07
Ubuntu dev really needs to take a look at SUSE to see how they do it. For starters, SUSE loads DMRAID during the install, and installs it by default. The problem I see with Ubuntu, is that you can install it when on the live CD, but it doesn’t even give you the option to install it during the install (to HD) process. The old RAID how-to is not needed with the current installer from what I have seen.

danwood76, didn’t you have to manually install DMRAID? I also got it installed with the right partitions, etc. but it would crash after GRUB since DMRAID was not installed. It would be nice if anything that is installed while on the live CD would be installed during the HD install. On that PC, I didn’t have the time to finish the install so I went back to SUSE. I rather have Hardy on that PC since I use it on 2 others, so I will probably go back and try again. But anyways, the route you took (and I tried) is the easiest route for Hardy, IMO.

---

### Post by danwood76 on 2008-06-08
Its been a couple of months since I installed hardy, I know with gutsy I followed the community guide which is a lot more hasstle and you dont get a full 'fresh' ubuntu system after it.

Not sure if I had to install it separately or not, I did have to do a bit of messing around as dmraid doesnt seem to like discovering all my disks.
It finds all the disks but only seems to discover partitions for one (my second disk of course), I have to manually patch the initramfs files to get it to load my first disk.

I might do a reinstall and see what happens, then write a guide for it.
As you say it probably should be installed by default or at least give you the option when you install.
I know the fedora installer worked on fakeraid when I installed it (FC5) though I don't like fedora compared to ubuntu.

---

### Post by Jebtrix on 2008-06-09
Well I did end up trying RAID0 with 5 sata drives (only got half the speed of fjgaude's RAID5, very disappointing and maybe dmraid has a performance issue??). I used your method danwood76 and it's fairly straight forward and here some steps that were needed.

0. Boot with try ubuntu livecd
1. Install dmraid from the livecd.
2. Follow the howto to do fdisk and mkfs.
*Note: had an issue with swap for some reason. Simple fix, just leave space for swap on the raid array and add/activate it after installation.
3. You will then probably get an error about cant update intrafms from livecd. Just do "dmraid -an" to deactivate array, then dmraid -ay to reactivate. If you don't you wont see the array partition in /dev/mapper.
4. Run the install from the Desktop.
5. When it gets to partitioning pick your partition ie. /dev/mapper/sdae_asd1 and mount it as root /
6. When it comes to selecting adding a bootloader it will fail. You can go to Advanced to select a partition to add a bootloader, and even see the /dev/mapper partitions but it will not let you hit OK. Thats fine, let it go.
7. Once installation is finished DO NOT REBOOT. (You will get a bootloader/grub failure message, ignore it)
8. Follow the fakeraid howto here to bind proc and dev to /target (/target is the mounted installation you just did created by the installer)
9. mkdir /target/boot/grub 
10. Copy /boot/grub/* to /target/boot/grub
11. Drop into chroot /target
12. Install dmraid. (You should see the partiton(s) in /dev/mapper, if not do a dmraid -an, then dmraid -ay)
13. Install GRUB
14. Follow the howto to setup device hd0 and set root
15. Run update-initramfs
*Note: whats great about this method, is that fstab and menu.list were set up properly with uuid's (at least for me)
16. Reboot
17. Follow howto to set swap in the space you left for it.
Done

---

### Post by fjgaude on 2008-06-09
Say, folks, to get above about 110MB/sec required that your drive controller be on at least a PCI-E X1 bus, or of course PCI-X. Mine is on the former.

When I tried raid0, four drives, about three years ago, I got 110MB/sec working off a straight PCI bus. That bus has a maximum throughput of 132MB/sec. The PCI-E X1 bus maximum is 500MB/sec.

Check your motherboard to see if you can find out the bus used for the drive controller[s].

---

### Post by Jebtrix on 2008-06-09
Ah....I wondered.. The only reason I'm still confused is that on my winbox with 2 sata's in RAID0, Sandra shows sustained output around 226Mb/s with burst into the 300s... difference in benchmark algorithm maybe? Now I'm really curious.

---

### Post by fjgaude on 2008-06-09
> **Jebtrix said:**
> Ah....I wondered.. The only reason I'm still confused is that on my winbox with 2 sata's in RAID0, Sandra shows sustained output around 226Mb/s with burst into the 300s... difference in benchmark algorithm maybe? Now I'm really curious.

You are using the very latest hard drives, the 2nd generation of perpendicular magnetic read heads? To get as you get means each are at 113MB/sec. Mine are 70. Wait you show Mb/s, is that bytes or bits, an eight to one difference.

Sandra and hdparm are not that different in sequential reads, from my experience. I don't use Sandra anymore since I've gone virtual with WinXP.

What motherboard are you using?

---

### Post by Jebtrix on 2008-06-09
After some reading that makes sense for the speeds I'm getting on dmraid. A sata controller usually has 4 ports, in Sata I at 150/MBs it does make sense. My mobo has 6 Sata II ports (not sure if its 6 on one controller though, or 4 and 2 on another). So with SATA II I should have 300/MBs to work with. I guess since I don't have SATA II HDs, I'm getting pinched into the SATA I hole. Guess somebody needs to try 4 Sata II's.. :confused:

---

### Post by Jebtrix on 2008-06-09
I'm using an ASUS M2N-E AM2 NVIDIA nForce 570 Ultra MCP

---

### Post by fjgaude on 2008-06-09
> **Jebtrix said:**
> After some reading that makes sense for the speeds I'm getting on dmraid. A sata controller usually has 4 ports, in Sata I at 150/MBs it does make sense. My mobo has 6 Sata II ports (not sure if its 6 on one controller though, or 4 and 2 on another). So with SATA II I should have 300/MBs to work with. I guess since I don't have SATA II HDs, I'm getting pinched into the SATA I hole. Guess somebody needs to try 4 Sata II's.. :confused:

No, no, with SATA each drive has the port speed, either 150 or 300. Now drives internal read/write are not at 150MB/sec quite yet.

Your speed may be controlled by something else, it's not the controllers or the MB, I don't think, though I'm not familiar enough with that chip set on yours.

What is the hdparm speed of one of your drives... you can test one even if it is in a software raid array, just as /dev/sd[nn].

---

### Post by danwood76 on 2008-06-09
What you may have is a chipset that can do RAID0 on X number of drivers but can only suck data from the bus at say 100MB/s. (or 133, whatever)

You have an nvidia chipset, which is probably pretty crap for hard disk performance (theyre very very new at hard disk controllers compared to someone like intel)
I am on an intel NB and an ICH8 hard disk controller.
My disk speeds were slower with the same drives on my old P4 system with an ICH5, this is mainly because the bus speed was PCI and my NB was only running at 230MHz.
Im now running faster controllers (ICH8) with my NB running at 425MHz allowing for greater data speed.

You will always be limited by the speed of all the busses around your CPU, RAM, NB, and the internal speeds of each device, every part introduces latencies in data transfer and so you will never achieve the rated data transfer rates.

---

### Post by Jebtrix on 2008-06-09
True nvidia is newer at the chipset game but I've had great performance on Winboxes since nForce4. I'm going quick put on WinXP and just satisfy my current disbelief at 111MB/s with 4 Satas (Needed to use the 5th Sata I had to get a machine back up and running, but using 5 still gave me 110-113MB/s avg)

Block size 128

```
root@ubuntu:/# dmraid -r
/dev/sdd: nvidia, "nvidia_affijdhe", stripe, ok, 156301486 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_affijdhe", stripe, ok, 488397166 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_affijdhe", stripe, ok, 488397166 sectors, data@ 0
/dev/sda: nvidia, "nvidia_affijdhe", stripe, ok, 72303838 sectors, data@ 0
root@ubuntu:/# hdparm -tT /dev/mapper/nvidia_affijdhe1

/dev/mapper/nvidia_affijdhe1:
 Timing cached reads:   2442 MB in  2.00 seconds = 1221.33 MB/sec
 Timing buffered disk reads:  336 MB in  3.01 seconds = **111.73 MB/sec**
root@ubuntu:/# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   2494 MB in  2.00 seconds = 1247.93 MB/sec
 Timing buffered disk reads:  140 MB in  3.02 seconds = ** 46.39 MB/sec**
root@ubuntu:/# hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   2496 MB in  2.00 seconds = 1248.61 MB/sec
 Timing buffered disk reads:  204 MB in  3.01 seconds =  **67.69 MB/sec**
root@ubuntu:/# hdparm -tT /dev/sdc

/dev/sdc:
 Timing cached reads:   2486 MB in  2.00 seconds = 1243.65 MB/sec
 Timing buffered disk reads:  200 MB in  3.02 seconds =  **66.32 MB/sec**
root@ubuntu:/# hdparm -tT /dev/sdd

/dev/sdd:
 Timing cached reads:   2496 MB in  2.00 seconds = 1248.52 MB/sec
 Timing buffered disk reads:  174 MB in  3.01 seconds =  **57.83 MB/sec**
```

---

### Post by fjgaude on 2008-06-09
Your speed is either being controlled by the software of the dmraid or by the slow controller... how can we know which?

Check your MD manual and see if they show a diagram of the chip set and bus. From there you should see if your disk controller is PCI or PCI-E.

In my early experiments with raid I have from one to four 40MB/sec drives give me 44MB/s, then 80, and 112 followed by 104, going from one, two, three, four drives, on a controller on the PCI bus. I was using dmraid. So I know the PCI bus is good for less than 132MB/sec, but can't say what dmraid does.

I gave up dmraid for mdadm and forgot the raid software on the motherboard.

---

### Post by danwood76 on 2008-06-10
The speeds on my second RAID0 seem to make sense of the x2 rule:
```

danny@danny-desktop:~/Desktop$ sudo hdparm -tT /dev/mapper/isw_cjfgejeghi_HDd

/dev/mapper/isw_cjfgejeghi_HDd:
 Timing cached reads:   9726 MB in  2.00 seconds = 4866.00 MB/sec
 Timing buffered disk reads:  428 MB in  3.01 seconds = 142.23 MB/sec
danny@danny-desktop:~/Desktop$ sudo hdparm -tT /dev/sdc

/dev/sdc:
 Timing cached reads:   9010 MB in  2.00 seconds = 4509.68 MB/sec
 Timing buffered disk reads:  234 MB in  3.02 seconds =  77.48 MB/sec
danny@danny-desktop:~/Desktop$ sudo hdparm -tT /dev/sdd

/dev/sdd:
 Timing cached reads:   9808 MB in  2.00 seconds = 4908.32 MB/sec
 Timing buffered disk reads:  230 MB in  3.01 seconds =  76.41 MB/sec

```
Cached reads are about the same, buffered reads on the set are almost the addition of the two drives.
My first set also performs the same:
```

danny@danny-desktop:~/Desktop$ sudo hdparm -tT /dev/mapper/isw_bbbbfiiiih_HDb

/dev/mapper/isw_bbbbfiiiih_HDb:
 Timing cached reads:   9866 MB in  2.00 seconds = 4937.46 MB/sec
 Timing buffered disk reads:  306 MB in  3.01 seconds = 101.52 MB/sec
danny@danny-desktop:~/Desktop$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   9124 MB in  2.00 seconds = 4565.58 MB/sec
 Timing buffered disk reads:  170 MB in  3.03 seconds =  56.07 MB/sec
danny@danny-desktop:~/Desktop$ sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   9108 MB in  2.00 seconds = 4557.50 MB/sec
 Timing buffered disk reads:  160 MB in  3.03 seconds =  52.75 MB/sec

```

---

### Post by Unix_Slayer on 2008-06-10
Man... I'm going to need to bookmark this thread. I have two separate 5 terabyte a piece, disc arrays to setup. I have 5 WD RE2 GP's in one array, and the same in the other, amounting to 10 terabytes. I wish there was a way to convert them from Win Vista to linux without destroying them. They are filled with everything I have on file. I would even convert them from ntfs, to ext3 if need be. I'm using a Silicon Image 4726 on one, and a 3132 on the other. The funny thing about the 4726, is that it shows a very small supposed partition available. This is where the card stores the raids. It can't be partitioned, but shows up every time in Vista. I'm wondering how the grub would take it as. I've booted up with them in Kubuntu, but they don't show in the operating system. The bios to the Silicon Image card shows at startup. You guys have any clue what would be the best way to go about getting them to work in linux?

---

### Post by danwood76 on 2008-06-10
For Silicon Image RAID you also need dmraid, you shouldnt have to reformat them ext3, my 1TB array is NTFS as I still use vista with the drive.

If you load up the Live CD and install dmraid from synaptic, run the following command and your array should get listed:
```

sudo dmraid -ay

```

---

### Post by Unix_Slayer on 2008-06-10
> **danwood76 said:**
> For Silicon Image RAID you also need dmraid, you shouldnt have to reformat them ext3, my 1TB array is NTFS as I still use vista with the drive.

If you load up the Live CD and install dmraid from synaptic, run the following command and your array should get listed:
```

sudo dmraid -ay

```

I wish it were that easy.

```
mgm@Apevia:/etc/X11$ sudo dmraid -ay
[sudo] password for mgm:
ERROR: pdc: seeking device "/dev/sdg" to 18446744073709502976
ERROR: pdc: seeking device "/dev/sdg" to 18446744073709533696
ERROR: pdc: seeking device "/dev/sdg" to 18446744073709371904
ERROR: pdc: seeking device "/dev/sdg" to 18446744073709412864
ERROR: sil: seeking device "/dev/sdg" to 18446744073709354496
No RAID disks
```

---

### Post by fjgaude on 2008-06-10
Do you have ntfs-3g installed? Don't remember if it is there by default.

---

### Post by Unix_Slayer on 2008-06-11
> **fjgaude said:**
> Do you have ntfs-3g installed? Don't remember if it is there by default.


It's already installed.

---

### Post by fjgaude on 2008-06-11
I'm not sure what to suggest... it looks like while Ubuntu dmraid can't see the array that has been assembled in your BIOS.

When you boot into Ubuntu you do have the drives seen by the BIOS, eh?

---

### Post by Unix_Slayer on 2008-06-11
> **fjgaude said:**
> I'm not sure what to suggest... it looks like while Ubuntu dmraid can't see the array that has been assembled in your BIOS.

When you boot into Ubuntu you do have the drives seen by the BIOS, eh?

Yes. It's not a raid in the bios. It's not a software raid, I believe. It uses the Sil4726 chipset. I actually created the raid set in the Silicon Image bios, when the system boots up. The Silicon Adapter sees it first, but not Linux. It works fine in Vista, and XP.

---

### Post by fjgaude on 2008-06-12
Well, it seems dmraid should see the array and show using:

```
sudo dmraid -tay
```

Then when you see the results, you mount the array to a previously created mountpoint:

```
sudo mount -t ntfs /dev/mapper/sil_nnnnnnnnnn /raid
```

The /raid is the mountpont, created off of /. Such works but any other would also.

---

### Post by sbaker on 2008-06-26
> **danwood76 said:**
> Its been a couple of months since I installed hardy, I know with gutsy I followed the community guide which is a lot more hasstle and you dont get a full 'fresh' ubuntu system after it.

Not sure if I had to install it separately or not, I did have to do a bit of messing around as dmraid doesnt seem to like discovering all my disks.
It finds all the disks but only seems to discover partitions for one (my second disk of course), I have to manually patch the initramfs files to get it to load my first disk.

I might do a reinstall and see what happens, then write a guide for it.
As you say it probably should be installed by default or at least give you the option when you install.
I know the fedora installer worked on fakeraid when I installed it (FC5) though I don't like fedora compared to ubuntu.

Hi there,

I have set up Ubuntu on a raid0 set using dmraid and it worked perfectly. That was until I installed a second raid0 set. It then refused to find the partitions on my first raid0 set. Will patching initramfs fix this and if so how do I do it?

---

### Post by danwood76 on 2008-06-26
Yes you basically patch the DMRAID patch within the initramfs section.
I will have a look at how I did it when I get home.

The method I used will break each time dmraid is updated, and you have to re patch.
I think there is probably a better way of doing it, creating my own loop script.
I will post back later when I get home from work.

---

### Post by Jebtrix on 2008-06-26
I'm using two RAID0 now too with no problems. The second RAID0 is NTFS with my winxp development environment that I just made an entry in fstab for access from linux. What exactly do you mean it can't find partitions? Is it not booting at all? I'm guessing the BIOS is setup to boot from the correct array and grub is only installed on the one array right? I wonder if using UUIDs to reference the arrays would help.

---

### Post by Jebtrix on 2008-06-26
Just throwing it out there.. I wonder if you can just swap (if its sata drives) the connectors for the raids, put sata1,2 on sata3,4 and vice versa. In essence, try to change the order in which your sata raid controller sees the raid sets. Maybe disconnect the first raid, boot,shutdown, then reconnect the first raid to see if the raid controller changes the order it lists the raid sets.. just an idea....

---

### Post by danwood76 on 2008-06-26
No, the problem is that dmraid only enumerates one raid set in the initramfs.
If your lucky this will be the boot set but if your unlucky like me or the poster above then it enumerates the incorrect one.

The hack is to make it call 'dmraid -ay RAID_SET_NAME' instead of just 'dmraid -ay'

---

### Post by Jebtrix on 2008-06-26
Ah, well just thought jiggling around the raid set ports/bios order might make dmraid detect a different one first.

---

### Post by danwood76 on 2008-06-26
Yeah I tried all that and failed, it worked fine with only one set plugged in.
It didnt matter which sata ports I had my drives in it always picked the wrong one 'doh!'

If you can only boot to the live CD you will need to mount your / partition and chroot into it to perform the following steps.
You can find out how to do that in the guide referenced earlier in this thread.
You may also need to use nano instead of gedit to edit the text files.

Right to perform my hack we first need to find out the name of your default array, with a bit of luck you already know but otherwise open up your fstab:
```

gedit /etc/fstab

```
And whichever partition is mount as / is your drive, so mine is:
```

# /dev/mapper/isw_bbbbfiiiih_HDb6
UUID=2f8fc25a-7dce-4c41-97f2-97d0fcc49fd6 /               ext3    relatime,errors=remount-ro,data=writeback 0       1

```
Ok so from the above I can see the raid array is called isw_bbbbfiiiih, you can verify this by running 'sudo dmraid -ay isw_bbbbfiiiih' this should output all the partitions on your boot RAID0 set.

Then we need to open up the initramfs patch file for dmraid, the initramfs script files are located: /usr/share/initramfs-tools/scripts/local-top/
If you look in there the dmraid file is: /usr/share/initramfs-tools/scripts/local-top/dmraid

So we open that as root:
```

sudo gedit /usr/share/initramfs-tools/scripts/local-top/dmraid

```

AT the bottom you will see something like this:
```

[ -x /sbin/dmraid ] && /sbin/dmraid -ay

```
You simply add your drives ID to the end of it, mine then looks like this:
```

[ -x /sbin/dmraid ] && /sbin/dmraid -ay isw_bbbbfiiiih

```
Then we need to update the initramfs to include this:
```

sudo update-initramfs -u -k all

```
This should update each installed kernels initramfs, then if you reboot it should initialise the correct array and boot.

Like I said earlier you will have to repeat this if dmraid gets updated and replaces the initramfs script in the process.

---

### Post by Jebtrix on 2008-06-26
You really need to add your expertise to the wiki :)

---

### Post by sbaker on 2008-06-26
That's great. I will give a go when I get home tonight. Sounds exactly like the problem I've been having.:)

---

### Post by sbaker on 2008-06-29
Worked perfectly. Many, many thanks. I agree with Jebtrix, you should add your expertise to the wiki. It's great to have Linux up and running at last!!:)

---

