---
title: "Unable to ubuntu boot at all"
date: 2015-01-27
forum: General Help
---

### Post by alasdair3 on 2015-01-27
I have been running ubuntu server 14.04.1 from 1 16GB USB 3 quite happily for some time. The usb contains the default LVM install with home, root and swap volumes.

Today I had a problem where one of my services (subsonic) would not run properly and looking into this I noted that the root volume on my lvm was full. I used a ubuntu desktop live usb to resize the root volume. However, the system then failed to boot at all, asking me to insert boot media.

I could still boot from the live disk so I did that and ran boot-repair. I then got an error telling me that because GPT was detected I needed to create a bios boot partition. There was a 512mb fat32 partition with the flag boot created by default during the initial install. I deleted this and created a new ext4 partition of the same size with the grub_bios flag as instructed by boot-repair. However I still get the same error message upon trying to run it.

I'm pretty stuck now. I know the system can boot from usb because the live usb works fine but can't figure out how to repair / reinstall the boot loader for my main system.

I'd be very grateful for any advice on how I can fix this.

Many thanks in advance for your help.

---

