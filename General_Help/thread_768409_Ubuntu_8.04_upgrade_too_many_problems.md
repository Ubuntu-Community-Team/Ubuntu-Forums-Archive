---
title: "Ubuntu 8.04 upgrade: too many problems"
date: 2008-04-26
forum: General Help
---

### Post by Lead Expression on 2008-04-26
Hi
Today I've upgrade my Ubuntu 7.10 to 8.04. Maybe this is a terrible error: during the installation I've two error from python library (python-numby) and at the end an error on new update-manager package that says me "System can be unusable". This is. ATI driver now doesn't work, system is very, very slow, battery control and wlassistant crash... and, this is terrible to me, VMWare doesn't work. It is installed but it doesn't run. Running from terminal it says me:

```
~$ vmware
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
```

but no problems seems to be. Reinstalling it from Gutsy repository doesn't seems to go. I need Win for my thesis. If I can't resolve this problem I have to erase Ubuntu and install Windows... :(

There's a way to downgrade to 7.10? I think I will upgrade to 8.04 when bugs is resolved, now I need a stable system... :(

---

### Post by SunnyRabbiera on 2008-04-26
hmm, well VMware is not my favorite VM software so cant help you there...
did you try virtualbox instead, thats my preferred VM client

---

### Post by bollix47 on 2008-04-26
[_Here_]("http://ubuntuforums.org/showpost.php?p=4357442&postcount=10") is the post that I used to install vmware-server on Hardy.

I could be wrong but I believe when your kernel changes as it did when you upgraded you have to run the vmware-config.pl script again after first installing the build-essential etc.

As for the ATI driver have you checked under System > Administration > Hardware Drivers to see if it shows your device driver and if so, check the box next to it?

---

### Post by Lead Expression on 2008-04-26
I don't think I would like to re-configure a virtual machine. I think it can be faster to return to my previous system... or configure a "real" windows machine :(

---

### Post by Lead Expression on 2008-04-26
Thx Bollix
I've just VMWare installed, I would like not to reinstall it and lose all configurations...

Maybe I had. So I've reinstalled it, but nothing. I've tried to run 8.04 with old kernel but same errors. I've tried to run vmware-config.pl but "command not found". Tried to run locate, so, but:

```
locate: can not open `/var/lib/mlocate/mlocate.db': Nessun file o directory

```

For ATI drivers, I tried to disinstall and reinstall from "Restricted Drivers", but it's the same.
And in the restricted drivers doesn't appear drivers for bcm43xx chipset (thanx god I use ndiswrapper...) and some other things.

Any ideas? In this conditions, system is really bad :(

---

### Post by Lead Expression on 2008-04-27
Excuse me, it is possible a downgrade to 7.10? If so, I'll be glad to return to my previous working settings. This way I don't know what to do, system is really unusable... :confused:

---

### Post by bollix47 on 2008-04-27
As far as I know you can't simply downgrade.  You would have to do a fresh install to get 7.10 back.

[_re locate problems_]("http://ubuntuforums.org/showthread.php?t=766601&highlight=locate")

If you're going to do a fresh install you could try the 8.04 live cd and if it works okay then do a fresh install with that.

Whichever you choose to do it's always a good idea to back up your data first.

---

### Post by Deeta on 2008-04-27
there seems to be some new locate version shipped in 8.04

just try 'mlocate' instead of 'locate'

---

### Post by Lead Expression on 2008-04-27
Thank you for the link, I don't think it can be a problem releated to locate.

I've reinstalled vmware and run locate. The problem remain:

```
nik@nik-laptop:~$ sudo locate vmware-config.pl
nik@nik-laptop:~$ sudo vmware-config.pl
sudo: vmware-config.pl: command not found

```

The strange thing is that in /usr/bin there's vmware-config-network.pl but not vmware-config.pl.

:confused:

---

### Post by bollix47 on 2008-04-27
What method did you use to re-install vmware?

Did you try mlocate as Deeta suggested?

---

### Post by Lead Expression on 2008-04-27
Idem using m-locate. I've reinstalled vmware and retried, but the result is the same

```
nik@nik-laptop:~$ sudo mlocate vmware-config.pl
nik@nik-laptop:~$ sudo vmware-config.pl
sudo: vmware-config.pl: command not found
```

I've also disinstalled obsolete packages (some of them I need for GDL, but... :( ) and reinstalled two times python packages that give me problems. The second time I haven't that error.

Vmware and ATI driver still doesn't work. Now I retry to disinstall and reinstall them. Maybe I'll be lucky...

Edit: ...I'm not... :(

I've the same problem with ATI I had with old distributions. In 7.04 upgraded to 7.10 I have not to do anything, simply install restricted drivers on 7.04 go fine either on 7.10. Now I read this:

```
nik@nik-laptop:~$ glxinfo | grep dire
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

Vmware give me the same error. Can you understand it? I don't know what to do, I have only verified if mentioned package are correctly installed.

---

### Post by Lead Expression on 2008-04-27
Another news: I've understand that I've to reconfigure all my software, so I started from ATI.
Incredible, when I type:

```
nik@nik-laptop:~$ sudo dpkg-reconfigure xserver-xorg
sudo: dpkg-reconfigure: command not found
```

So I go to Synaptics, disinstall and reinstall dpkg. Now it "quasi" work. If I run that, I've this error after configuring mouse (I post you two tries):

```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080427122651
nik@nik-laptop:~$ sudo dpkg-reconfigure xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080427122713
```

I think there's something wrong... :confused:

I repeat, I've only gave OK when the upgrade started! :lolflag:

---

### Post by bollix47 on 2008-04-27
You could try to install envy to get your ATI card working.

```
sudo apt-get install envyng-core
envyng -t
```

Select #3 for ATI.

---

### Post by Lead Expression on 2008-04-27
Thank you for your help but...

```
nik@nik-laptop:~$ glxinfo | grep dire
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```

I think I've not to deselect restricted drivers 'cause envy-core remove fglrx. It's correct?

Edit: Tried, it's the same

---

### Post by bollix47 on 2008-04-27
Did you install envyng?

Were there any errors during the install?

Did you reboot after the install?

---

### Post by Lead Expression on 2008-04-27
I've installed envy as you post. No errors occurred. It has disinstalled previous drivers and ask me to reboot. After reboot nothing's changed. I've try this procedure for 2 times, but no differences :(

Edit: one difference: system seems to go a little faster, a little slower than 7.10. This way is usable :)

Now my first interest is on Windows emulation. If I can't use vmware I think I will use virtual box... I think it is not the best, I can't understand why there's this incompatibility (it is not a kernel problem, I've the same with old kernel

---

### Post by bollix47 on 2008-04-27
Just to make sure that there is no vmware-config.pl on your system try the following:

```
sudo updatedb
mlocate vmware-config.pl
```

You can try virtualbox (I have it installed as well as vmware) or you can try installing vmware-server again using the link I referred to in post #3.

Good Luck either way.

---

### Post by Lead Expression on 2008-04-27
Tried those commands and reinstalled several times vmware-server, but I still have same error:

```
nik@nik-laptop:~$ sudo updatedb
nik@nik-laptop:~$ mlocate vmware-config.pl
nik@nik-laptop:~$ sudo vmware-config.pl
sudo: vmware-config.pl: command not found

```

```
nik@nik-laptop:~$ vmware
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware-server/bin/vmware: /usr/lib/vmware-server/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

```

I've checked, libgcc and libpng12 are present.

Well, if no one had same problem or can help me, I think I've to try virtualbox.

Thank you very much for your help and your patience :)

---

### Post by bollix47 on 2008-04-27
Near the bottom of the post on installing vmware you will see a couple of link commands.  

Have you tried these?

---

### Post by Lead Expression on 2008-04-27
The problem is this:

```
nik@nik-laptop:~/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Error: Unable to execute "/usr/bin/vmware-uninstall.pl.

Failure

Execution aborted.

```

vmware successfully disinstalled via Synaptics.

Edit: excuse me, I haven't understand.
I've type the ln command but now I can't install vmware. After installation, configuration give me this error

```
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Do you want networking for your virtual machines? (yes/no/help) [yes] 

Configuring a bridged network for vmnet0.

Your computer has multiple ethernet network interfaces available: eth0, eth1. 
Which one do you want to bridge to vmnet0? [eth0] 

The following bridged networks have been defined:

. vmnet0 is bridged to eth0

Do you wish to configure another bridged network? (yes/no) [no] 

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes] 

Configuring a NAT network for vmnet8.

Do you want this program to probe for an unused private subnet? (yes/no/help) 
[yes] 

Probing for an unused private subnet (this can take some time)...

We were unable to locate an unused Class C subnet in the range of private 
network numbers.  For each subnet that we tried we received a response to our 
ICMP ping packets from a host at the network address intended for assignment to
this machine.  Because no private subnet appears to be unused you will need to 
explicitly specify a network number by hand.

What will be the IP address of your host on the private 
network? 

The answer "" is invalid.  It must be of the form a.b.c.d where a, b, c and d 
are decimal numbers between 0 and 255.

Invalid default answer!
Execution aborted.

dpkg: errore processando vmware-server (--configure):
 il sottoprocesso post-installation script ha restituito un codice di errore 1
Sono occorsi degli errori processando:
 vmware-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have this if I try to run update

```
nik@nik-laptop:~/vmware-server-distrib/vmware-any-any-update116$ sudo ./runme.pl
Updating /usr/bin/vmware-config.pl ... corrupted
The file /usr/lib/vmware-server/modules/source/vmmon.tar that this script was 
about to install already exists. Overwrite? [yes] y

The file /usr/lib/vmware-server/modules/source/vmnet.tar that this script was 
about to install already exists. Overwrite? [yes] y

Updating /usr/bin/vmware ... No patch needed/available
Updating /usr/bin/vmnet-bridge ... No patch needed/available
Updating /usr/lib/vmware-server/bin/vmware-vmx ... No patch needed/available
Updating /usr/lib/vmware-server/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/usr/lib/vmware-server/modules/source" has been updated.

Before running VMware for the first time after update, you need to configure it 
for your running kernel by invoking the following command: 
"/usr/bin/vmware-config.pl". Do you want this script to invoke the command for 
you now? [yes] y

sh: /usr/bin/vmware-config.pl: not found

```

This 8.04 is a disaster, to me! :(

---

### Post by Lead Expression on 2008-04-27
Another bad notice: ndiswrapper doesn't work with new kernel. Now I'm using old kernel (very slow...). I've repeated the procedure for installing driver but I can't scan the network.

I think there's something wrong in this distribution... I can't believe nothing works fine after upgrade!

---

### Post by bollix47 on 2008-04-27
I think maybe you need a fresh install of 8.04.

You could download the live CD and try it out to see how it works on your computer before you install it.

Hardy was installed freshly on both my computers (one uses ATI) and I have none of the problems that you're experiencing.

---

### Post by danwood76 on 2008-04-27
Ndiswrapper working perfectly here.

Clean install is always the best way to do a OS upgrade.
Also you end up with a cleaner system at the end.

---

### Post by Lead Expression on 2008-04-27
Well, maybe this will be my destiny...
Only one doubt: I've the /home directory in a partition. I've to backup this directory or I can format partition containing root directory and install ubuntu without problems?

---

### Post by danwood76 on 2008-04-27
what you can do is on the /home partition mount it under the live cd and rename your user accounts folders.

so like mine is danny when I did my update I renamed it danny_gutsy then did the install.

Choose manual partitioning and tell it to use the correct partitions as /home and /
this way you loose no data in your home directory.
This includes your user settings which you can import when you need them, just by copying the relevant hidden directory.
I always find it quite nice having a clean OS for a few days after an upgrade, then I destroy its clean image with skins and so forth :)

---

### Post by at2000 on 2008-05-04
From the error in the first post of this thread, I think it is simply missing library. You can do the following

[INDENT]sudo ln -sf /usr/lib/libpng12.so.0 /usr/lib/vmware-server/lib/libpng12.so.0/
[/INDENT]
[INDENT]sudo ln -sf /lib/libgcc_s.so.1 /usr/lib/vmware-server/lib/libgcc_s.so.1/[/INDENT]

---

### Post by lewac on 2008-05-06
uhh... always. ALWAYS backup up your "about-to-be-upgraded" partition BEFORE upgrading ANYTHING. In fact its a good idea to image ALL partitions that you are "fond of". because anything can go amiss (and sometimes it does). we use "partimage" for this out of "rescueCD" (you can google that to find out more). this cd has a lot of useful apps ready to be called upon.

note that this is good practice REGARDLESS of which OS you're about to install (unless you plan on wiping the entire drive anyway).

---

