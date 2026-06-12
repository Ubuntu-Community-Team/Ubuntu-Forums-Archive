---
title: "installed ubuntu with no GRUB"
date: 2007-04-10
forum: General Help
---

### Post by leveliv on 2007-04-10
I installed Ubuntu through VMware (that was the only way I could get it work) and I installed it to the Harddrive partition I wanted to perfectly fine then it asked where I wanted to install GRUB it said hd0 so I said yeah whatever...so now I restart the VMware machine...and close it...restart my XP machine hoping to be able to just select the disk and boot from it...but I did and nothing happens...it's liek there is no boot loader at all. I can see the Partition in XP using ExplorerFS ...I have a USB pen drive..can I install GRUB on there and boot from that? or can I just make it so I have grub on that HDD that I have Linux installed on already?

---

### Post by spankymasterc on 2007-04-10
u cant do that ..... so u installed ubuntu using vmware and u are expenting it to show a bootloader in the startup? doesnt work that way..... u cant do that unless u natively install the os.... im not sure if theres a workaround that but i dont know maybe u can turn your virtual harddrive into a physical drive? maybe i understood you wrong but thats what i got from reading your post :::Cheers::: correct me if im wrong....

---

### Post by heimo on 2007-04-10
You installed it as a vmware client? Open your vmware software, see if you have the Ubuntu installation there? Start it. Does it boot? That's how virtualization should work. It provides "a computer inside computer". It'll be a bit slower than if run natively.

---

### Post by spankymasterc on 2007-04-10
No i think he was expecting it to show up like a actual drive..... i mean like he was installing ubuntu .....

Let me explain....

Vmware is software that creates a VIRTUAL machine inside your running OS in other words its just a VIRTUAL drive and not an actual drive ...... i dont understand why u wouldnt be a able to install ubuntu natively but if you ask we can help 

::::Cheers::::

---

### Post by heimo on 2007-04-10
> **spankymasterc said:**
> No i think he was expecting it to show up like a actual drive..... i mean like he was installing ubuntu .....

Yes. That's my understanding too. He did install Ubuntu, but as a virtual computer, which is now a bunch of files under XP. Boot manager was installed to virtual hard disk image. It's a wonderful way to evaluate Ubuntu, and perhaps in some cases to use too, but doesn't give all benefits of running native Ubuntu. Or rather, I'd say that you still rely on proprietary software to run your free operating system, which isn't quite optimal. :)

---

### Post by leveliv on 2007-04-10
I installed it using VMware...because the disc I was using didn't work too great so I used an ISO. I installed it to a physical disk...actually partition. I know it is there...I just can't boot into it.

---

