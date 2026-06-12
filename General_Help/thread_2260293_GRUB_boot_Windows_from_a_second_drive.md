---
title: "GRUB boot Windows from a second drive"
date: 2015-01-10
forum: General Help
---

### Post by In8e8d on 2015-01-10
I have been knocking my head agains the wall for hours trying to get GRUB to boot Windows7 from a separate disk.  About a dozen threads exist, but none of them have a solution that seems to work for me.

Has anyone been able to set this up successfully?

---

### Post by Mark Phelps on 2015-01-10
> from a separate disk

If you mean from a second INTERNAL disk, the easy solution is to open a terminal, enter "sudo update-grub" -- and let os_prober find Windows and the GRUB editor add it automatically to the GRUB default configuration file.  Doing it manually is a lot of unnecessary work.

IF you mean from an EXTERNAL disk -- forget it.  Windows doesn't boot from external drives.

---

### Post by In8e8d on 2015-01-10
It is an internal disk.  The os_prober found it, it just doesn't boot I get a c/h/s error.  I also tried managing adding it to the configuration file using some different code - same issue.

From what I understand there is some issue with Windows boot manager not wanting to run if it wasn't the primary disk.  Which I can sort of confirm:

Successfully boot Window from grub:
1. Boot to Windows disk
2. Soft restart 
3. Boot to Unbuntu disk
4. Load Windows from grub

Unsuccessful boot Window from grub:
1. Boot to Unbuntu disk
2. Load Windows from grub

I could just load a different OS by selecting different disk from the BIOS, its just not as sleek.  I also can't imagine I'm the first guy to want to boot Windows from a separate disk by booting grub first

---

### Post by oldfred on 2015-01-11
Windows does seem to like to be the first drive.
Interally the BIOS reports drives a 80, 81 where boot drive is 80. 
So if you boot grub on a second drive Windows may then be 81 and not be happy.

The newest os-prober has a lot going on, some of which I do not fully understand. But some have had success with just the old style entry. The drivemap command is to switch the drive order, or I believe the 80,81 entries that BIOS puts on drive. 

 menuentry "Windows " {
drivemap -s (hd0) (hd1)
set root='(hd1,msdos1)'
ntldr /bootmgr
} 


 #Add menu entry to 40_custom, change example from (hd1, msdos1) or sdb1 to your partition.
gksudo gedit /etc/grub.d/40_custom

 #update grub menu after any change
sudo update-grub

If it works we then can turn off os-prober to eliminate the standard entry from the menu.

---

