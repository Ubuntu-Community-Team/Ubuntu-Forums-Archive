---
title: "File not found: windows.vmdk"
date: 2007-08-30
forum: General Help
---

### Post by simonsocial on 2007-08-30
When I try to run m virtual machine in VMWare player I get the following error: -

File not found: windows.vmdk

This file is required to power on this virtual machine.  If this file was moved, please provide its new location.

The file is there but it doesn't pick up on it. I have googled this but I haven't found an solutions.

Any ideas would be great,

Thanks!

---

### Post by spupy on 2007-08-30
Vmdk files are the harddisks of the Virtual Machine. When you are asked to provide its new location, you mean it opens a Open dialog, but it doens't recognize the file when you select it?
Open up the *.vmx file of your VM. Find a row similar to this:
```
ide0:0.fileName = "Windows XP Home Edition.vmdk"
```
This line points to he vmdk file. Edit it to point to the vmdk file. Better use absolute path - /home/user/... or wherever your vmdk file is.

---

### Post by simonsocial on 2007-08-31
After seeing your post i realise that it because i'm using a SATA disk not IDE, so I changed the values to sda instead of ide. This allow VMware to find the file but its now say that it can't find a operating system.



PXE-M0F: Exiting Intel PXE ROM
Operating system not found

---

### Post by roofone on 2007-10-22
I have the same issue on a thinkpad t42: File not found: windows.vmdk.

My windows partition is /dev/sda.

If I change "ide0.0" in windows.vmx to anything else (e.g. "asdf0.0") the vm boots, but I get the OS not found error (unless I have my ubuntu install CD in the CD drive, it starts that fine).

I wonder if I the hard drive cylinder/sector settings are wrong, or if the mbr is in an unusual spot.

---

