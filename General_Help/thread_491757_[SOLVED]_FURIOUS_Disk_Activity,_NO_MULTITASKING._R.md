---
title: "[SOLVED] FURIOUS Disk Activity, NO MULTITASKING. Resources Totally Hogged. WHY??"
date: 2007-07-04
forum: General Help
---

### Post by OzzyFrank on 2007-07-04
OK, I was thinking it was something amiss between my system and its relationship with package managers, but now I don't think it is. While updating or installing, my system would start slowing down, eventually coming to a complete halt, but not crashing as such, as the hard drive activity is non-stop, which is why I thought it had to do with poor multitasking while installing apps or system updates. However, just before all I was doing was running a few programs like browser, web page editor, Writer, and a few others... nothing to put a strain on any system... and yup, the cursor started slowing down again, downloads would eventually halt, with this constant disk activity happening all the while. This has also happened offline so in case you want to say I'm being hacked, I don't think that is it (and NOTHING can use the modem until I let it pass - could be 2 hours or so!).

What could be doing this? It's nothing I initiate, and now after a few times not running package managers i can rule them out, so what could this background process be that is causing me to lose multitasking? How can I find out what is going on, and how to stop this? Seriously, it like trying to play Quake while SETI@home is running, while the drive is being defragmented and a virus scanner is running... on Vista on a Pentium 90Mhz with 8Mb RAM (that is faulty, hehe).

Is this happening to anyone else? Other symptoms are that nothing can stop this when it starts, except for ctrl+alt+backspace, and even that can take quite a few seconds before it is recognised (and the disk activity continues for a few seconds more before finally logging me out). Anything that was running in the background will crawl to a complete halt till I let this pass, or force a logout. The shortest this has lasted for is probably half an hour, and has dragged on for over 2.5 hours before. As I've said, things start slowing down, some things you click on start not registering (but might an hour or so later!), then eventually the PC is unusable (as I've said, not really "frozen" due to the drive activity, but may as well be since I can't even type some text).

I hate to say it, but I'm really starting to dread logging into Ubuntu, as if it starts when I'm working on a document, and I can't save it, I either have to wait god knows how long or lose data when logging out and in again. I would REALLY appreciate some help on this. I'm hoping someone knows what this is all about, since it seems to be a background process that Ubuntu initiates, not me.

PS: Not sure what kind of hard disk tuning hdparm (in Services) does, but I've disabled and enabled it to no effect. Like I've said, it's like I'm running some heavy duty system apps like defragmenter etc all at once.

Also, note my 512Mb of RAM has tested fault free, and I have a new Seagate drive, latest model (not that I think they have much to do with this error).

---

### Post by Das Oracle on 2007-07-04
when this happens, have you tried running top in a terminal? see if any programs are using a great deal of memory. The hard drive action you hear is when you run out of memory and ubuntu uses a  swap file as more memory. You can confirm this, again, by top as it will display your memory and swap usage. Please post what you find in top.

**note** to organize stuff by memory, cpu, etc in top press shift+. or shift+,

*I know i specifically have that issues when songbird is running for some reason. but other than that I don't have this problem

---

### Post by OzzyFrank on 2007-07-04
Thanks for that! Here's the output; hope someone can make sense of it and tel lme what to do to the offending app/process:

top - 15:11:16 up 13:51,  2 users,  load average: 0.18, 0.14, 0.88
Tasks: 136 total,   1 running, 135 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.7%us,  0.3%sy,  0.0%ni, 98.3%id,  0.3%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:    515168k total,   508616k used,     6552k free,     5588k buffers
Swap:        0k total,        0k used,        0k free,   149728k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
17750 root      15   0  311m  25m 8404 S    1  5.0   1:34.26 Xorg                                                                                            
18002 root      15   0 88508  12m 8788 S    0  2.6   0:12.58 firestarter                                                                                     
19296 ozzman    15   0  2316 1188  880 R    0  0.2   0:00.23 top                                                                                             
    1 root      18   0  2908 1408   88 S    0  0.3   0:01.52 init                                                                                            
    2 root      RT   0     0    0    0 S    0  0.0   0:00.26 migration/0                                                                                     
    3 root      34  19     0    0    0 S    0  0.0   0:00.12 ksoftirqd/0                                                                                     
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                      
    5 root      RT   0     0    0    0 S    0  0.0   0:00.11 migration/1                                                                                     
    6 root      34  19     0    0    0 S    0  0.0   0:00.32 ksoftirqd/1                                                                                     
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                      
    8 root      10  -5     0    0    0 S    0  0.0   0:00.26 events/0                                                                                        
    9 root      10  -5     0    0    0 S    0  0.0   0:00.14 events/1                                                                                        
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                         
   11 root      10  -5     0    0    0 S    0  0.0   0:00.01 kthread                                                                                         
   35 root      15  -5     0    0    0 S    0  0.0   0:00.75 kblockd/0                                                                                       
   36 root      10  -5     0    0    0 S    0  0.0   0:00.11 kblockd/1                                                                                       
   37 root      18  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                          
   38 root      20  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                    
  129 root      10  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                                                         
  156 root      15   0     0    0    0 S    0  0.0   0:01.52 pdflush                                                                                         
  158 root      10  -5     0    0    0 S    0  0.0   1:08.27 kswapd0                                                                                         
  159 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                           
  160 root      16  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                           
  791 root      15   0     0    0    0 S    0  0.0   0:00.00 kirqd                                                                                           
 2046 root      10  -5     0    0    0 S    0  0.0   0:08.26 ata/0                                                                                           
 2047 root      10  -5     0    0    0 S    0  0.0   0:00.76 ata/1                                                                                           
 2048 root      12  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                         
 2053 root      11  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                                                       
 2054 root      10  -5     0    0    0 S    0  0.0   0:03.23 scsi_eh_1                                                                                       
 2062 root      10  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                   
 2063 root      10  -5     0    0    0 S    0  0.0   0:00.02 khubd                                                                                           
 2090 root      10  -5     0    0    0 S    0  0.0   0:00.00 khpsbpkt                                                                                        
 2233 root      10  -5     0    0    0 S    0  0.0   0:00.00 knodemgrd_0                                                                                     
 2462 root      10  -5     0    0    0 S    0  0.0   0:07.60 kjournald                                                                                       
 2663 root      18  -4  2904 1064  188 S    0  0.2   0:00.67 udevd                                                                                           
 3629 ozzman    15   0 11020 1588  280 S    0  0.3   0:22.35 artsd                                                                                           
 3638 root      12  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused                                                                                       
 3821 root      14  -5     0    0    0 S    0  0.0   0:00.01 kgameportd                                                                                      
 3948 root      10  -5     0    0    0 S    0  0.0   0:00.00 cx88 tvaudio                                                                                    
 4262 root      16   0  2448  736  228 S    0  0.1   1:08.36 mount.ntfs-3g                                                                                   
 4266 root      19   0  4380 2808  368 S    0  0.5   3:30.81 mount.ntfs-3g                                                                                   
 4596 root      18   0  1652  104   32 S    0  0.0   0:00.00 getty                                                                                           
 4597 root      18   0  1652  104   32 S    0  0.0   0:00.00 getty
******************

Hey, the Swap bit looks suss... but I have a swap file. Tried originally making my own one bigger than Ubuntu makes it by default, but ended up with the 1.44Gb that Ubuntu specified it wanted. Is this saying the swap partition isn't being used? I didn't do this... did Ubuntu (if this is what is happening), and how/why? And how can I increase the swap size? I noticed just then in gparted that the maximum size is 1.44Gb, so if i want to resize it, I can only make it smaller.

---

### Post by kerry_s on 2007-07-04
no, that just say's the swap is not being used yet, which is weird because it looks like it's used most of your ram. 1 gig is more than enough for swap, more than that is usually wasted space, so your good there don't mess with that.
once you start using apps you should see that get used.

if you don't need dual core support(aka:generic) try switching to the i386 kernel. i've seen some machines have problems with the generic kernel.

other than that i would need to know more about your machine (make, model, specs).
512ram is just enough to run gnome comfortably, but if you multi task you might want to switch to something lighter on resources, right now your being tapped out just running gnome with no apps open.

---

### Post by hikaricore on 2007-07-04
You may also want to check the output of:

```
dmesg
```

When/If your system starts to slow down again.
Just to see if you're getting any weird error messages.

---

### Post by swisscow on 2007-07-04
When I run top it shows that I have a 3gb swap file, even though none of it is being used.

I have in the past to my shame tried using different OS,s and then restored my Ubuntu partitions back - but for some reason the UUID of the swap file needs updating. This could help, I am guessing.

Here are the instructions I followed, from step 2 down (you may need to step 1)

Based upon some guess-work and to threads on these forums [http://ubuntuforums.org/showthread.p...ghlight=swsusp](http://ubuntuforums.org/showthread.p...ghlight=swsusp) and [http://ubuntuforums.org/showthread.p...highlight=uuid](http://ubuntuforums.org/showthread.p...highlight=uuid) , I did the following to restore swapping on my system because apparantly somewhere something has gone wrong with my swap partition setup... 
 
 Logged in as root:
 
 1. I opened GParted (System > Manage > GNome Partition Editor) and right-clicked the partition that was intended to be swap but now marked "unknown" (see previous post) and selected 'Format as > Swap'. Then clicked 'Edit > Apply'.
 
 2. Right-clicked the newly formatted swap partition and selected 'Swap on', applied again and closed GParted.
 
 3. Went to Locations > Computer > Filesystem > /dev/disk/by-uuid/ and by right-clicking and selecting each of the symlinks in that folder, found which uuid pointed to the partition I had just assigned as swap (2). Then right-clicked the symlink, chose 'Rename...' and hit Ctrl+C to copy the uuid to clipboard. Closed the window (without changing the uuid ofcource!).
 
 4. Opened a Terminal screen and entered the command: 

```
sudo gedit /etc/fstab
```
 and found in the Text-editor the line where is said
 
```
UUID=.....some-wrong-uuid.... none            swap    sw              0       0
```
 and pasted the new uuid over the old one with Ctrl+V. Then Ctrl+S to save the change and closed the editor again.
 
 5. Then entered in the Termina screen: 

```
sudo gedit  /etc/initramfs-tools/conf.d/resume
```
 and pasted the new uuid again over the old one after RESUME=UUID=... Then saved the changes again.
 
 6. Then entered in the Terminal Screen this command:
 
```
dpkg-reconfigure initramfs-tools
```
7. After all that, first rebooted the system and checked if swap use was normal again by opening System Monitor (System > Manage > System Monitor) on the tab Graphs: it said Swap 0 bytes of 1.6 GB...
 
 Ffffewwww.... Swapping has been restored again

---

### Post by southernman on 2007-07-04
> Swap: 0k total, 0k used, 0k free, 149728k cachedThat line tells me your swap file is not on.

You can turn it on in gparted by right clicking the partition and select swapon, or you could use the terminal and do "swapon" (that may not be the full command).

---

### Post by GeneW on 2007-07-04
[I]
3. Went to Locations > Computer > Filesystem > /dev/disk/by-uuid/ and by right-clicking and selecting each of the symlinks in that folder, found which uuid pointed to the partition I had just assigned as swap (2). Then right-clicked the symlink, chose 'Rename...' and hit Ctrl+C to copy the uuid to clipboard. Closed the window (without changing the uuid ofcource!).[/I]

Where is this "Locations" menu?  I'm running Gnome and don't have such a thing.

---

### Post by Rui Pais on 2007-07-04
> **GeneW said:**
> [I]
3. Went to Locations > Computer > Filesystem > /dev/disk/by-uuid/ and by right-clicking and selecting each of the symlinks in that folder, found which uuid pointed to the partition I had just assigned as swap (2). Then right-clicked the symlink, chose 'Rename...' and hit Ctrl+C to copy the uuid to clipboard. Closed the window (without changing the uuid ofcource!).[/I]

Where is this "Locations" menu?  I'm running Gnome and don't have such a thing.

Locations is on main menu. Or using Nautilus, Locations>Computer can be reached on Menu, Places->Computer.
A better and simple method to find UUIDs is do on terminal:
```
blkid
```
or if you want the uuid of a specific partition /dev/sdXX:
```
sudo vol_id -u /dev/sdXX
```
hth

> **southernman said:**
> That line tells me your swap file is not on.

You can turn it on in gparted by right clicking the partition and select swapon, or you could use the terminal and do "swapon" (that may not be the full command).

yes thats right. Seems that swap is not mounted/used... probably because of something like swisscow said, an UUID change.
But, keeping in track with the problem here, that shouldn't be the issue, on the opposite. 
If swap is not mounted, is not used and the write on disc is even reduced, all memory is managed at RAM...

---

### Post by GeneW on 2007-07-04
blkid gave me this:

```

[root@ewilson-laptop] blkid 
/dev/sda1: TYPE="ntfs" 
/dev/sda2: LABEL="IBM_SERVICE" UUID="44A2-082F" TYPE="vfat" 
/dev/sda3: UUID="b9305275-ca75-4e92-8311-9fad6658a4d4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="1539e1bc-7922-4af9-8273-a2363b612483" TYPE="swap" 
/dev/mapper/sda5: TYPE="swap" UUID="1539e1bc-7922-4af9-8273-a2363b612483" 
/dev/mapper/sda3: UUID="b9305275-ca75-4e92-8311-9fad6658a4d4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/mapper/sda2: LABEL="IBM_SERVICE" UUID="44A2-082F" TYPE="vfat" 
/dev/mapper/sda1: TYPE="ntfs" 
```

So I pasted 1539e1bc-7922-4af9-8273-a2363b612483 into my fstab file so that the line for /dev/sda2 looks like this:
```
UUID=1539e1bc-7922-4af9-8273-a2363b612483 none swap sw 0 0
```

And pasted the same UUID to:
/etc/initramfs-tools/conf.d/resume

And then ran:
dpkg-reconfigure initramfs-tools

And then typed:
swapon -a

After that top says:
Swap:  2112508k total,        0k used,  2112508k free,   331924k cached

---

### Post by Rui Pais on 2007-07-04
> **GeneW said:**
> ...
So I pasted 1539e1bc-7922-4af9-8273-a2363b612483 into my fstab file so that the line for /dev/sda2 looks like this:
```
UUID=1539e1bc-7922-4af9-8273-a2363b612483 none swap sw 0 0
```

And pasted the same UUID to:
/etc/initramfs-tools/conf.d/resume

And then ran:
dpkg-reconfigure initramfs-tools

And then typed:
swapon -a

After that top says:
Swap:  2112508k total,        0k used,  2112508k free,   331924k cached

But then I rebooted, and when the system came back up, blkid showed a different UUID and swap was back to not working.

UUID changed? thats weird? 
have you formated or partitioned anything meanwhile (not necessarily at Ubuntu)?

Are you sure that you saved the changes on /etc/fstab?

I doubt that dpkg-reconfigure initramfs-tools is needed... 
do you mind to redo that steps but skip that one.

the swapon activates the

---

### Post by GeneW on 2007-07-04
I did it all a second time and now it seems to be sticking.

---

### Post by OzzyFrank on 2007-07-04
Hi and thanks all. Yes, I thought from that info that my swap wasn't activated, as it listed the amount of RAM so the amount of swap should have been listed too. I went into gparted and yes, just right-click the partition and choose "swapon". The output of top is now:

top - 01:45:19 up  8:49,  2 users,  load average: 0.30, 0.17, 0.11
top - 08:20:58 up 15:25,  3 users,  load average: 2.24, 1.42, 1.12
Tasks: 143 total,   3 running, 138 sleeping,   0 stopped,   2 zombie
Cpu(s): 11.7%us,  4.2%sy,  0.0%ni, 82.3%id,  0.6%wa,  1.0%hi,  0.1%si,  0.0%st
Mem:    515168k total,   508860k used,     6308k free,     1428k buffers
Swap:  1510068k total,      104k used,  1509964k free,    90308k cached

I would bet this started after the very first drive rename Ubuntu did. Oh, you were wondering how UUIDs could possibly have changed? Well, only a few days after installing Feisty in May I let it update the kernel, then the next reboot I had no mounted drives (or Ubuntu was doing its automount thing, but drives weren't as specified in fstab). Since then I have gone into fstab to change my drives from **hda** to **sda** and back again 4 times. At least no matter what the Ubuntu drive was listed as it would boot into the system... had wondered whether the swap was being affected, but figured the system would throw up a big stink without one, so of course would surely alert me to the fact the swap was missing. Seems it will try to trod along without a swap without complaint (but with noticable performance degradation).

I hope the development team addresses this weird thing, as I expect to boot up again to no mounted drives and to do a quick edit of fstab, but of course I shouldn't have to be doing this, and of course would be quite nerve racking for newbs. Not to mention having a system that all of a sudden slows to a crawl coz of a non-existent swap partition.

Anyway, thanks all... will see how things go but this should be it. I mean, zero swap to 1.44Gb should make a difference, hehe. So thanks for the great info guys; many of us wouldn't even know commands like **top** exist.

---

### Post by southernman on 2007-07-04
Your welcome Ozzy... (maybe I should wait till you've had a chance to run the box a day or two, before saying that!).

With only 512MB of RAM, you definately need to use a swap file. I run 1024MB and my swap rarely gets pulled into play.

---

### Post by OzzyFrank on 2007-07-05
Yes, I was wondering whether the **swapon** would last after the next reboot, and it didn't. At least til I solve this I know I can at least manually turn the swap on. I will have to check the UUID issue mentioned in this thread, as that what I think it must be. Have a look at **fstab**:

# Entry for /dev/sdb1 :
UUID=2d0e29e9-b3c6-4fb7-b2fa-7e876dc2f630 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=ae50f6e3-cae4-4313-8876-fd919322f913 none swap sw 0 0

Spelling mistake or not, it is telling me the swap partition (sdb5) is unknown, and I gather fixing that would be useless, as it appears to be a comment (but I changed it anyway). Now, I have had issues with hda becoming sda then hda then sda, etc, since installing Feisty, but I thought the UUIDs were sort of hardwired an not as easily changeable. I'll have to use that tip for sussing out UUIDs and if it is amiss, I gather changing it in fstab should mount the swap successfully from now on (?).

Can anybody tell me what the hell happened since Edgy? Nothing like this ever happened back then, but starting afresh on a new drive with Feisty, it's happened a few times after updates. I originally got the impression hda meant the drive was IDE, since when I saw drives being mentioned as sda in forums, they were talking about SATA drives. I installed Feisty, and my drives started with "s", so thought "Oh, they must have changed it to all drives starting with s", but then a couple weeks later they were back to the familiar hda etc. And they changed every few weeks.

Since I have had this memory issue since not long after installing Feisty, I would have to assume the swap got disabled back then. Since I can't just change aa "s" to an "h" or vice versa for the swap (unless that line isn't a comment), I'll see if i can nut out this UUID issue.

EDIT: Not much luck finding the swap's UUID so far, as **sudo vol_id -u /dev/sdb5** has no result, literally. Trying this with other partitions either gives me the UUID or **/dev/sdb7: error open volume** if it can't find it. But when I do it for the swap, I just get the command prompt again with no output whatsoever.

**blkid** wasn't that useful either, as it only listed the Ubuntu partition's UUID, as you can see:

/dev/sda1: TYPE="ntfs" 
/dev/sdb5: TYPE="swap" 
/dev/sdb6: TYPE="ntfs" 
/dev/sdb1: UUID="2d0e29e9-b3c6-4fb7-b2fa-7e876dc2f630" SEC_TYPE="ext2" TYPE="ext3"

Also should ad mention of the swap from **dmesg** output:

[  477.822861] Adding 1510068k swap on /dev/sdb5.  Priority:-1 extents:1 across:1510068k

---

### Post by OzzyFrank on 2007-07-05
Oh, will I have to do more than just change a UUID in fstab when I finally locate the swap's? That's assuming they don't match.

PS: Addressing questions about causes of UUID changes, like partitioning, I can tell you that if mine has changed, it was not due to anything I did. As for the hda vs sda thing, not my fault either, nor was the one time that my Mac OSX partition changed from being hda7/sda7 to what it is now, sda3 (I swear I didn't do that, but the kernel update, along with the usual "h" to "s" change. I don't even know if you can swap partitions numbers around, but Ubuntu seems to tell me you can, hehe).

EDIT: Looking through tips, I went to **/dev/disk/by-uuid **and there are 4 entries, including the Mac OSX and Windows partitions, but none for the swap! What the hell is going on?

Thought I would look elsewhere, and in **/dev/disk/by-path** there is one for sdb5 (swap) which is **pci-0000:00:1f.1-scsi-0:0:1:0-part5**. In** /dev/disk/by-id** there is one too: **scsi-1ATA_ST3320620A_9QF3JTA4-part5**.

Oh, and had a look in Qparted and for the swap an option was **Activate**... do I need to be doing this as well as the **swapon** in Gparted? I figured they'd be the same thing, but have no idea why Qparted would have that option open, seeing it is already being used right now (and so in Gparted the option is now **swapoff**).

---

### Post by Rui Pais on 2007-07-05
> **OzzyFrank said:**
> Oh, will I have to do more than just change a UUID in fstab when I finally locate the swap's? That's assuming they don't match.

PS: Addressing questions about causes of UUID changes, like partitioning, I can tell you that if mine has changed, it was not due to anything I did. As for the hda vs sda thing, not my fault either, nor was the one time that my Mac OSX partition changed from being hda7/sda7 to what it is now, sda3 (I swear I didn't do that, but the kernel update, along with the usual "h" to "s" change. I don't even know if you can swap partitions numbers around, but Ubuntu seems to tell me you can, hehe).

Hi,
the changes from hda to sda are due to changes on the kernel module (driver) that deals with hard discs. It used to be 2 different modules, one for PATA and one new for SATA. 
Then they change new for deal with both drives (seems that old have confuse code and hard to mantain). 
Then they change something inside that made the names change from hdXX to sdXX... but only on certain conditions (in my case if i boot from a pata disc it says that disc is hda and my 2nd, a sata, is sd**a**, but if i boot same kernel from sata, it says hda is sda and 2nd sata turn on sd**b**. 
And to make things worst a weird bug appeared somewhere (its new code...) that changes (randomly?) the nomenclature for pata and numeration discs for sata (sometimes my sata is change to sdc or sde for no reason at all). 
:(

We can only hope that with times things settle down and became more stable.

Now, UUIDs are the best way to make those changes "invisible" to the user.
Your problem is here, and its more harder then a simple mane change. 
Apparently, for some reason, your kernel seems to be incapable of detect UUID of some partitions... I never heard of nothing related.

Use gparted to ensure that your sda5 is really formated to be swap. Note that anytime you reformatted it change UUID and implies that you manually change your fstab (the down side of using UUIDs). The line with # are in fact comments, change it don't change nothing... You must ensure that you can get the correct uuid of swap partition and its the same that appear on the line of fstab that starts with "UUID=" and ends with "none swap sw 0 0"

Btw, whats your:
```
ls -l /dev/disk/by-uuid/
```
?

---

### Post by OzzyFrank on 2007-07-05
**ls -l /dev/disk/by-uuid**

lrwxrwxrwx 1 root root 10 2007-07-06 07:56 01C5829F12BE4EC0 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-07-06 07:56 2d0e29e9-b3c6-4fb7-b2fa-7e876dc2f630 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2007-07-06 07:56 480A8D0B272B1472 -> ../../sdb6
lrwxrwxrwx 1 root root 10 2007-07-06 07:56 BDB3D2A39D0B85DD -> ../../sdb3

As you can see, no sdb5, but as mentioned, entries for that partition exist in those other folders in /dev that I noted. And yes, the swap is formatted as such, or at least I assume Ubuntu did that for me when it set it up, considering it is in use right now. Not sure, but I don't think the swap can be used if it is formatted as anything else. Oh, and yeah, Gparted reports it as** linux-swap**.

Funny thing is fstab has a UUID for it, whether it is right or not, so at one point Ubuntu had no problem with it. Any other ideas, guys? Cheers

PS: Can confirm that once I turn the swap on manually, it definitely is in use, as I am watching it in **top** as I load more intensive apps like the Update Manager etc. Also, to save anyone asking, yes I am definitely sure the swap is sdb5, as Gparted etc agree with that (as well as some of the output I've pasted in this thread).

---

### Post by Rui Pais on 2007-07-05
> **OzzyFrank said:**
> ...
And yes, the swap is formatted as such, or at least I assume Ubuntu did that for me when it set it up, considering it is in use right now. Not sure, but I don't think the swap can be used if it is formatted as anything else. 
yes thats right... 

thats very stange. Do you mind to make swapoff, reformat again from the command line and reboot to see if kernel detects the reformated one?
```
sudo swapoff /dev/sdb5
sudo mkswap /dev/sdb5
```

the last line will reformat and will output if process gone right and the new UUID (you can copy to your fstab, the n). 
Don't forget to reboot to see if the kernel detects and see its uuid correctly

good luck.

---

### Post by OzzyFrank on 2007-07-05
I'll try that, but it's getting on 1am so will do it in the morning (my kids are here for the holidays, otherwise I'd no doubt geek through the night, hehe). But as I said, there doesn't seem to be anything wrong with the swap once I manually activate it, but if this can fix the problem, I'd be glad to format it.

---

### Post by Rui Pais on 2007-07-05
> **OzzyFrank said:**
> I'll try that, but it's getting on 1am so will do it in the morning (my kids are here for the holidays, otherwise I'd no doubt geek through the night, hehe). But as I said, there doesn't seem to be anything wrong with the swap once I manually activate it, but if this can fix the problem, I'd be glad to format it.

i doubt too... the problem is not swap working, but its uuid not be detected by the kernel :( 
I don't know how that things are done, but i think it's just a label that the formater set on partitons, and i suspect that for some reason that failed on your previous formating. 
I'm hoping that a format, from the command line to avoid any bugs in interfaces like gparted or qparted, set the partition to a correct, uuid available, state :) (hope)

Have a good night. (Kids are more important then geek around computers :D)

---

### Post by OzzyFrank on 2007-07-06
Hiya

I can confirm that formatting the swap will force the system to assign a new UUID, and that makes it easier to get it set up properly again. I'll outline the steps for those who might need them:

I went to **Gparted** and did it nice and easily from there (formatted the swap partition as** linux-swap**), then rebooted, ran **sudo swapon /dev/sdb5** and then **top** to make sure the swap was being used. Then I used** ls -l /dev/disk/by-uuid** to see if sdb5 was now listed, and sure enough it was. Then all I had to do was copy the UUID and paste it over the old one in **fstab** (**sudo gedit fstab**). The swap has been fine ever since, and I now know how to fix it up if it ever happens again.

Many thanks to all for your invaluable help.

---

