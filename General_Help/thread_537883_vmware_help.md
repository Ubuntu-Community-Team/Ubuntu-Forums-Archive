---
title: "vmware help"
date: 2007-08-29
forum: General Help
---

### Post by Riffer on 2007-08-29
I installed vmware and used the tutorial 
[http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/](http://www.venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/)
to install my present windows install.

I had it up and running, but I screwed up a few things and deleted this virtual machine.  Now after reinstalling it through vmare I get this msg.

Cannot open the disk '/var/lib/vmware-server/Virtual Machines/Windows 2000 Professional 2/Windows 2000 Professional 2.vmdk' or one of the snapshot disks it depends on.
Reason: The partition table on the physical disk has changed since the disk was created. Remove the physical disk from the virtual machine, then add it again.

I have completely removed vmare and reinstalled, still the same msg.  I redid the windows drivers and again same problem.  What am I missing?

Also when I install the scsi drivers in windows I get an error msg that it couldn't find the file, any ideas?

---

### Post by tzulberti on 2007-08-30
Search in all the file for the files .vmdk. I recommendo that you use "sudo updatedb; locate *.vmdk".
The unistall, doesn't delete you virtual machines.

---

### Post by Riffer on 2007-08-31
well for some reason ubuntu crashed and burned and in fact my new MB screwed up ( the onboard sound was wonky as in fuzz instead of sound) so a quick reinstall of the MB and ubuntu and I'm up and running.

I must say I'm kinda scared to try vmware again.

So question?  With this setup of vmware, will windows apps run under Ubuntu?  Or will I have a window open that is running windows there?

---

### Post by gtdaqua on 2007-08-31
> **Riffer said:**
> 
So question?  With this setup of vmware, will windows apps run under Ubuntu?  Or will I have a window open that is running windows there?


I dont understand. What are you exactly asking? Windows apps most certainly do not work under Linux (u need something like wine to get it working). Windows can however work inside a VM which can run on top of Ubuntu. no problems here. 

So you will have a GUI in VMware running in Ubuntu from which you can add VMs and run them like a separate machine. Obviously the VM is independent of the host OS (Ubuntu) and will run any application normally.

---

### Post by Riffer on 2007-08-31
Thanks, I think I understand.  Its jsut that I read somewhere that that by using vmware windows apps will run natively on Ubuntu.  As you explained it Windows will run in its own desktop under Ubuntu.

Any way I may try it again.

---

### Post by gtdaqua on 2007-08-31
thats right - u need to first install windows inside the vm and then start using it as separate machine (the virtual console will be on ubuntu).

Here is a screenshot for you:

[http://en.wikipedia.org/wiki/Image:VMware_screenshot.png]("http://en.wikipedia.org/wiki/Image:VMware_screenshot.png")

---

### Post by mesocal on 2007-12-20
if you want to run windows, you have two options in vmware  ( making this simply):

Install Vmware Workstation 6 or Vmware Server ( the free version with a little less to it).

Now you can 

A: Create a new virtual machine (real easy, just answer the questions).
once this is created,  Power On the vm.  Make sure before you power it on, you have a Windows Installation disk in the drive.  When the vm boots up, it will read first from the drive (assuming your bios is set this way) and it will start the windows install process.  very typical from here on out,  it will install on virtual memory so dont worry about erasing info (unless you select Physical Drive when creating the vm).

B:  Boot up in windows and download Vmware Converter.  This will take a snapshot of your os and convert it into an vm image.  the whole thing takes about an hour.  very simple,  download and run it - again just answer the easy questions. be sure to save the file somewhere you can access it once you boot up in linux.  once in linux,  run your Vmware Workstation or Vmware Server.  Select File --> Open. now browse to wherever you saved the converted file and open it.  everything SHOULD start up smoothly.

This was just the Cliff Notes of the process.  There are some great sites/tutorials out there.

Goodluck.

---

