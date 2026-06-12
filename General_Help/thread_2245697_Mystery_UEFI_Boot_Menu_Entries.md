---
title: "Mystery UEFI Boot Menu Entries"
date: 2014-09-25
forum: General Help
---

### Post by Dennis N on 2014-09-25
This is my UEFI boot menu, detailed form:

```
dmn@Sydney:~$ sudo efibootmgr -v
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0001,0000,0003,0004,0007,0009,000B,000C,000E,0010,0012,0014,0015
Boot0000* ubuntu	HD(1,800,100000,a1e435e2-5bbe-47f1-af26-a8efc2b58fd1)File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* Hard Drive 	BIOS(2,0,00)..GO..NO........O.W.D.C. .W.D.5.0.0.0.A.A.K.X.-.0.0.E.R.M.A.0.................>..Gd-.;.A..MQ..L. . . . .W. .-.D.C.W.2.C.M.E.5.T.7.1.8.7........BO
Boot0003* ubuntu	ACPI(a0341d0,0)PCI(1f,2)03120a000100ffff0000HD(1,800,100000,a1e435e2-5bbe-47f1-af26-a8efc2b58fd1)..BO
Boot0004* ubuntu	ACPI(a0341d0,0)PCI(1f,2)03120a000100ffff0000HD(1,800,100000,a1e435e2-5bbe-47f1-af26-a8efc2b58fd1)..BO
Boot0007* ubuntu	ACPI(a0341d0,0)PCI(1f,2)03120a000100ffff0000HD(1,800,100000,a1e435e2-5bbe-47f1-af26-a8efc2b58fd1)..BO
Boot0009* ubuntu	ACPI(a0341d0,0)PCI(1f,2)03120a000100ffff0000HD(1,800,100000,a1e435e2-5bbe-47f1-af26-a8efc2b58fd1)..BO
Boot000B* ubuntu	ACPI(a0341d0,0)PCI(1f,2)03120a000100ffff0000HD(1,800,100000,a1e435e2-5bbe-47f1-af26-a8efc2b58fd1)..BO
Boot000C* ubuntu	ACPI(a0341d0,0)PCI(1f,2)03120a000100ffff0000HD(1,800,100000,a1e435e2-5bbe-47f1-af26-a8efc2b58fd1)..BO
Boot000E* ubuntu	ACPI(a0341d0,0)PCI(1f,2)03120a000100ffff0000HD(1,800,100000,a1e435e2-5bbe-47f1-af26-a8efc2b58fd1)..BO
Boot0010* ubuntu	ACPI(a0341d0,0)PCI(1f,2)03120a000100ffff0000HD(1,800,100000,a1e435e2-5bbe-47f1-af26-a8efc2b58fd1)..BO
Boot0012* ubuntu	ACPI(a0341d0,0)PCI(1f,2)03120a000100ffff0000HD(1,800,100000,a1e435e2-5bbe-47f1-af26-a8efc2b58fd1)..BO
Boot0014* ubuntu	ACPI(a0341d0,0)PCI(1f,2)03120a000100ffff0000HD(1,800,100000,a1e435e2-5bbe-47f1-af26-a8efc2b58fd1)..BO
Boot0015* ubuntu	HD(1,800,100000,a1e435e2-5bbe-47f1-af26-a8efc2b58fd1)File(\EFI\UBUNTU\GRUBX64.EFI)..BO


```

I am wondering what is the meaning of the identical entries 0003 to 0014 with references to ACPI and PCI? I find none of them boot anything - I am just returned to the UEFI boot menu. Only 0000,0001 and 0015 are functional (only one OS - Xubuntu, is on the system). I also notice that these ACPI type entries are growing in number - another one was added after the recent kernel update. 

Unless they have some purpose, I plan to delete them. Any reason why not?

---

### Post by T.J. on 2014-09-25
Have you reinstalled multiple times?   

If they are of no use to you personally, I would delete them.  Boot entries are only useful for booting and as long as you aren't picking up a Windows restore partition or anything of that nature, you should be able to delete the entries safely.

---

### Post by oldfred on 2014-09-26
Is there a bug in the kernel update that is writing extra UEFI entires? It should not if you already have one.
If it happens again I would check bug reports and if nothing report it.
There was a fix where some systems were bricked in the beginning with UEFI. Main issue was some early UEFI would fill NVRAM over 50% and stop working.  Originally blamed on Linux but found to also be eventually caused by Windows also. But real issue was Vendors UEFI was not correctly freeing memory.

 modprobe efivars
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by Dennis N on 2014-09-26
> Have you reinstalled multiple times? 
No reinstalls have been done.
> Is there a bug in the kernel update that is writing extra UEFI entires?
Two days ago, I made a copy of the UEFI boot menu - there were 9 entries that began with "ubuntuACPI..." Now there are 10 of them. The only event was a kernel update. So it looks like a good suspect.

I was interested in what these the purpose of these entries might be. My best guess is that they are for a network boot. Probably a default entry, like the drive entries? If so, definitely poorly labeled as 'ubuntu'. A user would expect them to boot ubuntu. 

I have deleted all but one of them, as they all fail to do anything, and just return to the UEFI menu after a second. I thought a UEFI system was supposed to go through its boot menu until it comes to a bootable entry?

---

