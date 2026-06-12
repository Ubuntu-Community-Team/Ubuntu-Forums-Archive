---
title: "I MUST run this windows program -- help!"
date: 2007-01-02
forum: General Help
---

### Post by polkadotchickens on 2007-01-02
Okay.  I've been totally windows-free for an entire year now, but it turns out that the software I need to work on image processing for my thesis is only available for windows.  Don't you dare tell me there's an equivalent that's just as good or better for Linux -- I've been there.  There's not.  The program I need to run, AIP4Win, is astronomical image processing software, and the only program that has a key function that I need.

My problem is, the older version of this program installs and *seems* to run fine using wine, but the images never display correctly.  Like, they display as completely black, no matter how I adjust them.  So I tried installing the newer version, which should fix this problem I hope, as well as just be better anyway, but it won't install with wine.  The install wizard starts fine, has a few unimportant display issues, but then there are two problems that arise:
1. If I try to change the directory to install to (i.e., change it from c:/program files to my /usr/local/lib), the install wizard crashes.  Every time, no matter where I run it from or sudo or not.
2. If I just let it go on thinking it's going to install to c:/program files, it puts some kind of garbage on my computer that won't run the program, and if I try using the install wizard to "repair" the installation, it doesn't do anything.  Tracking down the crap it "installs" is really hard, and to make the install wizard behave as if there's nothing on there anymore, I have to delete my whole ~/.wine directory.  Not like I have anything else in there, but it's irritating nonetheless.

What I need is any advice anyone might have -- whether you know about some other (FREE!) way I can run this software, or some way to force it to behave under wine.  Installing a dual-boot is not an option, since I do not have a copy of windows that will run on my system76 laptop (the old copy I have is a recovery disk for dinosaur dell machines).  

Thanks!

---

### Post by hikaricore on 2007-01-02
If you have a copy of any windows version on cd or such, you can install it via VMware Server, which is the free version of VMware which actually emulates a system you can run windows ontop of.

Just curious does your software use DirectX or Direct3d for anytype of rendering?  This isn't supported very well with wine, so this could be your issue.  And what type of error output are you getting when running this software through wine from a terminal?

---

### Post by Doug11 on 2007-01-02
I have a couple of progies that wont run in wine too. As stated above, install a VMware server and install your windows into that. Works like a charm for me.

Here's a good link I used,,  [http://doc.gwos.org/index.php/VMWare_WindowsXP](http://doc.gwos.org/index.php/VMWare_WindowsXP)

---

### Post by rbalfour on 2007-01-02
If it doesn't run under wine properly doubtful there is a "magic" hack to force it.
You could install a Virtual Machine. (vmware, I believe is free to a point) 

I am think there are some Windows XP VMWARE installs floating around somewhere on the Internet.

---

### Post by paridoth on 2007-01-02
> **rbalfour said:**
> 
I am think there are some Windows XP VMWARE installs floating around somewhere on the Internet.

ut oh, you can't talk about stuff like that

---

### Post by cmost on 2007-01-02
Congratulations on your switch to Linux!  Please consider using a LEGAL copy of Windows and run it in VMware, Parallels, QEMU, XEN, or the new KVM (if you processor supports it.)  I find that good ol' Windows 98 Second Edition simply flies in a VM equiped with 512 MB of RAM while being compatible with the majority of Windows software.  Otherwise, you're SOL.  Personally, I use VMWare Workstation for all my virtualization needs and i've never had any issues running Windows that way.

---

### Post by hikaricore on 2007-01-03
> **paridoth said:**
> ut oh, you can't talk about stuff like that

i think you've confused what what said :)

---

### Post by rbalfour on 2007-01-03
> **paridoth said:**
> ut oh, you can't talk about stuff like that

Yes I can, I have seen one VMWARE from Microsoft to Test the new SQL on Windows 2003 server and one with a Vista beta to test apps. Granted both VMware images I have seen have some limited functions. But I am pretty sure you could use them to run one application. If you are implying about Pirated software, I am not. Just to clear that up.

Here is a link to one:

[http://www.vmware.com/vmtn/appliances/directory/649](http://www.vmware.com/vmtn/appliances/directory/649)

Vista was removed, but it was there. The server image should work.

But if your software package requires Windows XP, wait until after Feb 2007, there will be a few online software sellers dumping stock.

---

### Post by polkadotchickens on 2007-01-08
thanks so much everyone!

I now have VMware server up and running Windows XP, and my program is working like a charm.  What I'm wondering now is, how can I transfer files between my real ubuntu machine and my virtual windows machine?  All the images I need to analyze in windows are on my ubuntu machine.

---

### Post by cmost on 2007-01-08
You'll have to setup a private network between the host (Ubuntu system) and the guest (Windows system.)  They appear to each other as two seperate, real workstations.  When you installed VMware Server, you should have had the option to setup and configure a virtual network between the two systems.  Once done, you should be able to configure a shared folder on your host system and then map a drive letter to that on your guest system.  You'll have to setup and configure Samba on Ubuntu, but, it's pretty straightforward.

---

### Post by polkadotchickens on 2007-01-09
I don't think I told it to set up that option during the install.  Is there a way to do it after the fact?

---

