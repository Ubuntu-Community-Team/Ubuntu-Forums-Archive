---
title: "USB keyboard not working in GRUB2"
date: 2016-06-05
forum: General Help
---

### Post by themainliner2 on 2016-06-05
When powering up my PC for the first time, or after shutting down and re-powering up, my** Logitech K360 USB Keyboard** works: I am able to enter the *BIOS* and use the* arrow keys* / *enter* in the *GRUB2* menu to select none default boot options.

When rebooting the keyboard does not working in GRUB2 and I am unable to select a distro (with the arrow or page up / down keys) or confirm and boot the default distro (enter) but have to wait for the timer to count down and the default distro to boot. I hate irritations that appear to start for no reason and prove difficult to correct. The keyboard was working correctly in GRUB2...the first time I noticed the problem was around the time I upgraded to 16:04 (possibly a coincidence). Only a couple of months ago I was happily rebooting and navigating the GRUB menu and selecting none default options to my hearts content.

Most of the similar posts I've seen are resolved by enabling Legacy USB support the BIOS (using if PS/2 keyboard if necessary). My BIOS looks like this:

[http://i66.photobucket.com/albums/h257/themainliner/bios1_zpsik4fzvwt.jpg](http://i66.photobucket.com/albums/h257/themainliner/bios1_zpsik4fzvwt.jpg)

I also added this line to /etc/grub/default (updating grub afterwards)[INDENT][B]GRUB_TERMINAL=usb usb_keyboard
sudo update-grub[/B]
[/INDENT]
I'm not even convinced this *is* a valid GRUB2 option, I think it is, and can only be: **GRUB_TERMINAL=console**. However, it didn't interrupt boot, hang GRUB or return an error...I tried it anyway.

I tried reseting the BIOS (jumper) and then enabling Legacy USB support again. I've tried using different USB slots and different USB keyboard - same result.

Here is some corollary information that may be helpful:

[INDENT][B]Logitech K360 USB Keyboard
Sabertooth FX 990 r1.0 motherboard 
[/B][/INDENT]
[INDENT=2][B]BIOS version=1604 (24/102012 latest)

[/B][/INDENT]
[INDENT]Xubuntu 16:04
[/INDENT]
[INDENT]Debian 8.4
Windows 7 Ultimate
[/INDENT]
[INDENT=3]several other distros...
[/INDENT]

This is the contents of my **/etc/default/grub** file:
[INDENT]GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ivrs_ioapic[9]=00:14.0 ivrs_ioapic[10]=00:00.1 iommu=pt iommu=1"
GRUB_CMDLINE_LINUX=""

[/INDENT]
Thanks in advance! :wink:

---

### Post by X-RED_Tech on 2016-06-05
I've never seen things like iommu=pt or iommu =1
?????

You probably need "iommu=soft" and eventually turn off IOMMU in UEFI (on in some boards) and nothing else.

---

### Post by themainliner2 on 2016-06-05
Those two entries are for *QEMU/KVM* (I'm passing through my VGA card). These particular entries features in most (all?) of the guides.

Why do you recommend turning it off and will I still be able to use visualization (and passthrough)?

Many thanks for the suggestion, I crawled my way upstream to source I trusted and double checked those settings :-\" they should be (and now are):

[INDENT][B]amd_iommu=on iommu=pt
[/B][/INDENT]

Maybe my VMs will perform better/be more stable. :biggrin:

I will also remove the entries and turn *IOMMU* off in the *BIOS* and test, though I admit I'm clueless as to how this would effect *GRUB* and the *USB Keyboard*. :-k

---

### Post by X-RED_Tech on 2016-06-05
The IOMMU issue is common in certain AMD chipsets present in many different makes/models. Up until now this is what I gathered about it:
 - In order to work as expected with Ubuntu and other distros the grub parameter I mentioned is always required and some boards also require IOMMU activated while others is the other way around. Depends on how broken the IOMMU implementation is, I guess, but always broken in a way or another nevertheless. It doesn't take long to search this forum and find different boards with the same or similar problems without tweaking - in some only USB3.0 ports/hub don't work; others miss built-in audio, Ethernet, etc. - and the solution has always been the same.
I wasn't aware IOMMU had some roll in virtualization. Perhaps it does with KVM, I don't know, so far I have only used the good old Virtualbox. Would you please post the source/guide where those grub parameters are mentioned?

---

### Post by wildmanne39 on 2016-06-05
Please use thumbnails or Url's when posting images because many people have slow internet conections and loading pages with large images is very difficult for them.

---

### Post by themainliner2 on 2016-06-05
Apologies I was looking for thumbnail option I guess I really need to make one and link to the larger on from it...sorry.

---

### Post by themainliner2 on 2016-06-05
> **X-RED_Tech said:**
> I wasn't aware IOMMU had some roll in visualization. Perhaps it does with KVM, I don't know, so far I have only used the good old Virtualbox. Would you please post the source/guide where those grub parameters are mentioned?

Indeed, I know that r1 of the Sabertooth FX990 has a broken IVRS table...I tried remove the two switches from **GRUB_CMDLINE_LINUX_DEFAULT** and then I disabled IOMMU in the BIOS and then all hell borke loose! LOL **Xubuntu** did boot with a metric *fruit* ton of USB parsing errors (I am guessing here, and I'm no expert, just an MCSE Support Engineer, but I think IOMMU does have something to do with the detection and initializations of USB...) neither my keyboar dor mouse worked and then the OS hung. I tried booting into **Debian** and IOMMU bitmap table could not be loaded and this caused a kernel panic. I'd seen enough. I expect I could've loaded **antiX** up which has *no* KVM setup and IOMMU GRUB switches...I suspect it would've worked fine.


As for the main guide I've followed I started at the Arch Forums, which not isn't maintained anymore and moved to [Alex's ]("http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-3-host.html")[Williamson ]("https://www.blogger.com/profile/02071923591707250496")[ Blog]("http://vfio.blogspot.co.uk/2015/05/vfio-gpu-how-to-series-part-3-host.html"). "[FONT=Arial]You may also want to add the option [/FONT][FONT=Courier New]iommu=pt[/FONT][FONT=Arial], which sets the IOMMU into passthrough mode for host devices."[/FONT]

The damn annoying thing is that even with IOMMU *disabled* the fruiting USB keyboard still didn't work in GRUB! :grin:

---

### Post by X-RED_Tech on 2016-06-05
> **themainliner2 said:**
> "[FONT=Arial]You may also want to add the option [/FONT][FONT=Courier New]iommu=pt[/FONT][FONT=Arial], which sets the IOMMU into passthrough mode for host devices."[/FONT]

The damn annoying thing is that even with IOMMU *disabled* the fruiting USB keyboard still didn't work in GRUB! :grin:

My point is that all solutions I read point to "iommu=soft" being always needed, regardless of other parameters. This supposedly lets the OS itself deal with it and all devices work. What further implications this ca have in virtualization, especially KVM, I know nothing about.
Even [this]("http://vfio.blogspot.com.es/2014/08/iommu-groups-inside-and-out.html") from the blog you suggested is kinda over my head.

---

### Post by themainliner2 on 2016-06-05
Over your head, how do you think I feel...but at least I've got a working VM with VGA passthrough and gaming install of Windows running at almost bare metal performance levels...so I'm doing something right.

I need to do some more research on **IOMMU**, and it's switches and I will try **iommu=soft**. I'm at home and Live Environment=Test Environment :lolflag: so bear with me as I test all the options...I'll be back (especially if I ever find a fix). :biggrin:

---

### Post by themainliner2 on 2016-06-06
OK, I had to re-enable IOMMU in the BIOS, but as I reported earlier this had no effect on the USB keyboard in GRUB: I still couldn't select or other entries.

I removed the two IOMMU entries in grub: this had no effect on either the keyboard or the running of VMs...so I may yet strip that out of my procedure for building and running QEMU/KVM Virtual Machines with VGA Passthrough...

This doesn't take me any further forward with the USB keyboard or why this has only just started happening when my BIOS version (1604) hasn't changed since I bought the board. This makes me suspect the issue is GRUB2, version 2.02~beta2.

---

