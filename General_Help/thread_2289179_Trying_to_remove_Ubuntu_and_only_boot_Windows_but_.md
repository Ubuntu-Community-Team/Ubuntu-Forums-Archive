---
title: "Trying to remove Ubuntu and only boot Windows but stuck in grub console"
date: 2015-08-02
forum: General Help
---

### Post by eamon2 on 2015-08-02
Hi ive been trying to remove ubuntu from dual booting on my surface pro 3. I followed this guide so far:

[http://askubuntu.com/questions/489929/delete-ubuntu-from-dual-boot-windows-8-1-in-gpt-disk](http://askubuntu.com/questions/489929/delete-ubuntu-from-dual-boot-windows-8-1-in-gpt-disk)

I removed the two ubuntu partitions using the windows disk management tool, then i booted into the windows recovery environment and ran the two commands 
[LIST=1]
[*]bootrec /fixboot
[*]bootrec /fixmbr
[/LIST]
According to the post this should have then booted me straight into windows on restart. However when i restart i am launched into a grub console and stuck there.

I ran boot-repair on a live usb to try and fix the grub so I could at least boot into windows through grub however that did not work. Here is my boot-repair log:

[http://paste.ubuntu.com/11984232/](http://paste.ubuntu.com/11984232/)

Ive been searching all day and I am unable to find a solution, if anyone can help that would be greatly appreciated!

---

### Post by NoWayWin8 on 2015-08-02
From your description it sounds like you tried to fix it from the Windows Recovery Environment. The instructions say you must boot from the Windows installation CD and use the "repair your system" option.

---

### Post by yancek on 2015-08-02
The link you posted shows how to put windows code in the MBR after deleting Linux/Ubuntu partitions.  First off, that is backward and one should restore the MBR before deleting/re-formatting partitions.  Although it should work that way, it is much safer restoring the MBR first.  I don't know what your previous setup was but the boot repair shows windows code in the master boot record but it also shows an EFI partition with efi files for both windows and Ubuntu.  That doesn't usually work well, combining them.  You need to do one or the other.  Were both EFI previously or MBR?

It's also my understanding that you need a windows installation DVD and the recovery CD does not have the files needed to repair the MBR if that's what you want.
Might be a good idea to wait for someone who knows more about UEFI to post.

---

### Post by oldfred on 2015-08-02
Your system is UEFI, you should not have any boot code in MBR. Always boot in UEFI.
That you now have code in MBR is not an issue as long as you do not try to boot in BIOS mode as that will just give errors, but will find boot loader in MBR.

You have to delete the ubuntu folder in the ESP - efi system partition and remove the ubuntu entry in UEFI. Not sure if you also still want rEFInd or not.

Boot-Repair shows these in your ESP which you should delete:
      ```
 /EFI/refind/MokManager.efi 
                       /EFI/refind/MokManager.efi~ /EFI/refind/grubx64.efi 
                       /EFI/refind/shim.efi /EFI/refind/shim.efi~ 
                       /EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi 


```    

You want to delete the 0000 ubuntu entry, reconfirm by running efibootmgr again just before deleting. And you want to change 0001 Windows to be first in boot order. You should be able to do that in your UEFI, or again from efibootmgr. 
 efibootmgr -v
```
BootCurrent: 000B
Timeout: 2 seconds
BootOrder: 000B,000A,0009,0000,0001
Boot0000* ubuntu    HD(2,c8800,64000,10ab0890-dbfc-49a3-b7ce-7e397cc7fbb9)File(EFIubuntushimx64.efi)
Boot0001* Windows Boot Manager    HD(2,c8800,64000,10ab0890-dbfc-49a3-b7ce-7e397cc7fbb9)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D
```

      
 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). 
Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. And example #3 is boot order.
efibootmgr -b XXXX -B
[URL="http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD"]http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD
      [/URL] 

 You would first type sudo efibootmgr -v to get a list of boot options. Note the number associated with the Windows entry -- for instance, it might be Boot0001. You'd then type 
sudo efibootmgr -o 1 
 (You can specify a set of boot loaders to be tried in order, as in 
sudo efibootmgr -o 1,9 
to use 1, then 9 if that fails)


Change boot order with efibootmgr, some require all 4 char others 1 is ok.
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)

    [URL="http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD"]
[/URL]

---

### Post by eamon2 on 2015-08-02
Thanks everyone, I'm gonna try and implement olfred's solution now:

Here is what i get when i run efibootmgr -v:

```
ubuntu@ubuntu:~$ efibootmgr -v
BootCurrent: 0002
Timeout: 2 seconds
BootOrder: 0002,0000,0001
Boot0000* ubuntu    HD(2,c8800,64000,10ab0890-dbfc-49a3-b7ce-7e397cc7fbb9)File(\EFI\ubuntu\shimx64.efi)
Boot0001* Windows Boot Manager    HD(2,c8800,64000,10ab0890-dbfc-49a3-b7ce-7e397cc7fbb9)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...................
Boot0002* USB Drive    ACPI(a0341d0,0)PCI(14,0)USB(1,0)HD(1,800,f4f800,00000000)..BO
```

Next I ran the command to delete the 0000 boot entry:

```
ubuntu@ubuntu:~$ sudo efibootmgr -b 0000 -B
BootCurrent: 0002
Timeout: 2 seconds
BootOrder: 0002,0001
Boot0001* Windows Boot Manager
Boot0002* USB Drive
```

View the boot list again:
```
ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0002
Timeout: 2 seconds
BootOrder: 0002,0001
Boot0001* Windows Boot Manager    HD(2,c8800,64000,10ab0890-dbfc-49a3-b7ce-7e397cc7fbb9)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...................
Boot0002* USB Drive    ACPI(a0341d0,0)PCI(14,0)USB(1,0)HD(1,800,f4f800,00000000)..BO
```

Now change the boot order:
```
ubuntu@ubuntu:~$ sudo efibootmgr -o 1,2
BootCurrent: 0002
Timeout: 2 seconds
BootOrder: 0001,0002
Boot0001* Windows Boot Manager
Boot0002* USB Drive
```

Display the boot list one more time:
```
ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0002
Timeout: 2 seconds
BootOrder: 0001,0002
Boot0001* Windows Boot Manager    HD(2,c8800,64000,10ab0890-dbfc-49a3-b7ce-7e397cc7fbb9)File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...................
Boot0002* USB Drive    ACPI(a0341d0,0)PCI(14,0)USB(1,0)HD(1,800,f4f800,00000000)..BO
```

Now im gonna try restarting and see what happens.

---

### Post by eamon2 on 2015-08-02
ok so that didnt seem to work. I no longer boot into the grub console but i am stuck in a loop. When i restarted it flashes the surface logo like it normally does then thinks for a little bit and resets again, continuing the loop. Any ideas what to try next?

---

### Post by eamon2 on 2015-08-02
I ran boot-repair again (because i was out of ideas) and got this:

[http://paste.ubuntu.com/11990344/](http://paste.ubuntu.com/11990344/)

So the ubuntu files are still there. Was i meant to delete the entire folder somehow with something other the efibootmgr?

---

### Post by oldfred on 2015-08-02
You can use anything to delete the ubuntu folder. Naulitus or command line.
If in Windows I think you have to mount the efi partition as Windows does not normally show it.

If issues with Windows you are into Windows repairs. Did you try f8?
       Windows 8 UEFI fixes
[URL="http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader"]http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader
[/URL]
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[URL="http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB"]http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB
      [/URL]
 [http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
    [URL="http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB"]
[/URL]

[URL="http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader"]
[/URL]

---

