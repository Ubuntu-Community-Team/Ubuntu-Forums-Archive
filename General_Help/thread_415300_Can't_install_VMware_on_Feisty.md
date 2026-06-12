---
title: "Can't install VMware on Feisty"
date: 2007-04-20
forum: General Help
---

### Post by froggy on 2007-04-20
```
# uname -a
Linux tadpole 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

```

When I run ./runme.pl from vmware-patch-any-any
```
# cd vmware-any-any-update109
root@tadpole:/home/froggy/vmware/vmware-any-any-update109# ./runme.pl 
Updating /usr/bin/vmware-config.pl ... corrupted
Updating /usr/bin/vmware ... No patch needed/available
Updating /usr/bin/vmnet-bridge ... No patch needed/available
Updating /usr/lib/vmware/bin/vmware-vmx ... No patch needed/available
Updating /usr/lib/vmware/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/usr/lib/vmware/modules/source" has been updated.

```
Them vmware-config.pl crashes.

Any suggestion?

Thanks

---

### Post by kpkeerthi on 2007-04-20
Same here after upgrading to Feisty. See [http://ubuntuforums.org/showthread.php?t=415062](http://ubuntuforums.org/showthread.php?t=415062)

Someone in the above thread posted that VMWare **workstation** 6 Beta works in feisty. Does anyone know if I would be able to use the virtual machine files (.vmdk) I created with VMware **server** in workstation. I do not want to reinstall windows over again.

---

### Post by edweird13 on 2007-04-20
Yeah Ive been using workstation 6 beta for about a month now

---

### Post by sphatiga on 2007-04-20
The any-any patch just worked fine for me.

I had to run the vmware-config.pl first. Then it will abort when it gets to the compiling the vmmom module. 

I then ran the runme.pl from the any-any patch and got the same output as the OP did except for the vmware-config.pl being corrupted. That is probably your problem. I redownloaded the vmware server from their website and did a fresh install of fiesty. So I'm not sure if you guys are trying to do an update or not. 

But it worked fine with a clean install of fiesty and a clean vmware-config.pl

```

Updating /usr/bin/vmware-config.pl ... now patched
Updating /usr/bin/vmware ... No patch needed/available
Updating /usr/bin/vmnet-bridge ... No patch needed/available
Updating /usr/lib/vmware/bin/vmware-vmx ... No patch needed/available
Updating /usr/lib/vmware/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/usr/lib/vmware/modules/source" has been updated.

Before running VMware for the first time after update, you need to configure it 
for your running kernel by invoking the following command: 
"/usr/bin/vmware-config.pl". Do you want this script to invoke the command for 
you now? [yes] yes


```

---

### Post by froggy on 2007-04-20
Actually this was a clean, new install, no upgrade. I first did run vmware-install.pl which aborted, then downloaded the vmware-any-any 10.9 patch and tried to run it.

I am not installing vmware server, but 5.5.3 workstation.

BTW, can you run Windows XP inside vmware server? I have 1 critical application that only runs under M$.

Thanks

---

### Post by sphatiga on 2007-04-20
yep I use vmware server for windows xp . I myself have one app that is still windows only that I have to use unfortunately.

If for some reason you have to use vmware workstation, from what I've heard the 6.0 beta works in fiesty. I'm not sure of what the difference is between the workstation and server vmware programs, but server works fine for virtualizing Winxp.

---

### Post by sewmyheadon on 2007-04-20
I also run Win XP inside of VMWare Server, but so far, only on Edgy.  It's splendid - even faster than running natively on the machine.

I'm really curious to see how VMWare runs on Feisty, though.  I read about the VMI enhancements for server and wonder if it's easy, or automatic, to install this technology on Feisty.  Sounds like it offers better Kernel support of virtualization, making it faster.

---

### Post by kpkeerthi on 2007-04-20
The [any-any-jumbo-bimbo]("http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0") fix worked for me. phew! It saved me from reinstalling vmware and windows. I hate to reinstall.

---

### Post by rbmorse on 2007-04-20
I can tell you the Vmware workstation 6 RC works spectacularly on Feisty. Install from the tarball is absolutely clean.  Picks up existing VMs just fine, but for Windows the situation will get complicated as there are enhancements for VMs created from Workstation 6 to be had. There is a converter...it did not work very well in the Beta but I have not tested the one in the RC. IMOH, the improvements will merit reinstalling Windows (something I was convinced was far, far behind me).

---

### Post by fjm03 on 2007-04-21
The [COLOR=Red]any-any patch[/COLOR] solved the big problem (no VMware Server) after upgrading from Edgy to Feisty, but it also removed the VMware Server launcher from the Applications >>Systems Tools menu path that survived the upgrade from Edgy to Feisty.

The VMware Server can now  only be launched from a terminal after the following disclaimer is displayed:[B] /usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
[/B] 
The VMware Server, installed under Edgy, is no longer recognized as an installed application under Fiesty and therefore a launcher  can't be added to either the Applications menu or the Gome Panel.

---

### Post by sewmyheadon on 2007-04-21
Can you reinstall VMWare Server without too much hassle?

---

### Post by Neo40 on 2007-04-21
I have installed Vmware Workstation 6.0 Beta. Then I created a win98 virtual machine but after installed win98 and "rebooted" I get this error message:
```

While initializing device VMCPD:

Windows protection error. You need to restart your computer.
```

Any idea what is wrong?
Thanks

---

### Post by hdotcom on 2007-04-21
> [QUOTE]
The any-any patch solved the big problem (no VMware Server) after upgrading from Edgy to Feisty, but it also removed the VMware Server launcher from the Applications >>Systems Tools menu path that survived the upgrade from Edgy to Feisty.

The VMware Server can now only be launched from a terminal after the following disclaimer is displayed: /usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

The VMware Server, installed under Edgy, is no longer recognized as an installed application under Fiesty and therefore a launcher can't be added to either the Applications menu or the Gome Panel.
Reply With Quote
[/QUOTE]

I am facing the same problem. However it seems to be working fine with VMS 1.01 and not 1.02. The problem however is that 1.01 has a lot of bugs so cant revert back. Has any found a fix to the above mentioned problem? Is it VMS or the kernel thats causing it?

---

### Post by stell86 on 2007-04-21
same error after upgrade to feisty
> r----@ubuntu1:~/vmware/bin$ ./vmware
/home/r----/vmware/lib/vmware/bin/vmware: /home/r-----/vmware/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)


I did rerun vmware-config.pl and have latest headers installed.
Also followed advice on the "any-to-any patch" advised of in [_**this**_]("http://ubuntuforums.org/showthread.php?t=413646") thread pointing to [_**this**_]("http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0") item in the VMware forums.

Reran the vmware-config.pl, but still get the same error if I run vmware from the commandline.

As previous posters have written: Help would be really appreciated - re-installation of XP is not something I look forward to...:)

---

### Post by sewmyheadon on 2007-04-21
Do either of these help?
[http://www.vmware.com/community/thread.jspa?messageID=383856&#383856](http://www.vmware.com/community/thread.jspa?messageID=383856&#383856)
[http://www.vmware.com/community/thread.jspa?messageID=595186&#595186](http://www.vmware.com/community/thread.jspa?messageID=595186&#595186)

---

### Post by spankymasterc on 2007-04-21
man i dont know what all you ppl complaining but i have a clean install of feisty installed vmware workstation 6.0 no hassle what so ever runs fast! on my

intel core 2 duo 6400
1 gig ram
e-geforce 7600 gt oc

---

### Post by stell86 on 2007-04-22
> **sewmyheadon said:**
> Do either of these help?
[http://www.vmware.com/community/thread.jspa?messageID=383856&#383856](http://www.vmware.com/community/thread.jspa?messageID=383856&#383856)
[http://www.vmware.com/community/thread.jspa?messageID=595186&#595186](http://www.vmware.com/community/thread.jspa?messageID=595186&#595186)
@spankymaster:
I think the words "clean install of feisty" should be bold and underlined and italics... :)
as well as 'workstation', which is not 'vmserver', which is what I'm using...

@sewmyheadon:
I saw your reply too late - after I tried some other options:
 - Did an install of VMPLAYER with [Automatix]("http://www.getautomatix.com") - this seemed to use install to same (some) of vmserver-directories
 - ran my installed VM (WinXP) , but did not like the lack of 'control' that vmplayer has vs VMserver (personal preference)
 - UNinstalled vmplayer with Automatix - this unfortunately removed some of vmserver's directories
 - removed the vmware(server) dir in my home folder:```
rm -fr /home/r----/vmware
```
 - removed vmware from /etc:```
rm -fr /etc/vmware
```
 - Re-installed VMWARE-server from downloaded package
 - repointed menu-item to new install folder
 - VMWARE server now works and my VM-winxp is available - re-install of vmware is much quicker than re-install of WinXP  :)

I noticed that if I run it from the commandline, I still get the 'error'/comment: > /usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
but my VMSERVER is still working

I don't know if that 'any-to-any' patch still has an effect.

I'll try the one solution provided in your link: [on the VMware-forums]("http://www.vmware.com/community/thread.jspa?messageID=595186&#595186"):```
sudo cp /usr/lib/libpng12.so.0 /usr/lib/vmware/lib/libpng12.so.0/ 
```
and report back.

[EDIT] 3mins later:
the above 'copy'-command does get rid of the 'libpng12.so.0' error/comment'
VMWARE server starts from the commandline without any issues/comments.

Thanks Eric for pointing the thread in VMware-forums.
[/EDIT]

---

### Post by sewmyheadon on 2007-04-22
Cheers ;)

Glad it worked.

---

