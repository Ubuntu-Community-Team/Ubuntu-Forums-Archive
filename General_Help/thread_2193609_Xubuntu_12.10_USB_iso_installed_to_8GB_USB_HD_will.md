---
title: "Xubuntu 12.10 USB iso installed to 8GB USB HD will not boot"
date: 2013-12-13
forum: General Help
---

### Post by tssmith11 on 2013-12-13
Before I start, I have read multiple posts on these forums and have not been able to solve this issue, everyone seems very helpful so I figured I'd try to get a faster resolution by posting my own thread.

I'll try to give as much info as possible. Please note that I am 100% new to linux/ubuntu/xubuntu and building computers, so hopefully this isn't too painful. I am already starting to learn some of the lingo but please be descriptive (thank you)

I am building a setup to run Xubuntu 12.10 with an MSI G Z77A-GD65 motherboard

I used Unetbootin on my macbook pro to mount the iso file to a Sandisc cruzr(?) 8GB USB drive

I got everything plugged into the motherboard including the Sandisc installation USB, an 8GB Emtec flash drive (to install to) and an ASUS wifi USB stick

on the first startup, I went into BIOS and made the change to boot from my Sandisc USB drive then rebooted and started installing. There was nothing on the 8GB Emtec drive to begin with and I had no problems installing. After a successful installation and reboot, I removed the ISO drive and tried booting from the Emtec USB, this was showing up as USB 2.0 PMAP. 

At this point I tried a lot of things, including re-installing, trying to boot UEFI vs legacy, checking all the different USB boot options, hitting F11 and booting straight from USB that way, etc. I ended up plugging the Emtec USB into my macbook pro to see if something was wrong with it. It didn't mount but I ran disk utility and saw that it was there, I saw 2 partitions I believe. One was fat32 and another was linux or something (I can't remember but I can check if its important). 

Now whenever I try to start up it either says insert boot media and press any key, or it goes straight into BIOS. When I have UEFI on and try to boot straight from the USB the screen goes black then goes back into BIOS. 

I tried installing boot repair (with the iso usb in and hitting 'try xubuntu') I was able to succesfully install boot repair but then could not figure out how to run it. Now I am just helpless and not sure at all what to do.

Any help is greatly appreciated! Please let me know if you need any more information, and I'll be happy to get it as quickly as possible. 
Thank you

---

### Post by tssmith11 on 2013-12-13
Maybe I missed something in the whole, install Xubuntu to a USB flash drive, should this be complicated? Now I'm reading about a persistent live system, would this be better for me?

---

### Post by oldfred on 2013-12-14
Your 8GB is not large but should work.
If you had a FAT32 partition as the first partition, then that would be a UEFI install with gpt partitioning. If you have a bios_grub partition that would be a BIOS boot install on gpt partitioned drive. And neither would be a BIOS boot install on MBR partitioning.

But black screen after install is usually a video issue or other boot parameter needed. Since it is one install, you do not see a grub menu and it just continues to boot, but then if correct driver not available or driver needs a boot parameter it may fail.
What video card/chip are you using. Often nomodeset works, but Intel usually needs different parameters.
Since only one system, you may need to hold shift key from UEFI/BIOS boot until menu appears. Some with UEFI have to use escape key instead.
Also some settings in UEFI/BIOS make a big difference.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)


 Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
Editing the GRUB 2 Menu During Boot
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

   [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

