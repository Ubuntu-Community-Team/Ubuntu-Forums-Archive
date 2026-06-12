---
title: "How to have GRUB on two hard drives and fix giant GRUB partition?"
date: 2020-09-27
forum: General Help
---

### Post by SpectrumDT on 2020-09-27
I have two hard drives - let's call them sda and sdb. sda used to be my main one; it has GRUB and Linux (Kubuntu 20.04) on it. 

I had one problem with it: When I installed, I accidentally gave GRUB a humongous partition of 200 GB. I'm pretty sure this is orders of magnitude more than what GRUB needs, but I am unsure how to fix it. GParted does not want to shrink the partition. 

I figured: *"Let's also install GRUB on sdb. That way, if I have two working GRUBs and I accidentally mess up one of them, I can still boot."*

I installed GRUB on sdb using:

```
$ sudo grub-install /dev/sdb
```

Now I can boot from sdb. But I can no longer boot from sda! My old GRUB is broken and now says this when I try to boot from it: 

```
Loading Operating System ...
    error: symbol `grub_calloc' not found
    Entering rescue mode...
    grub rescue>
```

This suggests that GRUB is way more brittle than I thought. I did not consciously change anything on sda, but somehow my GRUB there broke. :( Maybe the **grub-install** command I used above didn't do what I thought it did...

Can anyone please advise me? How can I have a GRUB installation on each hard drive that both let me boot my Linux, and without letting GRUB hog more space than it needs?

In case it matters: I believe my firmware uses BIOS rather than EFI. My motherboard is from 2010 or 2011, I think.

([Crossposted from Superuser. See the other post for some pictures...](https://superuser.com/questions/1588932/how-to-have-grub-on-two-hard-drives-and-fix-giant-grub-partition))

---

### Post by oldfred on 2020-09-27
Are both drives gpt partitioned?
For BIOS boot from gpt, you need a 1 or 2MB (not GB) unformatted partition with the bios_grub flag.
That is because gpt does not have space after protective MBR, like MBR partitioning. And for BIOS boot grub needs some place for core.img. Normally in sectors just after MBR with BIOS/MBR configuration.

You should be able to boot from either drive, but updates may then only apply to one drive or the other. And eventually may get out of sync as one is more updated than other.

# With BIOS (only) grub stores and saves the install drive
#To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short 

For full details on boot configuration:
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

