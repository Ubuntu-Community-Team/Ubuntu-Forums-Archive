---
title: "Get Me Out Of WINDOWS!!!"
date: 2017-11-26
forum: General Help
---

### Post by Smallwheels on 2017-11-26
For two years I've been using a Chromebook. It is getting old so I got a new Acer A3 today with an Intel i3 chip. It's running Windows 10 and I hate it. It took over five hours just to complete its updates. Then I spent another five hours just trying to get rid of things and making a recovery drive. Which failed because the dumb OS wouldn't recognize the thumb drive. It knew it was there because it showed up in the drives section but just wouldn't allow me to utilize it. The recovery program said an 8 GB drive was needed (which I have). Once I got the stupid Windows software to recognize the external drive I ran the recovery program again. Now it's telling me I need a 16 GB drive for the recovery, WHICH I DON'T HAVE.  How do people live with Windows without throwing their machines against a wall and then stomping on them? 

I need some help.

I downloaded an ISO file. The torrents I tried haven't worked. So I downloaded it. Finding a burner that will transfer the file to an external thumb drive has been unsuccessful. Some of them don't say they can burn to a USB drive. Can somebody please recommend a free file burner for Windows 10 that will do this? 

Once I have one, how should it be done? Do I open the ISO file by extracting the files before burning them to the thumb drive or burn the file to the drive and extract them there? Do they even need extracting? 

Once I reach that step how do I do a checksum so I know the file hasn't been corrupted? Maybe that step needs to be done earlier. I need to know about that too.

Do I need to partition the thumb drive first? I don't know how to do that in Windows. I only have my Chromebook and such tools aren't available for it.

I'm not sure but so far this Acer A315-51 computer seems OK. Unfortunately the track pad is in the way of where my hand should rest on the left side. It has already made the cursor jump to elsewhere in the post and start messing up the other sentences. I can probably adjust to it. 

If you know of some solutions to this task please let me know. I really want to get out of Windows hell. I will dual boot the machine because I have a guitar amplifier that works with software that is not compatible with GNU/Linux. Thus Windows will stick around to work with that software. 

On Sunday I'll buy a bigger thumb drive for the Windows recovery files. Once that is done, with your help, I'll get GNU/Linux onto the machine. 

One more thing. Since this is a new machine are there special things that must be done to boot into a different drive? Years ago I read somewhere that Microsoft had done something to prevent other drives that weren't Windows from functioning as boot drives.

Thanks for all the help. 

Michael

---

### Post by howefield on 2017-11-26
I'd recommend Etcher from etcher.io for burning an iso to a flash drive. What iso file is it that you have downloaded ?

---

### Post by Smallwheels on 2017-11-26
I downloaded an Ubuntu 64bit file.

---

### Post by ubname on 2017-11-26
> **Smallwheels said:**
> I downloaded an Ubuntu 64bit file.

What have you downloaded 16.04 ?  17.10 ?

What system are you using now? the one you downloaded the iso with? (windows ?  chromeos?)

---

### Post by dragonfly41 on 2017-11-26
When I purchased a Dell tower PC recently I had to purchase a SanDisk 32GB flash drive for my Windows Recovery.   And it has to be dedicated to this purpose.   
But I do use Windows 10 + Ubuntu to test cross platform.   Updates do take a long time in Windows.

In addition to advice on UEFI in this Ubuntu forum read more here ...

[https://community.acer.com/en/discussion/526858/aspire-3-a315-31-coa7-bios-has-not-option-to-boot-using-usb](https://community.acer.com/en/discussion/526858/aspire-3-a315-31-coa7-bios-has-not-option-to-boot-using-usb)

and ensure that you downloaded the correct iso.

[Added note]
 You do realise that you need a *second* flash drive into which you will burn the Ubuntu iso?

---

### Post by oldfred on 2017-11-26
Since an UEFI system, you do not have to have an installer to create a bootable Ubuntu install flash drive.
       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[URL="http://ubuntuforums.org/showthread.php?t=2299040"]http://ubuntuforums.org/showthread.php?t=2299040

      [/URL]
 Most find this works, if you want an installer:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 


Acer (all models we have seen so far) is not as bad as some brands, but does have a unique requirement of setting an UEFI password and enabling trust on the Ubuntu/grub .efi boot file after you have installed. Otherwise it will not show ubuntu entry in UEFI boot options.

For more info on UEFI install see link in my signature.

      
 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[URL="https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757
[/URL]
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 

[URL="https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]
[/URL]

---

