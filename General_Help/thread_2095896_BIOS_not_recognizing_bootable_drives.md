---
title: "BIOS not recognizing bootable drives"
date: 2012-12-18
forum: General Help
---

### Post by felinoel on 2012-12-18
[I]BIOS is American Megatrends
[/I]

So I've been trying to wipe my server with a different OS but tried several different USB bootloaders to get it to recognize it but figured since it was an underused OS that even the official one not working was to be expected.

So then I used an optical drive instead, but it still refused to recognize any bootable media in the drive. I figured though that this was because the optical drive has a vast history of not working with Ubuntu... but... that wouldn't stop it from working in BIOS, right?

In the BIOS screen it recognizes that the drives are there to be booted from, but when I set it to ONLY ever boot from that drive it doesn't start up at all and just requests a bootable object to boot from.

Help?

---

### Post by oldfred on 2012-12-18
How old is system. Those in the last 6 years should boot from a USB device. Before that many had USB ports but they were not bootable.

My 6 year old laptop boots from USB port, but if I happen to have another flash drive installed it does not work.
My 6 year old desktop works from flash drive, but not as a USB device. At first I tried every USB boot option and none worked. But then when choosing which hard drive to boot from the USB flash drive appeared.

Then is flash drive correctly configured as a bootable device. MBR must have boot loader.

---

### Post by felinoel on 2012-12-18
> **oldfred said:**
> How old is system. Those in the last 6 years should boot from a USB device. Before that many had USB ports but they were not bootable.

My 6 year old laptop boots from USB port, but if I happen to have another flash drive installed it does not work.
My 6 year old desktop works from flash drive, but not as a USB device. At first I tried every USB boot option and none worked. But then when choosing which hard drive to boot from the USB flash drive appeared.

Then is flash drive correctly configured as a bootable device. MBR must have boot loader.I just got it a month or twelve ago.

I used a USB booter to install Ubuntu on it originally, so I know it did work at one time.

I set the BIOS to only boot from either the jump drive or the optical drive, it did not boot.

---

### Post by oldfred on 2012-12-18
Did you try hard drives and then under hard drives choose flash drive?

Or maybe flash drive is not bootable anymore?

---

### Post by felinoel on 2012-12-18
> **oldfred said:**
> Did you try hard drives and then under hard drives choose flash drive?

Or maybe flash drive is not bootable anymore?Try hard drives..? You mean changing what it boots to? Yes I changed what it boots to, I set it to only jump drive or optical drive.

I tried a different jump drive, and even an optical drive.

---

### Post by oldfred on 2012-12-18
No. 

On my system one of the boot choices is which hard drive. My USB flash drive then only appears under that hard drive listing. And then only when the flash drive is bootable. I can choose in BIOS, but since I am only booting one time, I use my one time boot key (f12 for me), choose hard drive and then flash drive appears.

All the USB boot entries do not work on my system with a USB flash drive.

See attached.

---

### Post by felinoel on 2012-12-18
> **oldfred said:**
> No. 

On my system one of the boot choices is which hard drive. My USB flash drive then only appears under that hard drive listing. And then only when the flash drive is bootable. I can choose in BIOS, but since I am only booting one time, I use my one time boot key (f12 for me), choose hard drive and then flash drive appears.

All the USB boot entries do not work on my system with a USB flash drive.

See attached.
Mine doesn't seem to have that, mine automatically detects what is there and lets you choose from those detected.
It even says the specific brand name.

---

### Post by oldfred on 2012-12-18
Then I would think the flash drive is the issue.

Some have had flash drives work on one system and not on another. Sometimes it seems to be the flash drive and sometimes the installer used or just reinstalling or redownloading got a correct image.

---

### Post by felinoel on 2012-12-18
> **oldfred said:**
> Then I would think the flash drive is the issue.

Some have had flash drives work on one system and not on another. Sometimes it seems to be the flash drive and sometimes the installer used or just reinstalling or redownloading got a correct image.

Hmm, I tried eight different bootloaders, guess I will try a different jump drive then.

---

