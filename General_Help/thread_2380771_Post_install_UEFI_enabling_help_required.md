---
title: "Post install UEFI enabling help required"
date: 2017-12-21
forum: General Help
---

### Post by MibunoOokami on 2017-12-21
Long story short I'm trying to enable UEFI on a machine and after finally resetting the BIOS password, I'm not being given an option to change boot mode to UEFI. I've ran boot-repair and it can't fix the issue. 

From what I've read, the steps I have taken appear to usually be done pre - install. The machine in working on has had Ubuntu running on it problem free for some time. [Here]("https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757") is one post I read, and [another]("https://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi"), and funnily enough I almost had the same [problem]("https://ubuntuforums.org/showthread.php?t=2337173") a year ago but was doing a fresh install. 

Basically I'd like to know if there's a work around to get it booting properly, or do I need to break the bad news to the owner that they may need to nuke the system back to some version of Windows?

---

### Post by yancek on 2017-12-21
I don't see how you can expect any help when you don't even give minimal information on the hardware you are running.  Different manufacturers have different methods of accessing and modifying the BIOS so the absolute minimum information required would be the manufacturer of the computer.  I would not expect boot repair to be able to modify anything in your BIOS. 

> 
From what I've read, the steps I have taken appear to usually be done pre - install.

What steps, you need to post the information.  You make reference to some sites you used but don't post any links.  How are we supposed to know what you are referrring to?

If the machine was running problems free for some time and suddenly stopped running without problems, then likely there was some type of change to hardware/software or a hardware failure that you aren't mentioning.

---

### Post by MibunoOokami on 2017-12-21
> **yancek said:**
> I don't see how you can expect any help when you  don't even give minimal information on the hardware you are running.   Different manufacturers have different methods of accessing and  modifying the BIOS so the absolute minimum information required would be  the manufacturer of the computer.  I would not expect boot repair to be  able to modify anything in your BIOS. 



What steps, you need to post the information.  You make reference to  some sites you used but don't post any links.  How are we supposed to  know what you are referrring to?

If the machine was running problems free for some time and suddenly  stopped running without problems, then likely there was some type of  change to hardware/software or a hardware failure that you aren't  mentioning.


You must have read and replied while I was adding links, I  couldn't link them just to the words with my cellphone. My understanding  is that some sort of unauthorised Windows update removed grub. It's  another Acer Aspire model desktop PC, since I'm a little familiar with  these I thought I'd be smart and do a boot-repair and now neither OS  work.

---

### Post by oldfred on 2017-12-21
Your links are all on Acer issues which are unique to Acer.
But even with Acer you have to boot in UEFI mode & install in UEFI mode.
What model Acer?
Many have required updates to newest UEFI from Acer, some older threads mention downgrading UEFI. So there was a version of Acer UEFI that did not work. Newer threads say newest UEFI from Acer does work.

Microsoft so far, have required vendors to use UEFI Secure boot on all systems with Windows 8 or later pre-installed. But vendors must let users turn off UEFI secure boot. 
Older systems may be BIOS only.

What version of Ubuntu?
While mostly Lenovo, 17.10 has caused issues on a few Acer models also.
       Ubuntu 17.10 "corrupting" BIOS - many LENOVO laptops models Intel SPI & kernel issue Also some Acer
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147)

---

### Post by MibunoOokami on 2017-12-21
> **oldfred said:**
> Your links are all on Acer issues which are unique to Acer.
But even with Acer you have to boot in UEFI mode & install in UEFI mode.
What model Acer?
Many have required updates to newest UEFI from Acer, some older threads mention downgrading UEFI. So there was a version of Acer UEFI that did not work. Newer threads say newest UEFI from Acer does work.

Microsoft so far, have required vendors to use UEFI Secure boot on all systems with Windows 8 or later pre-installed. But vendors must let users turn off UEFI secure boot. 
Older systems may be BIOS only.

I'm pretty sure it's the same model as mine which is Z3-7100. Has Windows 10, now that I can enter BIOS it lets me enable/disable secure boot, the only difference I have noted when disabling it is that under boot options it brings up a line called ```
Launch CSM
```

> **oldfred said:**
> 
What version of Ubuntu?
While mostly Lenovo, 17.10 has caused issues on a few Acer models also.
       Ubuntu 17.10 "corrupting" BIOS - many LENOVO laptops models Intel SPI & kernel issue Also some Acer
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147)

I'm not entirely sure of the version, it's not the most recent (I.E 17.XX) likely 16.04 or 16.10

---

### Post by oldfred on 2017-12-22
Use 16.04.3, the most current.
 16.10 		Yakkety Yexpired  			2017-07

---

### Post by MibunoOokami on 2017-12-22
> **oldfred said:**
> Use 16.04.3, the most current.
 16.10         Yakkety Yexpired              2017-07

Pardon my ignorance, does that mean I need to do a fresh install with 16.04.3 rather than being able to somehow get the machine to boot with/from UEFI?

---

### Post by oldfred on 2017-12-22
Unless it directly boots, you cannot easily run fixes as they are not available in an ordinary repository.

If just settings in UEFI, then it still should boot. And then you could update to current version. But better to install LTS long term support version that does not require frequent updates.

---

### Post by MibunoOokami on 2017-12-23
Upon doing a fresh install (although not initially a desirable option) the machine is back in working order, well almost. I'll mark t his thread as solved and crates a new one then link it momentarily.

This is the link to my new thread. [https://ubuntuforums.org/showthread.php?t=2380857&p=13723657#post13723657]("https://ubuntuforums.org/showthread.php?t=2380857&p=13723657#post13723657")

---

