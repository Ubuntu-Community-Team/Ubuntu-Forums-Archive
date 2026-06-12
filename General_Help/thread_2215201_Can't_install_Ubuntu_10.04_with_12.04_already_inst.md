---
title: "Can't install Ubuntu 10.04 with 12.04 already installed"
date: 2014-04-05
forum: General Help
---

### Post by jeffbeyer42 on 2014-04-05
[COLOR=#333333][FONT=UbuntuRegular]I have a machine with Ubuntu 12.04 LTS Desktop installed and everything works find. I would like to install 10.04 LTS on a second partition.

As standard procedure, I tried booting from a 10.04 DVD through the BIOS. When the 10.04 disk is in the drive, it is not listed as a bootable device. Only my linux partition is listed as bootable drive. The DVD drive is listed as a bootable device with other distributions such as 13.04 and 13.10. My kernel version is Ubuntu 3.11.0-19.33~precise-generic 3.11.10.5. My grub version is 1.99-21buntun3.14.[/FONT][/COLOR]

---

### Post by ajgreeny on 2014-04-05
Your question suggests you do not fully understand how to boot to a live DVD, but aside from that, is the 10.04 a good burn that will boot on another machine?
Did you insert the DVD and then reboot the computer making sure that the DVD is first priority boot device?

However, I presume you are aware that 10.04 desktop version is no longer supported, so you will not get any security updates in future.  Why do you want to install that old version, anyway?

---

### Post by jeffbeyer42 on 2014-04-05
Yes, I do know how to boot to a live CD as I've done it numerous time.s
Yes, I have a good burn and tested elsewhere
Yes, I'm fully aware 10.04 is not supported anymore but I need it for a legacy development project

When I insert the 10.04 DVD and reboot, I cannot set the DVD as the first priority in the BIOS.  It is not even listed as an available device with the 10.04 DVD.  It is listed as an available device with other distros such as 12.04 and 13.04 etc.

---

### Post by Warren Hill on 2014-04-05
Is running 10.04 inside [VirtualBox]("https://www.virtualbox.org/") an option?  10.04 will install after 12.04 if you can get it to boot of the CD or alternatively from [USB]("https://help.ubuntu.com/community/Installation/FromUSBStick").

But unless you can get it to boot from USB or CD.  I don't see how you can get it installed.

---

### Post by jeffbeyer42 on 2014-04-05
Thanks.  Any specific reason why I can't get it to boot from the CD?  Do you think I could completely reformat the drive and start fresh?  I don't necessarily need to keep 12.04 around for this effort.

---

### Post by Warren Hill on 2014-04-06
Can't think of any reason boot device is usually set in the BIOS. If it won't boot from a 10.04 CD I wouldn't think it will boot from any other CD/DVD.  One thought 10.04 was a CD not DVD.  Have you tried creating a CD instead of a DVD?

---

### Post by sikander3786 on 2014-04-06
> **jeffbeyer42 said:**
> Thanks.  Any specific reason why I can't get it to boot from the CD?  Do you think I could completely reformat the drive and start fresh?  I don't necessarily need to keep 12.04 around for this effort.

Try a Live USB or a CD instead of DVD as others suggested.

There is no reason for reformatting the whole drive and start fresh. HDD installation can't/won't/shouldn't prevent booting up a Live/Installation CD/DVD/USB/Floppy. There is no link whatsoever. If you are thinking that Ubuntu 12.04 install is preventing you from booting up Ubuntu 10.04, just throw it out of you mind and concentrate on your installation medium/Bios settings.

Hope you get it done soon.

Regards.

---

### Post by jeffbeyer42 on 2014-04-06
Media and burn had not impact. Unified Extensible Firmware Interface (UEFI) Boot was enabled in my BIOS. After disabling it, I could boot from the 10.04 CD / DVD.

---

