---
title: "How to boot from CD? (Asus X541NA)"
date: 2017-12-24
forum: General Help
---

### Post by anon3140 on 2017-12-24
I am trying to boot from CD or USB on an Asus X541NA laptop. In the boot options, the only option is to boot into Windows. I have already disabled Secure Boot and Fast Boot.  I do not know if it is UEFI or BIOS . I would assume UEFI because it's a new computer, but the BIOS/UEFI menu refers to itself as 'BIOS Utility' and the Main menu refers to 'BIOS Information' and 'BIOS Vendor'. The version is 314, vendor is America Megatrends, GOP version is 10.0.1036 (not sure if any of that is relevant). I do not see any option for Legacy or CSM, or to switch between UEFI and BIOS/Legacy.
In the boot menu, the priorities list only has Windows as an option. I do have the option to 'add new boot option'. When trying to add a boot option, I have to select path for boot option. When selecting a path for the boot option, I am first asked to select a file system. I only have one option which is PCI(12|0)\DevicePath(Type 3, SubType 12)HD(Part1.Sig44fa2e2a-a76b-478e-863a-a9675829c331). I am forced to select this as it is the only option. After selecting  it, I am asked to select a file to boot. My only option is <EFI>. Within <EFI> I can choose either <Microsoft> or <Boot>. Within <Boot> my only option is bootx64.efi. Within <Microsoft> I can select <Boot> or <Recovery>. Within <Recovery> there is no option. Within <Boot> I have languages to choose from. When selecting one (<en-US> for example) I then have no options. So ultimately out of all the options, all I can do is <EFI><Boot>bootx64.efi. I tried creating a new boot option with bootx64.efi but that doesn't change anything, I still can't boot from CD or USB.
I also tried restarting my computer with a live CD in the CD drive and a live flash drive in a USB port, and they still don't show up as boot options.
I apologize if some of the information I posted is irrelevant, or if there is anything I left out that I should have included.
I don't care about installing an operating system, I only want to be able to boot from a live CD and/or live flash drive.
What should I try next?
Thanks.

---

### Post by speartip on 2017-12-25
Looking at this, you need to reboot your laptop with CD or USB inserted, then keep pressing the ESC button as it restarts, until the boot menu is displayed.
[https://trickiknow.com/how-to-boot-asus-laptop-from-usb-install-windows/](https://trickiknow.com/how-to-boot-asus-laptop-from-usb-install-windows/)

---

### Post by anon3140 on 2017-12-25
> **speartip said:**
> Looking at this, you need to reboot your laptop with CD or USB inserted, then keep pressing the ESC button as it restarts, until the boot menu is displayed.
[https://trickiknow.com/how-to-boot-asus-laptop-from-usb-install-windows/](https://trickiknow.com/how-to-boot-asus-laptop-from-usb-install-windows/)

Thanks for the reply. I tried that, and it did take me to a boot menu, but the only options are the default Windows option, the test boot option I created (which also boots into Windows), and enter setup. Enter setup just takes me to the BIOS settings that I've already looked around in.

So unfortunately no progress there.

---

### Post by leunam12 on 2017-12-26
Do you have a bootable USB or CD? Dragging and dropping the ISO into the USB drive doesn't make it bootable. You have to use program such as RUFUS or Unetboting to "burn" the ISO to the USB drive. If you do have a bootable device then, try this: Boot into Windows and then click "Restart" while holding the Shift key. Keep holding shift until a blue screen appears and see if the option to use a USB device is there.

---

