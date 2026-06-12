---
title: "Virtualization of a Windows 2003 installation from linux"
date: 2007-02-21
forum: General Help
---

### Post by v_oo_v on 2007-02-21
Hi everybody,

I have tried several virtualization apps such as VmWare server & Virtual Box to run Windows 2000/Xp/2003 _**inside**_ Ubuntu.

I have a windows 2003 installed on the same hard disk:

```
hda1 > Windows 2003
hda2 > Ubuntu (ext3)
hda3 > Swap
```

I would like to know if there is any solution to run Windows inside ubuntu from its source partition, instead of installing an virtual machine under any virtualization software. 

Thanks in advance and best regards.

P.S: _**Yes, I used google**_, but I consider the Ubuntu forums as a reliable information source.

---

### Post by veloce on 2007-02-21
Yes, it is possible.  BUT, it's not easy. You'd want to be very sure that you couldn't achieve what you want any other way.

There are no howtos on this.  You might want to start by reading the section in the vmware-server manual about installing a virtual os onto a physical drive.

---

### Post by boredandblogging.com on 2007-02-21
If I'm not mistaken, virtualization tools were not meant to be run like this. The guest OS was meant to be just a file (a big file, but a file nonetheless) that you could copy and move over to another host machine and use it.

---

### Post by v_oo_v on 2007-02-22
Auto reply (just a little more deep google search using advanced operators):
[COLOR="Blue"]
[http://rougebob.com/Running-a-Windows-Partition-in-VMware.htm](http://rougebob.com/Running-a-Windows-Partition-in-VMware.htm)[/COLOR]

Easy, but unfortunately as per vmware's docs 2003 server can't be booted that way currently (maybe in teh future).

Also, as I have seen , KVM and XEN are not exactly as fast as a native install but could have better perfomance than vmware & virtualbox.


Thanks to all.

---

### Post by veloce on 2007-02-22
I get near native performance from win xp with vmware server under ubuntu on my dell laptop.  The dual core helps heaps and you need to run vms with lower memory than native.  For some reason, vmware server under linux is significantly better than vmware server under windows at running the same win xp vm.  It seems to use less memory and run quicker.

This machine also has intel's vm86 - maybe linux allows better use of this?

---

