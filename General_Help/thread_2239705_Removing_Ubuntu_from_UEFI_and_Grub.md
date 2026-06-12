---
title: "Removing Ubuntu from UEFI and Grub"
date: 2014-08-15
forum: General Help
---

### Post by Mario_Del_Boccio on 2014-08-15
So after some testing I decided to get rid of ubuntu on my computer. It just didn't have the full DPI support and I wanted among other things. So I got delete the 3 partitions I created and then I reallocate the space back into windows. I then boot into my USB windows recovery drive and fix the mbr. I then restarted. Well I guess grub wasn't removed as I got a BASH line editing grub screen. I then decided that I wasn't getting anywhere with that and changed boot priority in the UEFI to my USB and Windows. Ubuntu was still on the UEFI???? I guess I need to get rid of it somehow. Right now I can boot into windows just fine, but I want ALL traces of Ubuntu gone. What do I need to do?

---

### Post by Cliff_Simonds on 2014-08-15
Do you have a system image of windows? Then you can use a live dvd or usb of ubuntu and use gparted and destroy _ALL _disk partitions by deleting them, then use a recovery disk to restore your windows image. This works with windows 7... for windows 8 you probably have to use a 3rd party imager. This works perfect because windows cannot "see" linux ext4. Hope this helps.

---

### Post by oldfred on 2014-08-15
UEFI has its own NVRAM memory. You have to first delete ubuntu folder in efi partition or else it will update UEFI NVRAM again, then delete from UEFI. Some UEFI  systems have the efibootmgr built into the UEFI so it may have a setting for maintenance?

       # from liveDVD or flash and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

Did you install correct proprietary driver? With new systems the open source drivers are behind and do not support the new systems well. Or if the Intel driver, you often just need a boot parameter to tell it the correct settings.

---

### Post by Mario_Del_Boccio on 2014-08-15
Ok so I understand now that I need to use efibootmanager. How do I go about installling this program if I deleted the ubuntu partitions? I have the ubuntu iso image on a usb flash drive but I will make a rescue dvd. Would I need to somehow put efibootmanager on that rescue dvd? Sorry I'm a bit new to all this.....thanks

---

### Post by oldfred on 2014-08-15
Just use the Ubuntu live installer.

Not sure what rescue CDs may now include that. They would have to be recent to include UEFI support.

---

### Post by Mario_Del_Boccio on 2014-08-20
Which efi manager download should I get? I see several, like amd64, hardy heron, i386, and otheres.......I'm assuming the amd64 would work fine with the live installer of ubuntu?

---

### Post by oldfred on 2014-08-20
If you have the 64 bit version of Ubuntu, it includes the efibootmgr. 
Or from command line just install it.
sudo apt-get install efibootmgr

It says in synaptic:
Note: efibootmgr requires that the kernel module efivars be loaded prior
to use.  'modprobe efivars' should do the trick.

---

### Post by Mario_Del_Boccio on 2014-08-20
Ok so I was able to "try ubuntu" from the rescue usb drive. It loaded up and I ran the efi command. It loaded into the efi boot manager but would not recognize the command "-b" or "-B" at all. I tried everything. I did load the drivers with the modprobe command but nothing. It clearly shows the ubuntu boot option that I want to delete but I don't know why I can't delete it....

---

### Post by oldfred on 2014-08-20
Post exactly want command you used.

shows order:
sudo efibootmgr -v

This was example #5.
[http://linux.dell.com/cgi-bin/gitweb...README;hb=HEAD]("http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD")
A system administrator wants to delete the Linux boot option from
   the menu.  'efibootmgr -b 4 -B' deletes entry 4 and removes it
   from BootOrder.

---

### Post by Mario_Del_Boccio on 2014-08-20
> ubuntu@ubuntu:~$ modprobe efivars
ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0000,0003,0002,2001,2002,2003
Boot0000* Windows Boot Manager    HD(2,1f4800,82000,3bd63d9c-4838-437c-bb07-461309acf5f1)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* EFI USB Device (USB DISK 2.0)    ACPI(a0341d0,0)PCI(14,0)USB(1,0)HD(1,1f80,776080,429a87cb)RC
Boot0002* Lenovo Recovery System    HD(3,276800,1f4000,c64cca0f-f36e-4d89-ae40-c8304e9e8168)File(\EFI\Microsoft\Boot\LrsBootMgr.efi)RC
Boot0003* ubuntu    HD(2,1f4800,82000,3bd63d9c-4838-437c-bb07-461309acf5f1)File(\EFI\ubuntu\shimx64.efi)
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC
ubuntu@ubuntu:~$ efibootmgr -b 3 -B

boot entry: 3 not found



I tried messing with the order of the -b or -B and didn't get anything to work. Every time it said command not recognized or boot not found. Is this just me?




> ubuntu@ubuntu:~$ modprobe efivars
ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0000,0003,0002,2001,2002,2003
Boot0000* Windows Boot Manager    HD(2,1f4800,82000,3bd63d9c-4838-437c-bb07-461309acf5f1)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* EFI USB Device (USB DISK 2.0)    ACPI(a0341d0,0)PCI(14,0)USB(1,0)HD(1,1f80,776080,429a87cb)RC
Boot0002* Lenovo Recovery System    HD(3,276800,1f4000,c64cca0f-f36e-4d89-ae40-c8304e9e8168)File(\EFI\Microsoft\Boot\LrsBootMgr.efi)RC
Boot0003* ubuntu    HD(2,1f4800,82000,3bd63d9c-4838-437c-bb07-461309acf5f1)File(\EFI\ubuntu\shimx64.efi)
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC
ubuntu@ubuntu:~$ efibootmgr 0003 -b
efibootmgr: option requires an argument -- 'b'
efibootmgr version 0.5.4
usage: efibootmgr [options]
    -a | --active         sets bootnum active
    -A | --inactive       sets bootnum inactive
    -b | --bootnum XXXX   modify BootXXXX (hex)
    -B | --delete-bootnum delete bootnum (hex)
    -c | --create         create new variable bootnum and add to bootorder
    -d | --disk disk       (defaults to /dev/sda) containing loader
    -e | --edd [1|3|-1]   force EDD 1.0 or 3.0 creation variables, or guess
    -E | --device num      EDD 1.0 device number (defaults to 0x80)
    -g | --gpt            force disk with invalid PMBR to be treated as GPT
    -H | --acpi_hid XXXX  set the ACPI HID (used with -i)
    -i | --iface name     create a netboot entry for the named interface
    -l | --loader name     (defaults to \elilo.efi)
    -L | --label label     Boot manager display label (defaults to "Linux")
    -n | --bootnext XXXX   set BootNext to XXXX (hex)
    -N | --delete-bootnext delete BootNext
    -o | --bootorder XXXX,YYYY,ZZZZ,...     explicitly set BootOrder (hex)
    -O | --delete-bootorder delete BootOrder
    -p | --part part        (defaults to 1) containing loader
    -q | --quiet            be quiet
       | --test filename    don't write to NVRAM, write to filename.
    -t | --timeout seconds  set boot manager timeout waiting for user input.
    -T | --delete-timeout   delete Timeout.
    -u | --unicode | --UCS-2  pass extra args as UCS-2 (default is ASCII)
    -U | --acpi_uid XXXX    set the ACPI UID (used with -i)
    -v | --verbose          print additional information
    -V | --version          return version and exit
    -w | --write-signature  write unique sig to MBR if needed
    -@ | --append-binary-args file  append extra args from file (use "-" for stdin)
ubuntu@ubuntu:~$ 


I put the -b after the boot number in this command and at least got a menu but doing -B after this was the same thing.

---

### Post by oldfred on 2014-08-20
That is the extent of my knowledge and I have seen several other users delete the Ubuntu entry.

Not sure why your system will not delete it.

Does Lenovo have any edit capability from inside its UEFI menus? A few system do have that.

---

### Post by Mario_Del_Boccio on 2014-08-23
Ok so I'm going to mess around with it a bit more and see if I messed up or maybe it just needs a bit of encouragement. So the good news is this doesn't affect windows bootup (which I need for school). However the ubuntu entry  is annoying. Is there any way (Reset, reinstall, delete, etc) that I can get rid of it the hard way? Reinstalling windows? I will do anything (since my data is all backed up) to make it disappear. I mean if theres a way to access efi manager in ubuntu, shouldn't there be a way in windows command prompt? thanks

---

### Post by oldfred on 2014-08-23
If you have Windows as default boot entry in UEFI, you should just auto boot into Windows and not see any other entries.
Or did you also add an entry into the BCD inside Windows? Then you have to edit that with Windows inside Windows with bcdedit.

---

