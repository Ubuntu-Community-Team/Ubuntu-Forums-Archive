---
title: "No suspend after upgrade"
date: 2012-10-28
forum: General Help
---

### Post by moteprime on 2012-10-28
[B]How to troubleshoot broken suspend after upgrade to 12.04/12.10
[/B]

Hi.
I got Ubuntu 12.10 Desktop AMD64 on Ideapad s205 AMD E-450.
After upgrading to 12.04 and now to 12.10, suspend stopped working, it just locks up my laptop and I have to unplug it and remove the battery to get it back up and running.
The newest kernels don't fix it, and I reported bugs on launchpad that haven't caught anybodies attention.
AMD Catalyst Centre caused the locks when I installed it on 11.10, but after upgrading to 12.04 and 12.10 the laptop also locks up when using the Radeon driver. 


What can I do to get it to work, it a bother to have to shut it down all the time.
Thanks.

---

### Post by moteprime on 2012-10-30
-Nobody?

---

### Post by ppq on 2012-10-30
I can reproduce this on my S205 with 12.10 amd64 and fglrx. Both suspend and hibernate are broken. :(

---

### Post by moteprime on 2012-10-31
> I can reproduce this on my S205 with 12.10 amd64 and fglrx. Both suspend and hibernate are broken. 

-But I'm just so glad that I'm not I only one on this planet with this problem.

I got a bug report here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1022974]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1022974")

Have you had any luck finding out how to go on solving this?
Thank you.

---

### Post by ppq on 2012-11-03
I tried blacklisting acer_wmi, switching back and forth between radeon (from [xorg-edgers PPA]("https://launchpad.net/~xorg-edgers/+archive/ppa")) and fglrx (9.010 from PPA and 12.11 beta from [here](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)) and installing vanilla kernels from [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") (3.7 daily 201211030405).
No luck so far.

---

### Post by moteprime on 2012-11-04
Have you ever had it working? -I did at som point on 11.10, but some update broke it. Unfortunatly it's to long ago and i can't remember the details.
If i try running 11.10 live session it does not work.
Have you got any idea why it is so hard getting help solving this issue, is it because everybody but me knows that it is unsolveable?

---

### Post by ppq on 2012-11-04
It worked for me in 12.04. I didn't use my S205 for a while so I can't tell when it stopped working. As far as I know, it doesn't work in 12.04 today, either.

I just shuffled through some old 3.2.0 kernels in 12.10, versions 3.2.0-23 to -32. Nothing works. Which is strange because it definitely worked with -23 under 12.04.

I don't feel like reinstalling again - would you try Ubuntu 12.04 with [this Kernel](http://packages.ubuntu.com/precise/kernel/linux-image-3.2.0-23-generic) (and [these](http://packages.ubuntu.com/precise/kernel/linux-headers-3.2.0-23) headers)? You may have to remove linux-headers-generic and linux-image-generic because they always depend on the latest kernel available.

Edit: One could also try Suspend while running [the old 12.04 Live-CD](http://old-releases.ubuntu.com/releases/12.04/ubuntu-12.04-desktop-amd64.iso)

---

### Post by moteprime on 2012-11-05
Thank you for your reply.
I have a smaller partition with Quantal on for testing purpose, and i will test the kernels you suggest as soon as possible. If we can find the exact kernel where the break is, i think that we have a good chance to get it fixed. Are there any difference if it is 32 or 64 bit?

---

### Post by ppq on 2012-11-05
I tested it in Quantal (12.10), but I don't have 12.04 (Precise) installed. Would you try it in Precise with the mentioned kernels?

I only tried 64bit.

---

### Post by jonnybignote on 2012-11-05
I can't get it working cleanly in 12.04 - keeps crashing, whether on suspend or on resume - no discernable patter to it so far.

I have pm-suspend logs that refer to NetworkManager55 failure to suspend, though I think that should just result in loss of network connectivity at resume, as opposed to complete system freeze.  I was running nouveau but changed to proprietary Nvidia - one of the newer ones, 300-something (I'm not at home) and the problem still remains.  I woke up this morning to find screen frozen with small band of colour across the top...

---

### Post by moteprime on 2012-11-05
@ppq - Yes, No Problem. I was short of time and did a quick reply. I will get the versions right. Thanks for the heads up. ;-)
I will test it on a precise installation with the kernels you described. 

@jonnybignote
Nvidia? This is a spcefic Ideapad S205 suspend problem.

---

### Post by jonnybignote on 2012-11-05
> **moteprime said:**
> @ppq - Yes, No Problem. I was short of time and did a quick reply. I will get the versions right. Thanks for the heads up. ;-)
I will test it on a precise installation with the kernels you described. 

@jonnybignote
Nvidia? This is a spcefic Ideapad S205 suspend problem.

Oops - missed that sorry...

---

### Post by moteprime on 2012-11-06
@ppq
I installed Precise and the kernel, not from the links you posted but from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
Does it make a differrense?
These are the files:
> 
linux-headers-3.2.23-030223_3.2.23-030223.201207121235_all.deb
linux-headers-3.2.23-030223-generic_3.2.23-030223.201207121235_amd64.deb
linux-image-3.2.23-030223-generic_3.2.23-030223.201207121235_amd64.deb
Installed with "sudo dpkg -i *.deb"
The result was a negative, it locked up. Will try with 3.2
As i remember it, the bug started in Oneiric, so i will try installing it to.
Can how GRUB is installed ot setup affect the suspend function?

---

### Post by moteprime on 2012-11-06
Tested:
Precise with kernel 3.2.0-030200 -Negative
Precise with kernel 3.2.23-030223 -Negative
Oneiric with stock kernel 3.0.0-12 -Negative
Oneiric with kernel 2.6.39-02063901 -Negative
Quantal with with 3.7.0-030700rc2 -Negative

How GRUB is installed, or setup, can it affect the suspend function?

---

### Post by ppq on 2012-11-07
Thanks for testing all those combinations, moteprime :)

There are some UEFI issues regarding the S205, some of which affecting s2ram/s2disk/shutdown. Lenovo did a pretty bad job implementing UEFI in this device. That's why I always install my operating systems in "BIOS CSM" mode on this device: Standard MBR/MSDOS partition label, "boot" flag for the root-partition ( / ) and an installation of grub-pc (not grub-efi) to the MBR of the disk. The installer **always** installs in UEFI mode, I had to use *debootstrap* to do a manual install using a Live-CD.

Do you use a UEFI-mode install?

---

### Post by moteprime on 2012-11-07
> Thanks for testing all those combinations, moteprime :)
No problem, i really would like suspend working again. And this is the first time i encountered anybody that helps, and even got the same problem.
-i still d not understand why we are the only ones having these troubles?

I got a dualboot setup with Windows, once in a while i need it for something windows only, or something drm related. I know for sure that i will need it if i wipe it. ;-)
Up until now i used easybcd and got grub-pc installed via chroot on a live session. 
But the new grub in Quantal seems to be able to handle it after i ran boot-repair. I had help here on the forum getting it done, and i do not exately know what went on before and after.
As far as i can tell going through installed packages i got grub-pc installed and nothing grub efi related.

---

### Post by ppq on 2012-11-07
I guess it's because people don't upgrade their machines very often :P
Anyway, it **is** very strange that new installations of old, known-to-work Ubuntu releases don't work anymore!

---

### Post by moteprime on 2012-11-08
**Yes it is!** It makes me think that maybe there are something in my (yours?) installation that are different from before, and other peoples?

Is it not possible to find out why or what fails?

---

### Post by ppq on 2012-11-09
I asked some people who have a S205, too. 12.04, 64 bit, installed a while ago, booting via EasyBCD. Everything works for them.
I recommended them not to reinstall :mad:

Just trying to find similarities: Do you happen to use a SSD in your S205? I have a Samsung 470 64GB SSD.

---

### Post by moteprime on 2012-11-10
I can't understand this.
I don't use ssd, there are nothing different about my S205 from others. And it does not even work from a live session. -Does it for you?

Edit: Are there any way to finde out what exactly goes wrong then i tries to wake up?

---

### Post by ppq on 2012-11-10
Well, there's /var/log/pm-suspend.log. It shows "success" for all steps except NetworkManager.
But disabling it (sudo service network-manager stop) and/or switching off WLAN using the hardware switch before suspending doesn't help, either.

---

### Post by moteprime on 2012-11-10
In my case i does appear that the laptop mostly wakes up as supposed to, the led's light up, the fan starts and the harddisk to, but it's the  graphics that aren't comming to life (it looks that way). Could it be Xorg, compiz or Unity. -It could maybe explain why it does not seem to be related to the kernel.
Wonder if a Lubuntu og debain installation will work?
You mentioned others with S205's, are any of them linux geniuses, by any chance? ;-)


PS: my S205 are a E-450

---

### Post by ppq on 2012-11-10
Mine has a E-350. I don't think it's just X that doesn't wake up. When you try to press CTRL+ALT+DEL or SYSRQ R-E-I-S-U-B, nothing happens. The SYSRQ command does an emergency reboot which **always** works when it's a software-related problem that doesn't affect the kernel. It doesn't work here, though.

Also, other services like networking don't start when "waking up" this way, at least I can't ping the S205 (LAN).

---

### Post by moteprime on 2012-11-10
Yes, you are right...
:-(

---

### Post by moteprime on 2012-11-11
I been through all the logs and done more testing, but no errors or fails gets recorded.
Is it not possible to find out what it is that fails?

---

### Post by ppq on 2012-11-11
No, it's not. Ubuntu freezes before it's able to write logs when waking up.

If it wasn't working in Windows, I would say it's a hardware-related problem. 

I think we should test it with other distributions' Live-CDs.
Or... well, we could try kernel .debs from Debian in Ubuntu (which *should* be possible theoretically), or compile our own.

---

### Post by moteprime on 2012-11-11
I all ready tried Debian (negative), Fedora would not boot from the stick i made with unetbootin.
Do you have any good ideas about what Ditros to try?

---

### Post by ppq on 2012-11-11
Maybe openSUSE?

BTW: No need to use Unetbootin, you can copy the Fedora .iso image to your stick using dd: ```
sudo dd if=/path/to/fedora.iso of=/dev/sdx
``` where /dev/sdx is your USB-stick (double-check that, obviously).
This works for most Live-CDs nowadays, including [U|Ku|Xu|Lu]buntu

---

### Post by moteprime on 2012-11-15
Sorry for not getting back to you, but i have had other things to focus on. -Among the more plesant ones, are a new Nexus 7. :-)
I tried some different distro's but have not had much luck, with the one that are not ubuntu or debian based.
Are the only way out of this suspend problem/bug not to report a bug on bugzilla.kernel.org?
I still cannot understand why we are the only ones with thi problem?

---

### Post by moteprime on 2012-11-17
-And i also thought, if it is possible to put the kernel in som sort of debug mode just before initiating suspend, so that we had a chance to see whats wrong?

---

### Post by ppq on 2012-11-27
Hi! Sorry, I've been busy with lots of other things. Would you mind testing something? I don't have much time right now...

[iucode-tool](http://packages.ubuntu.com/quantal/iucode-tool) upgrades the CPU's byte code at boot time, everytime you boot. It was initially created for Intel CPUs, but should work for AMD, too. Installing it (and, maybe, rebooting) is enough, no need to do something else.

Perheps s2disk works afterwards..

---

### Post by moteprime on 2012-11-29
Hi. Thanks for getting back, i was starting to loose hope. ;-)
I have tested your suggestions, but cannot be sure about the result. My test installating doesn't behave like its feeling good anymore. Not booting half the times, crashing and so on.
In the comming weekend i will make a new installation and test on it.
Isn't it ok just to install uicode-tool from the repoes?

---

### Post by ppq on 2012-11-29
Sure, just install it with apt-get. I just wanted to make clear that "iucode-tool" is the package name by linking to packages.ubuntu.com :)

---

### Post by sjs2 on 2012-12-02
In my Novatech laptop (actually a rebadged Clevo W76K) hibernate/suspend  stopped working sometime during 12.04. I tried all the fixes I could  find on the web, but the only thing that worked was to downgrade the  kernel to the most recent version that I knew worked (3.0.0-28 ). This  seems to be OK on both 12.04 and 12.10, without any problems in  functionality, as far as I can see.

On the other hand my daughter has a Dell Inspiron 1546 which hibernates but just won't suspend whatever I do.

---

### Post by moteprime on 2012-12-02
It's a negative.
I installed a fresh 12.10(64), on a seperat partition, updated it and installed uitool-code. Rebooted it, and put it into suspend. I again had to remove the battery to wake it up.
What should uicode-tool have done?

---

### Post by moteprime on 2012-12-06
Would it be possible to put the kernel in debug mode,to try to find out that's hanging?

---

### Post by moteprime on 2012-12-12
Hi, there.
I'm testing Raring for QA team, and reported a bug on launchpad:
[https://bugs.launchpad.net/bugs/1089339](https://bugs.launchpad.net/bugs/1089339)
If you can please help on it.

---

### Post by kharsha on 2012-12-14
I tested it in Quantal then i try only 64bit

---

### Post by ppq on 2012-12-14
I filed a bug, too, like penalvch recommended.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1090534](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1090534)

---

### Post by moteprime on 2012-12-15
Great. -I subscribed to it.

Why did he not want you to participate in the bug, but to report a new bug instead?

---

### Post by ppq on 2012-12-15
There's an important principle: One bug report per person, per device (laptop), per specific problem.
I forgot about that before posting to your bug :oops:

---

### Post by moteprime on 2012-12-15
I had to admit i did not know that.. :oops: shame here to.
But many times, lots of users with the same bug make lots of comments on a bug? And we have the same laptop with the same bug?
Aren't the new bug you reported just going to be mark as a duplicate?

---

### Post by ppq on 2012-12-15
Yes, but lots of duplicates are better than lots of comments. And it increases the chance that a developer will look at the problem ;)

---

### Post by moteprime on 2012-12-15
There's no arguing that. :-)
Thanks

---

### Post by ppq on 2012-12-24
Hey guys, ):P

After trying lots of distributions, releases, Live-CDs and so on, I'm more and more confused.
Back then, it worked with all these Live-CDs, now it does not. The *only* possible difference in the setup is something UEFI-related.
That's why I'm going to wipe everything again, re-flash the UEFI-BIOS, install Windows 7 (this strange implementation of UEFI firmware seems to be made **just** for Windows) and try to boot Ubuntu via EasyBCD again. 
( [http://www.servethehome.com/uefi-bootable-usb-drive-windows-8-windows-server-2012/](http://www.servethehome.com/uefi-bootable-usb-drive-windows-8-windows-server-2012/) )

I used this setup once and it is the only way to boot Ubuntu I didn't try since the suspend problem appeared. It's a pain in the ***, though.

Well, let's see :)

Merry Christmas!

---

### Post by ppq on 2012-12-24
Yep, it's UEFI.
**Suspend works in 13.04 daily live after installing Windows 7 in UEFI mode**
Thank you, Lenovo, for such a crappy netbook. ](*,)

---

### Post by moteprime on 2012-12-26
You did really figure it out? :o
Sorry i have not replied sooner, but all this Christmas stuff you know..
So what do i have to do to get it to work??
here's my setup: [http://paste.ubuntu.com/1466625/](http://paste.ubuntu.com/1466625/)

I can't believe it, your a hero.

---

### Post by ppq on 2012-12-26
Hi moteprime,
I did the following:

**1** install Windows 7 in UEFI mode:
**1.1** You need to manipulate a Windows 7 DVD for that. You probably want the Danish version: [Windows 7 SP1 media refresh x64 Danish]("http://msft.digitalrivercontent.net/win/X17-24277.iso") ([other languages]("http://www.mostiwant.com/blog/download-windows-7-sp1-integrated-dvd-iso-official-direct-download-links/"))
**1.2** Grab a 4 GB USB key, create a single FAT32 partition on it and set the boot flag on this partition (this actually shouldn't be necessary, but the S205 wont boot it without)
**1.3** Open the Windows 7 ISO file with Ark, File-Roller or another archive manager (or just loop-mount it) and copy all the contents to your USB key
**1.4** Copy the "boot" directory into the "efi" directory (copy it, don not move it!)
**1.5** Go inside the directory "sources" and open the file "install.wim" with File-Roller or another archive manager (p7zip has to be installed!)
**1.6** *Inside* this archive, navigate to 1/windows/boot/efi. There is a file "bootmgfw.efi". Via Drah&Drop, extract this file (and only this!) into efi/boot/ on the USB key and rename it to "bootx64.efi". Your Windows 7 UEFI USB key is now ready to boot :)
**1.7** Start the S205 and immediately press Fn+F11 to get into the boot menu. Choose your USB key to boot from. Windows Setup will start.
**1.8** In the Windows installer, delete all partitions on your hard drive. (You should have made backups by now ;) ) Create one new partition. Windows will ask to create another "system partition". After that, press Shrift+F10 to open up a console. Type "diskpart" and "list disk". Check if there's a * in the column "GPT", there should be one. If not, something went wrong.
**1.9** Install Windows. After that, check if you can suspend using a Ubuntu Live CD, it should work.
**2** Install Ubuntu (or Xubuntu, Kubuntu, ...). 
**2.1** During the installation, select manual partitioning. Shrink the Windows partition to a minimum of 16 or 20 GB or so, create a swap partition (size of your RAM) and an ext4 partition (mark for use as / ). **Mark the small vfat partition for use as the UEFI system partition, do not format it.**
**2.2** Install Ubuntu. You won't be able to boot it afterwards.
**2.3** Boot a Ubuntu Live CD again. Add ppa:yannubuntu/boot-repair, install boot-repair and run it. Select "Recommended repair". 

By now, Ubuntu should be able to boot. If you wish you can wipe Windows now (you don't have to, of course).

---

### Post by moteprime on 2012-12-27
OH, thank you for this extensive guide.
Before i do anything, i think that i need to understand what the problem is.
From what i can figure out it looks like it will work if windows are installed for working with uefi, and has a boot partition on a vfat?

---

### Post by belrik on 2012-12-28
I wonder, is there a quicker way to achieve this? Windows must be manipulating the EFI boot entries somehow so could we use efibootmgr to replicate that without installing Windows? 

Would it be possible for you to give us the result of "sudo efibootmgr -v" after Windows has "fixed" your EFI bios?

Then maybe we can just add the efi entry and make it work without needing to install Windows. From reading other forum posts we can see that the Ubuntu EFI entry must be moved down the boot order as booting with that instead of directly from the HDD device prevents the wifi from working (shows as hardware disabled) so perhaps the problems run deeper than just wifi. The ubuntu EFI boot entry would seem to be the root cause of a number of issues so suggest we look into that.

Thanks

---

### Post by moteprime on 2012-12-30
Hi again.
The guide did not work for me, and as Christopher on Launchpad sez, the hardware in our Ideapads are different. But thanks a lot for writing it.

Well, i had it with this crappy laptop. The hours i spend to get it to works in Ubuntu are a waste. It is only made for running windows, and that for somebody else than me.
I gave up, and went and got a e130 thinkpad. Everything works out of the box, except a couple of the function keys.
It's a bliss.

---

### Post by ppq on 2012-12-30
> **belrik said:**
> I wonder, is there a quicker way to achieve this? Windows must be manipulating the EFI boot entries somehow so could we use efibootmgr to replicate that without installing Windows? 

Would it be possible for you to give us the result of "sudo efibootmgr -v" after Windows has "fixed" your EFI bios?

Then maybe we can just add the efi entry and make it work without needing to install Windows. From reading other forum posts we can see that the Ubuntu EFI entry must be moved down the boot order as booting with that instead of directly from the HDD device prevents the wifi from working (shows as hardware disabled) so perhaps the problems run deeper than just wifi. The ubuntu EFI boot entry would seem to be the root cause of a number of issues so suggest we look into that.

Thanks

Hi,
when my laptop was in CSM compatibility mode, I was able to get some output from efibootmgr, but I was unable to create new entries. The commands were executed without errors, but when I would run efibootmgr again, nothing would be different.

This is the output now, while in UEFI mode:
```

bene@s205:~$ sudo efibootmgr -v
[sudo] password for bene: 
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0003,0002,0004,0005,0006
Boot0000  Setup    
Boot0001  Boot Menu    
Boot0002* USB FDD:    030a2400d23878bc820f604d8316c068ee79d25b6ff015a28830b543a8b8641009461e49
Boot0003* ATA HDD0: SAMSUNG 470 Series SSD                      ACPI(a0341d0,0)PCI(11,0)ATAPI(0,0,0)..bYVD.A...O.*..
Boot0004* USB HDD: SanDisk Cruzer Blade    ACPI(a0341d0,0)PCI(13,2)USB(1,0)3.!..3.G..A.....
Boot0005* USB CD:    030a2400d23878bc820f604d8316c068ee79d25b86701296aa5a7848b66cd49dd3ba6a55
Boot0006* PCI LAN: Realtek PXE B02 D00    BIOS(6,0,5265616c74656b20505845204230322044303000)..................@.......@...@.............................................A.....................
bene@s205:~$ sudo efibootmgr ## this looks exactly the same as before
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0003,0002,0004,0005,0006
Boot0000  Setup
Boot0001  Boot Menu
Boot0002* USB FDD:
Boot0003* ATA HDD0: SAMSUNG 470 Series SSD                  
Boot0004* USB HDD: SanDisk Cruzer Blade
Boot0005* USB CD:
Boot0006* PCI LAN: Realtek PXE B02 D00

```

Summary by boot-repair: [http://paste.ubuntu.com/1478637/](http://paste.ubuntu.com/1478637/)

Edit: One could try to set the laptop in UEFI mode by wiping the disk completely (dd if=/dev/zero to get rid of GPT traces), resetting the laptop a few times (no power, no battery, holding the power button for 30 sec) and booting a Ubuntu Live CD and checking if waking up from suspend works. 
Unfortunately I didn't try this before doing it my way (see previous post).
When it works one just needs to install Ubuntu while letting it create the vfat UEFI partition , and then use boot-repair to magically make it bootable.

---

### Post by belrik on 2013-01-04
I spent this evening trying to remove and then re-create the EFI partition. I started with using boot-repair with the EFI options enabled and then reformatted the EFI partition and re-created it from scratch. No difference.  I have a single /EFI/ubuntu/grubx64.efi file there and for some reason although that boots it behaves strangely and seems to break wifi.  Interestingly I noticed that I get different results if I choose "ubuntu" in the BIOS boot menu as opposed to setting it to default above the disk drive under boot options. For some reason doing that is invoking the boot in a different way and I see garbled text on the console but the wifi doesn't break. Suspend and shutdown are still broken whatever I do though, resulting in a hang.

I don't have a spare laptop so I can't wipe this to install Windows, will just have to wait until this is fixed upstream.

---

