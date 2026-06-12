---
title: "how to?'s for a newbee"
date: 2008-04-26
forum: General Help
---

### Post by creekchub on 2008-04-26
i want to try a linux base system.  i downloaded the iso but while running winmd5sum they are not the same.  where can i get a good copy of the iso?  i did manage to burn one cd before i knew about the checksum. it will boot and i can get to the partition but there is not a wasy to install with out wiping out my windows.  i want to run a dual boot system for now just to get my feet wet!

---

### Post by AndyCooll on 2008-04-26
I good way to download a distro and ensure it works is by via a torrent since the client will check the integrity of the download.

You can find some howtos in my signature, including howto dual boot.

:cool:

---

### Post by JimmyHopkins on 2008-04-26
> **creekchub said:**
> i want to try a linux base system.  i downloaded the iso but while running winmd5sum they are not the same.  where can i get a good copy of the iso?  i did manage to burn one cd before i knew about the checksum. it will boot and i can get to the partition but there is not a wasy to install with out wiping out my windows.  i want to run a dual boot system for now just to get my feet wet!

When asking how you want to partition your hard drive (step 4 in the install process), select manual.

---

### Post by creekchub on 2008-04-26
ive downloaded it 3 times from the Ubuntu home website and each time the download does not match in the winmd5sum.  anyhow the one copy i have will go thru boot and when i get to the partitioner i only get 3 options 
option 1 (guided- use entire disk)which erases windows completly
option 2 (guided- use the largest continuious free space)  well it say i do not have enough free space!  the windows i am running is 2k pro and i have one partiton 
option 3 (manual) i do not feel i can tackle that as of yet so can you or anyone else lend a rookie a hand!

---

### Post by ibuclaw on 2008-04-26
[EDIT] I might as well shed some light onto this matter...

1) I think the md5sum is wrong for the time being, it will be fixed soon!

2) Ubuntu also comes with a cool app called "Wubi" which installs Ubuntu within your Windows Drive without wiping any partition data (Ubuntu will just reside on one large virtual filesystem within your Windows NTFS partition).

Download the [LiveCD.]("http://www.ubuntu.com/getubuntu/download")

Burn it to a CD, and when you insert it while Windows is running, an Autorun menu will pop-up.

Just select the "Wubi Installation" in the Menu.

And when you reboot your PC, you'll see "Ubuntu" in your Windows Boot Menu,

That's the best way to get your feet wet.

If you like it, you can uninstall Wubi like any other Windows Program (in your Add/Remove Apps Menu). And have a go at it yourself on a real hard drive.

Regards
Iain

---

### Post by creekchub on 2008-04-26
ive downloaded it 3 times from the Ubuntu home website and each time the download does not match in the winmd5sum.  anyhow the one copy i have will go thru boot and when i get to the partitioner i only get 3 options 
option 1 (guided- use entire disk)which erases windows completly
option 2 (guided- use the largest continuious free space)  well it say i do not have enough free space!  the windows i am running is 2k pro and i have one partiton 
option 3 (manual) i do not feel i can tackle that as of yet so can you or anyone else lend a rookie a hand!

---

### Post by JimmyHopkins on 2008-04-26
> **creekchub said:**
> ive downloaded it 3 times from the Ubuntu home website and each time the download does not match in the winmd5sum.  anyhow the one copy i have will go thru boot and when i get to the partitioner i only get 3 options 
option 1 (guided- use entire disk)which erases windows completly
option 2 (guided- use the largest continuious free space)  well it say i do not have enough free space!  the windows i am running is 2k pro and i have one partiton 
option 3 (manual) i do not feel i can tackle that as of yet so can you or anyone else lend a rookie a hand!

I'm sorry, but the only option is to manually partition. Try it out, it has a nice GUI. Before installing, go to system->admin->gnome partition editor (it may just be called partition editor), and right click on your windows partition, and click resize. Give ubuntu about 10 gigs for a demo install. If you want all of your music on your ubuntu partition (you could just access it from your windows partition), ubuntu COULD work with only 5 gigs-ish (but that isn't much space).

---

### Post by creekchub on 2008-04-26
care to walk me through for manual partition.  that sounds about what i want to do anyhow!

---

### Post by JimmyHopkins on 2008-04-26
Well, I made a crappy video showing how to do it. Please download it. ([http://www.megaupload.com/?d=V6UZ5IUT](http://www.megaupload.com/?d=V6UZ5IUT))


A few things to note:

1. When you are done, hit apply before you exit. I didn't hit apply because I didn't want to partition my external HDD.

2. In the video, the partition editor is editing "sdb". You should probably choose "sda". I chose sdb because it is my external HDD with only one partition. If I chose sda, you'd see a mess (I have about 6 partitions, which is bad for demonstarting. So I used my external with 1 partition)

3. I resized the partition. You can resize it to whatever you want. The only number you should use is a swap partition that is "1024" MiB big. If you have an 80 GiB HDD, and you want 10 gigs for ubuntu, go into the calculator and multiply 10 by 1024, since 1024 megabytes (MiB) equals 1 gigabyte (GiB). That's why your swap partition is 1024 MiB big, it's also 1 GiB big (which is a good size for your swap partition.


4. As I said, your swap should be 1 gig. You can have windows and ubuntu be however big you want, though. If you want windows to be shrank to 30 gigs, multiply 30 times 1024, and enter it in the box (when it asks for the partition's new size).

EDIT: A few things I forgot. When you are done partitioning and exit gnome partition editor, you should then start the ubuntu installer. Choose manually partition. Right-click on the 1 GiB swap partition you created, and select "edit". Set the mount point as "swap". Then right click the "ext3" partition you created, choose edit. Set the mount point as "/". Then click on the box that will format your swap partition and ext3 partition (basically format everything that isn't your windows partition), and continue on with the install. If you are unsure, do what I've said, and before continuing, take a screenshot (press "printscreen sysrq" on your keyboard) and post it on the forum so we can see how you partitioned your HDD. Note that your HDD isn't partitioned until the last step of the installer, so if you accidentally continue onto step 5, you aren't screwed.


If you can't figure out which partition is your windows partition, its file system is probably either "fat32" or 
"ntfs".

---

### Post by creekchub on 2008-04-26
well i just rebooted and checked the disk for errors and it found errors in 40 files so. guess i am going to have to burn another cd!

---

### Post by JimmyHopkins on 2008-04-26
Make sure you burn at a low speed (4X), to prevent errors (any data CD should be burnt at 4X. Videos and music cd are fine at high speeds).

Also, did you understand my post?

---

### Post by creekchub on 2008-04-27
yea i did understand and thanks.  i finally got to try some of the distro out today but it seems to lock up after about 20 min. of use. i like what i see and may try Kbuntu

---

