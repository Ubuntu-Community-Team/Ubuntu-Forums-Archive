---
title: "How to clean up after installing/uninstalling Ubuntu on Win8.1 machine"
date: 2015-12-07
forum: General Help
---

### Post by t0p on 2015-12-07
I tried to install Ubuntu on a HP laptop preinstalled with Windows 8.1.  I couldn't get the dual-boot to work - I could only get to Ubuntu by going into Windows, holding <shift> and clicking Restart, then going through Troubleshoot, Advanced Options, UEFI firmware settings, and F9 Boot device options etc...

Anyway, I decided to clean it all off the computer and try again sometime, so I deleted the Ubuntu partition and extended the Windows partition to take up the unallocated space.

Now, if I go through the <shift>/Restart etc palaver, to OS boot manager, I get a number of options: ubuntu (ST100LM024); and if I select to Boot from EFI file, I get the options
> 
<.>
<..>
<microsoft>
<boot>
<HP>
<ubuntu>

and under the <ubuntu> option I get the choice of:
> 
shim64.efi
grub64.efi
MokManager.efi

The shim64.efi and grub64.efi both take me to a grub command line prompt.  Which means grub is still there, even though I deleted the Ubuntu partitions and reallocated them to Windows.

Which also makes me think:  I deleted the Ubuntu partition then extended the Windows partition to take up the unallocated space.  And when I look at the Windows partition editor, it shows that the Windows partition is indeed larger, filesystem NTFS.  But I was not given an opportunity to reformat the ex-Windows space, so has it really been reformatted to NTFS?  Or is it still ext4?  Deleting the Ubuntu partition and reallocating it to Windows was a push-button instantaneous affair, whereas my reformatting experiences with, for example gparted, have taken at least some amount of time - usually, the larger the space you are reformatting, the longer the reformatting takes.  And the partition that was Ubuntu, then unallocated, then consumed by Windows was quite large (hundreds of GBs).

So: is this going to lead me into problems at some point?  If so, how can I make sure the old partition space is now reformatted NTFS?  And how can I clean up the Boot device options menu to remove all the redundant options that lead to grub?

---

### Post by T.J. on 2015-12-07
> **t0p said:**
> The shim64.efi and grub64.efi both take me to a grub command line prompt.  Which means grub is still there, even though I deleted the Ubuntu partitions and reallocated them to Windows.

UEFI is not the same as the traditional MBR BIOS. By design, it does remove boot files, but you can remove them manually if you feel the need. It probably is unnecessary.

> Which also makes me think:  I deleted the Ubuntu partition then extended the Windows partition to take up the unallocated space.  And when I look at the Windows partition editor, it shows that the Windows partition is indeed larger, filesystem NTFS.  But I was not given an opportunity to reformat the ex-Windows space, so has it really been reformatted to NTFS?  Or is it still ext4?

No.  It is NTFS for all intents.  The data was not directly erased, however the physical space was reallocated to NTFS.  Contrary to what many people think, when you reformat a drive you do not erase it, you merely tell the computer that the physical space is "empty" and the data that is left there can be overwritten as needed.  Purposely erasing every bit of the drive is time consuming.  If you did so every time, a format would take several minutes or hours depending on drive geometry. Just considering it "blank" is not only faster, it extends the life of your hard disc.


> So: is this going to lead me into problems at some point?  If so, how can I make sure the old partition space is now reformatted NTFS?  And how can I clean up the Boot device options menu to remove all the redundant options that lead to grub?

Unlikely.  As long as your computer boots into Windows first, it is really not that important.  If you really want to you can remove them. Let me know.

---

