---
title: "turn bios files into img"
date: 2024-04-18
forum: General Help
---

### Post by ubto66 on 2024-04-18
[https://www.bios-mods.com/forum/showthread.php?pid=141098#pid141098](https://www.bios-mods.com/forum/showthread.php?pid=141098#pid141098)
[https://files.catbox.moe/9dt19z.7z](https://files.catbox.moe/9dt19z.7z)

Picture of files in folder named
Lenovo X220 v1.46 Modified Bios (no whitelist only)
[https://privatebin.piquark6046.dev/?c6a054392e742e27#6LZkUyf7zdeyTfPtjSRs1g8tiPVm2tk82dKUiCM3Cjrj](https://privatebin.piquark6046.dev/?c6a054392e742e27#6LZkUyf7zdeyTfPtjSRs1g8tiPVm2tk82dKUiCM3Cjrj)

can you tell how to turn the bios files into an img file. Such
that the img can get flashed onto an usb stick. Creating
an usb stick which will when connected to the lenovo x220i
boot and flash the new bios onto the computer?
Thanks.

---

### Post by Rubi1200 on 2024-04-20
It's not clear to me what you are hoping to achieve here.

Flashing the BIOS is not without risks; do you have solid backups?

What is currently installed and what are you wanting to do?

---

### Post by ubto66 on 2024-04-20
> It's not clear to me what you are hoping to achieve here.

the notebook in question runs bios version 1.31. Newest available bios version is 1.46. I want to
flash the bios version 1.46 onto the notebook.

The common bios version 1.46 which lenovo provides has a pci wifi card white list. And the pci wifi card
I want to mount onto the notebook is not on the list.

[https://files.catbox.moe/9dt19z.7z](https://files.catbox.moe/9dt19z.7z)
A person has made his own bios 1.46 version. His version removes the pci wifi card white list. I want
to flash his bios version 1.46 onto the notebook. I do not know how to.
On the picture you see the files of the bios 1.46 version which has no pci wifi card white list. My
understanding is that bios has to be flashed onto the notebook from within a windows system running on
the notebook. I have deleted the windows system from the notebook and the notebook
is running a gnulinux system like ubuntu.

Do you know how I can flash the bios 1.46 no white list version onto the notebook?

One option would be to make an img file version of the bios. Burn it onto an usb stick. Connecting the
usb stick to the lenovo x220i the notebook would boot the img from the usb stick and flash
the bios onto the notebook. That way no windows system would be required flashing the new
bios version on the notebook.

> Flashing the BIOS is not without risks; do you have solid backups?

I am considering the notebook written off. If it bricks it bricks. Should you flash your computer with
bios software made by an unknown person? No. But I want to get rid of
the pci wifi card white list. And this is the only option I know of.

---

### Post by him610 on 2024-04-20
I had to look it up to figure what it meant, "explain pci wifi card white list in ubuntu"
> A PCI WiFi card whitelist in Ubuntu prevents the use of an unsupported card. The ThinkPad BIOS, for example, only allows the system to boot with an authorized adapter installed. If an unsupported card is detected, the BIOS will stop the system and display a message on the screen. The card's sub-vendor PCI-ID is checked against a whitelist in the BIOS.

Did you ever consider why the vendor may have put your specific wifi card on white list?
Because bad things may happen, or not, or it may have only not been tested by Lenovo. 
It is a risk you are willing to take evidently.

Upgrading your Bios is not difficult, and you don't need Windows to do it. Well, maybe Lenovo needs it. :)

Then again, maybe the new version removes the suspect wifi card from the white list.

---

### Post by tea for one on 2024-04-20
Your question piqued my curiosity. 
A bit of free time today allowed a little experiment.
 
Here is my soupçon of absurdity:-

Download the zip file and extract it to your preferred location 
Open the folder Lenovo X220 v1.46 Modified Bios (no whitelist only)
Copy the contents (23 items) to a small USB stick (1GB) formatted fat32
Open Disks (gnome-disk-utility) > Select USB device > Drive Options > Create Disk Image
After a successful image is created, delete the contents of the USB device
Use your favourite utility to flash the img to a suitable usb device (I used dd to the same 1GB stick)

During this process, no errors were reported.
> **ubto66 said:**
> I am considering the notebook written off. If it bricks it bricks.
Regrettably, I cannot test the result but I’m happy to try if you send me the laptop ;)

---

### Post by him610 on 2024-04-20
> the pci wifi card
I want to mount onto the notebook is not on the list.
You should consider an intel wifi card, not a leading, bleeding edge one.  Maybe one from one or two generations earlier - better chance of compatibility with today's software.

Intel Linux wifi drivers are not an afterthought like some other manufacturers.

---

### Post by ubto66 on 2024-04-28
I created an img from an usb memory stick. Burned the img to an usb memory
stick using dd. No error messages. Connected the burned usb memory
stick to the thinkpad x220i. The notebook does not boot the img and it
does not work. I tested various settings in the notebook's bios
regarding booting. It did not work. Suggesting gnome disk utility is not how
you turn the bios files and folders into an img.

Can you specify which folders and files you
moved to the usb memory stick?

---

### Post by tea for one on 2024-04-28
> **ubto66 said:**
> The notebook does not boot the img and it
does not work.
I did mention that my suggestion contained an element of absurdity and it was untested.

Quite probably, the files "Lenovo X220 v1.46 Modified Bios (no whitelist only)" were simply not suitable.

If Lenovo advise that you can upgrade the firmware within Windows, then you can download a Windows iso (free of charge) 
and temporarily install Windows to perform this task.

---

