---
title: "Another problem installing ubuntu"
date: 2020-01-12
forum: General Help
---

### Post by Tom_Carr on 2020-01-12
I am trying to install ubuntu on a dell laptop.  This is a different computer than the one in another thread where I could not get into  the bios.

On this laptop, I can get into the bios just fine.  I want to make the  computer boot from the  DVD.  I go to Boot / boot option priorities.  I want to set option 1 to read from the DVD but it only gives me 3 options:  

Windows boot manager
Onboard NIC (ipv4)
Onboard NIC (ipv6)

I go to "File Browser Add Boot Option", and select "ATAPI PLDS DVD +/- RW"  but  it doesn't add another option.

Boot list option is set to UEFI.

What  am I doing wrong?

---

### Post by CelticWarrior on 2020-01-12
You should be using a USB, not a DVD.

And you need to understand UEFI. Where those options appears is NOT where you should be selecting the boot from external media.

---

### Post by Tom_Carr on 2020-01-12
I don't know anything about UEFI. I am not a computer professional. I just use ubuntu on the desktop for my own home use. Has it gotten more complex? A DVD worked fine when I installed it on another Dell two years ago.

---

### Post by Tom_Carr on 2020-01-12
[COLOR=#000000] "Where those options appears is NOT where you should be selecting the boot from external media."[/COLOR]

Where should I be selecting them?

---

### Post by CelticWarrior on 2020-01-12
Saying it bluntly, you're missing some 20 years of knowledge updates. And for more than a decade now, computers don't have BIOS, they have UEFI. Unfortunately many manufacturers keep naming the firmware as "BIOS" or "UEFI BIOS" but actually the only proper naming convention is "UEFI", the thing that replaced the 40-something years old BIOS technology.

There are a few difference particularly regarding the requirements for OSes - Windows strictly forces installation in the recommended UEFI mode in GPT drives and Legacy mode ("BIOS") in MBR ("msdos") drives. Also differences where the bootloaders are installed now, the ESP (EFI System Partition), and not in the MBR like in the old days and, of course, only one bootloader could be installed in the MBR.

Also, the firmware usually has a "boot override" feature that is what we use to boot external media (not really a new feature but more important then ever). Usually but not necessarily the boot options appear in the rightmost menu, the same one where - again, usually but not necessarily - the "save changes and reboot" options are.

Also relevant in some systems and/or if specific drivers or software that install drivers (Virtualbox) are to be used is the new UEFI-only Secure Boot feature that you may need to disable. Again, this is somewhere in firmware (UEFI) settings.

---

### Post by Tom_Carr on 2020-01-12
I'm 70  years old and I have some memory problems.  I know that at some point I will not be able to keep up with the tech, but I want to try to keep up as long as I can.  Last time I installed ubuntu  was 18.04 about a year and a half ago.  At that time I just burnt the DVD, put it in the computer drive, turned on the computer and followed the prompts on the screen.  It was easy.  On one computer I had to go into the bios and change it so it booted from the DVD, but it was easy to change the bios.

Reading over what you wrote, I may not follow everything you said, but I don't see that it tells me how to get this particular computer to boot from the DVD.

But thanks for trying to help.

---

### Post by dragonfly41 on 2020-01-12
What laptop and version of Windows? Is it Windows 10?

Try following a tutorial such as here.

[https://www.intowindows.com/how-to-create-windows-10-bootable-dvd/](https://www.intowindows.com/how-to-create-windows-10-bootable-dvd/)

You will need to download the [Ubuntu desktop iso file]("https://ubuntu.com/download/desktop").

---

### Post by Impavidus on 2020-01-12
DVDs are a bit old-fashioned and slow, but should still work – at least, if your computer has a working dvd drive. Those are getting rare. On the other hand, there are still old computers in use that can't boot from usb and need that dvd.

Uefi is the replacement for bios. Although uefi has existed for a bit longer, the great majority of computers remained in legacy mode (which emulates bios) until Microsoft demanded a switch to uefi for preinstalled Windows 8 systems in 2012. Many computers are older than that and changing is a bit hard without wiping all your existing systems, so I expect bios will stay with us until all computers from before 2013 have died of old age.

Can you read the dvd when running Windows? If not, you may have a bad burn or a faulty dvd drive.

---

### Post by Tom_Carr on 2020-01-12
> **Impavidus said:**
>  
 
Can you read the dvd when running Windows? If not, you may have a bad burn or a faulty dvd drive.

Yes, I can read the DVD

---

### Post by Tom_Carr on 2020-01-12
> **dragonfly41 said:**
> What laptop and version of Windows? Is it Windows 10?

 

Dell laptop.  Windows 10.

---

### Post by Tom_Carr on 2020-01-12
The big problem remains changing the boot sequence so it will boot from the DVD.

If you boot from a usb drive, don't you still have to change the boot sequence?

---

### Post by Dennis N on 2020-01-12
> **Tom_Carr said:**
> The big problem remains changing the boot sequence so it will boot from the DVD. If you boot from a usb drive, don't you still have to change the boot sequence?
It's not usually necessary to change anything in the BIOS. Did anyone mention the one-time boot menu? On my Dell, just press F12 when booting starts to interrupt the booting and get that menu. See image attached. I press F12 repeatedly to be sure the keypress is recognized - otherwise, it continues to boot.

DVD option is in there as well as USB.

---

### Post by rsteinmetz70112 on 2020-01-13
> **Tom_Carr said:**
> Dell laptop.  Windows 10.

Model Number?

DVDs should work just fine. I sometimes even use a USB DVD

---

### Post by Tom_Carr on 2020-01-14
> **Dennis N said:**
> It's not usually necessary to change anything in the BIOS. Did anyone mention the one-time boot menu? On my Dell, just press F12 when booting starts to interrupt the booting and get that menu. See image attached. I press F12 repeatedly to be sure the keypress is recognized - otherwise, it continues to boot.

DVD option is in there as well as USB.

I tried F12 and it brings up a boot menu different than the one you show.  How do I take a screen shot of the boot menu and then move it up here to show you?

---

### Post by oldfred on 2020-01-14
My UEFI Dell does not have screen shots. My Asus desktop does let me take screenshots inside UEFI and save to a FAT32 partition.
For my other systems I just take a photo, shrink it as most camera now use have too large of a photo. Extra resolution not required and makes photo too large to upload.

You use Forum's advanced editor and click on the paperclip icon to add screenshots or smaller photos.
 Post #4 1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

I am a bit older and have to keep notes.

Did you copy ISO or install ISO to DVD. You cannot just copy an ISO as that is not normally directly bootable.
I used to use DVDs, but burned a lot of coasters (bad burns).  Flash drives can be reusable, although best to always have one live installer of current version as repair disk.

Also link on how to create a  bootable DVD or USB flash drive, using Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Dell typically requires drives setting in UEFI changed from RAID/Intel RST to AHCI.
Dell also requires UEFI update and if SSD, SSD firmware update.
How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

---

