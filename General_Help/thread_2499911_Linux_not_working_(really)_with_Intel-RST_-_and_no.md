---
title: "Linux not working (really?) with Intel-RST - and no end..."
date: 2024-08-15
forum: General Help
---

### Post by iyogi on 2024-08-15
Hello,

I hope this to be the correct place for the following theme.

As it is with Linux' inability to get on with that stupid INTEL RST-stuff for nearly ten years now, with seemingly nobody caring, I can no longer tinker about with Linux, as I have been doing for weeks now, instead of getting things done with my computer. Despite all liking for Linux with its underlying conception & endeavours - & after years of using it - seems I'm compelled to abandon it & go back to Windows slowly but surely. All the more woeful as there seem to be drivers in Linux capable to cope with Intel RST (see below). 

Studying hundreds of websites since, downloading & testing tens of Linux-distros (incl. Ubuntu, Debian, Endless-OS), each rumoured as the one being capable of handling Intel RST, yet ended up in no avail at all.

After acting the fool / putting on the barmy stick some days ago as my last try yet, buying an M.2 SATA III-SSD and installing it besides the M.2 NvME-drive already in place on my Clevo L140CU-machine (the latter just like that ever-increasing number of other machines only permitting Intel-RST as SATA-mode & forbidding AHCI, I still have one question left:

Is there anybody out there with a plausible explanation why on the one hand

- Linux completely refuses to get installed on machines with Intel-RST inevitably switched on

- while at the same time in Live-mode (unlike the NVMie-drive) being able to see and address the abovementioned SATA-drive without any difficulties - exactly as happens in Windows too?

Up to now, I wouldn't have expected stuff like that from Linux.

Cheers,

Yogi

---

### Post by TheFu on 2024-08-15
Why do you care about supporting EoL RST?  [https://www.intel.com/content/www/us/en/support/articles/000055419/technologies/intel-rapid-storage-technology-intel-rst.html](https://www.intel.com/content/www/us/en/support/articles/000055419/technologies/intel-rapid-storage-technology-intel-rst.html)  That would be a waste of time.  It is dead.
> Windows® 10 Enterprise Long-Term Servicing Channel (LTSC) users may face challenges since access to the Microsoft Store may be limited.  Windows 10® LTSC device functionality and features are not expected to change over time and end users are advised not to make updates directly.

So, it isn't just Linux.

Or did I read that wrong?

I have an 11th gen Dell Latitude laptop.  Came with RST enabled.  Before I even booted the pre-installed OS (not Linux), I changed the BIOS setting to AHCI (among a few other BIOS changes) and installed a 24.04 flavor of Linux.  It has been working fine.  Of course, I wiped that other OS completely.  BTW, this was all just a few days ago, so it is fresh in my memory.  I changed about 15-20 BIOS settings to ensure no issues with Linux.  I was also worried about the Iris Xe GPU, but that "just worked", which was nice and unexpected.  The only thing I haven't tested and don't plan to use is the fingerprint reader.  Everything else work without any special effort, post-install. That includes the blacklight on the keyboard and all the controls on the Fn keys.  It has a stock kernel, no OEM stuff.

That laptop is on Canonical's certified lists.  They tested it with 20.04 using an OEM kernel.  So, if your vendor has added the RST drivers to a custom kernel, it should work.  I know that OEMs tend to be slow with Linux support (it isn't the Linux kernel teams' responsibility to make drivers), it is the vendor.  So rather than complaining about Linux, **complain to the vendor.**  They did this.

If Linux doesn't meet your needs, don't use it.  It is your choice.

OTOH, there are a few options if you've like to use Linux.  
a) disable RST and enable AHCI in the BIOS
b) Run MS-Windows on the hardware and place the different Linux systems into virtual machines.
c) Run Linux on the hardware and place MS-Windows into a virtual machine

Of course, doing research to ensure your hardware is compatible with Linux **BEFORE making the purchase** is the best option. When vendors don't behave as we like, don't reward them with our money.  That's the ultimate lesson here.  Show love to vendors that are all-in on the OS we prefer.

Is Intel RST really that big of a deal to you?  To me, it was just something I knew to disable.  The NVMe SSD is still really fast, but I haven't run my own tests.  To me, even SATA SSDs are so fast as not to matter.

**Update: **Just to be clear, I didn't even try to use RST with my install.  Perhaps that was a mistake after reading oldfred's post below.  IDK.  I do know I didn't want to be forced to use an OEM kernel or deal with special drivers.  I used to run with JFS since I felt that ext2 wasn't a great file system. This was before ext3 was stable.  Anyway, JFS drivers weren't included which wasn't a big deal, until the computer refused to boot and using any standard Linux save-your-butt distro refused to see the JFS file systems.  I learned an important lesson that day.  When ext3 was stable, I switched over to it.  I know I wanted a journaled file system, which ext2 isn't.

---

### Post by oldfred on 2024-08-15
I have an 11th Gen Intel based Dell.
And while I have regularly posted the change to AHCI is required, I forgot with this system.
It installed Kubuntu with Secure Boot & Intel RAID on.

System only has NVMe, so added a VMD driver.
Did not even know what that was, but found this:
Linux* Kernel v4.14 contains latest upstreamed fixes for Intel® VMD

inxi shows this:
RAID:
  Hardware-1: Intel Volume Management Device NVMe RAID Controller driver: vmd

---

