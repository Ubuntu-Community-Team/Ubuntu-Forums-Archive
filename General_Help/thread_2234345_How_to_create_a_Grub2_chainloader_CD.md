---
title: "How to create a Grub2 chainloader CD?"
date: 2014-07-14
forum: General Help
---

### Post by Neill_R on 2014-07-14
Hi

I am basically looking for someone to assist me in converting the article 

[https://help.ubuntu.com/community/BootFromUSB?action=recall&rev=46](https://help.ubuntu.com/community/BootFromUSB?action=recall&rev=46) 

so that it relates to GRUB2 and not GRUB.

What I am trying to do is create a CD that will ensure the divers for USB disk drivers are loaded and chain loads to my USB disk by search for a particular file. The MBR of that USB disk has a GRUB2 menu.

I do use 

# sudo mkisofs -R -b boot/grub/stage2_eltorito -no-emul-boot -boot-load-size 4 -boot-info-table -o UbuntuBootCDForUSB.iso iso/

but instead use

# sudo genisoimage -r -J -o UbuntuBootCDForUSB.iso iso/

but I need to create the /iso/boot/grub/grub.cfg file that does the chainloading **How to do this**?

Once this is done, one further requirement is to "umount" or mark as read only all internal hard drives. 
**What would be the best way to do this?**

---

### Post by yancek on 2014-07-14
> but I need to create the /iso/boot/grub/grub.cfg file that does the chainloading **How to do this**?

Manually in a text editor by modifying a current grub.cfg file to suit your needs.  Also, in the command to create the iso, you may need the eltorito.img file in the grub directory.

---

### Post by sudodus on 2014-07-14
Maybe these links can help you with chainloading.

[https://help.ubuntu.com/community/Installation/FromUSBStick#Chainloading](https://help.ubuntu.com/community/Installation/FromUSBStick#Chainloading)
[URL="http://ubuntuforums.org/showthread.php?t=2196858"]
Howto help USB boot drives[/URL]

By the way, cross-references might help people looking for help :-)

---

### Post by Neill_R on 2014-07-14
thanks for your replies unfortunately They do not solve my problem please refer to [https://help.ubuntu.com/community/Bo...=recall&rev=46]("https://help.ubuntu.com/community/BootFromUSB?action=recall&rev=46")    
I need and example in grub2 that will start Ubuntu kernel wait 15 seconds for the USB disks to initialise  and then search --file LID and set root to the device it finds and then boot to that device by chainloading But I don't full understand the command syntax. then i have to create the iso file that I can burn to produce the CD.  Then I want to close(umount) or set as read only any internal hard drives. so that the OS on the USB can not in anyway interfer with those internal disks

---

### Post by sudodus on 2014-07-14
Do you want to make a standard menuentry for grub2? Then you can simply check the file /boot/grub/grub.cfg in any installed current Ubuntu flavour. Or  check this link.

[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_USB_drives_with_grub2_and_iso_files_.27grub-n-iso.27](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_USB_drives_with_grub2_and_iso_files_.27grub-n-iso.27)

and the links from it for example

[booting with grub2]("https://help.ubuntu.com/community/Grub2/ISOBoot")

[link to Pendrivelinux]("http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/")

---

### Post by sudodus on 2014-07-14
See this link for grub commands

[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html)

[https://www.gnu.org/software/grub/manual/grub.html](https://www.gnu.org/software/grub/manual/grub.html)

---

### Post by oldfred on 2014-07-14
Is this a very old system that will not boot flash drive? My systems from about 2006 all boot flash drives, but that was about the time they added that capability.

Most use plop on CD to boot USB if no other way.
       Sometimes plop will work.
[http://www.plop.at/en/bootmanagers.html](http://www.plop.at/en/bootmanagers.html)

Or as some of the links you have used, you actually boot from CD with kernel on CD and have rest of system on flash drive. Never tried that so do not know details.

I do not think you can totally prevent access to hard drive. Anyone with physical access can get into system. But you can modify fstab to hide mounts and require system admin to use them.

---

### Post by Bucky Ball on 2014-07-14
*Thread moved to [I]**General Help***.[/I]

---

### Post by Neill_R on 2014-07-14
oldfred 

Thanks for the link Tons to read there it is going to take some time to sort that out. 

Just so I make myself clear I am trying to create a way to boot to an OS on a USB which has Grub2 installed on the MBR. The target system frame (PC) is completely unknown. If it has hard disks THEY MUST NOT BE TOUCHED. The Floppy or CDROM boot device must wait to ensure all the USB HDD have initialised and then determine by searching for a signature file set that as root and chain load to the MBR of the found device where the GRUB2 menuon the USB HDD will be activated and the user can choose from the available options. 

One other thing it was when I was try to create a VirtualBox guest OS I discovered it did not have the option to boot from a USB. if I solve this I will be able to screen capture my GRUB2 menu as my guest OS boots up.

search --file /LID 
get me hd0,msdos4 as the target root

this is because all internal HDD have been unplugged and my target USB is the only one plugged in

also this PC is new and recognises USB and in fact can boot from them. 

I am not clear on how i get from the search to setting the root and then chain-loading to the MBR of that device so that its Grub2 can take over.

any help here would be gratefully received

---

### Post by oldfred on 2014-07-14
In BIOS and grub hd0 is always the boot drive. And the BIOS enumeration may change. I skipped a port with my 4 hard drives on the Motherboard. If I plug in a flash drive it is sde, but if I reboot it is sdb. And no matter what drive I boot from it is hd0, so my chain entries may need adjusting. I just set up a couple and when one does not work, just manually edit grub to change from hd2 to hd1 or whatever.

I use entries like this to chain, second one is just a blank like to have a spacer:

```
 menuentry "Chainload Other Systems Grub Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}

   menuentry " " {
set root= 
}

   menuentry "Reboot" {

 reboot

 }
```

```
 menuentry "Boot from USB Drive" {
    set root=UUID=XXXX-YYYY
    linux /vmlinuz root=UUID=XXXX-YYYY ro quiet splash
    initrd /initrd.img
}
      
 A menuentry like this should always use the latest entry:

   menuentry "Latest Kernel in sda1" {
insmod ext2
set root=(hd0,1)
linux /vmlinuz root=/dev/sda1 ro
initrd /initrd.img
}

     

```
The set root and search are options or complimentary. Before search and UUIDs you just set root and that had to be the correct device. Now the search by UUID will override a set root and boot only that UUID.

I have not created a flash drive with the new grub in 14.04, yet.
But noticed this:
 new grub2 2.00 adds if logic and the set=root not just set
But that may be optional.


If you system is new, then it is also UEFI and that adds as from UEFI menu you can boot with either UEFI or BIOS and once you start booting in one mode cannot change to the other mode.
And if system is new, why a CD/DVD to boot? Just boot flash drive.


       Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)


 Herman has instructions for grub2 rescue boot CD, USB, or floppy. Also grub legacy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM)

I do not think there is a way to prevent a user from interrupting grub and manually booting into your hard drives. Only after fully booted can you hide the hard drives, but really need to know what they are to mount in fstab. If for many systems, it becomes a lot more complex & I do not know how.

---

### Post by Neill_R on 2014-07-14
because my HDD are unplugged and I have two USB sticks sda and sdb (bootable) to grub menu i just tried this
on boot press c
grub(2)
search --file /LID it returns hd0 of course 
set root=hd0
chainloader +1
boot

this takes me to my grub 2  menu which is what I want I will now reconnect the internal drives and I expect to set HD0 become HD4 2 internal plus another USB data stick

No I got my numbering system wrong it was HD3 (0,1,2,3) 
Now to get this working from a boot from a CD-ROM

---

### Post by yancek on 2014-07-14
> No I got my numbering system wrong it was HD3 (0,1,2,3) 

Remember that Grub2 counts hard drives from zero but partitions from one.  I had a hard time getting used to that from Grub Legacy.  Good luck with it.

---

### Post by sudodus on 2014-07-15
> **Neill_R said:**
> ...
Just so I make myself clear I am trying to create a way to boot to an OS on a USB which has Grub2 installed on the MBR. The target system frame (PC) is completely unknown. If it has hard disks THEY MUST NOT BE TOUCHED. The Floppy or CDROM boot device must wait to ensure all the USB HDD have initialised and then determine by searching for a signature file set that as root and chain load to the MBR of the found device where the GRUB2 menuon the USB HDD will be activated and the user can choose from the available options. 

What do you mean by 'THEY MUST NOT BE TOUCHED'?

- Do you mean that the booting should not write anything onto the hard disks,
- or do you mean that they should not be mounted,
- or do you mean that they should not be possible to mount?
> 
One other thing it was when I was try to create a VirtualBox guest OS I discovered it did not have the option to boot from a USB. if I solve this I will be able to screen capture my GRUB2 menu as my guest OS boots up.

Virtualbox doesn't boot from USB, but [KVM-VirtManager]("https://help.ubuntu.com/community/KVM/Installation") can do it.
> 
search --file /LID 
get me hd0,msdos4 as the target root

this is because all internal HDD have been unplugged and my target USB is the only one plugged in

also this PC is new and recognises USB and in fact can boot from them. 

I am not clear on how i get from the search to setting the root and then chain-loading to the MBR of that device so that its Grub2 can take over.

any help here would be gratefully received

If you 'only' want an installed system, that boots from USB, you can install any Ubuntu flavour to it (like any installed system) and go. It will be portable as long as you don't install proprietary drivers. See this link

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

But if you need some extra security, that is what we should discuss, and how to add it to a 'standard system installed into a USB drive'.

---

