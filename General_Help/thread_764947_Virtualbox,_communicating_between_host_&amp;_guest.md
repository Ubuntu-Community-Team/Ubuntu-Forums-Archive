---
title: "Virtualbox, communicating between host &amp; guest OS"
date: 2008-04-24
forum: General Help
---

### Post by ecs_pf5 on 2008-04-24
I've installed Virtualbox on Kubuntu & installed Microsoft Windows XP as a guest OS. That's all up and running.

Now, I have a USB pen drive plugged in which is mounted okay and visible on the desktop of Kubuntu, but it contains files which I want to somehow place on the virtual XP's desktop.

I've been playing around with Virtualbox's 'shared folders' feature but can't seem to get it to work (maybe it's not what I think it is :confused:

I placed a folder 'VM Shared' on Kubuntu's desktop & specified it in Virtualbox as a shared folder, then tried playing around with variations around 'x:\\vboxsv r\share' on the virtual XP, but to no avail..

Anyone point me in the right direction as I'm a bit lost?

---

### Post by RagingAardvark on 2008-04-24
Have you used "Net use" from XP to map to the shared drive?

---

### Post by ecs_pf5 on 2008-04-24
No but I'll look it up :) thanks for the lead


okay net use on it's own tells me just, 'there are no entries in the list'.

I tried net use "x:\\vboxsvr\VM Shared", but it said 'system error 67, the network name cannot be found'.


Never used 'net use' before so still a bit in the dark..

Guessing the x: should be replaced by something specific to the kubuntu install? or no.. not according to a few googlesearches


I found an instruction to

> 
VBoxManage sharedfolder add "VM name" -name "sharename" -hostpath "C:\test"
which I guess translates for me to


> 
VBoxManage sharedfolder add "Windows XP" -name "vmshared" -hostpath "/home/user/Desktop/vmshared"
(guessing that was intended for use in the kubuntu console?) - but it couldn't find VBoxManage

[edit] ok.. fair do's, it didn't like the capitalisation - it found vboxmanage ok.

but strange output:

```

user@kubuntu:~$ sudo vboxmanage sharedfolder add "Windows XP" -name "vmshared" -hostpath "/home/user/Desktop/vmshared"
VirtualBox Command Line Management Interface Version 1.5.0_OSE
(C) 2005-2007 innotek GmbH
All rights reserved.

[!] FAILED calling aVirtualBox->FindMachine(Bstr(argv[1]), machine.asOutParam()) at line 5957!
[!] Primary RC  = 0x80070057
[!] Full error info present: true , basic error info present: true
[!] Result Code = 0x80070057
[!] Text        = Could not find a registered machine named 'Windows XP'
[!] Component   = VirtualBox, Interface: IVirtualBox, {76b25f3c-15d4-4785-a9d3-adc6a462beec}
[!] Callee      = IVirtualBox, {76b25f3c-15d4-4785-a9d3-adc6a462beec}
user@kubuntu:~$


```

here's the details of the VM I set up;

> 
General
Name: Windows XP
OS Type: Windows XP
Base Memory: 1280 MB
Video Memory: 128 MB
Boot Order: Floppy, CD/DVD-ROM, Hard Disk
ACPI: Enabled
IO APIC: Disabled
 
Hard Disks
Primary Master: XP.vdi [Normal, 20.00 GB]
 
CD/DVD-ROM
Image: VBoxGuestAdditions_1.5.0_OSE.iso
 
Floppy
Host Drive: /dev/fd0
 
Audio
Adapter: OSS Audio Driver
 
Network
Adapter 0: NAT
 
Serial Ports
Disabled

Shared Folders
Shared Folders: 1




[edit] wait a minute, 'Guest Additions' isn't set up. It downloaded.. It mounted.. but I never realised it was something that then needed actually installing inside the guest OS (doh)..


okay that seems to have given me an item 'VirtualBox Shared Folders' under 'Entire Network' in XP's 'Network Places'. But, there's nothing in it. And, 

> 
sudo vboxmanage sharedfolder add "WinXP" -name "vmshared" -hostpath "/home/user/Desktop/vmshared"


Is still saying it can't find a registered machine called WinXP

(I did change the name of the VM) 





oh wait, it's suddenly started working. sudo vboxmanage etc etc.. never did succeed, it seems to have started working by itself despite that.

\\VBOXSVR\vmshared appeared inside 'VirtualBox Shared Folders' under 'Entire Network' in XP's 'Network Places' - sometime after positively installing the Guest Additions thing inside XP.





If anyone can explain & clarify how all this works, what's actually needed & what's not, would be interested to hear. I've gotten it working by muddling through here but really am none the wiser & it's be good to know the correct procedure :)



Thanks Aardvark for setting me on the right track

---

