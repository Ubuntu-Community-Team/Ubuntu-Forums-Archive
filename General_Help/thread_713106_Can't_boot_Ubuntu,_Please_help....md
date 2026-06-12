---
title: "Can't boot Ubuntu, Please help..."
date: 2008-03-02
forum: General Help
---

### Post by Prizo on 2008-03-02
Well, hello there. I really need help with booting Ubuntu, Seems like no matter what I try I always get lockup.
I recorded half of what it said while in lockup:

[<c011e4b6>]native_apic_write_atomic+0x6/0x10
[<c011563d>] send_IPI_mask_bitmask+0x4d/0xc0
BUG: Unable to handle Kernel paging request at virtual adress 086f46
Printing EIP: 
c0105822
*PDE= 00000000
Recusive die () failure, output suppressed
Kernel panic - Not syncing: fatal exception in interrupt
BUG: Unable to handle Kernel paging request at virtual adress ffffd310
Printing EIP:
c011e4bb
*PDE= 00004067
*PTE= 367de021
Oops: 0003 [#53]
SMP
Modules linked in: intel_agp ITCO_vendor_support soundcore agpgart snd_page_alloc shpchp pci_hotplug evdev battery squashfs loop uniohfs hls_cp437 isofs sg sr_mod cdrom sd_mod usbnid hid ata_piix e100 mii ata_generic uhci_hcc libata scsi_mod enci_nod usbcore thermal processor fan fuse appadmod
commoncap
cpu: 0
EIP: 0060: [<c011e4b6>] Not tainted VLI
Eflags: 00010006 (2.6.22-14-generic #1)
EIP is at native_apic_write_atomic+0x6/0x10


I hope there's a way to fix it some how.

Thanks for any help.

---

### Post by sancho panza on 2008-03-02
I may not be able to help, someone else might be able to able to help better if you are a little more descriptive. When exactly does this come up? When you are trying to start the liveCD? What happens before you actually get to this point? etc.

Cheers!

---

### Post by Prizo on 2008-03-02
Yes, It happens when loading from LiveCD.
I noticed that the problem comes while loading Hardware drivers.

---

### Post by sancho panza on 2008-03-02
Ok, that could be useful...I'm sorry I forgot to mention that you need to put up your hardware configuration. List anything you know...Processor specs, cache, ram, graphics card, sound card, wireless, hard drive, etc.

Hope someone can help you then...Cheers

---

### Post by Prizo on 2008-03-02
Argh okay, my spec:

CPU: Intel Core 2 Duo E6300, 1866 MHz (7 x 267)
Mobo: Intel Broadwater i946GZ
Video card: NVIDIA GeForce 8800 GTX  (768 MB)
Audio card(onboard): SigmaTel STAC9227 @ Intel 82801GB ICH7 - High Definition Audio Controller [A-1]
HDD: WDC WD1600JS-00SGB0  (149 GB, IDE)
DVD: (LG) HL-DT-ST DVDRAM GSA-4163B  (DVD+R9:4x, DVD+RW:16x/8x, DVD-RW:16x/6x, DVD-RAM:5x, DVD-ROM:16x, CD:40x/24x/40x DVD+RW/DVD-RW/DVD-RAM)
Network(onboard): Intel(R) PRO/100 VE Network Connection(not wireless)
RAM: 2x Kingston (1 GB DDR2-667 DDR2 SDRAM)
L2 Cache:	2 MB  (On-Die, ASC, Full-Speed)
L1 Code Cache:	32 KB per core

I hope it helps :(

Anyways, thanks for trying helping me.

---

### Post by Prizo on 2008-03-02
'bump'

---

### Post by sancho panza on 2008-03-02
Sorry nobody dropped by. I've often heard ppl talking that some graphics cards have issues with ubuntu. So try digging around on these forums and internet for your card's compatibility with ubuntu.
Also, as a last shot, try moving this post to the [installation/upgrades section]("http://ubuntuforums.org/forumdisplay.php?f=140").

Dont give up...Cheers!

---

### Post by Prizo on 2008-03-03
Thanks for advice. I'll try to move this thread to installation/upgrades section:)
Another thing, I dont think its a Video card problem because when I had 7900gt I could boot and Install Ubnutu fine, a few weeks later something went wrong
and my problem started...

---

### Post by NightwishFan on 2008-03-03
Although I doubt this will help, have you tried booting in safe graphics mode?

Also if all else fails use the alternate install cd.

---

### Post by zxscooby on 2008-03-03
you might have to add the noapic boot flag 

check this post
[http://ubuntuforums.org/showthread.php?t=614326&highlight=f730us+noapic](http://ubuntuforums.org/showthread.php?t=614326&highlight=f730us+noapic)

---

### Post by xen-uno on 2008-03-03
Do you get as far as the X then a message about running in low resolution mode? I did and neither Configure or Continue would get me further after it would kick back out to the command line ... it would just hang. The Alt cd and Supergrub got me all the way ... and other than breaking Pidgin tonight it has run great.

If the above works, you'll probably need to take a look at [**this**](http://www.robdian.co.uk/content/view/56/27/) to get the latest NVidia drivers installed (NVIDIA-Linux-x86_64-169.12-pkg2.run). There's a couple other thing you need to do before that ... see if you can get alt installed 1st.

---

### Post by Prizo on 2008-03-03
Ok, I tried to to add noapic boot flag in both normal and safe graphics modes, without quite splash flag and it seems like its only booting in a half, I mean I saw busybox loading up and I can use built in commands.
With quite splash it just locksup with "Fixing recursive fault but reboot is needed!" oh and another thing, with noapic and without quite splash flags I noticed a strange message about cache "[sda] write cache: enabled, read cache: enabled, doesnt support DPO or FUA"

---

### Post by Prizo on 2008-03-03
'bump'
Ow come on people :< 
There must be a way to fix this problem.:(

---

### Post by sancho panza on 2008-03-04
Move the thread to installation section and try ur luck there.

---

