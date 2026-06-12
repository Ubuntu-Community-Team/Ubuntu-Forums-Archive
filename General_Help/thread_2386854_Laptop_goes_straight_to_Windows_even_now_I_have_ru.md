---
title: "Laptop goes straight to Windows even now I have run boot repair and deleted Windows"
date: 2018-03-11
forum: General Help
---

### Post by crisisengine on 2018-03-11
Hello everyone. I hope you're having a nice day :)

About a month ago, I installed Solus on my Hp 15 (I think) laptop, in a dual boot with windows. It worked fine but, when I turned my computer on, it went straight to Windows. I could only get round this by spamming the F9 key at startup so it went to the list of boot options. When I tried to change the boot order in the BIOS/ UEFI settings, rather than listing multiple OSs/ Boot managers, it only listed "OS Boot Manager" which seemed to be Windows.

I used it like this for a while but I knew it was only a temporary solution. I have since also installed Lubuntu which had the same problem. Naively, I wondered if deleting the Windows partition would make a different to the problem so I did this. Now, when  I turn it on,  it goes straight to a Windows recovery screen of some kind and I still have to do the F9 procedure to get to either of the other OSs.

I eventually managed to do boot repair, to see if that would help, but it didn't make any difference. The results are here: [http://paste.ubuntu.com/p/64ZM5SKn7r/](http://paste.ubuntu.com/p/64ZM5SKn7r/)

I'd really appreciate your support with this.

Joe : )

---

### Post by yancek on 2018-03-11
The boot repair output shows entries for Lubuntu (shown as Ubuntu) so you need to change the order to put it first.  If you are still able to boot it by any means, do that and open a terminal and enter the command below and post the output here and someone should be able to explain how to set Lubuntu first:

```
sudo efiboootmgr
```

---

### Post by crisisengine on 2018-03-11
Ok, here's the output:

BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0001,3001,0002,0003,0007,0008,2001,2002,2003
Boot0000* Internal EFI Shell
Boot0001* Windows Boot Manager
Boot0002* Grub2Win EFI
Boot0003* ubuntu
Boot0005* Notebook Hard Drive
Boot0006* Network Adapter (IPv4 Legacy)
Boot0007* Phoenix OS
Boot0008* Linux Boot Manager
Boot000A* Internal EFI Shell
Boot000B* Internal EFI Shell
Boot000C* Internal Hard Disk or Solid State Disk
Boot000E* Internal Hard Disk or Solid State Disk
Boot000F* Internal Hard Disk or Solid State Disk
Boot0011* Internal EFI Shell
Boot0012* Internal Hard Disk or Solid State Disk
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3000* Internal Hard Disk or Solid State Disk
Boot3001* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk
Boot3004* Internal Hard Disk or Solid State Disk
Boot3005* Internal Hard Disk or Solid State Disk
Boot3006* Internal Hard Disk or Solid State Disk
Boot3007* Internal Hard Disk or Solid State Disk

---

### Post by oldfred on 2018-03-11
You have an HP.
HP violates UEFI standard that says NOT to use description as part of boot.
And only valid default decription is "Windows Boot Manager".
Various work arounds, some just live with manual UEFI boot escape f9 like you have been doing.
UEFI does have a default hard drive or fallback boot that seems to work with many HP. That uses /EFI/Boot/bootx64.efi which is the same path & file used to boot an external drive/installer in UEFI mode.
You show multiple bootx64.efi in various folders?

Do not know how Solus boots, but it does not have the mount of an ESP - efi system partition in its fstab, so it may be BIOS/CSM/Legacy boot?
How you boot install media is then how it boots once installed.

You also have grub2win, systemd, phoenixOS, and goofiboot as EFI folders. Not familiar  with any of them
Typical install has /EFI/Microsoft for Windows, /EFI/ubuntu for Ubuntu and sometimes /EFI/Boot for fallback boot.

Major issue is you have two ESP. While UEFI allows more than one ESP, we do not see any system that works with more than one ESP at a time. Some have two FAT32 partitions and move boot flag back & forth. But you have boot flag on your Solus partition, which may mean it was BIOS boot?
But you need to use gparted to remove boot flag from sda6. With UEFI on gpt drives, boot flag/ESP setting can only be on a FAT32 formatted partition.

Boot-Repair also sees all the HP .efi files (and your other .efi) and adds boot entries to grub. It creates 25_custom. Many delete most or all the entries or turn off execute bit so not included in grub menu. I assume those HP files are either accessed from HP's UEFI or from Windows for system processes.
       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub 
    
You also are showing a lot of UEFI entries. You can see in terminal without running Boot-Repair.
sudo efibootmgr -v
If duplicate or obsolete entry you can remove with efibootmgr.
See 
man efibootmgr
       Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B 

To get HP to default boot ubuntu many use the hard drive entry or fallback entry.
The /EFI/Boot/bootx64.efi is normally a copy of Windows .efi boot file. We used to have to manually copy shimx64.efi to bootx64.efi, but now Boot-Repair does that and backs up current bootx64.efi.
Can you manually boot one of the (many) hard drive entries. And if so, can you make it the default or first in boot order.
Some also use efibootmgr to set boot order, but becuase of description checks it may not stick.
      
 Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
sudo efibootmgr -o 2,1
see also 
man efibootmgr

---

### Post by crisisengine on 2018-03-11
Thankyou so much for this. I have been trying some of these things in various configurations but I will cut the long story short. 
I ended up deleting the ESP with Windows etc. on it. 
When I turn the computer on, nothing comes up but I am able to access UEFI system tools.
I can access live DVDs (I am currently writing this on the live DVD of Lubuntu).

When I went on the "boot from EFI file" option on the F9 menu, no directory came up.
I created  a FAT formatted partition, from the live DVD, in the place of the old one.
Now when I select "boot from EFI file," it shows a directory, like it used to. 
The directory is empty.

Is is possible to create an EFI file, in this directory that would boot to Lubuntu? If I called it bootx64.efi, would that mean HP would default to it in the absence of a Windows one?

> UEFI does have a default hard drive or fallback boot that seems to work  with many HP. That uses /EFI/Boot/bootx64.efi which is the same path  & file used to boot an external drive/installer in UEFI mode.

---

### Post by oldfred on 2018-03-11
Use Boot-Repair to reinstall grub.
That should recreate /EFI/ubuntu folder.

Then you can copy /EFI/ubuntu to /EFI/Boot
And rename /EFI/Boot/shimx64.efi to bootx64.efi.

If using command line see this section in link below in my signature for detailed commands.
Systems that only boot Windows from UEFI.

---

### Post by crisisengine on 2018-03-11
Thanks! It's working now.

I actually didn't see your post but, by trial and error I managed to move and rename the right grub files such that it boots automatically to grub and Lubuntu. I'm pretty sure I've managed to bypass all the HP weirdness. Thanks for the help.

---

