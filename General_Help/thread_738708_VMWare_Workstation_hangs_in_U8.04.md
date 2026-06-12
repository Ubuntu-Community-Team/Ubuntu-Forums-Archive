---
title: "VMWare Workstation hangs in U8.04"
date: 2008-03-28
forum: General Help
---

### Post by wcorey on 2008-03-28
Workstation 6 worked fine under Ubuntu until something happened earlier today and now starting a vm, any vm, immediately completely freezes Ubuntu 8.04 right after the hint to remember to install VMWare tools. The only thing I did was install libvirtd and kvm as the kvm manager wouldn't start and a forum solution was to install those two packages. I removed those two packages, removed and reinstalled VMWare Workstation, re configured VMWare Workstation and still as soon as the 'remember to install vmware tools' dialog box OK is clicked the interrupts are disabled and the machine locks/freezes/hangs/goes into a soft wait with interrupts disabled. Are there any solutions out there? I am not sure if this is the best forum but hopefully this can be moved if it isn't. I found nothing under VMWare to help. 

TIA,

Walt

---

### Post by wcorey on 2008-03-29
Now I have a slightly different problem. I thought if I completely removed workstation and reinstalled it would resolve the issue. It appears to not have been completely uninstalled as there are remnants in /etc and the system tools menu still has vmware workstation and vmware player still listed even though they don't exist as binaries. What's more is I can not reinstall as that fails in the install script.

(Reading database ... 100684 files and directories currently installed.)
Unpacking vmwareworkstation (from vmwareworkstation_6.0.3-80005_amd64.deb) ...
[: 882: ==: unexpected operator

dpkg: error processing vmwareworkstation_6.0.3-80005_amd64.deb (--install):
 subprocess pre-installation script returned error exit status 1
[: 45: Illegal number: abort-install
Errors were encountered while processing:
 vmwareworkstation_6.0.3-80005_amd64.deb


I am very much hoping someone knows how to resolve these two issues.

---

### Post by jerrylin on 2008-03-30
I have the same problem. I have KVM stuff installed as well. As soon as I try to start any virtual machine, my whole system freezes.

I'm just curious, where did you get the .deb for VMware Workstation?

---

### Post by wcorey on 2008-03-30
> **jerrylin said:**
> I have the same problem. I have KVM stuff installed as well. As soon as I try to start any virtual machine, my whole system freezes.

I'm just curious, where did you get the .deb for VMware Workstation?

There is a Ubuntu (or at least 8.04) program called alien that converts an rpm into a deb. 

It took Friday night and most of Saturday to circumvent the issue but I am not happy with the results. VMWare now works again though. The short version of what I did was go into my bios and disable virtualization support. Some call thiis disabling virtualization in the kernel, no it is turning off Intel_VT. There was one entry in a thread like this that referenced a module in the kernel that was the thrust of the problem. I don't recall the name and I can not find the board thread I found yesterday. If I had found that thread Fri I never would have uninstalled VMWare but, the module I believe was called something like rmmon or rtmon and it was activated when I used Symantic to install KVM, LIBVirt and one other. For reference in the Ubuntu thread that has libvirtd and kvm it refers to the third package to install in order to get KVM working in Hardy to begin with. One of them brought down this kernel module that VMWare can not deal with causing the kernel to lock up, softwait, hang, freeze, whatever. There is nothing a user should be able to do to cause an OS to hang. That VMWare causes the Linux OS to hang I believe is a major bug in VMWare Workstation. This is the rationale of the whole Intel ring architecture.  Granted, VMWare does not run in ring 3 but because of that it should be extremely well behaved and NEVER force the kernel into a softwait with interrupts disabled. OK, sorry, I am editorializing rather than answering your question. This does need to be investigated further as VMWare workstation should not preclude the use of KVM nor should it require Intel_VT to be disable. Oh, yes, so by disabling Intel VT (turning Virtualization off in the BIOS) the rmmon or whatever module interacting with VMWare never gets loaded. If you pursue this, and please do, and find out the name of that module and/or a definitive VWWare solution please convey that back to me.

Thanks and I hope this helps you,

Walt

---

### Post by wcorey on 2008-03-30
I found the other thread message (This from the VMWare site: 

[I]The actual problem is the new kvm module in fedora 7
when VT is on, the kvm_intel module is inserted by default.
then vmware will freeze.
If VT is tunred off ( I heard for AMD, it's always on), the kvm_intel will fail to lanch so that vmware runs fine.
In summary, rmmod kvm_intel before you run vmware should alwasy do the trick.
[/I]

---

### Post by Ace2016 on 2008-03-30
Have you tried VirtualBox? it has proper debs for ubuntu

Its always been faster than vmware for me

---

### Post by wcorey on 2008-03-30
> **Ace2016 said:**
> Have you tried VirtualBox? it has proper debs for ubuntu

Its always been faster than vmware for me

I did come across this:
[http://ubuntuforums.org/archive/index.php/t-594881.html](http://ubuntuforums.org/archive/index.php/t-594881.html) 

which is very interesting. Frankly, I was interested in VMWare Workstation due largely to name recognition. Based upon those benchmarks it is 100% slower than KVM, VirtualBox etc. Definately cause for pause. 

What I am interested in is an industrial strength environment to virtualize, at least initially, several WinXP boxes I want to consolidate away. One thing Microsoft has been extraordinarily bad at is migrating applications as people move up the WinTel trail. One solutoin is to strip the WinXP (in this case) environment down to only that which is essential to support the application(s) being migrated to newer (faster) hardware and then virtualizing the remaining 'box' to a small tight VM. I don't need multiple versions of Word or IE, I just need the application(s) I want to continue using, the requisite registry that has the object registrations necessary and enough of the OS to run it. As for the virtualization software I'd like it to be small, lightweight, fast (as transparent as possible) and something that will be supported going forward. I did notice as far as VirtualBox that Sun just bought the company. That bodes well for it but KVM being part of Linux bodes well for it as well. I am a little concerned VirtualBox says hardware support gets in the way. I thought the reason Intel and AMD added support for virtualiation was to get it out of the OS and application layer. It sounds like VirtualBox is rationalizing why they don't take advantage of it. And touting OS/2 in their marketing? That's so 80's. 

To go back to the issue of this thread for a moment, once I disabled hardware virtualization the XP guests now run noticeably slower.

---

### Post by jerrylin on 2008-03-31
I've had incredibly terrible guest OS performance with VirtualBox... I dunno what it is but I used to get slow performance every few seconds then it'd return to normal, then slow again. So when you scrolled down a webpage it'd do nothing for a few seconds then fly down the page all at once.

I looked this up and tried a few things to fix it... ultimately I tried VMware Workstation and had no problems.

---

### Post by jerrylin on 2008-03-31
Corey,

Thanks for the post. I have solved my freeze-up problem. It is simply to remove the KVM module (I did not remove libvirt or any of those other modules). 

This is an alternative to disabling Intel_VT. Does KVM even work if you have Intel_VT disabled?

---

### Post by wcorey on 2008-03-31
> **jerrylin said:**
> Corey,

Thanks for the post. I have solved my freeze-up problem. It is simply to remove the KVM module (I did not remove libvirt or any of those other modules). 

This is an alternative to disabling Intel_VT. Does KVM even work if you have Intel_VT disabled?

It shouldn't, I haven't tried it as KVM, to my knowledge, requires hardware virtualization. OK, so when you say you removed the kvm module do you mean remove the package, permanently removed the package, or did an rmmod on it, or modprobe remove? I saw a reference to rmmod but wasn't clear if that would remove part of the kernel, permanently remove the ability to run with it or what? 

Could you elaborate? As I said earlier I would be interested in trying KVM but, at present, it seems like a lot of work to create a vm. My earlier experience with kvm was with Fedora 8 and it was a joke. The cursor and mouse pointer were in different locations and I had to coax the cursor (a finger) to go where I wanted it to. I also had no connectivity to my NAS unit and could not use the cdrom to boot from. I believe the behavior in U8.04 is much improved over Fedora8. So if you could elaborate on removing the kvm module I would appreciate it. From what I gather VMWare Workstation does not use hardware virtualization but once I turned it off in the bios Workstation ran but was embarrassingly slow. For $189 I do not want embarrassingly slow.

Thanks!

Walt

---

