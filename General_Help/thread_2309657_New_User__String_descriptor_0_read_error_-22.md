---
title: "New User*  String descriptor 0 read error: -22"
date: 2016-01-12
forum: General Help
---

### Post by TM_ on 2016-01-12
Hello there,

I seem to get this error "String descriptor 0 read error: -22" (with more lines after that, refer to image down below) after selecting Ubuntu 14.04 from grub and then loading into ubuntu(it displays a black screen then loads ubuntu normally). I believe i got this error right after updated my graphics driver with NVIDIA following the instructions from here: 

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Ubuntu_14.04_and_up](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Ubuntu_14.04_and_up)

Can anyone tell me if this is serious and what is it?

I found this thread which had a similar issue (  [http://ubuntuforums.org/showthread.php?t=2247230](http://ubuntuforums.org/showthread.php?t=2247230)  ) but since i got some extra lines of errors occurring, i thought i would ask the community.

For more info i ran lsusb-t and this is the output


/:  Bus 06.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
        |__ Port 5: Dev 3, If 0, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 5: Dev 3, If 1, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 5: Dev 3, If 2, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 6: Dev 4, If 0, Class=Vendor Specific Class, Driver=xpad, 12M
        |__ Port 6: Dev 4, If 1, Class=Vendor Specific Class, Driver=, 12M
        |__ Port 6: Dev 4, If 2, Class=Vendor Specific Class, Driver=, 12M
        |__ Port 6: Dev 4, If 3, Class=Vendor Specific Class, Driver=, 12M
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M
        |__ Port 1: Dev 3, If 0, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 1: Dev 3, If 1, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 1: Dev 3, If 2, Class=Human Interface Device, Driver=usbhid, 12M
        |__ Port 3: Dev 4, If 0, Class=Wireless, Driver=btusb, 12M
        |__ Port 3: Dev 4, If 1, Class=Wireless, Driver=btusb, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/2p, 480M
    |__ Port 2: Dev 2, If 0, Class=Mass Storage, Driver=usb-storage, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 480M

I also got an image extra lines of errors:

[ATTACH=CONFIG]266678[/ATTACH]

Thanks

---

### Post by TM_ on 2016-01-13
Anyone got any ideas?

---

