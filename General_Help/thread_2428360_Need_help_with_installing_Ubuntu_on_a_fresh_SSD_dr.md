---
title: "Need help with installing Ubuntu on a fresh SSD drive."
date: 2019-10-03
forum: General Help
---

### Post by tpakulski on 2019-10-03
Hi,

I've pretty much screwed myself and I will try to explain why.

I have 3 different drives on my computer (2 internal and 1 external drive).

Once I had Windows, I've made a move to install Ubuntu on my external drive, then decided to remove Windows completely but also I knew that I will buy and use SSD drive in the future.

So I have purchased a new SSD drive but the problem is, I have tried and failed at everything that I could possibly do to make a bootable ISO for my new SSD.

That includes Windows virtual machine, trying with Rufus via WINE, Unetbootin and a DVD... that can't be rewrited once more.

As for DVD, I was following steps from the official Ubuntu site guide, tried to burn an ISO but after it has finished it could not be booted nor opened, instead it prompts an error "Unable to access "DISK NAME" Error mounting /dev/sr0 at /media/MYNAME/ubuntu 18.04.3 LTS amd64: wrong fs type, bad option, bad superlock on /dev/sr0, missing codepage or helper program"

I suck at terminal thing, don't want to remove my whole computer within a second.

Is there anything that I can actually do right now or am I stuck forever with my sluggish external drive?

Thanks

---

### Post by GhX6GZMB on 2019-10-03
You need to boot a live image from DVD. The DVD drive needs to be the first in the boot sequence in the BIOS/EFI.
The installer will then format your SSD.

---

### Post by sdsurfer on 2019-10-04
^^ Agreed, check your BIOS first. Then once you install successfully, go back in again and put your new OS first.

Way back when I knew very little about Ubuntu/Linux (not that I know a whole lot more now,) what I did was unplug all my other drives and plugged in **only** my new SSD. I ran the install on the new SSD, then shut down, re-plugged in the drives, and configured GRUB. Doesn't sound like you are dual booting but if you are, there are lots of articles out there on how to configure GRUB.

---

