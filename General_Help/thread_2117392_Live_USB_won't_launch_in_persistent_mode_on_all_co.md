---
title: "Live USB won't launch in persistent mode on all computers"
date: 2013-02-18
forum: General Help
---

### Post by nk565 on 2013-02-18
I'm very new to Ubuntu (second day using it) so I may not know all the terms of what I'm trying to say.

I set up Ubuntu on a 32GB USB drive with a 25GB partition to save all my data on. This works fine on the computer that I set this up on (runs windows 7), and opens up to

[IMG]http://i.imgur.com/rp5sXQk.jpg[/IMG]

and it saves all my data between sessions, etc.

Then I tried plugging it into my other computer (running windows 8 UEFI). After configuring the BIOS to have USB priority, it boots to

[IMG]http://i.stack.imgur.com/55q9B.jpg[/IMG]

It doesn't give me an option to boot in persistent mode. It does start up if i select trial mode, but none of my data or partitions show up. I tried running boot repair, but it didn't seem to do anything.  I also tried this on another Windows 7 PC (can't confirm right now, but I'm pretty sure it also used UEFI) and had the same issue.

Why do they boot to different screens, and how can I get my Windows 8 computera to boot in persistent mode?

---

### Post by nk565 on 2013-02-18
I Just confirmed that the other Windows 7 PC also uses UEFI.

Edit: I just tried it on a vista machine that uses BIOS, it didn't help. But something else I noticed was that it does save data between session on other machines, but its not the same data that I had on the first machine. If I start live mode on any of the other three machines, it has one set of data.  If I start it on the original machine, it has a different set of data. I have no idea where its storing the data for these other computers.

---

### Post by nk565 on 2013-02-18
Looking around some more, my newest guess at the problem is that the casper-rw partition isn't working on any computer other than the original.

---

### Post by searchfgold6789 on 2013-02-18
Did you create a separate partition yourself, or let the USB Disk Creator do its work? If you did the former, I would redo the USB disk and let the USB Creator do it automatically.

See more on UEFI booting here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
It seems that, for the most part, it recommends turning UEFI/QuickBoot/FastBoot/SRT/Smart Response Technology OFF in your BIOS.

---

### Post by nk565 on 2013-02-18
> Did you create a separate partition yourself, or let the USB Disk  Creator do its work? If you did the former, I would redo the USB disk  and let the USB Creator do it automatically.

The Disk creator made the partition, and I expanded it.

> See more on UEFI booting here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
It seems that, for the most part, it recommends turning UEFI/QuickBoot/FastBoot/SRT/Smart Response Technology OFF in your BIOS.

It wouldn't boot at all at first.  Then i turned off safeboot and it worked. But booting isn't the problem, it just doesn't seem to be booting to the right partition (I have no idea where its writing all the data).

---

### Post by nk565 on 2013-02-18
Here is a picture of my boot settings

[IMG]http://i.imgur.com/9nJ2Tud.jpg[/IMG]

Also, because the UEFI page mentions it, my computer boots to this screen

[IMG]http://pix.toile-libre.org/upload/original/1347445119.png[/IMG]

But all the computers do because the disk is 32 bit.

---

### Post by C.S.Cameron on 2013-02-18
> **nk565 said:**
> I'm very new to Ubuntu (second day using it) so I may not know all the terms of what I'm trying to say.

I set up Ubuntu on a 32GB USB drive with a 25GB partition to save all my data on. This works fine on the computer that I set this up on (runs windows 7), and opens up to

[IMG]http://i.imgur.com/rp5sXQk.jpg[/IMG]

and it saves all my data between sessions, etc.

Then I tried plugging it into my other computer (running windows 8 UEFI). After configuring the BIOS to have USB priority, it boots to

[IMG]http://i.stack.imgur.com/55q9B.jpg[/IMG]

It doesn't give me an option to boot in persistent mode. It does start up if i select trial mode, but none of my data or partitions show up. I tried running boot repair, but it didn't seem to do anything.  I also tried this on another Windows 7 PC (can't confirm right now, but I'm pretty sure it also used UEFI) and had the same issue.

Why do they boot to different screens, and how can I get my Windows 8 computera to boot in persistent mode?


Try pressing any key when starting the boot and the first screen should appear, thus giving the option for persistence.

---

### Post by nk565 on 2013-02-18
> Try pressing any key when starting the boot and the first screen should appear, thus giving the option for persistence.


Actually I figured that out, it didn't help.

---

### Post by C.S.Cameron on 2013-02-18
Does one of the computers have a casper-rw partition on it?

A persistent thumb drive will use that rather than the casper-rw partition on the thumb drive.

Does the thumb drive have both casper-rw file and partition?

I'm wondering how there could be two sources of saved data and settings.

---

### Post by nk565 on 2013-02-18
> Does one of the computers have a casper-rw partition on it?


If any of them did, it would have to be the original computer because its the one thats different, but I know the original is using the USB's casper-rw partition because I see everything saving there.

> Does the thumb drive have both casper-rw file and partition?


I think so, [IMG]http://i.imgur.com/adnBw5P.png[/IMG]

I just don't know how it would save to the other partition (which was created when the live USB was), from what I understand nothing but the casper-rw partition should save anything.

---

### Post by C.S.Cameron on 2013-02-18
If there is a casper-rw file on the root of the thumb drive, does isolating or deleting it do anything to help boot the casper-rw partition?

---

### Post by nk565 on 2013-02-19
> If there is a casper-rw file on the root of the thumb drive, does isolating or deleting it do anything to help boot the casper-rw partition?

I'll check if there is tomorrow. How do I isolate it?

Just a quick thought before I head off to bed.  Maybe the reason none of it is showing up is because it isn't giving me the option to log into the account I created. Tomorrow I'll try making account on one of the other computers, rebooting it, and seeing if my original account shows up at the log in screen. I'll post an update tomorrow after I try it. I'm doubtful this will work though.

---

### Post by C.S.Cameron on 2013-02-19
> **nk565 said:**
> ...How do I isolate it?...


Move the casper-rw file to a different folder or rename it.

---

### Post by nk565 on 2013-02-19
Well, I started trying the new account thing, and I think it was working, but I didn't get to finish my PC shut down the wrong way and now the USB will only start in live mode, so I'm just going to start over. I wanted to start over anyways because I didn't want the partition to be as big as it was anyways.

---

### Post by oldfred on 2013-02-19
Most Windows 7 systems are BIOS installed even if UEFI/BIOS. And then your install to the flash drive will be a BIOS boot.

But all Windows 8 are UEFI with gpt partitioning and secure boot. Only the 64 bit version of Ubuntu works with secure boot.

With a 32GB flash I might consider a full install, but if one system is BIOS and the other UEFI you may have issues. 
You may be able to install with grub-pc for BIOS boot and grub-efi for UEFI boot as Ubuntu is the same either way. But you have to use gpt partitioning on your flash drive. I know gpt works on flash drive as I have that on a couple of flash drives, but am only booting with BIOS. With BIOS gpt also needs a tiny bios_grub partition.

---

### Post by nk565 on 2013-02-19
> But all Windows 8 are UEFI with gpt partitioning and secure boot. Only the 64 bit version of Ubuntu works with secure boot.


Problem is, not all the computers I'm planning to use this USB on support 64 bit operating systems.

Anyways, I'm still making the new USB and i'll see if everything works fine now.

---

### Post by aspireone722 on 2013-02-19
have you tried Unetbootin?

---

### Post by C.S.Cameron on 2013-02-19
For what it is worth, the following is how I make a Persistent flash drive:

Boot Live CD or Live USB.
Plug in flash drive.
Start Gparted.

Create 2 GB FAT32 partition, (on the left side of the bar). (size is optional, extra space can be used for file storage and transfer to Windows machines).

Create a 4 GB ext2 partition to the right of this, labeled it "casper-rw". (ext3 and ext4 also work).

Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition).

Close gparted.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, Go to the root folder of your Live USB
    Enter the syslinux directory, (or for UNetbootin the root directory).
    Make the syslinux.cfg file writeable
    Replace the contents of the file syslinux.cfg with:

```
    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

Shutdown, remove CD, reboot.


First time booting go to users and groups and create an account with yourself up as an Administrator, with password if desired.

Note:
The above code will bypass the Try/Install and Language screens.

---

### Post by nk565 on 2013-02-19
> For what it is worth, the following is how I make a Persistent flash drive:

The program I used for the Live USB created the persistent partition for me, I just expanded it later.


I have *literally* no Idea what the hell is going on, but I just recreated my  live USB, booted it, **and it booted to the login screen with my account there.** I did a double take here. So I log in, and my desktop is just the way I left it before formating the USB.  I'm just sitting there with a blank expression trying to figure out how the hell this could possible happen if I just wiped and remade the live USB. I look through the files, and it looks like the steam game I downloaded is gone, but steam itself is still there. I figure this means, and I have no idea how this could happen, but the place where it was storing most of my data was my computers primary HDD (obviously the game I got downloaded to the USB). I look at my HDD in Gparted, and look at what I found.

[IMG]http://i.imgur.com/BdaM9Y0.png?1[/IMG]

I'm at a loss for how that partition was created. The USB casper-rw partition was created automatically by the program, I don't know how to make one manually (now I do thanks to [[COLOR=#000000]C.S.Cameron[/COLOR]]("http://ubuntuforums.org/member.php?u=317145")), and I didn't even know it was possible to have the casper-rw partition on another drive.



So I guess I have my original problem mostly figured out now.  Ignoring all the questions I have on how the hell that partition got there, is it safe to delete that partition from my HDD? Its not going to affect my other data, right? And deleting it should force my computer to resort to using the correct casper-rw partition, correct?

---

### Post by nk565 on 2013-02-19
Right after I posted I realized what happened.  The program never created the casper-rw partition on the USB, it did it on my hard drive both times. Looking at my flash drive, this is what it looked like before I followed that tutorial to extend the partition

[IMG]http://i.imgur.com/2zb4yg4.png[/IMG]


There is only one partition. I realize now that I created the casper-rw partition after the live USB stick was created, without knowing what i was doing. All in all, it seems like it was the programs fault for creating the casper-rw partition on the wrong drive.

But my question from the last post i made still stands, can I delete the casper-rw partition from my HDD, and will that make the casper-rw partition on my USB work?

---

### Post by C.S.Cameron on 2013-02-19
> **nk565 said:**
> 
But my question from the last post i made still stands, can I delete the casper-rw partition from my HDD, and will that make the casper-rw partition on my USB work?

I have had problems with using stuff from PendriveLinux.com myself.
So have many others.

You should have no problem removing casper-rw partition from the HDD. Use Gparted.

You should be able to simply shrink, (to the left), the FAT32 partition on the flash drive and create a new ext2 partition labeled casper-rw.

Probably better to start over following my advice above.

---

### Post by nk565 on 2013-02-19
> Use Gparted

I'm falling in love with this program, its an amazing partition manager.

> You should be able to simply shrink, (to the left), the FAT32 partition on the flash drive and create a new ext2 partition labeled casper-rw.

Yep, already done.

> Probably better to start over following my advice above.


I'm going to test it out after I delete that partition from my HDD, I'll probably mark this thread as solved if it works.

---

### Post by nk565 on 2013-02-19
Alright, it finally worked. For anyone looking this up in the future

The Problem: The live USB program created the casper-rw partition on the HDD instead of the flash drive. And apparently Ubuntu likes using that casper-rw partition better than the flash drive one if both exist.

The solution: Create the casper-rw partition manually on the flash drive, and delete the one stored on the HDD.

---

