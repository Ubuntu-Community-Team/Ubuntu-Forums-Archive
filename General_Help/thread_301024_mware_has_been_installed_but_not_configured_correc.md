---
title: "mware has been installed but not configured correctly over and over"
date: 2006-11-16
forum: General Help
---

### Post by jtkelly on 2006-11-16
I have been running vmware workstation 5 with windows xp and have been very happy with it's behaviour for the guest operating system. I am now experiencing a problem with vmware where each time I try to start it Vmware fails to launch and the message I get is vmware has been installed but not configured correctly . please run /usr/bin/vmware-config.pl
I do this and it fails with trying to stop Virtual ethernet .
I have to reboot and then run vmware-config.pl. This completes and then I am able to run vmware. But the problem comes back as soon as I start it again and I have to repeat the reboot and config. I thought at first that it was due to installing patches to Ubuntu but I am now positive that it has nothing to do with it. It's weird because vmware ran fine without this problem for a long time, now it is constanty failing on reboots.

The reconfig states the following but always completes fine
None of the pre-built vmmon modules for VMware Workstation is suitable for your running kernel. Do you want this program to try to build the vmmon module for your system (you need to have a C compiler installed on your system)? [yes]
]

Starting VMware services:
Virtual machine monitor done
Virtual ethernet done
Bridged networking on /dev/vmnet0 done
Host-only networking on /dev/vmnet1 (background) done
Host-only networking on /dev/vmnet8 (background) done
NAT service on /dev/vmnet8 done

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

I would change the group to rw.

Any help would be appreicated.  I really think some process is updating something on boot causing VMWARE to fail until rebuilt.

John

---

### Post by mbeierl on 2006-11-17
Doesn't sound familiar, but I must ask:  why are you changing the group permissions on your parport devices?  According to your ls command output, the owner and group are both root, so the permission change will have no effect - because the owner (root) already has rw access.

---

### Post by ariel on 2006-11-19
I have the same problem.

I found this: 

[http://jeremy.co-comp.co.uk/archives/6-VMware-need-to-re-run-vmware-config.pl-every-reboot-on-linux.html](http://jeremy.co-comp.co.uk/archives/6-VMware-need-to-re-run-vmware-config.pl-every-reboot-on-linux.html)

[http://www.vmware.com/community/message.jspa?messageID=506544](http://www.vmware.com/community/message.jspa?messageID=506544)

I tried the solution, but it didn't work for me. In my case, it is not as painful because I don't have to reboot, I just have to run the vmware-config.pl before launching vmware. It's annoying though.

You might have better luck trying vmware workstation 5.5.3 which claims to have edgy support. It was released just two days ago.

Cheers
A

---

### Post by jtkelly on 2006-11-20
Hello,

 The reason I am changing the permission for the para ports is so that I can print to it in vmware (not running as root).  If I dont I can not get access to the prot.  BTW,  I also have to rmmod lp prior to starting up vmware and then do a modprobe lp after I exit vmware. Also, in redhat there is a file in /etc/securities that allows you to set the permissions on a devive when you log in and then out.  Cant seem to find the same on Ubuntu.

I just heard about the new vmware so I will be trying it out shortly.  Hope it works.  Still confused in one area that seems to be around dbus and libdbus-1.so.3 .  from some forumns it is being stated that the new version of dbus is the cause but there is mentioned to libdbus-1.so.  I only have libdbus-1.so.2 and not libdbus-1.so.3.  When trying to install libdbus-1.so.3 it fails on some required libraries vesions.  Trying to find out how to install libdbus-1.so.3 with updates to any dependancy libraries.

jk

---

### Post by melancholeric on 2006-11-20
I had the exact same problem with VMware server. Initially it worked fine when I tested it with virtual Damn Small Linux.

A couple of days later it gave the same error message: installed but not configure, please run vmware-configure.pl. Running that was aborted because it couldn't stop virtual ethernet.

So, I thought I'd just uninstall and reinstall, but that seemed a bit too much of a hassle, so I looked around a bit if there's an easier way to fix it.

Surely enough, there was a blank file /etc/vmware/not_configured 

After deleting (or renaming) this file everything seemed to work just fine.

---

### Post by ariel on 2006-11-22
> **jtkelly said:**
> Hello,

 The reason I am changing the permission for the para ports is so that I can print to it in vmware (not running as root).  If I dont I can not get access to the prot.  BTW,  I also have to rmmod lp prior to starting up vmware and then do a modprobe lp after I exit vmware. Also, in redhat there is a file in /etc/securities that allows you to set the permissions on a devive when you log in and then out.  Cant seem to find the same on Ubuntu.

I just heard about the new vmware so I will be trying it out shortly.  Hope it works.  Still confused in one area that seems to be around dbus and libdbus-1.so.3 .  from some forumns it is being stated that the new version of dbus is the cause but there is mentioned to libdbus-1.so.  I only have libdbus-1.so.2 and not libdbus-1.so.3.  When trying to install libdbus-1.so.3 it fails on some required libraries vesions.  Trying to find out how to install libdbus-1.so.3 with updates to any dependancy libraries.

jk


I installed 5.5.3 on edgy, from the .tar.gz ; it ran smoothly and noticeably faster than 5.5.2, in my case at least.

however today after a clean boot vmware 5.5.3 again was complaing about not being correctly configured :((, maybe there is a problem with my system, I can't believe they did not fix this in the new release.

---

### Post by lapsey on 2006-11-26
> **melancholeric said:**
> I had the exact same problem with VMware server. Initially it worked fine when I tested it with virtual Damn Small Linux.

A couple of days later it gave the same error message: installed but not configure, please run vmware-configure.pl. Running that was aborted because it couldn't stop virtual ethernet.

So, I thought I'd just uninstall and reinstall, but that seemed a bit too much of a hassle, so I looked around a bit if there's an easier way to fix it.

Surely enough, there was a blank file /etc/vmware/not_configured 

After deleting (or renaming) this file everything seemed to work just fine.

absurdly, this works!

```
sudo mv /etc/vmware/not_configured /etc/vmware/not_configured.old
```

---

### Post by Redeyes_Gambit on 2007-01-12
LOL! I was having a similar problem (kept asking me to configure) and this worked! *is shocked*

Many thanks!

---

### Post by Dubbayoo on 2007-01-12
I had this problem when I had both vmplayer and vmware workstation installed. I think both were trying to run scripts on startup. I removed workstation and it's been fine ever since.

---

### Post by Contrid on 2007-01-13
> **melancholeric said:**
> I had the exact same problem with VMware server. Initially it worked fine when I tested it with virtual Damn Small Linux.

A couple of days later it gave the same error message: installed but not configure, please run vmware-configure.pl. Running that was aborted because it couldn't stop virtual ethernet.

So, I thought I'd just uninstall and reinstall, but that seemed a bit too much of a hassle, so I looked around a bit if there's an easier way to fix it.

Surely enough, there was a blank file /etc/vmware/not_configured 

After deleting (or renaming) this file everything seemed to work just fine.

I can't believe this!!!
It actually works. You have no idea how many times I've reinstalled VMWare. ](*,)

---

### Post by nbppp2 on 2007-01-14
Thanks for the help so far.  I updated from dapper and VMware server no longer ran.  kept giving me that need to reconfigure error.  I followed the directions on here and now the error is 

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

Can anyone help me get this resolved?  Thank You.

---

### Post by nbppp2 on 2007-01-14
ok I found a solution.  

You can find it here

[URL="http://www.vmware.com/community/thread.jspa?messageID=484981"]

the command 

*apt-get remove libdbus-1-2*  

is what finally worked for me.

Hope this helps.

---

### Post by likwid on 2007-01-15
> **melancholeric said:**
> I had the exact same problem with VMware server. Initially it worked fine when I tested it with virtual Damn Small Linux.

A couple of days later it gave the same error message: installed but not configure, please run vmware-configure.pl. Running that was aborted because it couldn't stop virtual ethernet.

So, I thought I'd just uninstall and reinstall, but that seemed a bit too much of a hassle, so I looked around a bit if there's an easier way to fix it.

Surely enough, there was a blank file /etc/vmware/not_configured 

After deleting (or renaming) this file everything seemed to work just fine.
Thanks for workaround! Is there any way to prevent this file from being created??

---

### Post by ac0rn on 2007-07-23
Yes, thank you VERY much. I wasted almost a whole day on this problem. Don't know why i couldn't find this post at first... oh well, thanks again!

---

