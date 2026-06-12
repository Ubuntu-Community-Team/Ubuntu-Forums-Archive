---
title: "Copying files beteen virtual machine &amp; host."
date: 2007-04-13
forum: General Help
---

### Post by Error47 on 2007-04-13
I am using VMware Server to run Windows XP. I've got a file in my windows machine, that I need transfered to the host machine which is linux.  I do not know how to get my external HD working on vmware with windows, I can't get my USB flash drive to work either. There are no problems, it's just I don't know how to get it to work. It's a large file, so I need my external HD to work . Can anyone help?

Thanks.

---

### Post by raja on 2007-04-13
You have to enable USB devices in the VMware server. After you plug in the USB hard drive, if it gets automatically mounted in the ubuntu host, unmount it. Now, it should get mounted in the xp guest.

---

### Post by Error47 on 2007-04-13
> **raja said:**
> You have to enable USB devices in the VMware server. After you plug in the USB hard drive, if it gets automatically mounted in the ubuntu host, unmount it. Now, it should get mounted in the xp guest.

I do not know how to do any of that. I am only a beginner linux user. 

Also, how can I get my firewire external HD, and my iPod working on my virtual machine. 

Thanks alot.

---

### Post by raja on 2007-04-13
Think of your virtual machine as a stand alone pc for all purposes. So you use stuff with it just as you would with a windows pc. The only difference is that the mouse and usb devices are shared between the guest and the host. Use the disk mounter applet in Ubuntu to easily see which disks are mounted and unmount them. (Right click on the top panel, select add to panel and choose the disk mounter). Once the USB device is not mounted in Ubuntu, it is ready to be plugged in the guest OS. See if it automounted there (is there an additional disk in My Computer ?). Otherwise in the menu in the vmware server, there is an entry like devices where you should find USB devices where you should be able to see the device and connect.

---

### Post by Error47 on 2007-04-14
I unmounted or ' ejected ' my usb drive. I did not see it in Windows. I also don't see where I can add it in the vmware settings.

---

### Post by raja on 2007-04-14
Unfortunately, I am not using VMware server currently to show you a screenshot. Did you install the vmware tools? If not do that first. 

I found a screenshot showing the menu entry for USB devices. You may find [this page]("http://www.networkcomputing.com/channels/storageandservers/showArticle.jhtml?articleID=197008134&pgno=3&queryText=") useful to solve your problems.

---

### Post by Error47 on 2007-04-15
I was able to get the USB drive working. Some files I need to copy are very large. How can I use my external Hard Drive on my virtual machine?

---

### Post by Error47 on 2007-04-17
Doesn't work anymore. Never played around with it at all. The windows system detects that some USB device has been connected, but can not do anything with it. When I go to the removable drive that it is suppose to be in, it just says, please insert this drive or something. This is not an easy way to move large files, I need some easy options.

---

### Post by allforcarrie on 2007-04-19
i have the same problem no windows drivers seem to work.

---

### Post by Error47 on 2007-04-21
I keep getting a message in windows that says unknown device when I try to use my USB device. It does detect it though. It has worked before, but I can't get it to work anymore.

---

