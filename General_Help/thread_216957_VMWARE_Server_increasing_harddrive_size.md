---
title: "VMWARE Server increasing harddrive size"
date: 2006-07-16
forum: General Help
---

### Post by nami on 2006-07-16
Hi

I setup a virtual machine on my computer and set the hard drive to 4gb.  After installing an OS on it, I now would like to increase that 4gb to about 10gb.  How can I do this without creating a new image from scratch?

Thanks

nami

---

### Post by Stambo00 on 2006-08-08
A simple way I have found to solve this problem is too create a new virtual drive. For a virtual Windows that I wanted to increase I simply went to the Virtual Machine Settings in VMware Server and added a new hard disk.

Then in inside Windows I went to the control panel, then Administrative Tools, then Computer Management, then Disc Management, and then formated the new drive as a primary partition by right clicking on the blank drive and following the default steps.

I'm sure you could follow similiar steps in creating a new drive in a virtual linux image.

---

### Post by rbmorse on 2006-08-09
I'm running a Win2K VM in Vmware Workstation on top of Kubuntu Dapper and it works the same way. Painless.

---

### Post by David Corrales on 2006-08-09
You could also try Parallels which allows you to resize already created drives. Costs $50 so it's not expensive.

---

### Post by mannheim on 2006-08-09
I believe you can use "Virtual Disk Manager" to do this (though I haven't used it). According to VMWare's documentation [here]("http://www.vmware.com/pdf/server_vm_manual.pdf"), this utility comes with VWMWare server and can increase the size of disks. (See page 139 of that pdf manual.)

---

### Post by seaniekaye on 2008-04-17
Hi - I found a simple way to do this.

Go to command prompt and navigate to your VMware program directory. (the one that contains the file vmware-vdiskmanager.exe)

Then enter this at the command prompt 

vmware-vdiskmanager -x sizeGB file.vmdk

Obviously, replace size with any number, and give the full or relative path to the virtual disk you want to increase in size.

---

