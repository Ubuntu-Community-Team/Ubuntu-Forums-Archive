---
title: "ACPI: PCI Interrupt"
date: 2008-06-08
forum: General Help
---

### Post by Poffertje on 2008-06-08
Hello!

I'm a relatively new Linux user, with my only true experience in Archlinux for a few months.  After asking myself just why I prefer to tediously configure everything myself, I decided to give Hardy Heron a go (I did briefly try Dapper and Feisty in the past, IIRC).  Just wanted to mention that I'm amazed at how seamlessly this distro works out of the box.  It's polished polish.

Anyway, onto my problem.  I'll start by admitting that I don't know a whole lot about ACPI or IRQ, so please bear with my broken explanation.  And apologies if this is the wrong section.

I had no problems installing or logging into Ubuntu initially, but I am now.  I'm not sure what caused this, but I receive an error similar to the below at every attempt to boot up now, and the loader just stalls until I manually hit the restart button.  Keep in mind that I do receive 1-3 of these things, and the IRQ numbers are often different.

```
ACPI: PCI Interrupt 0000:05:02:0[A] -> GSI 18 (level, low) -> IRQ 19
```

Despite this error, I managed to get back on without any issues on one occasion; but unfortunately the problem persisted after rebooting.  I did update my system--this was on the second boot, I believe, of a completely fresh install--and install the proprietary NVIDIA drivers during the time I was on, if that helps.  It may also be worth mentioning that I've had similar issues with other distros failing to boot up.  The latest Archlinux LiveCD won't start up, nor will PC-BSD or FreeBSD.  On the other hand, I've had no issues with others (SLAX, Parted Magic, you could also count Ubuntu in some ways).

By the way, I actually did this fresh install because I couldn't get the sound working with pulseaudio (worked fine when ALSA was selected).  Seeing as Ubuntu installs so smoothly, I decided I'd be best off trying again to see the default sound settings.  I had no issues with pulseaudio after the reinstall.  Oh, I'm pretty sure I updated my system and I'm 100% sure that proprietary NVIDIA drivers were installed without any issues durign the previous install, yet I can't remember one of these errors.

I've tried everything suggested in the [_related help_]("https://help.ubuntu.com/community/DebuggingIRQProblems") short of moving around the PCI cards, but I will probably try that tomorrow.  I only really have one PCI card installed--an Audigy 2 ZS--which I'm not using at the moment, in addition to the PCI-E video card.  Furthermore, I have tried disabling all onboard devices with no success.

Just figured I'd shoot this post off before I go to bed.  After fiddling with multiple distros for the week and running into similar problems, I think it's about time I submit and turn to others' knowledge.  Let me know if you need any hardware details, I'm too tired to post them at the moment.

Many thanks to any help that you can provide.

Edit:  Just wanted to add that when using "pci=noacpi" or "acpi=off",  these errors are not displayed but the system hangs anyway.  What is displayed, as is normally just above the error, is the following:
```
lo: Disabled Privacy Extensions
```
*Not sure if this is "LO" or "IO".*
There is another similar line involving "NET" just above that.  I'll confirm this tomorrow.

---

### Post by Poffertje on 2008-06-09
Any ideas?

Edit: Fixed after removing the Audigy.

---

### Post by aliozer on 2008-11-13
I have a very similar problem. My system is a Dell Inspiron 530 with Ubuntu 8.0.4 and kernel 2.6.24.3. The system boots w/o any problems as is. But when I plug in a PCI wifi adapter  (Linksys WMP55AG), it stalls during bootup after displaying the message:

```
wlan: 0.9.4
ath_pci: 0.9.4
ACPI: PCI Interrupt 0000:02:00 -> GSI 21 (level, low) -> IRQ 18
```

Any ideas on how to solve this problem?

---

### Post by BinaryPrashant on 2008-11-18
Same problem here. Smashing my forehead on CPU.....

ACPI: PCI Interrupt 0000:01:00.0(A) -> GSI 21 (level, low) -> IRQ 16

Waiting for reply..
Thanks,
-BinaryPrashant.

---

### Post by BinaryPrashant on 2008-11-18
Anyone there to help us??

---

### Post by BinaryPrashant on 2008-11-20
> **BinaryPrashant said:**
> Same problem here. Smashing my forehead on CPU.....

ACPI: PCI Interrupt 0000:01:00.0(A) -> GSI 21 (level, low) -> IRQ 16
:lolflag:
     Problem was in my inbuilt 56kbps modem installed in PCI slot which I did not use for long time.....
I do not know what was the actual problem there however I can boot ubuntu as usual after removing modem. Problem comes back when I insert Modem back..

Thanks,
BinaryPrashant:guitar:

---

