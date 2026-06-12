---
title: "Grub destroyed on dual boot pc"
date: 2019-10-24
forum: General Help
---

### Post by rouvenster on 2019-10-24
Hello all, 
I use a computer for a while now with 2 UEFI partitions, the main one was Chakra and the second one was Windows 10. Both are installed on an SSD, while my personal files and /home sit on a normal HDD.
A week ago I decided do drop Chakra and try KDE NEON instead. I wiped the Chakra / and /home partitions and replaced them with the Neon ones. All worked well  until I played a bit with the /etc/default/grub to boot from another kernel (5.x fail completely at AMD gpu drivers) and mistakenly forced my grub to boot immediately to memtest instead of a kernel. From there, it spiraled to chaos...I didn't know what to do so I followed an advice from internet to boot from a live usb and run [Boot-repair]("https://help.ubuntu.com/community/Boot-Repair") tool. It seemed to work (recommended settings) but when rebooting, instead of the annoying memtest or kernel I booted to the grub 2.02 "**[B]minimal BASH like line editing** is supported" [/B]nightmare thing. I tried several "tricks", but none of them worked (changing UEFI to legacy in the BIOS, redo the boot-repair tool but manually change stuff...etc).
I can boot manually typing

```

set root=(hd1,gpt6)
linux  /boot/vmlinuzxxxxxxx.xxxx  root=/dev/sdb6
initrd /boot/vmlinuzxxxxxxx.xxxx
boot
```

And then everything works, even my /etc/default/grub is still there with the things I added. 

The problem is I am stuck with manual booting, doing grub-install or update-grub doesn't help at all, I always end up to the "**[B]minimal BASH like line editing** is supported" [/B]nightmare.

_**Any Idea how to repair my GRUB permanently ?**_

Other interesting stuff :
[LIST]
[*]At some point it seems I destroyed my windows boot partition as well since if I try to boot to Windows it drops to BSOD : **Unmountable** Boot **Volume** Error" 
[*]The fastest and easiest way for me to boot is to use the [Super Grub2 Disc which detects everything, all my kernels, all my grub files, everything works]("https://www.supergrubdisk.org/super-grub2-disk/") 
[*]rescatux doesn't works but maybe because I tried to use the BETA version, have to try some more 
[/LIST]


Thanks for your help

---

### Post by ajgreeny on 2019-10-24
It will make life a lot easier for us to help you if we can see all the details of where you have got to at present, so see **Boot-Repair** in my signature below and follow the instructions there to install and run the Boot-Info-Script, using a live system if necessary.	 

**Do not run the default repair just yet**, (though perhaps I'm too late telling you that as you seem to have done so already)  but simply copy back here the **pastebin** link you get which will show us a lot more about your system and the current situation.

---

### Post by yancek on 2019-10-24
The first step you should have taken with boot repair is to use the Create BootInfo Summary option rather than recommended repair.  Unless you are very familiar with Grub and UEFI, you will run into problems and posting the link you get from the BootInfo Summary here will be helpful as there are a number of experts here who should be able to help so please do that now.

> changing UEFI to legacy in the BIOS,

Windows 10 is almost always a UEFI install.  Grub installed in Legacy mode will not boot a windows UEFI although you should be able to boot it from the BIOS setup firmware on boot.  Did you install the new system UEFI?

---

### Post by rouvenster on 2019-10-24
> **ajgreeny said:**
> It will make life a lot easier for us to help you if we can see all the details of where you have got to at present, so see **Boot-Repair** in my signature below and follow the instructions there to install and run the Boot-Info-Script, using a live system if necessary.     

**Do not run the default repair just yet**, (though perhaps I'm too late telling you that as you seem to have done so already)  but simply copy back here the **pastebin** link you get which will show us a lot more about your system and the current situation.

Thank you for your reply, [here is the info-script pastebin]("http://paste.ubuntu.com/p/TCr4VjQwPs/")

I hope it helps

---

### Post by rouvenster on 2019-10-24
> **yancek said:**
> The first step you should have taken with boot repair is to use the Create BootInfo Summary option rather than recommended repair.  Unless you are very familiar with Grub and UEFI, you will run into problems and posting the link you get from the BootInfo Summary here will be helpful as there are a number of experts here who should be able to help so please do that now.
Windows 10 is almost always a UEFI install.  Grub installed in Legacy mode will not boot a windows UEFI although you should be able to boot it from the BIOS setup firmware on boot.  Did you install the new system UEFI?

Thank you for your reply. All systems were installed as UEFI (running the usb installer as UEFI from BIOS). The changes I made were just random try to see if it helps as some people suggested it resolves the grub bash black screen problem. I turned it back to "both legacy and UEFI" as it always was in the BIOS.
 [Here is the pastebin of boot-repair]("http://paste.ubuntu.com/p/TCr4VjQwPs/").

---

### Post by oldfred on 2019-10-24
You need to boot in UEFI boot mode.
You have grub installed in the MBR of sdb, and BIOS boot will load that grub. Manual booting may allow booting, but you need grub installed in UEFI boot mode.
Boot-Repair's advanced mode when booted in UEFI mode, will usually let you do a full reinstall of grub and convert to the UEFI version of grub.

Do you also have an ESP on sda?
But it says structure needs cleaning. Not sure what that error is, but if Linux ext4 first try fsck. If FAT32 ESP use dosfsck or if  NTFS use chkdsk.

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by rouvenster on 2019-10-24
> You need to boot in UEFI boot mode. I tried in the BIOS to change to "UEFI only" and I still got thrown to the basic bash grub.
> you need grub installed in UEFI boot mode. It was installed in UEFI mode, because at first I booted the live usb in legacy mode by mistake and when I lauch repair-boot it ordered me to reboot to UEFI mode, so I did.
> Boot-Repair's advanced mode when booted in UEFI mode, will usually let  you do a full reinstall of grub and convert to the UEFI version of grub I opened the advanced mode tab and didn't find anything about UEFI. Is it automatic?
> Do you also have an ESP on sda? Yes It's a FAT32 EFI partition to boot windows but is it possible it was also used to boot Linux ?
> use chkdsk I tried chkdsk with a windows usb it checked C:\  for 2 hours and didn't find any error.

I still don't understand why I need to do all that when clearly the boot works manually and it seems all I need is to use an app (obviously grub) to do the manual thing instead of me ? Even the Super Grub2 boot disk find the boot sequence alone ! I think there must be something very simple to fix it

---

### Post by rbmorse on 2019-10-24
In the machine's EFI setup, is the boot priority setting pointing at the correct device as the first boot option?

If you're not sure, post the output of:

 efibootmgr

---

### Post by rouvenster on 2019-10-24
> **rbmorse said:**
> In the machine's EFI setup, is the boot priority setting pointing at the correct device as the first boot option?

If you're not sure, post the output of:

 efibootmgr

BootCurrent: 000C
Timeout: 3 seconds
BootOrder: 0000,000A,000B,000C,0009
Boot0000* neon
Boot0009  Windows Boot Manager
Boot000A* CD/DVD Drive 
Boot000B* Hard Drive 
Boot000C* UEFI: Generic Flash Disk 8.07

Current is at 000C because I used the grub2disc usb to boot instead of manually typing stuff. As you can see 000 is KDE NEON and it doesn't boot

---

### Post by oldfred on 2019-10-24
UUIDs & GUIDs look ok, but it may not be booting because of all the partition issues as reported.

Does not look like fstab is trying to mount any of the partitions that are saying they have issues.

Can you boot recovery mode? You may have to press escape just after UEFI/BIOS screen, but before grub to get grub menu to choose recovery mode.

---

### Post by rouvenster on 2019-10-25
> **oldfred said:**
> UUIDs & GUIDs look ok, but it may not be booting because of all the partition issues as reported.

Does not look like fstab is trying to mount any of the partitions that are saying they have issues.

Can you boot recovery mode? You may have to press escape just after UEFI/BIOS screen, but before grub to get grub menu to choose recovery mode.

No it doesn't work, but I can boot the kernel recovery mode from the super grub disc on my usb drive. I'm not sure what to do after, I tried the grub recovery option, it says it was successful and boot to the desktop in some sort of safe mode but after reboot I still end up to the basic grub bash thing.

Here are some screenshots :


 
[That's how the super grub disc look after I tell him to detect boot possibilities]("https://ibb.co/7VnhJps")
[URL="https://ibb.co/dBxSYsz"]The list goes on....
[/URL][URL="https://ibb.co/qrc0CRv"]....and on...
[/URL][This is what I selected to boot recovery mode]("https://ibb.co/74jfhhW")
[The grub recovery from kernel recovery mode]("https://ibb.co/ChYj4J5")

Notice the MacOS entry detected both on super grub disc and kernel grub recovery ??? I never had at any point MacOS. I suspect this is some weird entry installed automatically from boot-repair program when I first launched the "recommended settings" option.

---

### Post by rouvenster on 2019-10-25
So I found an alternative solution : 
Since I can't manage to make GRUB work, I installed [rEFInd ]("http://www.rodsbooks.com/refind/")which is a really good customizable boot manager. It is way faster than the super grub disc (it is as fast as the original GRUB2) can manage different kernels and use the command lines I added in /etc/default/grub file.
It also let me boot to Windows, which I couldn't do until now. 

So to anyone having impossible problems with GRUB and doesn't want to reinstall whole systems, just
```

sudo apt install refind

```

---

### Post by oldfred on 2019-10-25
I have used rEFInd for emergency boot and have one older small flash drive set up just for that. It is a small application.

I used to use SuperGrub for my old BIOS systems. I think they since updated to work with UEFI. 
But that site has Rescatux which I believe is more for UEFI systems.

---

