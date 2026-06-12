---
title: "Struggling to load Ubuntu Kernel from Grub Menu"
date: 2022-03-28
forum: General Help
---

### Post by nerdwardnguyen on 2022-03-28
I have a dual-boot of windows and ubuntu on a desktop computer. A few days ago on boot I was brought to the GRUB menu as opposed to the UEFI menu. Tried to follow guides like this one: [https://www.unix-ninja.com/p/Manually_booting_the_Linux_kernel_from_GRUB](https://www.unix-ninja.com/p/Manually_booting_the_Linux_kernel_from_GRUB) to load the kernel from GRUB and boot but was unable to find the kernel. All of my partitions were either unidentified or Windows partitions. Booted from a usb and tried to use Ubuntu's Boot Repair tool, but there were no recommended fixes, but it did generate a pastebin:

[https://paste.ubuntu.com/p/5twKHq4kQg/](https://paste.ubuntu.com/p/5twKHq4kQg/)

Looking for help to boot my linux OS again preferrably without having to reinstall.

---

### Post by tea for one on 2022-03-29
[COLOR="#0000FF"]Line 77[/COLOR] - 1 OS detected
[COLOR="#0000FF"]Line 79[/COLOR] - OS#1:   Windows 8 or 10 on nvme0n1p4

[COLOR="#0000FF"]Lines 179 -190[/COLOR] - There is no sign of any Linux partitions.

Regrettably, it appears that your Ubuntu OS is not installed on your PC.
Where was it installed previously - Samsung nvme or Sandisk sda?

Do you have personal data backups?

---

### Post by Impavidus on 2022-03-29
What's your system supposed to look like? I can see two hard drives, one of 256GB and one of 1TB (plus the live disk you used for boot repair). The grub bootloader is in the EFI partition of the 256GB drive, along with the Windows bootloader. Both drives are fully allocated with Windows partitions, with no large unallocated blocks where Linux partitions might have been. So unless you have a third hard drive where Ubuntu was installed (and that is for whatever reason currently invisible), it appears your Ubuntu system was overwritten and has disappeared without a trace (except that bootloader).

Grub looks for the root partition on hd1,gpt4, but I can't say for sure whether that could be your sda or not.

So, is there supposed to be a third hard drive? Can you see that third hard drive in UEFI? Or has Windows been so "kind" to "optimise hard drive space" by deleting whatever it doesn't know and expanding Windows partitions?

---

### Post by DuckHook on 2022-03-29
It looks like you may have to reinstall.

As a side note to both tea for one's and Impavidus's observations, experiences such as yours is the reason that I will only run Windows inside a VM. I've found Windows to be a greedy little piglet that refuses to play nice with others. By confining it to a VM, I forestall any of its "clobber everything else" tricks.

---

### Post by ajgreeny on 2022-03-29
Have you had a large recent update of Windows as I believe that can make Linux partitions hidden to the system.

As I understand things, it does not actually overwrite data on the partitions but rewrites the partition table or something similar and clever use of Testdisk or other software can restore everything back for you.

However, I do not use Windows at all any more so may have things completely wrong about this partition problem so wait for other more knowledgable answers before jumping just in case you make matters worse.

---

### Post by nerdwardnguyen on 2022-03-29
Thanks everyone! The Linux partition was the entirety of the 1TB HD that you see there, it looks like windows has cannibalized that HD for itself so I'll have to reinstall T.T the annoying bit is that my wifi drivers don't work on install and the process to fix it took me an hour the first time and I didn't want to do that again.

---

### Post by tea for one on 2022-03-29
> **nerdwardnguyen said:**
> The Linux partition was the entirety of the 1TB HD that you see there, it looks like windows has cannibalized that HD for itself
Can you describe how that happened because it is somewhat unusual?
> **nerdwardnguyen said:**
> the annoying bit is that my wifi drivers don't work on install and the process to fix it took me an hour the first time and I didn't want to do that again.
As you have a Desktop PC, why not just use wired ethernet?

Assuming your Windows OS is working OK on your nvme drive, I suggest:-

Remove, isolate, de-activate your Windows drive.
Install Ubuntu on your Sandisk SSD in UEFI mode with GPT.
Allow the installer to create an ESP on the Sandisk SSD.
Boot either OS via UEFI boot menu.

In effect, keep each OS separate and avoid boot problems in the future.
Of course, you can set up a shared ntfs partition if required.

---

### Post by nerdwardnguyen on 2022-03-29
> Can you describe how that happened because it is somewhat unusual?
This computer started with a 250 GB SSD Hard drive for Windows. I wanted to add a new SSD to expand my memory capacity and while I was at it I decided to dual boot Linux as well. Actually on further recollection, it may not have been the whole hard drive, I may have split it 50/50.

> As you have a Desktop PC, why not just use wired ethernet?
I live in an apartment and getting ethernet to my PC is very inconvenient.

---

### Post by DuckHook on 2022-03-29
Is it absolutely essential that you dual boot? What about my earlier suggestion: running Windows as a VM within a Linux host? Or the reverse: running Linux within a VM using Windows as host? Both ways will avoid future problems of this sort.

---

### Post by nerdwardnguyen on 2022-03-29
No it is not essential that I dualboot, I'm just used to doing that. I've tried using VMs in the past and there's always some input lag that I found annoying when I code. I'll give a Linux VM a shot. I mostly use linux for coding side projects.

---

