---
title: "grub rescue problem"
date: 2017-08-11
forum: General Help
---

### Post by joe203 on 2017-08-11
For several months I have had a fully functional dual-boot system - Ubuntu 16.04 & Win10 Pro. After the last Win10 update 2 days ago, I am unable to boot the machine. Fails with an error: file '/boot/grub/i386-pc/normal.mod not found & displays grub rescue>

Have attempted various repairs:

1. ls, set prefix=....., insmod normal
2. boot-repair - the graphical way with recommended repair. This created a paste.ubuntu.com/2529234 url.
3. Read the thread started by n2222 & followed the steps described by oldFred.

The machine will boot using Ubuntu CD & if I click Files, I see a 109GB volume with numerous folders such as boot, bootinfo, boot-sav, along with numerous Win10 folders. I also see Computer which shows bin, boot, cdrom, dev, etc, home, lib ................

Thus I believe the disk is functional which is a question oldFred asked in the previous mention thread.

At this point, I am at a complete loss on what to try next - short of reformatting the disk & starting over which I would prefer NOT to do.

Any help will be much appreciated. Tnx  Joe

---

### Post by oldfred on 2017-08-11
Full link:
[https://paste2.org/Xy23L9BV](https://paste2.org/Xy23L9BV)

You have an HP which can make it a bit more difficult.
You also show Ubuntu, Mint & Kali.
The error on normal not found is something related to grub versions, often trying to boot an UEFI install with a BIOS version of grub in MBR. 
But you do not show any grub in MBR. 
But since you only have one /EFI/ubuntu, no Mint nor Kali UEFI entries, do they also use /EFI/ubuntu for UEFI boot? I do not know Mint nor Kali. But their version of grub may be enough different that it is causing the issue.

Boot-Repair seems to have picked a Mint install in sda13 as one to auto fix. Better to use Advanced mode an choose Ubuntu in sda11 to reinstall grub. Also check the option 'use standard EFI file' .

Ignore the far from start of drive warning from Boot-Repair, I have yet to see that as an issue on any UEFI system. It can be an issue with older BIOS boot systems with drives in IDE mode, not AHCI mode.

Is secure boot off?
Are drives set for AHCI in UEFI.
Can from your one time boot key, boot either ubuntu entries, one is shim & other is grub.

 escape + F9 for boot menu, F10 for bios setup
[http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453](http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453)
[URL="http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook"]http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook
[/URL] 
This is what Boot-Repair's use standard file copy does.
HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by joe203 on 2017-08-12
I'm not sure how HP got into the mix - the machine is a Dell M4700 notebook. Mint & Kali are also mysteries - the boot DVD is the one supplied with the Ubuntu Book 2016 edition covering 15.10 and 16.04. I have never played with Mint or Kali at any time.

Is it possible I wrote down the wrong 'paste url' -- what I thought I created was numbered 25292234. Should I run Boot Repair again & create a new url?

---

### Post by oldfred on 2017-08-12
Yes create new Boot info report and post full link.

---

### Post by joe203 on 2017-08-12
Ran boot-repair again -- [http://paste.ubuntu.com/25297291](http://paste.ubuntu.com/25297291)

---

### Post by oldfred on 2017-08-12
You must have done a major Windows update.
Windows since about Windows 7 and continuing with Windows 10 has a bug (feature?) where on update & rewriting partition table forget to include the Linux partition(s).

 ```
/dev/sda3         317,939,710   625,139,711   307,200,002   f W95 Extended (LBA)
/dev/sda5         553,459,712   625,139,711    71,680,000  82 Linux swap / Solaris
``` 

Note large gap from start of extended partition to start of swap. That probably was ext4 and sda5, with swap as sda6. Renumbering is not critical as Ubuntu uses UUID.
You can use testdisk or parted rescue to restore partition(s). If just one partition, parted rescue may be easier as start of extended & start of swap in sectors is where old partition was.
You may have to reinstall grub after recovery of missing partition. 
And with Windows 10 make sure fast start up is off. Windows on update will turn that back on, and install its boot loader back into MBR. So always have Ubuntu live installer handy. 

      
 backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print 

These are all essential either parted rescue or testdisk threads on similar recovery.

 [http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

### Post by joe203 on 2017-08-12
Thanks for all the info - Yes, the machine originally had Win7, was upgraded to Win10, and then Ubuntu 16.04 was added several months ago.

I will go thru the links you provided & see if I can recover. Will post again after that. Thanks again.

---

### Post by joe203 on 2017-08-13
Success - used parted & was able to recover ext4 as sda6. Ran boot-repair & now the machine will dual-boot. A minor problem with some old Ubuntu directories that appear within the Win10 file system, but no big deal.

Thanks for all your help oldfred.

---

### Post by oldfred on 2017-08-13
Glad it is working. :)

Be sure to have good backups.
Best to have Windows repair flash drive & Ubuntu live installer handy at all times.
Windows will most likely reset itself into MBR and turn fast start up on, with major updates. And may lose Linux partition, but that seems more common with the full reinstall or update of versions.

---

