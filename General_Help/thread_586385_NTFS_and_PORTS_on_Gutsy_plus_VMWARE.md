---
title: "NTFS and PORTS on Gutsy plus VMWARE?"
date: 2007-10-22
forum: General Help
---

### Post by dmontalvao on 2007-10-22
Hi all!

I am a recent user of Ubuntu. I started with Feisty, and now I am a Gutsy user. At the moment, I have dual boot with Windows XP Pro. However, after a not so long period of habituation, it came to me that I prefer Ubuntu to Windows! In my machine, a 4 year old one, you can clearly notice some differences concerning to performance.

I will buy a new HD (faster and bigger), and I will have to re-install everything again. My questions are:

- Should I keep a FAT32 partition for Documents as I have now, or NTFS is better when using Gutsy?

- Should I keep Dual Boot, use VMWARE on Gutsy, or both? What would be your advice from your experience (I don't want dual boot, but if u give me good arguments...)?

- Does VMWARE support access to ports, such as PCMCIA?

Thank you all for your help!

Cheers,
aka Lord Von M

---

### Post by puccaso on 2007-11-10
if you are not going to use xp anymore
just use ext3, or reiserfs
reiserfs has some performance uppers, but ext3 is generally better all round..

you can also read ext3 via xp, so it might be the best option.

dual boot
mm
it depends why you are wanting to use windows..
if its for certain games,
then yea - dual boot is the best..
but if its to use windows live messenger, or something else (please state)
you might be better with vmware OR virtualbox.. virtualbox lets u use windows in a seemless mode, so if ur using live messenger - u can run it, on virtual box looking like a linux app... without a windows background etc.. 

i dont know about vmware and pcmcia but i know virtualbox lets u access usb... also lets u access usb over a network!

so if u have a system running linux, with windows inside a virtualbox.. and u connect via another virtualbox client - if u plug a usb gadget to the client machine, the host machine will read it and let u use it.. 

hope this helps.

---

### Post by fjgaude on 2007-11-10
I've used VMware server, the free one, for a long time now and am happy with it. Works fine with USBs, printers, etc., that you use in Windows. It's fast and smooth... cut, copy, and paste reliably between apps in Ubuntu and Windows. Notice my signature.

---

### Post by dmontalvao on 2007-11-11
Thank you all for the support!

I already installed my laptop, and I decided to maintain dual boot. I also have a virtual machine inside my Gutsy, using VBOX and I am fully satisfied. I also tried Qemulator with Kqemu and it was way slower.

Just for you to understand why I need both dual boot and a virtual machine:

1) Dual Boot - I acquire signal with a National Instruments DAQCard (6062E) - PCMCIA device - and despite the fact I have Labview8.0 running on my Gutsy, I still need MAX which is an application that configures the hardware ans sensors and only exists for Windows. Otherwise, I would have to configure everything by hand. It's possible, but hard, so why bother if I acquire signal just once in a while?

2) Virtual Machine - Mostly I need it if ppl send me Word docs for me to change and send back to them. That way I won't screw formatting. I also use it for Solidworks and DWGEditor if I just want to do minor drawings. If major drawings are needed, I either run ProE in my Gutsy or Solidworks on WinXP. I also use FEM applications, like Ansys and Abaqus. The later I can only install on Windows.

Btw, I am a Mechanical Engineer and PhD student, and I am in need of a lot of specialized programs.

Thank you all!

---

### Post by puccaso on 2007-11-11
i understand your nessecity
the only other option i can fathom,
is to have a dual boot, and use vmware to boot the pysical partition.
it does take some doing, but eventuallyl you will have a much tighter, system.
two hardware profiles, one for native and one for vmware and you wil be able to do as you wish...

---

### Post by dmontalvao on 2007-11-12
Yeah, pucasso, it is indeed anoying to have 3 in 1, specially dual boot. I don't bother having a VM, specially when I am seeing some of my colleagues to use it with Vista (I just feel like LOOOOL!!!). I allocated 20Gb of my disk for dual boot, only for the purpose of signal acquisition (which is a lot, but I also installed Office and other apps just in case). Anyway, I will leave it like it is until we acquire a USB DAQ (we are now discussing that issue in our lab, since new laptops are not bringing PCMCIA anymore)!

Finally, just to say I am sort of a newb with Ubuntu (I started with Dapper but quitted - I had several problems with evolution and totem that annoyed me a lot, latter I tried Feisty and everything went ok). I already surpassed the "getting used to" fase, and actually, I can do mostly everything I want.

Although I am not going to follow your latest advice for now, that was really useful as I will surely try that at a later stage. Thank you very much.

Cheers mate! ;)

---

