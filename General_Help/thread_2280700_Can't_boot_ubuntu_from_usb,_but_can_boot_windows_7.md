---
title: "Can't boot ubuntu from usb, but can boot windows 7"
date: 2015-06-01
forum: General Help
---

### Post by heiNey on 2015-06-01
I'm not sure what the issue I'm having is, but it's very strange to me.

I am not able to boot from usb regardless of how I make the image.  I have tried LiLi, Unetbootin, Win32diskimager.  I have tried ubuntu 14.04, linux mint, etc. The screen just sits at verifying DMI pool data.

however, if i follow this guide here: [http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/) , I am able to use the SAME usb stick, and it will boot from the usb and install windows 7 no problem.  

anyone know what is going on?  it seems like im missing a boot manager maybe?  but it doesnt make sense how all of the isos and methods ive tried are giving me the same problem.

this is not the first time i've made bootable usbs, and i have never had a problem until now.

---

### Post by heiNey on 2015-06-02
bump.

help please?

---

### Post by kagashe on 2015-06-02
Although you might have made bootable usb before you may not have used it on UEFI machine. For making UEFI bootable usb the conventional methods may fail but a very simple method works. Just extract the ISO using 7-zip and copy it to FAT32 formatted usb stick. So simple.

---

### Post by heiNey on 2015-06-02
> **kagashe said:**
> Although you might have made bootable usb before you may not have used it on UEFI machine. For making UEFI bootable usb the conventional methods may fail but a very simple method works. Just extract the ISO using 7-zip and copy it to FAT32 formatted usb stick. So simple.

well, the weird part is i've done this on this particular computer several times, and it's not working this time.  i'll give the UEFI bootable usb a shot tomorrow.

---

### Post by sudodus on 2015-06-02
The Ubuntu 14.04.2 LTS desktop 64-bit iso file boots in UEFI as well as in BIOS mode simply cloned to a USB pendrive (without extraction). You can use Win32DiskImager or mkusb. Or you can use a tool that extracts it to a FAT32 file system (or do it manually as described by kagashe).

But first make sure that your iso file was downloaded successfully. Check the md5sum according to [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

or you can try it in another computer.

If the computer boots from a pendrive with Windows, it *should* boot from a pendrive with Ubuntu too. But some UEFI systems are tweaked beyond the UEFI standard in order to make it hard to boot anything but Windows. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

and it will be easier to give you relevant advice.

See also this link (and links from it, for example concerning UEFI) [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by heiNey on 2015-06-02
> **sudodus said:**
> The Ubuntu 14.04.2 LTS desktop 64-bit iso file boots in UEFI as well as in BIOS mode simply cloned to a USB pendrive (without extraction). You can use Win32DiskImager or mkusb. Or you can use a tool that extracts it to a FAT32 file system (or do it manually as described by kagashe).

But first make sure that your iso file was downloaded successfully. Check the md5sum according to [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

or you can try it in another computer.

If the computer boots from a pendrive with Windows, it *should* boot from a pendrive with Ubuntu too. But some UEFI systems are tweaked beyond the UEFI standard in order to make it hard to boot anything but Windows. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

and it will be easier to give you relevant advice.

See also this link (and links from it, for example concerning UEFI) [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

this is a computer i built myself, and it has worked before.  i'll try it manually and see if it works.

---

