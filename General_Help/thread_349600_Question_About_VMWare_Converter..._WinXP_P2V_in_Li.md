---
title: "Question About VMWare Converter... WinXP P2V in Linux?"
date: 2007-01-30
forum: General Help
---

### Post by SendDerek on 2007-01-30
Hello!

I just recently came across the program called VMWare Converter and I had some questions about it.

My main question is this, and it's probably a common one:  Can I use this software to convert my Windows XP partition into a virtual drive and then in turn, use VMWare Player in Linux to run that new virtual OS?  

I've noticed that the download itself was a .exe file and I was unable to find any alternative downloads for linux, so I'm assuming that I would need to run this software while in my Windows partition to create the Virtual Drive on another partition that is shared between my Windows installation as well as my Linux and then finally use VMWare Player to load the image.  

Does this sound correct?  There is also another program called VMWare Importer, but I have yet to find out what purpose that serves.

Here are the links to the software pages at VMWare:

[ VMWare Converter ]("http://www.vmware.com/products/converter/")
[ VMWare Importer ]("http://www.vmware.com/products/vmimporter/")

Thanks for any help in advance!

---

### Post by crispy_420 on 2007-01-30
Have you tried running this app from wine?

This looks interesting and I may have to try it out.

---

### Post by scullez on 2007-01-30
That's correct, you need VMware Converter + windows
more about it: [http://www.vmware.com/support/converter/doc/releasenotes_conv3.html](http://www.vmware.com/support/converter/doc/releasenotes_conv3.html)

p.s. very interesting & free alternative is VirtualBox: [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by SendDerek on 2007-01-31
> **scullez said:**
> That's correct, you need VMware Converter + windows
more about it: [http://www.vmware.com/support/converter/doc/releasenotes_conv3.html](http://www.vmware.com/support/converter/doc/releasenotes_conv3.html)

p.s. very interesting & free alternative is VirtualBox: [http://www.virtualbox.org/](http://www.virtualbox.org/)

So, would you recommend VirtualBox instead of VMware?

The reason VMWare converter sounds appealing is becaue VMWare player is something easily installed in ubuntu, and it sounds like Converter is easy to install and operate.  So, in my head it make sense to go from VMware to VMware products.  But, if this VirtualBox works just as well or better, then I think that would be a great alternative.  I think it's good to support open source products.

---

### Post by SendDerek on 2007-01-31
Also... does VirtualBox have the capabilities to convert a physical partition into a Virtual Machine?

---

### Post by Doc.Caliban on 2007-10-08
How about the other way around....

Can I convert my Ubuntu install into a VM so that I can run it under XP?

-Doc

---

### Post by mad_jack on 2007-11-04
> **SendDerek said:**
> So, would you recommend VirtualBox instead of VMware?

The reason VMWare converter sounds appealing is becaue VMWare player is something easily installed in ubuntu, and it sounds like Converter is easy to install and operate.  So, in my head it make sense to go from VMware to VMware products.  But, if this VirtualBox works just as well or better, then I think that would be a great alternative.  I think it's good to support open source products.

Pretty much a matter of personal choice. However there is nothing to stop you using VMware converter to generate an image of an OS partition, then using VirtualBox to run it. VirtualBox can use the .vmdk files created by VMware converter (and used by VMware server, workstation etc) natively.

Note though, that currently VirtualBox cannot take snapshops of .vmdk based virtual machines, as the disk is a "write-through" device in this case. Functionality for snapshops of write-through disks is planned in a future release though. VMware server may currently have the same limitation but I haven't checked this, so not sure.

If you are creating images of WIndows OS's be aware that there are some fairly severe licencing restrictions from Microsoft on this. Worse, opinion varies as to their interpretation on some aspects. Generally though, it should be reasonable to transfer a license from the original host machine to a virtual machine on that same host. My understanding is that you can do this with WinXP as long as you delete the original after the transfer, though Vista home editions are explicitly prohibited from being run under virtual machines (nothing stopping it technically, just legally). Other versions of VIsta I *believe* can be transferred **once!**, again with the proviso that your remove the original after transfer. Which should mean you can make a virtual machine from the original, just once - this should however suffice.

---

### Post by mad_jack on 2007-11-04
> **Doc.Caliban said:**
> How about the other way around....

Can I convert my Ubuntu install into a VM so that I can run it under XP?

-Doc

Yes, in at least 2 ways.

1. If you have a windows partition existing you can install and use the VMware converter to do it for you.
2. You can also run a VM using a "raw" disk partition. In your scenario this would be the Ubuntu partition.

However, with no axe to grind I'd recommend using a Linux distro as the host. Much easier to snapshot the guest OS, especially if it's windows based, so if it gets infected with anything nasty you can:

1. Revert it to last known "clean" state
2. Turn off networking at the host level (inacessible from the guest) and analyse the malware in a "jailed" environment
3. Use "seamless" windows for those odd windows applications you cannot live without and have them look like native X-Windows apps, including all the nice compiz/Beryl type wobbles etc.

Cheers!

2

---

### Post by dugh on 2007-11-17
VirtualBox doesn't have a way to easily convert a hard drive OS install to a virtual image.

And VMWare-Converter download is an installer that only runs in Windows (not Wine), so you'll need to convert the drive while running in Windows.

I've tried a 5 year old game, and some other Windows apps, and so far Wine has crashed every time.  I don't get why it is still around.

---

### Post by fjgaude on 2007-11-17
> **dugh said:**
> VirtualBox doesn't have a way to easily convert a hard drive OS install to a virtual image.

And VMWare-Converter download is an installer that only runs in Windows (not Wine), so you'll need to convert the drive while running in Windows.

I've tried a 5 year old game, and some other Windows apps, and so far Wine has crashed every time.  I don't get why it is still around.

Wine is for people who don't have a legal copy of Windows? Or maybe for those who wish to never have one?

---

