---
title: "Installed ubuntu on a portable hard drive after a boot in windows now it won't boot"
date: 2014-04-17
forum: General Help
---

### Post by callum4 on 2014-04-17
[FONT=arial]I installed ubuntu on a portable hard drive and it was working fine but after a boot in windows now when I start the computer it boots straight into windows not grub I have a video of orca on ubuntu so I can't reinstall the system but can somebody help me of this issue.[/FONT]

---

### Post by oldfred on 2014-04-17
From a live installer DVD or flash drive run this. You can also download a full repair ISO.
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by callum4 on 2014-04-17
It won't delete anything will it because I did say I have a video of orca and I don't want to loose it.

---

### Post by oldfred on 2014-04-17
It should just run a report of what you have where.

---

### Post by callum4 on 2014-04-17
I can't add the ppa.

---

### Post by oldfred on 2014-04-17
What live installer are you using?

---

### Post by callum4 on 2014-04-18
Ubuntu of course.

---

### Post by sdowney717 on 2014-04-18
bootinfo does not work in Trusty.

It will but who knows when, today, tomorrow, next week?

---

### Post by mJayk on 2014-04-18
Dont you just need to point your computer to boot from the external USB HDD ?

---

### Post by sdowney717 on 2014-04-18
I hit F8 while bios boots, then can select my usb hard drive.

---

### Post by oldfred on 2014-04-18
Boot-Repair does not have a trusty ppa yet.

 ----------- WORKAROUND 1
+ You can download the DEBs packages here: [https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages)
+ First install the 'glade2script' DEB, then 'boot-sav', then 'boot-repair'.
+ 
+ ----------- WORKAROUND 2
+ Use Boot-Repair-Disk [https://sourceforge.net/p/boot-repair-cd/home](https://sourceforge.net/p/boot-repair-cd/home)

My work around in 14.04 was to do ppa, but then change the ppa entry in sources.

 gksudo gedit /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list
['http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages]("http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages")'
From trusty above to saucy below.
['http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/binary-amd64/Packages]("http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/binary-amd64/Packages")'

---

### Post by callum4 on 2014-04-18
I tried all that.

---

### Post by callum4 on 2014-04-18
And I didn't install trusty tahr I installed sauchy salamander.

---

### Post by oldfred on 2014-04-18
Did you do some maintenance in Windows and it turned secure boot or fast boot back on? If so you need to make sure they are off. Windows may keep turning them on.
Only systems that are installed in secure boot mode will be offered to boot from UEFI if secure boot mode is on.

Did you install Ubuntu in BIOS mode and turned UEFI mode back on in UEFI/BIOS? Mode has to be correct.
Check your UEFI/BIOS settings.

---

### Post by callum4 on 2014-04-18
But it will delete my windows drive's data.

---

### Post by oldfred on 2014-04-18
What will delete your Windows?
You are not helping us help you as we need more info to know what your issues or concerns are.

Always best to have a Windows repair flash drive and a full image backup of Windows.

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

    
       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by callum4 on 2014-04-19
I don't have a flash drive or a backup utility.

---

### Post by callum4 on 2014-04-23
Well are you going to help me.

---

### Post by oldfred on 2014-04-23
Running Boot-Repair would be much better so we could see what your issues are. Plus it can fix some issues with just a click.

But this script is the first part of the output from the Boot-Repair report. download script and run it. Instructions in links.

 Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/latest/download](http://sourceforge.net/projects/bootinfoscript/files/latest/download)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in advanced  edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by callum4 on 2014-04-24
I give up I will reinstall the system because the recorder I used kept on feezing.

---

