---
title: "VM vs. Wine"
date: 2006-11-14
forum: General Help
---

### Post by Imsati on 2006-11-14
Another quick question, this time concerning VM Ware and Wine. The only thing keeping me from using Kubuntu 100% of the time is one Windows program I use to access an on-line game. The game is Gemstone 4, and the program I use to access it is called the Simutronics Game Entry. The SGE will download and install perfectly, and I can then access the game through I think it was 5 logins via it. After that fifth one though, it will continue to work, I log in successfully, but I can't see the online game. I know it logged in successfully because Simutronics has a record of my character being logged in at those times, I just can;t see anything.

A friend suggested I try VM instead. Is it more stable that Wine? Does it provide the same basic service (emulation-type?)? As it stands now, whenever I want to play, I boot into XP, and I dread every second of it. Please please help me make the switch 100%!

Thanks!

~Jay

---

### Post by skirkpatrick on 2006-11-14
VMWare allows you to run a 100% Windows OS on top of Linux.  It's great for those programs that just won't work in Wine.  However, VMWare doesn't emulate a 3D graphics card so if your game requires a 3D accelerated card, you're out of luck.

---

### Post by Imsati on 2006-11-14
99% text-based with minimal graphics to show current magic power, health, injuries, etc (yeah, I'm a nerd). You say 100% Windows OS on top of Linux...does that include all the nasty things that Win is prone to? Viruses, spyware, etc? Or is it still Linux with sort of a Win 'shell' inside it?

---

### Post by jtkelly on 2006-11-14
I have been running vmware workstation 5 with windows xp and have been very happy with it's behaviour for the guest operating system.  I am now experiencing a problem with vmware where each time I try to start it. Vmware fails to launch and the message I get is vmware has been installed but not configured correctly .  please run  /usr/bin/vmware-config.pl
which I do and it fails with trying to stop Virtual ethernet                                                 .
I have to reboot and then run vmware-config.pl.  Whcih completes and then I am able to run vmware.  But the problem comes back as soon as I start it again and I have to repeat the reboot and config.  I thought at first that it was due to installing patches to Ubuntu but I am now positive that it has nothing to do with it.  It's weird because vmware ran fine without this problem for a long time, now it is constanty failing. 

The reconfig states the following but always completes fine  
None of the pre-built vmmon modules for VMware Workstation is suitable for your running kernel.  Do you want this program to try to build the vmmon module for your system (you need to have a C compiler installed on your system)? [yes]
]

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done

The configuration of VMware Workstation 5.5.2 build-29772 for Linux for this
running kernel completed successfully.
You can now run VMware Workstation by invoking the following command:
"/usr/bin/vmware".

One additional note that I am finding out each time I run vmware after it is rebuilt is that the permission that I set on the follwoing devices are getting changed back to their original state 
 ls -l /dev/parport*
crw------- 1 root root 99, 0 2006-11-14 18:47 /dev/parport0
crw------- 1 root root 99, 1 2006-11-14 18:47 /dev/parport1
crw------- 1 root root 99, 2 2006-11-14 18:47 /dev/parport2
crw------- 1 root root 99, 3 2006-11-14 18:47 /dev/parport3

I would change the group to rw...

Any help in this matter would be greatly appreciated.  Its a great product and there is something simple that is going on outside of vmware that is causing this problem

Thanks
john



o

---

### Post by Imsati on 2006-11-14
Well, first off, I'm not trying to run XP on top of Kubuntu. I'm looking to ditch XP completely without ever looking back. All I want to run under VM is my program that let's me log into my game and kill stuff :)

---

### Post by jtkelly on 2006-11-15
I thought that I read that vmware does not support Directx

---

### Post by andyrobo60 on 2006-11-15
If its a text based game I cant see it using directX

> **Imsati said:**
> You say 100% Windows OS on top of Linux...does that include all the nasty things that Win is prone to? Viruses, spyware, etc? Or is it still Linux with sort of a Win 'shell' inside it?

Yes you can get viruses, spyware, etc but they have not way of getting to ubuntu. and you can set VMWare up so that it doesn't save any changes to XP. So once you have installed XP and your game you can set it so that it will always restore to the same point once VMWare is shut down. So if you get a virus all you have to do is reset VMWare and the virus will be deleted. This will mean that you cant save anything in XP but if the game is over the internet it shouldn't matter.

---

### Post by SlCKB0Y on 2006-11-15
> **jtkelly said:**
> I have been running vmware workstation 5 with windows xp and have been very happy with it's behaviour for the guest operating system.  I am now experiencing a problem with vmware where each time I try to start it. Vmware fails to launch and the message I get is vmware has been installed but not configured correctly .  please run  /usr/bin/vmware-config.pl
which I do and it fails with trying to stop Virtual ethernet                                                 .
I have to reboot and then run vmware-config.pl.  Whcih completes and then I am able to run vmware.  But the problem comes back as soon as I start it again and I have to repeat the reboot and config.  I thought at first that it was due to installing patches to Ubuntu but I am now positive that it has nothing to do with it.  It's weird because vmware ran fine without this problem for a long time, now it is constanty failing. 

The reconfig states the following but always completes fine  
None of the pre-built vmmon modules for VMware Workstation is suitable for your running kernel.  Do you want this program to try to build the vmmon module for your system (you need to have a C compiler installed on your system)? [yes]
]

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done

The configuration of VMware Workstation 5.5.2 build-29772 for Linux for this
running kernel completed successfully.
You can now run VMware Workstation by invoking the following command:
"/usr/bin/vmware".

One additional note that I am finding out each time I run vmware after it is rebuilt is that the permission that I set on the follwoing devices are getting changed back to their original state 
 ls -l /dev/parport*
crw------- 1 root root 99, 0 2006-11-14 18:47 /dev/parport0
crw------- 1 root root 99, 1 2006-11-14 18:47 /dev/parport1
crw------- 1 root root 99, 2 2006-11-14 18:47 /dev/parport2
crw------- 1 root root 99, 3 2006-11-14 18:47 /dev/parport3

I would change the group to rw...

Any help in this matter would be greatly appreciated.  Its a great product and there is something simple that is going on outside of vmware that is causing this problem

Thanks
john



o

Stop hijacking this thread. If you need help, make your own thread.

---

