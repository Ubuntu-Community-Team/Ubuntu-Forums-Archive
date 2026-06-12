---
title: "Black screen &amp; can't boot from USB/CD. Windows works."
date: 2012-11-16
forum: General Help
---

### Post by Sean Dewlin on 2012-11-16
Title says it all. This night I left my laptop on, but I left it working with battery (I forgot about it). So, during night it shut down. Or... Suspended? Hibernated? Now I cannot boot Xubuntu, all I can see is black screen. I cannot boot from USB/CD either - it just shows normal GRUB instead. When trying to boot from CD - disk goes really wild, it does more noise than TV. Seems like SWAP is full... I boot from Windows & install some random disk partition programs. Some of them show that SWAP is full, some of them show that it's okay.
boot.log
```

* Starting LightDM Display Manager[74G[ OK ]
saned disabled; edit /etc/default/saned
* Stopping Userspace bootsplash[74G[ OK ]

```
I've searched around for this and didn't find any solution. I also could not find how to format SWAP partition from Windows. I cannot boot with recovery mode either. **memtest said that there is more space used (on SWAP, perhaps?) then available. Like if 8 MB was used of 7 MB.**
kern.log
```

Nov 16 17:51:01 system64 kernel: [   23.711642] vgaarb: this pci device is not a vga device
Nov 16 17:51:01 system64 kernel: [   23.711656] vgaarb: this pci device is not a vga device
Nov 16 17:51:01 system64 kernel: [   23.711681] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
Nov 16 17:51:01 system64 kernel: [   23.711703] vgaarb: this pci device is not a vga device
Nov 16 17:51:01 system64 kernel: [   23.711717] vgaarb: this pci device is not a vga device
Nov 16 17:51:01 system64 kernel: [   24.307522] IPv6: wlan0: IPv6 duplicate address fe80::e2ca:94ff:fedf:3885 detected!

```
I feel doomed. Also I do not get that IPv6 error. WLAN indicator on my laptop lights up just after BIOS (I think it should light up when OS is loaded). Something from syslog.
syslog
```

Nov 16 17:51:21 system64 NetworkManager[868]: <info> (wlan0): IP6 addrconf timed out or failed.
Nov 16 17:51:21 system64 NetworkManager[868]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov 16 17:51:21 system64 NetworkManager[868]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov 16 17:51:21 system64 NetworkManager[868]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Nov 16 17:51:48 system64 acpid: client 1237[0:0] has disconnected
Nov 16 17:51:48 system64 kernel: Kernel logging (proc) stopped.
Nov 16 17:51:48 system64 rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="831" x-info="http://www.rsyslog.com"] exiting on signal 15.

```
Something with IPv6 again...

Anyone? I cannot even boot from USB/CD, any help is **greatly** appreciated.

---

### Post by offgridguy on 2012-11-16
You say in the title windows works.  If so go here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Download the iso file and burn it to a CD/DVD and you will have a live CD.
Boot from this, follow the instructions, either for repair or diagnosis and report, which
you can paste in this forum for someone to have a look at.

---

### Post by Sean Dewlin on 2012-11-16
I think I have mentioned that I cannot boot from USB/CD. It will not let me to.

---

### Post by offgridguy on 2012-11-16
> **Sean Dewlin said:**
> I think I have mentioned that I cannot boot from USB/CD. It will not let me to.

Have you tried changing the boot order in the BIOS ?

---

### Post by Sean Dewlin on 2012-11-16
I didn't know that I'm looking like a complete newbie. Yes, I tried. I also tried pressing F2 (selecting boot device) and it still results in GRUB being displayed with normal options (Ubuntu, Windows 7, etc.), so I don't even know. Although I'll try to burn boot-repair package right now - let's see if it will work.

---

### Post by offgridguy on 2012-11-16
> **Sean Dewlin said:**
> I didn't know that I'm looking like a complete newbie. Yes, I tried. I also tried pressing F2 (selecting boot device) and it still results in GRUB being displayed with normal options (Ubuntu, Windows 7, etc.), so I don't even know. Although I'll try to burn boot-repair package right now - let's see if it will work.

My apologies if i offended you, that was certainly not my intention.  I wasn't totally understanding your problem, my mistake.

---

### Post by greatsirkain on 2012-11-16
seeing as windows works get Sardu usb boot creator and select then get Hirens boot cd and put it in the correct sardu folder, (most of the other tool options are one click downloads from within the program, UBCD etc) when it's done boot from the usb and go to utilities and tell it to detect all operating systems in grub2, select the one you want and away you go.

If that doesn't work have a look at the other tools which includes any live operating systems you selected during the creation process (I haven't figured out how to set up persistence for ubuntu live yet, not sure you can on sardu) but it hasn't failed me yet.

Note the tools for fixing MBR etc, BootRepair on Ubuntu live does it

Edit: if after you've done the boot usb it still doesn't boot from it maybe consider resetting your CMOS from the BIOS, to restore factory defaults etc in case it's a hardware issue then you run the BIOS setup from scratch

---

### Post by Sean Dewlin on 2012-11-16
After many hours of searching I came to conclusion that this is a very weird hardware issue and I'm not the only one who has it. Windows turns off with the AC power connected, but it works good just with battery. Seems like it's something with motherboard/fan speed/CPU. Anyway, thanks for your replies!

---

