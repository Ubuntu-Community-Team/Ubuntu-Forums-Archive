---
title: "How to create bootable USB from Ubuntu ISO image?"
date: 2021-03-01
forum: General Help
---

### Post by shaira24 on 2021-03-01
Hello, I’m a novice with Linux system, my HP laptop is running with Windows 10 OS and I’m trying to install debian to my HP laptop for dual boot. Then I downloaded Ubuntu’s ISO file from [_UBUNTU.COM&#8194;__4_]("http://ubuntu.com/") but it’s not booting, I used UNetbootin to create bootable usb drive with Unetbootin and i get " this is not a bootable disk. please insert a bootable disk or floppy " message. I don’t where is the problem!

---

### Post by oldfred on 2021-03-01
What model HP?

Newer UEFI system or older BIOS based system?
If UEFI have you updated UEFI and if SSD, updated firmware?
Made Windows repair recovery disk and have good backups?

If UEFI secure boot is on, and you did not make a Secure boot version, it will not be seen as bootable.
Many just download again and use either a different installer or differnt flash drive or both and then it works. Not sure why.

More info in link in my signature below.

Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) & 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) or 
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by C.S.Cameron on 2021-03-01
Rufus, Etcher, Ventoy, Universal and Win32DiskImager are worth trying if UNetbootin is not working. First check the ISO's MD5SUM to make sure it is not corrupt.

There are many reasons a Live USB may not be working, see: [https://askubuntu.com/questions/1190764/why-doesnt-a-bootable-usb-boot](https://askubuntu.com/questions/1190764/why-doesnt-a-bootable-usb-boot)

---

### Post by HermanAB on 2021-03-02
You don't really need fancy software to create a bootable USB widget - quite the contrary.  

The ISO file *is* a complete bootable file system.  All that you need to do, is copy it byte for byte, exactly as is, to a USB stick.  

Windows has a utility called 'rawrite' which can do that.

---

### Post by C.S.Cameron on 2021-03-02
Herman
I just gave rawwrite a try and it only wants to write .img files to floppy disks.
Etcher clones ISO files to USB okay and is as easy to use as rawwrite.
I recall extracting an ISO file to a FAT23 partition on USB boots with UEFI, (but not BIOS mode)..

---

### Post by HermanAB on 2021-03-02
Simple: Rename the file to .img

BTW, there seems to now be a zoo of different versions of rawrite.  The original came with Windows NT (that’s when I last used it!) Note the name had only one w in it.

---

### Post by C.S.Cameron on 2021-03-02
The version I tried asked for a floppy disk, it would take 2000 floppies to hold an Ubuntu ISO. give rawwrite a try. If it works please post a link.

---

