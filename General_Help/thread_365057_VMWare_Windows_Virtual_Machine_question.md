---
title: "VMWare Windows Virtual Machine question"
date: 2007-02-19
forum: General Help
---

### Post by mjpatey on 2007-02-19
I want to access my Windows desktop inside Ubuntu using VMware.  Here's my understanding of what I'm about to do.  Please correct me if I'm wrong...

I'm about to use VMware Converter to "convert" my Windows desktop into something that VMware Server can use in Ubuntu.  In Ubuntu, I'll run the server program that will be able to access my Windows install and do all the things I want to do in Windows, inside a VMware window in Ubuntu.

Now here's my big question:  when I "convert" my Windows install into a virtual machine, does this mean that my Windows install will no longer be accessible by the traditional means?  Will I only have access to it from within VMware Server in Ubuntu?  This is crucial to me... I absolutely have to be able to access my Windows install normally after this process, or I can't do it.  It would freak out my wife.  :-)

In other words, does this do something permanent to my Windows installation that would prevent me from booting into it normally again?

Also, will this process even work in my case?  Ubuntu and the Windows install I want to virtualize are on the same machine.  Do they have to be on separate machines on a LAN or something, or will this work for me?

Thanks for any insight you may be able to offer!

-Mark

---

### Post by veloce on 2007-02-19
It's been done and described here, do a bit of searching here on the forum.  

What you are trying to do is create a virtual machine that uses a physical disk - your windows partition. key words are probably **vmware** and **physical.**

This is analogous to taking the windows disk and putting it in a different machine, so I have heard of issues with that horrible windows copy protection stuff.  I'm also unsure whether that upsets windows for when you want to go back.  However, there are people on the list who have described this exact setup.

Good luck.

---

### Post by mjpatey on 2007-02-19
Thanks, I'd tried that but with slightly different keywords... using "physical" narrowed it down somewhat, but all I can find is people needing help setting it up.

All I really need to know is whether this process "does something" to my Windows install.  Does it leave it alone, just creating hooks into it, or does it modify it in some way to make it accessible only from VMware, which makes it impossible to boot into Windows the normal way?

Thanks for any help you may have!

-Mark

---

### Post by ayates on 2007-02-19
I might be wrong on this, but from what I have read, the converter will make a disk file image of your Windows system. This can be accessed from Linux through Vmware(server, player,etc.). I don't think it will mess up your Windows installation and you should be able to boot it normally. But any changes you make to the Vmware Windows image will not reflect on your "real" Windows installation and vice versa.

---

### Post by mjpatey on 2007-02-19
Ah!  Good to know.  I was wondering how it would work if it DID allow you to actually modify the real files.

Anybody have an opinion as to whether VMware is the best way to go?  My setup is a bual-boot Windows and Ubuntu, and my goal is to run my existing Windows install from within Ubuntu.  What about VirtualBox?  Qemu?

Thanks!

-Mark

---

### Post by useResa on 2007-02-19
> **mjpatey said:**
> I want to access my Windows desktop inside Ubuntu using VMware. Here's my understanding of what I'm about to do. Please correct me if I'm wrong...

I'm about to use VMware Converter to "convert" my Windows desktop into something that VMware Server can use in Ubuntu. In Ubuntu, I'll run the server program that will be able to access my Windows install and do all the things I want to do in Windows, inside a VMware window in Ubuntu.
This depends on what you are using. If you use VMware Player you require a pre-made image of a Windows installation.
If you make use of VMware Server you basically create your own virtual machine in which you can install Windows by using the set-up CDRom.
Just like a regular install but the machine is "virtual".

> **mjpatey said:**
>  Now here's my big question: when I "convert" my Windows install into a virtual machine, does this mean that my Windows install will no longer be accessible by the traditional means? Will I only have access to it from within VMware Server in Ubuntu? This is crucial to me... I absolutely have to be able to access my Windows install normally after this process, or I can't do it. It would freak out my wife. :-)
The Windows that you create in the VM will only be accessible  from within Ubuntu since this is the host in which the VM runs. No host, no VM.

> **mjpatey said:**
>  In other words, does this do something permanent to my Windows installation that would prevent me from booting into it normally again?From a later reply by yourself I understand that you have a dual-boot. The installation that is part of the dual boot and the installation in the VM are NOT related or connected. So changes to the one will not influence the other. If this is your question.

> **mjpatey said:**
>  Also, will this process even work in my case? Ubuntu and the Windows install I want to virtualize are on the same machine. Do they have to be on separate machines on a LAN or something, or will this work for me?You can all this on one machine, but you need one main OS that runs as the host. In this host you can create (provided you have sufficient space) several virtual machines. For example, I have Ubuntu Edgy as a main OS (host) and have separate virtual machines for Windows XP SP2, PCLinuxOS 2007, Debian SID and one for Ubuntu Feisty.

> **mjpatey said:**
> Anybody have an opinion as to whether VMware is the best way to go?  My setup is a bual-boot Windows and Ubuntu, and my goal is to run my existing Windows install from within Ubuntu.  What about VirtualBox?  Qemu?
IMHO this is like asking whether Porsche is the best sports car. What I am trying to say is that each person has it preferences. I have always used VMware Server and are pleased with it.
Ask someone else and maybe they maybe advise Qemu.

---

### Post by Patrick K on 2007-02-19
useResa, can the VM Win installation read and write to the original Win installation's file system? In other words, can they share data? 

Just an example, the original has some image file on it's file system (FAT32 or NTFS) accessed by, say ACDSee. If ACDSee is installed on the VM Win install, can it access the files on the other system? Would the file system, FAT32 or NTFS, on the old Win matter? 

Since they are separate installations, would they, could they be networked together? 

Just trying to figure out how one could share existing data with the other.

---

### Post by veloce on 2007-02-19
> **Patrick K said:**
> 
Since they are separate installations, would they, could they be networked together? 

Just trying to figure out how one could share existing data with the other.

If all you want to do is share data between two os on a dual boot system, then I wouldn't suggest using vitualisation at all. The easiest way to do this is to have a Fat32 partition available to both os.  

If you want to be able to **change** the data with a windows program without leaving ubuntu, then you have two choices.  

[LIST=1]
[*]The one you've been chasing down - a vm operating under vmware server on ubuntu that uses the windows partition set up as a physical disk.  This runs a risk (of uncertain magnitude) that you will harm your windows partition. 

[*]A "normal" windows vm.  This would have a virtual hard drive stored somewhere on you ubuntu system on which you install the windows operating system.  
[/LIST]

Either way, the best way to access the fat32 drive is to share it with samba on the ubuntu host, then the vm can access it via a virtual "host only network" set up by vmware server.

---

### Post by useResa on 2007-02-19
> **Patrick K said:**
> useResa, can the VM Win installation read and write to the original Win installation's file system? In other words, can they share data?
Just to get your question right, can you please confirm the following:
Do you want to maintain the dual-boot installation (Windows and Ubuntu) and in Ubuntu you want to create a virtual machine in which you also want to install Windows.
Once you have achieved this, you would like to exchange data between the "dual-boot windows" and the "virtual windows".

Is my understanding of your question correct?

Or do you just want to exchange data between Ubuntu (host) and Windows (guest in VM)?

---

### Post by kbracer on 2007-02-19
I ran across this article on Digg today. Might be of help to you...
[B]
Convert Physical Windows Systems Into Virtual Machines To Be Run On Linux[/B]

[http://www.howtoforge.com/vmware_converter_windows_linux]("http://www.howtoforge.com/vmware_converter_windows_linux")

---

### Post by RikoW on 2007-02-20
Hi :)

just stumbled across the thread. I do have a dual boot Windows XP and Ubuntu Dapper Laptop. Under Ubuntu, I'm running VMware Workstation, which can boot the dual boot windows from the windows partition. Which means all changes/installation etc I do to XP in vmware will be available the next time I boot the laptop to windows. There is no virtual image created, which of course would use up lots of disk space. Works fro me since month flawlessly .... haven't booted the laptop to windows since then :)

Before you ANYTHING, you have to boot to windows and create a new hardware profile (Control Panels -> System -> Hardware). Just copy one which is there and make sure by the appropriate option, that you select your HW profile during boot-up.

How to do this and how to set-up vmware is described here:

[http://www.vmware.com/support/ws55/doc/disks_dualmult_ws.html]("http://www.vmware.com/support/ws55/doc/disks_dualmult_ws.html")

This is for VM workstation, which I use and it works. Don't know if you can do it with the Server version, too. It's probably a good idea to check the vmware forums for that:

[http://www.vmware.com/community/category.jspa?categoryID=21]("http://www.vmware.com/community/category.jspa?categoryID=21")

Good luck! I felt very un-easy when I did that and tried to boot XP the first time VMware :)

Cheers,

                    Riko

---

### Post by Patrick K on 2007-02-20
> **useResa said:**
> Just to get your question right, can you please confirm the following:
Do you want to maintain the dual-boot installation (Windows and Ubuntu) and in Ubuntu you want to create a virtual machine in which you also want to install Windows.
Once you have achieved this, you would like to exchange data between the "dual-boot windows" and the "virtual windows".

Is my understanding of your question correct?

Or do you just want to exchange data between Ubuntu (host) and Windows (guest in VM)?

The first option you mentioned. Keep the the dual boot (I have apps I use that are no longer available and I don't have the installation programs anymore. Some have been patched and the patches are no longer available) and exchange data between the two.

Another question. Is the VM Windows installation just as vulnerable to malware as a standalone install? If so, AV and a firewall would be needed, correct?

---

### Post by Patrick K on 2007-02-20
> **kbracer said:**
> I ran across this article on Digg today. Might be of help to you...
[B]
Convert Physical Windows Systems Into Virtual Machines To Be Run On Linux[/B]

[http://www.howtoforge.com/vmware_converter_windows_linux]("http://www.howtoforge.com/vmware_converter_windows_linux")

Thanks for the link. That looks like a great way to go. Too bad I don't have XP. I'm still with W98.

---

### Post by useResa on 2007-02-20
> **Patrick K said:**
> The first option you mentioned. Keep the the dual boot (I have apps I use that are no longer available and I don't have the installation programs anymore. Some have been patched and the patches are no longer available) and exchange data between the two.
This goes a bit beyond my knowledge, but maybe someone else will know this for sure. My current idea is that you will not be able to do so and let me explain why I think so.
My understanding is that the Windows session must be up and running in order to be able to "see" a shared directory. If you are running your Windows session in the VM you will NOT have your Windows session running but your Ubuntu session.
As such I think in order to share data you should have a separate partition (as indicated earlier) which you can share using Samba.
But once again: It is a bit beyond my knowledge so please get this confirmed.

> **Patrick K said:**
>  Another question. Is the VM Windows installation just as vulnerable to malware as a standalone install? If so, AV and a firewall would be needed, correct?
AFAIK it is just a vulnerable therefor I have AV and a firewall set up (after all it is still Windows albeit in a VM)

---

### Post by Patrick K on 2007-02-20
Thanks, I see your point. Makes sense. So no active exchange of data but probably able to access the same data via a shared partition. This is actually something I am now doing between W98 and Ubuntu.

---

### Post by useResa on 2007-02-20
> **Patrick K said:**
> Thanks, I see your point. Makes sense. 
Thank you, but please be aware that this is just how I see it.
The actual situation may be different.

> **Patrick K said:**
> So no active exchange of data but probably able to access the same data via a shared partition. This is actually something I am now doing between W98 and Ubuntu.
AFAIK If you can access this shared partition from Ubuntu you will also be able to access it from Windows in VM.

---

### Post by veloce on 2007-02-20
> **Patrick K said:**
> 
Another question. Is the VM Windows installation just as vulnerable to malware as a standalone install? If so, AV and a firewall would be needed, correct?

This depends on whether the vm has any connection to the outside world.  I run some vms with no virtual network card - no point having a firewall on those.  I have others configured to use host only networking and have another vm acting as a firewall for all of them. (IPCop + blockouttraffic in a vm with just 32Mb ram works really well).

I don't use av on any of them.  If a vm got a virus I'd delete the whole vm.  It's more efficiecnt for me to keep a backup of the vm rather than criple it's performance at certain tasks with av software.

---

### Post by veloce on 2007-02-20
> **Patrick K said:**
> The first option you mentioned. Keep the the dual boot (I have apps I use that are no longer available and I don't have the installation programs anymore. Some have been patched and the patches are no longer available) and exchange data between the two.


This is an excellent reason to create a virtual copy of your windows machine.  If you are then able to run everything in the virtual environment, you have a backup if anything happens to your windows system - which, given that it's win98 is just a matter of time.  Once you have this vm working - make a backup copy of it! vms can be copied easily - just copy the entire directory in which it is stored. 

If your windows is win98 then there is no need for a separate partition either - I was thinking it would be ntfs which can be a pain.  Just make sure you can read and write to the directories in the windows partition from Ubuntu, then share them using samba. 

(In fact, once you've got to that stage you can do away with the windows partition entirely, set vmware to start automatically on login and your users who must have windows can use windows straight from there!)

---

### Post by Patrick K on 2007-02-21
Thanks for the reply. I may give it a try pretty soon. BTW, this install of W98 has been very robust. The original install from 1998 is still running and is on it's 2nd motherboard (new video card, new memory, etc.) and 3rd set of drives. 

I was looking at VMware Converter Starter but it doesn't support W98. So I don't know how to virtualize the existing W98 install. This is what I would like to do, though.

---

### Post by useResa on 2007-02-21
> **Patrick K said:**
> I was looking at VMware Converter Starter but it doesn't support W98. So I don't know how to virtualize the existing W98 install. This is what I would like to do, though.
Well, actually they are not saying it is not supported. They indicate it is Experimental.
> 
**Supported Guest Operating Systems**

   The following 32-bit guest operating systems are fully supported by VMware Converter 3: [LIST]
[*]Windows NT
[*]Windows 2000 Professional
[*]Windows 2000 Server
[*]Windows XP Professional
[*]Windows 2003 Server[/LIST]Support for the following guest operating systems is Experimental. VMware Converter 3  can clone source images containing these operating systems, but the destination virtual machine  may or may not work without additional configuration after import. In particular, if the source image  contains unsupported hardware, you may need to modify the configuration of the destination  virtual machine before using it: [LIST]
[*]Linux
[*]Windows NT 3.x
[*]Windows ME
[*]Windows 98
[*]Windows 95
[*]MS-DOS
[*]64-bit guest operating systems[/LIST]Source: [http://www.vmware.com/support/converter/doc/releasenotes_conv3.html](http://www.vmware.com/support/converter/doc/releasenotes_conv3.html)

IMHO you could try the converter and build a VM from your W98 installation and see if it works BEFORE you remove your W98 installation.

---

### Post by djheadley on 2007-02-21
I'm dual booting with WinME (don't ask) and would also like to know how to make that partition a VM so eventually I could do away with it.

---

### Post by useResa on 2007-02-21
> **djheadley said:**
> I'm dual booting with WinME (don't ask) and would also like to know how to make that partition a VM so eventually I could do away with it.
I guess in your case the same applies as I have posted in reply [#20](http://www.ubuntuforums.org/showpost.php?p=2189688&postcount=20).
The support for WinME is Experimental. You could give it a try, but no guarantees are given ;)

---

### Post by Patrick K on 2007-02-21
I guess I missed the experimental part. That sounds like a pretty good plan. I just want to make sure my existing W98 remains undamaged. If it works in the VM, great, if not I shouldn't be any worse off. I'll need to find out how to make an "image" of the installation.

---

### Post by useResa on 2007-02-21
> **Patrick K said:**
> I guess I missed the experimental part. That sounds like a pretty good plan. I just want to make sure my existing W98 remains undamaged. If it works in the VM, great, if not I shouldn't be any worse off. I'll need to find out how to make an "image" of the installation.
There is a very clear - three page - explanation available of which [this](http://www.howtoforge.com/vmware_converter_windows_linux) is the first page.

---

### Post by useResa on 2007-02-22
From what I have "heard" Virtualbox, a top-notch Virtualization software like VMware, has recently been GPL-ed and will come fully integrated with Ubuntu 7.04 (as a result of talks between Innotek and Canonical).
 
I have not (yet) tried Virtualbox, but due to the fact that it may come integrated with Ubuntu it may be wise(r) to use this instead of VMware Server.
 
More information on the product can be found [here](http://www.virtualbox.org/).

---

### Post by Patrick K on 2007-02-22
Too bad it doesn't support W98. A good looking option for other OS's, though.

---

### Post by gabng on 2007-02-22
Hi, I would like to achieve somewhat the same goal.  I noticed the following post earlier in this thread:

> **RikoW said:**
> Hi :)

just stumbled across the thread. I do have a dual boot Windows XP and Ubuntu Dapper Laptop. Under Ubuntu, I'm running VMware Workstation, which can boot the dual boot windows from the windows partition. Which means all changes/installation etc I do to XP in vmware will be available the next time I boot the laptop to windows. There is no virtual image created, which of course would use up lots of disk space. Works fro me since month flawlessly .... haven't booted the laptop to windows since then :)

Before you ANYTHING, you have to boot to windows and create a new hardware profile (Control Panels -> System -> Hardware). Just copy one which is there and make sure by the appropriate option, that you select your HW profile during boot-up.

How to do this and how to set-up vmware is described here:

[http://www.vmware.com/support/ws55/doc/disks_dualmult_ws.html]("http://www.vmware.com/support/ws55/doc/disks_dualmult_ws.html")

This is for VM workstation, which I use and it works. Don't know if you can do it with the Server version, too. It's probably a good idea to check the vmware forums for that:

[http://www.vmware.com/community/category.jspa?categoryID=21]("http://www.vmware.com/community/category.jspa?categoryID=21")

Good luck! I felt very un-easy when I did that and tried to boot XP the first time VMware :)

Cheers,

                    Riko

Riko, can you elaborate more on how you set this up?

---

### Post by useResa on 2007-02-22
> **Patrick K said:**
> Too bad it doesn't support W98. A good looking option for other OS's, though.Sorry, totally forgot to check this.

---

### Post by RikoW on 2007-02-23
Hi,

> **gabng said:**
> Hi, I would like to achieve somewhat the same goal.  I noticed the following post earlier in this thread:
 [...]
Riko, can you elaborate more on how you set this up?

There isn't really much to elaborate! It's all described in the first link I provided and I just followed it. I don't remember, that I had to do anything special. There are two pieces of advise, though, I could give:

1) after you created a new hardware profile by copying under windows as described in the vmware instructions, boot again into windows and check that you can select between the different profiles during the boot process. After you selected windows in the grub menu, another text screen will appear that should ask you which profile to start. Boot into the new profile. Doesn't matter. When booting via vmware later, all the appropriate driver will to replaces with the virtual machine drivers.

2) After I set-up the virtual machine under vmware to boot the physical windows partition and I tried to boot for the first time (using this 'virtual' profile), I got a blue screen flashing and the virtual machine shut down without booting. That apparently has something to do with the ide driver for the harddrive. follow this link to fix that:

[http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=36&sliceId=SAL_Public]("http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=36&sliceId=SAL_Public")

Remember to boot into the profile, that you select for you virtual machine to change this driver. The profile for the dual boot will be untouched.

Again, just follow the instructions  in the manual to boot your dual boot windows in vmware workstation.

[http://www.vmware.com/support/ws55/doc/disks_dualmult_ws.html]("http://www.vmware.com/support/ws55/doc/disks_dualmult_ws.html")

I'm VERY happy with my set-up now. During the set-up, you are asked how much ram the virtual machine should have. Leave at least 300 MB for you Ubuntu host (that's on dapper), otherwise things will be painfully slow when you run vmware.

Report back with (hopefully) success or in case of problems (maybe start a new thread then) - good luck! :)

- Riko

---

### Post by Patrick K on 2007-02-23
I visited the VMware forum to ask if anyone had successfully converted W98. I am totally inhibited about asking there. It seems everyone is a heavy hitter. All IT pros. I could just see myself posting "Hi, nubee here, anyone converted W98 on their home computer?" These guys are all talking about converting scores and sometimes hundreds of computers. Oh well, maybe I'll screwup my courage and give it a shot.

---

### Post by useResa on 2007-02-23
> **Patrick K said:**
> I visited the VMware forum to ask if anyone had successfully converted W98. I am totally inhibited about asking there. It seems everyone is a heavy hitter. All IT pros. I could just see myself posting "Hi, nubee here, anyone converted W98 on their home computer?" These guys are all talking about converting scores and sometimes hundreds of computers. Oh well, maybe I'll screwup my courage and give it a shot.
Then you haven't -- obviously -- seen my posts at this forum ;) 
 
Don't worry too much about feeling a newb/n00b, if I have a question I just ask it.
I would suggest to just do the same (I did and most answers were helpful).
My suggestion is just to post the question in the [Converter forum](http://www.vmware.com/community/forum.jspa?forumID=357) if someone has succesfully used the Converter on a Windows 98 installation.
 
The other option -- indeed -- is just to toss your fears away and try the Converter.
 
Regardless what you choose, good luck!

---

### Post by gabng on 2007-02-24
> **RikoW said:**
> Hi,



There isn't really much to elaborate! It's all described in the first link I provided and I just followed it. I don't remember, that I had to do anything special. There are two pieces of advise, though, I could give:

1) after you created a new hardware profile by copying under windows as described in the vmware instructions, boot again into windows and check that you can select between the different profiles during the boot process. After you selected windows in the grub menu, another text screen will appear that should ask you which profile to start. Boot into the new profile. Doesn't matter. When booting via vmware later, all the appropriate driver will to replaces with the virtual machine drivers.

2) After I set-up the virtual machine under vmware to boot the physical windows partition and I tried to boot for the first time (using this 'virtual' profile), I got a blue screen flashing and the virtual machine shut down without booting. That apparently has something to do with the ide driver for the harddrive. follow this link to fix that:

[http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=36&sliceId=SAL_Public]("http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=36&sliceId=SAL_Public")

Remember to boot into the profile, that you select for you virtual machine to change this driver. The profile for the dual boot will be untouched.

Again, just follow the instructions  in the manual to boot your dual boot windows in vmware workstation.

[http://www.vmware.com/support/ws55/doc/disks_dualmult_ws.html]("http://www.vmware.com/support/ws55/doc/disks_dualmult_ws.html")

I'm VERY happy with my set-up now. During the set-up, you are asked how much ram the virtual machine should have. Leave at least 300 MB for you Ubuntu host (that's on dapper), otherwise things will be painfully slow when you run vmware.

Report back with (hopefully) success or in case of problems (maybe start a new thread then) - good luck! :)

- Riko

I was having BSOD at the Windows booting screen, and your second tip was what fixed it for me, to there was something to elaborate on! :P  Thanks!  Now I can run my Windows partition within Ubuntu!  Together with what's suggested in this [thread]("http://www.ubuntuforums.org/showthread.php?t=361528") it'll be perfect!

To the OP, in VMware server, when creating a VM, I see the option of Windows 98 in the guest OS selection.  I'd imagine that would mean it will support it.  But regarding running the Win 98 from the physical partition, you'll have to take some chances.  Good luck and let us know how it goes!

---

### Post by RikoW on 2007-02-24
> **gabng said:**
> I was having BSOD at the Windows booting screen, and your second tip was what fixed it for me, to there was something to elaborate on! :P  Thanks!  

[...]



Well, my second tip actually also comes from the vmware instructions, if you read all the way to the end :) But since I thought the BSOD was kind of a scary experience, I decided to provide help from the start :)

Glad I could help! Enjoy your virtual-physical windows install,

                     Riko

---

