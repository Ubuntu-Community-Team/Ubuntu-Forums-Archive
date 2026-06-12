---
title: "new system, dual booting, grub behaving strangely."
date: 2017-05-01
forum: General Help
---

### Post by merockstar on 2017-05-01
Hello. I just finished building a computer and I'm dual booting. I have an SSD drive with windows on it for gaming and a 2TB spindle drive with Ubuntu on it for general usage. 

[This]("https://www.newegg.com/Product/Product.aspx?Item=N82E16813130900&nm_mc=TEMC-RMA-Approvel&cm_mmc=TEMC-RMA-Approvel-_-Content-_-text-_-") is my motherboard.

Windows is booting up just fine. When I boot from the encrypted spindle drive to run Ubuntu half the time it goes straight to asking for an encryption password, with a nice looking GUI, but the only thing my keyboard will type is ctrl+alt+del, which I promptly use to restart, and boot back up again the exact same way. The second time I get a GRUB screen asking if I want to boot Ubuntu or do some other advanced options. It defaults to Ubuntu after a few seconds, then a get a much choppier looking encryption password screen, but my keyboard actually works and I get to log in. Anyway I can make it so I don't have to start my computer twice every time I want to boot into Ubuntu?

Also, with my bios I open the boot menu by tapping f11 when starting up. if nothing is picked it defaults to windows. earlier on I had attempted to dualboot both operating systems from the SSD, but found partitioning it to be a challenge, and opted to just give Ubuntu it's hard drive. But the remnants of that dual boot attempt still linger on my f11 screen. How might I get rid of that? Is it possible for the computer to default to the boot menu everytime I turn it on?

Also, since you're already reading, happen to have any opinion on what is the best way to lock down Windows? I want it to only run the games I select, and perhaps a sandboxed web browser. if any attempt is made to do anything I'd like a snarky error message to pop. should I make a new thread for that one?

thanks in advance. this community is always so graciously helpful.

---

### Post by yancek on 2017-05-01
You will probably need to post more information to get  solution to your booting problem and the best way to do that is to get the boot repair software from the site at the link below.  Run it selecting the option to "Create BootInfro summary" and do not try to do any repairs.  When it finishes, you should get a link which you can post here which will give details on your system and someone should be able to make a suggestion.

> Also, since you're already reading, happen to have any opinion on what is the best way to lock down Windows?

You'll probably get better advice on that on a windows forum.

---

### Post by oldfred on 2017-05-02
If using LVM & full drive encryption, be sure to mount LVM and unencrypt. Boot-Repair has trouble as both LVM and RAID use /mapper and it tries to figure out which you have but best to help it.

Are both systems installed in UEFI mode on gpt partitioned drives?

 May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by merockstar on 2017-05-02
> **yancek said:**
> 
You'll probably get better advice on that on a windows forum.

Good point. It's been so long since I've used windows that I forgot it wasn't Ubuntu.

> 
If using LVM & full drive encryption, be sure to mount LVM and unencrypt. Boot-Repair has trouble as both LVM and RAID use /mapper and it tries to figure out which you have but best to help it.


Can't remember if using LVM or not, but ran the scan anyway.

> 
 Are both systems installed in UEFI mode on gpt partitioned drives?

Not sure about UEFI, kind of new to building computers. I think the SSD drive with Windows is MBR partitioned, pretty sure that was related to the problem I ran into trying to install both OS' on the SSD card until I just gave up and gave Ubuntu the spindle.

I appreciate your help guys, here's the results of that scan: [https://paste.ubuntu.com/24500905/](https://paste.ubuntu.com/24500905/)

---

### Post by oldfred on 2017-05-02
Your sda is Ubuntu in BIOS/MBR boot mode with LVM and encryption.
You sdb is Windows with UEFI/gpt boot mode.

While you can boot from UEFI menu, some systems require you to turn on/off UEFI or CSM boot mode to boot. Most now seem to auto switch. But UEFI & BIOS/CSM are not compatible. Once you start booting in one mode, you  cannot switch, or grub only boots other installs in same boot mode.

Both Windows & Ubuntu install in the same boot mode UEFI or BIOS as you boot the installer from UEFI. Flash drive install will show two boot modes, one UEFI and one CSM unless UEFI secure boot is on, then only UEFI is available.

 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

You cannot easily convert sda to gpt. While conversion is possible, with the LVM difficult to resize to add space for ESP. And in UEFI mode grub only installs to an ESP - efi system partition on drive seen as sda. Often best with two drive systems to unplug other drive. You often have to reset UEFI to find unplugged drive with efibootmgr, but many find Windows, where the do not auto find Ubuntu.

Lots more info on UEFI in link in my signature.

LVM is really for advanced users. It requires special LVM tools. But if you need or want full drive encryption you have to use LVM.
I do not see much advantage to encrypting the operating system. That is open source. And 80/20 rule applies to my data, maybe if 90/10 or 90% of my data no one would care about and is not important enough to worry about.

---

### Post by merockstar on 2017-05-05
> **oldfred said:**
> Your sda is Ubuntu in BIOS/MBR boot mode with LVM and encryption.
You sdb is Windows with UEFI/gpt boot mode.

While you can boot from UEFI menu, some systems require you to turn on/off UEFI or CSM boot mode to boot. Most now seem to auto switch. But UEFI & BIOS/CSM are not compatible. Once you start booting in one mode, you  cannot switch, or grub only boots other installs in same boot mode.

Both Windows & Ubuntu install in the same boot mode UEFI or BIOS as you boot the installer from UEFI. Flash drive install will show two boot modes, one UEFI and one CSM unless UEFI secure boot is on, then only UEFI is available.

 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

You cannot easily convert sda to gpt. While conversion is possible, with the LVM difficult to resize to add space for ESP. And in UEFI mode grub only installs to an ESP - efi system partition on drive seen as sda. Often best with two drive systems to unplug other drive. You often have to reset UEFI to find unplugged drive with efibootmgr, but many find Windows, where the do not auto find Ubuntu.

Lots more info on UEFI in link in my signature.

LVM is really for advanced users. It requires special LVM tools. But if you need or want full drive encryption you have to use LVM.
I do not see much advantage to encrypting the operating system. That is open source. And 80/20 rule applies to my data, maybe if 90/10 or 90% of my data no one would care about and is not important enough to worry about.

Thanks for the input! Sounds like my best bet is to just leave it alone, seeing how everything is functional.

---

