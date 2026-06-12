---
title: "Questions about cloning"
date: 2021-09-10
forum: General Help
---

### Post by pslacker on 2021-09-10
Sorry to be a newbie with a long first post, but I'm trying to describe my situation as clearly as I can. Essentially I want to know about cloning, and later restoring, my original Windows setup — except that the cloned drive is larger than the original. 

Background:

After trying out various Ubuntu Live CD's on an old Windows laptop, I want to convert it to Xubuntu. My original plan was to set it up for dual boot, but I've run into enough problems that I think I'll have to make it Linux-only.

[The laptop drive already contains 3 partitions, and the instructions I was trying to follow called for the creation of two additional ones, which apparently is one more than the drive will allow — something to do with it using MBR instead of UEFI, and I don't feel confident in my ability to change that.] 

So dual boot seems like a no-go. 


Actually, I don't really mind because I think I'll do just fine with Linux-only, but I'd like to keep the option available if at all possible; after all, I might screw things up and leave my machine unbootable ... so I definitely want some kind of fallback plan. 

So I thought, why not simply clone the laptop HDD to an external one, and then if my experiment fails I can clone it back and carry on like nothing ever happened?

The laptop's drive is 500 Gb, but the backup drive I just purchased is 2 Tb (btw I also have an older 1 Tb drive I could format and use if necessary). I don't know how the size difference would affect cloning — do I need to leave the rest of the space on the 2 Tb drive unformatted? Or just empty? — or restoring, for that matter.  And does Clonezilla truly clone everything, including the MBR? Should I use something else instead? And are there any issues with launching Clonezilla from the live-CD environment and cloning from /dev/sda to a USB-attached drive? 

I've tried googling as much as I can, but all the instructions I find deal with how to rescue a failing drive (thus there's no need to restore from a larger drive to a smaller one) — whereas I basically want to make a backup so I can experiment with the original drive, then restore later if I need to.

Thanks in advance for any answers or advice, and certainly for your patience!

---

### Post by tea for one on 2021-09-11
Can you remove the Windows drive from the laptop and insert another drive?
This will keep your Windows OS intact and allow complete freedom to experiment.
No need to worry about cloning :)

Before doing anything at all make sure that you have backed up your personal data.

---

### Post by yancek on 2021-09-11
> The laptop drive already contains 3 partitions, and the instructions I  was trying to follow called for the creation of two additional ones,  which apparently is one more than the drive will allow — something to do  with it using MBR instead of UEFI, and I don't feel confident in my  ability to change that.] 
 

On an MBR drive, you can have only 4 primary partitions.  Create an Extended partition using the 4th primary and create 2 Logical partitions within the Extended partition.

---

### Post by sudodus on 2021-09-11
I agree with both previous replies.

I want to add something about Clonezilla. It can clone, but also create an image. This 'Clonezilla image' is a directory with a number of files. The big files are compressed. Clonezilla is also smart enough to only copy used blocks from the file systems that it understands (for example FAT32, NTFS of Windows and ext4 of Ubuntu). This means that the image will be much smaller than the drive, that was cloned. But when you intend to restore from the image to another drive, that other drive must not be smaller than the original drive.

---

### Post by pslacker on 2021-09-11
@yancek: Thanks for the clarification and suggestion. At this point in my journey I think it's safer for me (or at least more comfortable) to keep the number of things I've never done before to a minimum, though I may reconsider once I have a little more experience. 

@tea for one: I think you have pointed me to something I'd overlooked. In fact, the laptop already has two identical 500 Gb hard drives — the first (sda) partitioned as C: and D:, the second (sdb) partitioned as E: and F: (I guess I was on a bit of a partition kick 10 years ago!).

So maybe I'll just backup sdb's contents onto my new 2 Tb drive, and then do one of the following:

A) swap the positions of the two 500 Gb drives, putting sdb into sda's slot and vice versa, then install Xubuntu onto the 'new' sda;
OR
B) same as above, except don't put the original sda into sda's slot — just leave it in a drawer for safe keeping, meaning the 'new' laptop would only have a single 500 Gb drive. 

On the one hand it would be more convenient to simply swap the two drives, giving me easy access to anything from the original C: and D: in the future; on the other hand, I can live with just 500 Gb total storage on this laptop and maybe it's unwise to do anything with my 'failsafe' drive (the one I can use to restore Windows) other than store it safely. 

Any additional thoughts? (Thanks again.)

---

### Post by sudodus on 2021-09-11
1. Computers can be different, but I think most computers can boot from the second drive, where it is sitting already. No need to swap the position. But I am sure there are exceptions, where you would need to swap them. Often the drive, that is first to be recognized will have priority (to be booted from),

2. It would be wise to unplug or disconnect the Windows drive during the installation of Xubuntu. That way you will eliminate the risk of overwriting it.

3. After the installation you can plug the Windows drive back in, and when you know how to boot into Xubuntu, you can run the command in Xubuntu

```

sudo update-grub

```

and there will be an option in your grub boot menu for Windows too (the next time you boot).

---

### Post by tea for one on 2021-09-11
Two drives offer you great flexibility.

[COLOR="#0000FF"]sudodus[/COLOR] has smacked the nail firmly on its head.
Specifically point no.2  - eliminate the chance of human error by disconnecting your Windows drive.

Are you aware that Xubuntu will be able to read/write to Windows file systems but Windows cannot read/write to Linux file systems?

---

### Post by pslacker on 2021-09-11
@sudodus:

Let's see if I follow you.

1) Copy sdb's contents (my current E: and F: ) to external backup.
2) Remove sda (the Windows drive) from laptop; leave sdb where it is (in the 2nd bay).
3) Boot to live CD, and tell Xubuntu to install itself onto sdb (which maybe will appear now as sda, since there's only one drive?).
4) Remove CD and reboot directly to the newly formatted Xubuntu installation; verify that it runs as expected.
5) Power off, reconnect the original Windows drive in the first bay, and...

Here's where I'm confused:  the next time I power up, is there a chance for some kind of conflict between the two drives' MBR's? i.e. the Xubuntu drive and the Windows drive both shouting "pick me"?

And even if Xubuntu wins that fight, could anything be compromised in the Windows drive (or its MBR) that would cause problems if I ever needed to unplug the Xubuntu drive and just boot directly back into Windows? Especially if Xubuntu has write access — could I inadvertently corrupt things? (Of course it would probably be a good idea to change permissions on the C: partition to prevent this, but I still want to know what potential exists for me to screw something up.) 

Again, thanks for your patience. I'm sure I'm asking many things that a little more experience would make obvious.

---

### Post by sudodus on 2021-09-11
Are you booting in UEFI mode or BIOS mode (alias CSM alias legacy mode)? Check with

```

test -d /sys/firmware/efi && echo efi || echo bios

```

In BIOS mode there is no risk. In UEFI mode, there is a risk that Windows will damage the boot system for Xubuntu, particularly when Windows is doing major updates. But it is possible to restore the boot system of Xubuntu when booted from a USB drive.

---

### Post by pslacker on 2021-09-11
I'm not in a position to check at the moment, but I'm 99% sure it's BIOS (I had a problem getting it to boot from USB a few years ago, and it seemed at the time this was a limitation of BIOS if I recall.)

However, the more I think about it, I might just err on the side of simplicity and make it a one-drive laptop — hiding the Windows drive in a drawer and completely avoiding any complications.

If I do that, would I be correct in assuming that whichever operating system gets loaded will simply be decided by whichever drive is occupying bay #1? (The other bay would stay empty.) 

i.e. today I want to run Windows, so I'll insert the Windows drive; tomorrow I'll swap it for the Xubuntu drive and run Linux instead.  Since each drive would contain its own MBR — the Linux one saying this is a Linux-only computer and the Windows one saying this is a Windows-only computer — there'd be no conflicts with only one drive ever installed at a time. Is it as simple as that? 

(Of course if I wanted to have access to the same files from both environments, I'd have to store them on an external USB drive, but I don't expect much need for that.) 

Is this making sense, even if it seems unnecessarily limiting?

---

### Post by sudodus on 2021-09-11
That is how it works. But if one drive is made for UEFI mode and the other one for BIOS mode, you must also switch boot mode in the UEFI/BIOS system. Many computers (but not all) can be set to select automatically whatever boot mode is available (the bootloading structure found in the drive(s) connected).

I think you can go for a Xubuntu-only system. If you change your mind, it is easy to insert the Windows drive too (and test which is the best way to arrange the drives, if/when necessary).

In principle, Linux does not care much about the drives except for booting, after that it cares about the partitions and the file systems in those partitions. The partitions can be anywhere, in one single drive, in two or more drives, even in an external drive, for example a USB drive. If configured for it, an installed Xubuntu system is even portable between computers (use the internal Linux drivers, avoid proprietary drivers for graphics and wifi).

---

### Post by C.S.Cameron on 2021-09-13
Why not install Ubuntu to an external SSD. That will be fast enough and should not mess up your Windows drive.
It will work on both BIOS and UEFI computers.
You can take it with you when you travel for use on other computers if you wish.
You can test the method with a 8GB or larger flash drive and a persistent install of Ubuntu using **mkusb**.

---

