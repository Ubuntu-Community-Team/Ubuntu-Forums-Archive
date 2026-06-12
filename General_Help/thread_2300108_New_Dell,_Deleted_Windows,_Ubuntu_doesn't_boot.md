---
title: "New Dell, Deleted Windows, Ubuntu doesn't boot"
date: 2015-10-23
forum: General Help
---

### Post by pedro_miguel on 2015-10-23
Hi guys,

I've just bought a new Dell xps 13 that came with Windows 10, however I wanted to install Ubuntu 10, so I created a bootable usb [following these instructions]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu").
I then restarted the Windows and clicked F12 to boot from the usb, so far so good, then using a ethernet usb adapter I selected to install all the updates while installing Ubuntu.

Now comes the fun, I thought that everything would go smoothly so in all my wisdom I decided to tick the option that said something like, Erase everything and install Ubuntu, and as you have guessed it this option deleted Windows (not that I am complaining). The Ubuntu installation did not took more than 5minutes and at the end I received a pop up message to restart and to start using Ubuntu, now once I restarted and removed the usb I received the following message:

```
No bootable devices found
Press F1 key to retry boot.
Press F2 key to reboot into setup.
Press F5 to run onboard diagnostics.
```

Can anyone help me understand what did I do wrong/what's wrong and what do I need to do to fix this and be able to run Ubuntu?
Please I'm a complete newbie when it comes to solving installation problems between Windows and Ubuntu.

Thanks in advanced.
Pedro

---

### Post by yancek on 2015-10-23
The link you posted is how to create a bootable flash drive from an already installed Ubuntu.  Did you use another computer with Ubuntu on it to create the flash drive?  Something went wrong if it only took 5 minutes to install.  Did you do an md5 checksum on the Ubuntu iso file after you downloaded to verify that it was a good download?  Do you have another computer to use to re-create the bootable Ubuntu iso?  Try using pendrivelinux if it is a windows computer or unetbootin.  Either should work.

---

### Post by ajgreeny on 2015-10-23
> I've just bought a new Dell xps 13 that came with Windows 10, however I wanted to install Ubuntu 10, so I created a bootable usb following these instructions.
Do you really mean Ubuntu 10?  If so you will have to change from UEFI and boot the machine in CSM or legacy BIOS mode as Ubuntu 10 will not work on UEFI.

But why Ubuntu 10?  It lost support a long time ago and will get no more updates so I recommend 14.04, supported till 2019 and will work on UEFI.

---

### Post by pedro_miguel on 2015-10-23
Sorry ajgreeny, its a typo, I meant Ubuntu 15.04

---

### Post by pedro_miguel on 2015-10-23
Hi yancek, thanks for your reply. Yes I did use another laptop which has Ubuntu 14.04 to create the flash drive. How can I do a md5 checksum on the Ubuntu iso file?

---

### Post by Dennis N on 2015-10-23
Possibly you installed in Legacy (BIOS) mode, and the boot loader was installed to a partition. Then you would get this kind of error. Boot loader installation on a first install should be directed to the disk, like sda, rather than the partition the OS was installed on, like sda1.

Edit: Rereading post #1: as you used "Erase disk and Install Ubuntu" option (I had somehow thought otherwise) your boot loader should be in the right location since the installer controls this operation and knows where it should go.

---

### Post by grahammechanical on 2015-10-23
May I suggest that you restart the computer with the USB stick plugged in? Does that load into Ubuntu? Is it Ubuntu on the hard disk? Or is it the Ubuntu Try/Install session that loads?

This will determine if Ubuntu has installed to the hard disk and confirm that the Ubuntu boot loader (Grub) has installed to the USB stick and not the hard disk.

If you are loading into a Ubuntu installation on the hard disk then open a terminal and run these commands

```
sudo grub-install /dev/sda
sudo update-grub
```

Regards.

---

### Post by pedro_miguel on 2015-10-23
Hi grahammechanical, yes I did as you suggested and no, it does not load Ubuntu installation, instead it presents me with the options: 

Try ubuntu without installing, 
Install Ubuntu, 
OEM Install (for manufacturers), 
Check disc for defects

and if i restart without the usb drive i just get:

No bootable devices found
Press F1 key to retry boot.
Press F2 key to reboot into setup.
Press F5 to run onboard diagnostics.

---

### Post by pedro_miguel on 2015-10-23
> **yancek said:**
> The link you posted is how to create a bootable flash drive from an already installed Ubuntu.  Did you use another computer with Ubuntu on it to create the flash drive?  Something went wrong if it only took 5 minutes to install.  Did you do an md5 checksum on the Ubuntu iso file after you downloaded to verify that it was a good download?  Do you have another computer to use to re-create the bootable Ubuntu iso?  Try using pendrivelinux if it is a windows computer or unetbootin.  Either should work.


Hi yancek, just googled how to do a md5 checksum and the iso file seems to be correct, here is the output:

```
pedro@pedro:~/Downloads$ md5sum ubuntu-14.04.3-desktop-amd64.iso cab6dd5ee6d649ed1b24e807c877c0ae  ubuntu-14.04.3-desktop-amd64.iso
pedro@pedro:~/Downloads$ md5sum -c MD5SUMS 
ubuntu-14.04.3-desktop-amd64.iso: OK
md5sum: ubuntu-14.04.3-desktop-i386.iso: No such file or directory
ubuntu-14.04.3-desktop-i386.iso: FAILED open or read
md5sum: ubuntu-14.04.3-server-amd64.iso: No such file or directory
ubuntu-14.04.3-server-amd64.iso: FAILED open or read
md5sum: ubuntu-14.04.3-server-i386.iso: No such file or directory
ubuntu-14.04.3-server-i386.iso: FAILED open or read
md5sum: wubi.exe: No such file or directory
wubi.exe: FAILED open or read
md5sum: WARNING: 4 listed files could not be read
```

---

### Post by Sweet_Baby_Jamie on 2015-10-23
Boot from the USB stick, reinstall Ubuntu to your hard drive from the USB disk and make sure the bootloader is installed to the hard disk (sda).  That should do it!

---

### Post by pedro_miguel on 2015-10-23
> **Sweet_Baby_Jamie said:**
> Boot from the USB stick, reinstall Ubuntu to your hard drive from the USB disk and make sure the bootloader is installed to the hard disk (sda).  That should do it!

Hi sweet_baby_jamie, care to elaborate a bit more? I'm new when it comes to Ubuntu installations...How can reinstall Ubuntu to my hard drive? Is this just the case of selecting the option "Erase disk and install Ubuntu"? 

How can I make sure bootloader is installed in the hard disk (sda)?

Any detailed instructions would be very very welcome.

Regards

---

### Post by Dennis N on 2015-10-23
If you use "erase disk and install Ubuntu", the installer will put the bootloader in the right place. It's when you use the "Something Else" option that you have to choose where it's installed.

---

### Post by Sweet_Baby_Jamie on 2015-10-23
Since you already chose "erase disk and install Ubuntu" without success, you can choose "Something else" and make sure that the bootloader is installed to the hard drive.  I always choose to partition my hard drive like this: 

Twice my computer's RAM capacity as "**linux swap**,"
About 1/3 of the drive (at least 20 GB, which is way more than enough) as "**/**"
And the rest as "**/home**".  Format all the partitions this time, and next time you can UN-CHECK the format option for the /home partition.

This makes reinstalling at upgrade time super easy and preserves my school work, photos, music and stuff.  Even bookmarks and settings are saved!

The bootloader ordinarily goes in the "/" partition but you can let the installer put it wherever - as long as it's ON THE HARD DRIVE somewhere.

---

### Post by sudodus on 2015-10-24
The bootloader should be installed to the head (beginning) of the drive, often the first drive **/dev/sda**
(Do not install it to a partition, so no partition number.)

-o-

If you have Windows in the first drive /dev/sda and want to install Ubuntu to a second drive (maybe external and portable), you would install the bootloader to the head of that drive, **/dev/sdb**

In that case you have to select drive to boot from.

---

### Post by Sweet_Baby_Jamie on 2015-10-24
Yes.  Sudodus is right.  Thanks for the correction!

---

### Post by yancek on 2015-10-24
If you select the "Something Else" option during the installation, you will get an Installation Type window and near the bottom left there is a "Device for bootloader installation" which defaults to /dev/sda.  Check that it is correct before clicking on Install Now.

---

