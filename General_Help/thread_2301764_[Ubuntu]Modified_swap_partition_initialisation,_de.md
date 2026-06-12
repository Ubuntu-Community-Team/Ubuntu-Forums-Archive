---
title: "[Ubuntu]Modified swap partition initialisation, desktop environment crashes on login."
date: 2015-11-05
forum: General Help
---

### Post by ubupro97 on 2015-11-05
Ubuntu 14.04 (AMD64) running Gnome 3.

Should be latest updates as of yesterday.

I freed up a bunch of space on my Windows games hard drive, partitioned as ext3 & ext4, extended /home & / and some linux-swap (previously had none, made 12 GB to ensure hibernation is always possible on 8 GB memory). I'm stupid and there was a random 1 MiB unallocated that I couldn't add to the NTFS partition without moving ~280 GiB, so I added that as more swap. 

I discovered after a few boots that the swap needed to "onswap", I looked it up and found the initial installation had a different UUID for swap, found the new one and set that as well as adding a new line for the 1 MiB of swap (I'm just not a reasonably behaved human). I also updated the UUIDs for / and /home (even though they were working fine). I think I didn't change the UUIDs for either.

Now when I boot in either update, it boots to the login screen and if I login as my user or guest, it briefly loads, then displays a bunch of E: graphical garbage (red and green rectangles over the whole display, occurs same way on integrated graphics too) and logs out. I can login okay from terminal (Ctrl+alt+f1).

Things I changed prior to this boot:

* Installed Dropbox

* fiddled with Gnome Tweak Tool.

* disabled MSI fastboot (should be Windows only).

Edit:

In recovery tools, everything I try there seems to be a freeze on /dev/sdb6.

Picture:

[http://i.imgur.com/7LbqqF1.jpg](http://i.imgur.com/7LbqqF1.jpg)

Edit 2:

sdb6 is an ext4 partition, it is /home

---

### Post by TheFu on 2015-11-05
Please post the following, using code tags so the output lines up.
* sudo blkid
* sudo parted -l
* lsblk
* /etc/fstab

Each of these are required to help.

---

### Post by ubupro97 on 2015-11-05
> **TheFu said:**
> Please post the following, using code tags so the output lines up.
* sudo blkid
* sudo parted -l
* lsblk
* /etc/fstab

My apologies, I have little experience without the aid of some UI, so I am unsure how to save results from command line to a file that I can access. I just have a bad camera and a TV as display. I also haven't used BBCode for a long time..

```
blkid
```

[IMG]http://i.imgur.com/bG0YkQn.jpg[/IMG]

```
parted -l
```

[Img]http://i.imgur.com/9DSmH1o.jpg[/img]

```
lsblk
```

[Img]http://i.imgur.com/pDq7bKH.jpg[/img]

Note that to get all the above entries to fit on the screen, I had to unplug all the obselete hard drives in my desktop (no Linux partitions on any). This changed the mount from sdb to sda.

```
/etc/fstab
```

[Img]http://i.imgur.com/OMm470b.jpg[/img]

I have edited this a few times, so it is a bit messy. The /MEDIA7/ is obselete, I changed the comments left in installation when I shuffled the UUIDs so they matched the partitions. It's likely here I broke something.

---

### Post by sammiev on 2015-11-05
I never seen a Linux Swap on sda1 and 12GB?!?

Then again I see things on the HDD i never seen as well.

---

### Post by ubupro97 on 2015-11-06
> **sammiev said:**
> I never seen a Linux Swap on sda1 and 12GB?!?

Then again I see things on the HDD i never seen as well.

Please don't respond if you don't have anything to add (my apologies I am not allowed to ask that).

The space I freed up was a Windows partition before the Linux partition (sda1) which was running a different version of Windows, I added this swap after since it had none.

It's 12 GB because I wanted to ensure I could always hibernate, even if all of my 8 GB of memory is full and swap is already in use. There's a Windows RAID covering two drives, a copy of Windows on an SSD and a copy of Linux sharing a drive with some Windows storage.

> **TheFu said:**
> ...

I just went to boot my PC to follow someone else's instructions and it magically logged in fine.

I'm now really scared, terrified to touch anything and quite frankly less comfortable than having the problem and solving it manually.

The only thing I can think is that I replugged in all my other drives (sda, sdc, sdd) and removed a case fan.

---

### Post by Bucky Ball on 2015-11-06
If your machine is up and running again, please show the output of this command and the fstab file now, please:

```
sudo blkid
nano /etc/fstab
```

In the last fstab you have two /swap files set to go. You should get rid of one of them using Gparted (right click and make sure it is not swapon and the other one is) then delete its entry from fstab, reboot and check in Gparted all is present and you have one swap which is swapon.

Wouldn't worry too much about having more than 8Gb /swap for hibernate. Depending how resource heavy your computing practice is you may never use much of the 8Gb RAM in day to day use.

---

### Post by TheFu on 2015-11-06
I suspect there was just a loose SATA cable. Reseating it solved this issue.

For future use,
* images are wasteful and helpers cannot copy/paste solutions.
* images are unkind to people browsing here without much bandwidth.
* to capture output from commands, there are many ways.
```
lsblk | tee /tmp/log.lsblk
``` is 1 way. This gets STDOUT, but not STDERR.  

You can also open an editor, then copy/paste using the mouse. Text is easily copied/pasted on any X/Windows machine. Youtube has lots of videos showing this. Copy/paste from a terminal into these forums is trivial. Use the "Adv Reply" to get a larger menu - code tags make things much easier to see. [http://blog.jdpfu.com/code_tags](http://blog.jdpfu.com/code_tags) explains how to do it.

Anyway, if this issue is solved, please use the 'thread tools' above to mark it  [SOLVED]. This helps helpers and people seeking help, both.  Reseating a cable is a solution from  time  to time.

---

### Post by ubupro97 on 2015-11-06
> **Bucky Ball said:**
> 
In the last fstab you have two /swap files set to go. You should get rid of one of them...

Wouldn't worry too much about having more than 8Gb /swap for hibernate.

Yeah I did that straight away. Partition is unallocated, 12 GB swapon on boot.

I do sometimes heavily multitask while gaming, but I do rarely go past 8 GB. It's just HDD storage which I have far too much of, so I'm not worried about it going unused.

> **TheFu said:**
> I suspect there was just a loose SATA cable. Reseating it solved this issue.

For future use,
* images are wasteful and helpers cannot copy/paste solutions.
* images are unkind to people browsing here without much bandwidth.
* to capture output from commands, there are many ways.
```
lsblk | tee /tmp/log.lsblk
``` is 1 way. This gets STDOUT, but not STDERR.  

You can also open an editor, then copy/paste using the mouse. Text is easily copied/pasted on any X/Windows machine. 

Hmm, the disks were fine in Windows, so I doubt that was the issue. My BIOS does some weird things with Windows and maybe some sort of hybrid shutdown or fastboot feature was disabling some important hardwire component to speed up Windows boot time? (MSI mobo with clickBIOS.)

Yeah I'm sorry about the images, had no idea how go get the text using command line. I only had access to command line, so no mouse or copy and paste shooting.

Never thought of bandwidth limits before, but it makes sense. I did try a direct link, but apparently BBCode doesn't automatically parse them without using <URL> square brackets and I haven't used BBCode for a long time and couldn't remember the <URL=> or whatever syntax.

Thanks for the advise on getting the command line output to a file, no sure how I'd go about mounting somewhere to move files to from command line though.

I left the thread open in case anyone had some last minute suggestions to prevent the problem reoccuring before I reboot again (I just rebooted and everything is fine including swapon). Thread solved.

---

### Post by TheFu on 2015-11-06
If Windows8+, there are new BIOS settings specific that can break Win7 and earlier systems, including Linux. Inside the BIOS, it is "Windows 8 Support" or enable "Windows 7" support checkbox. Something like that.

---

