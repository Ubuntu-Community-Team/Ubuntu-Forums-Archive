---
title: "Problem with saving/using HDD with Ubuntu 12.04 LTS Server"
date: 2013-03-24
forum: General Help
---

### Post by AlexTepes on 2013-03-24
I'm using Ubuntu server 12.04, and I'm having trouble saving anything to the hard drive. Everything appears to be installed correctly from the live CD, and I'm no longer using a CD, however I can't do any of the following;

[LIST=1]
[*]Save ifconfig setups
[*]Download or make any changes
[*]Change my desktop environment
[/LIST]

What I mean is, I installed Openbox, Tint2, and wbar, they were all working perfectly, and they're now gone.
I also installed Compiz-Fusion, and Fusion-icon, gone also.
I've set my ifconfig for eth2 to 192.168.0.1, netmask 255.255.255.0. route add 192.168.0.1 to my WAN IP on eth0, set iptables configuration too.
But upon reboot it goes right back to default, eith eth2 not even up in ifconfig.

I'm running a 30GB KingSpec SSD drive on a AMD Phenom II x2 550be 3.2Ghz, 4GB 1333mhz DDR3.
I'm trying to use this as a router, and I'm using Openbox/etc for a lightweight gui so when I attach a screen and log in I can see different statics from conky and I'm not using a huge bulky environment that uses up a bunch of space/memory, but looks half decent.

```

root@ubuntu:/home/alex# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        26G  6.4G   19G  26% /
udev            2.3G  4.0K  2.3G   1% /dev
tmpfs           946M  948K  945M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.4G  144K  2.4G   1% /run/shm
cgroup          2.4G     0  2.4G   0% /sys/fs/cgroup

```

```
root@ubuntu:/home/alex# cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 4
model name	: AMD Phenom(tm) II X2 550 Processor

```

```
root@ubuntu:/home/alex# free -m
             total       used       free     shared    buffers     cached
Mem:          4725       1987       2737          0        146       1086
-/+ buffers/cache:        754       3970
Swap:         3835          0       3835

```


```
root@ubuntu:/home/alex# ifconfig
eth0      Link encap:Ethernet  HWaddr f4:6d:04:3c:d0:e7  
          inet addr:0.118.140.0  Bcast:255.255.255.255  Mask:255.255.254.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:24225 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14522 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12082900 (12.0 MB)  TX bytes:1623020 (1.6 MB)
          Interrupt:31 Base address:0x8000 

eth2      Link encap:Ethernet  HWaddr 00:50:ba:bf:09:26  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:febf:926/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1596 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1229 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:168693 (168.6 KB)  TX bytes:437750 (437.7 KB)
          Interrupt:20 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:655 (655.0 B)  TX bytes:655 (655.0 B)


```

My network settigs in ifconfig and iptables will reset as soon as I reboot. :/ But it's working "live". I feel like I'm on the Live CD via my SSD drive.

---

### Post by tgalati4 on 2013-03-24
Please describe exactly how you installed the components.  It sounds like you installed a 12.04 server, then manually added some desktop components, but you don't have a complete working distro.  You have created your own, minimal, custom distro, but the pieces don't work correctly.

When you boot, are you greated with a command line login?  Or does it boot directly into Openbox?  

Your network stack depends on your desktop environment and the gui's that setup up networking (network-manager--which you probably don't have installed).

What is the output of 

```
cat /etc/network/interfaces
```

Review the following:
```
man interfaces
apt-cache policy network-manager
apt-get policy network-manager
```

Supporting this system may be a challenge.

---

### Post by AlexTepes on 2013-03-24
> **tgalati4 said:**
> Please describe exactly how you installed the components.  It sounds like you installed a 12.04 server, then manually added some desktop components, but you don't have a complete working distro.  You have created your own, minimal, custom distro, but the pieces don't work correctly.


I installed Ubuntu server 12.04 with Xen-hypervisor, also have Gnome, and Unity installed.
It boots up and shows a Debian background image with outputs of it loading Xen and ramdisks.
After which is goes black and goes to what looks like a traditional Ubuntu login.

Gnome classic works, Unity seems to just stall and never completely load, User defined loads what looks like Gnome with no environment.

> **tgalati4 said:**
> 
When you boot, are you greated with a command line login?  Or does it boot directly into Openbox?  


Neither, it allows me to choose my desktop with my default user or "Other" to choose another username.
After installing Openbox and rebooting it completely disappeared from the hard drive, and same thing with anything I install. It just does not carry over to new user sessions(after reboot).
It acts exactly how a live CD/DVD would.

> **tgalati4 said:**
> 
Your network stack depends on your desktop environment and the gui's that setup up networking (network-manager--which you probably don't have installed).


It says booting without network managing, after taking a really long time to startup, but it is there on the Gnome-Classic interface.
But I have to setup ifconfig manually to get access to internet, or route in my Windows machine(ICS from Ubuntu to Windows, ie: Using Ubuntu as a router).

> **tgalati4 said:**
> 
What is the output of 

```
cat /etc/network/interfaces
```


root@ubuntu:/home/alex# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
*
# The loopback network interface
auto lo
iface lo inet loopback
*
# The primary network interface
auto eth1
iface eth1 inet dhcp
auto eth0
iface eth0 inet dhcp

> **tgalati4 said:**
> 
Review the following:
```
man interfaces
apt-cache policy network-manager
apt-get policy network-manager
```

Supporting this system may be a challenge.

Why do I need to use man for interfaces? I'm not having a problem with networking. I'm posting from my Windows PC right now.
The problem is Ubuntu/or my custom distro as you call it isn't saving my settings, anything I download or install disappears, and nothing I can recall setting up when installing would of made it behave like that.
I've downloaded iso files, images, you name it, after a reboot it disappears. Same with anything I set in iptables. Even if I put them in the config file.

---

### Post by oldfred on 2013-03-25
I think the issue is networking. Because you installed the desktop you now have two ways to configure network and they conflict. 

With servers you normally manually edit /etc/network/interfaces.
With desktop you use the gui and edit network connections with it. /System tools/Preferences/Network Connections
But they conflict, so you need to choose to edit with gui or uninstall the gui and directly edit file.

---

### Post by AlexTepes on 2013-03-25
> **oldfred said:**
> I think the issue is networking. Because you installed the desktop you now have two ways to configure network and they conflict. 

With servers you normally manually edit /etc/network/interfaces.
With desktop you use the gui and edit network connections with it. /System tools/Preferences/Network Connections
But they conflict, so you need to choose to edit with gui or uninstall the gui and directly edit file.

Can you explain installing Openbox, corky, wbar, having it work until you reboot?
What about having downloaded images and isos to /home/alex/Download/ and having them disappear too?

Something tells me you're not completely reading my statements. Because of the issue I'm having I cannot remove network-manager, it'll just return.

Maybe you can just tell me of a linux OS that just has a working iptables and ifconfig/network interfaces and I can move on from ubuntu, because this is the second PC I've had irreversible problems with the OS.
Just meaning, that's all it has.

Since 10.10 it seems it's been nothing but garbage for me and I need to stop using it, I miss 6.04, at least it worked right.
Maybe even 4.10, haha. But seriously. I'd rather just be able to remove xen, or whatever is making it impossible to save anything.
A friend suggested I should powercycle my SSD to see if that solves the problem. If not then I'm back at square one.

Update: It appears my SSD failed. Even over live using a myriad of commands and methods such as gparted, I was unable to repartition my HDD. So I put in my 500GB SATA 7200RPM and installing 12.10 on it right now. I had to take it out of my Windows PC, but no big deal, it already has a 1TB. I'd use my plethora of IDE hard drives but my new mobos only take Sata. Only my old Athlon 64 takes IDE, and I haven't decided what I'll be doing with that yet.

I'm creating my own server closet. I want to use this one that I'm debugging for handling routing and NFS. I think the Athlon might just run something small with PHP/MySQL on it.

Update 2: Ubuntu 12.10 installed properly, and I've set my preferences in network-management, everything is automatic. So it was my HDDs fault. Haha. Sorry for my ranting, this time.
Now to remove the worst creations in Ubuntu's history; Unity, and Ubuntu Software Center.

---

### Post by AlexTepes on 2013-03-25
Everything is good now and solved, something so simple and yet difficult to track down apparently. Haha.
But something so simple these days is getting harder and harder to get to:

[IMG]http://i47.tinypic.com/2zi0bog.png[/IMG]

Looks better than unity already.

---

### Post by tgalati4 on 2013-03-25
Well, sorry for sending you on a goose chase with a networking issue.  It looked like a networking issue, only because there are several frameworks involved with networking and they don't always play well together.  I'm surprised the SSD didn't spit out errors or that it was not obvious that it was in fact a hardware problem.  Perhaps the xen hypervisor was hiding the IO errors.  That is one downside of abstracting hardware in virtual machines.  The VM will keep running an instance, but if it never gets to bare metal, then do you really have a VM?  That is an interesting dilemma.

I'm glad you figured it out, since you had me and a few others stumped.  Your setup illustrates the point that there is no single, correct way to set up a linux system.  If it makes sense to you, then that is all that matters.

---

### Post by AlexTepes on 2013-03-26
> **tgalati4 said:**
> Well, sorry for sending you on a goose chase with a networking issue.  It looked like a networking issue, only because there are several frameworks involved with networking and they don't always play well together.  I'm surprised the SSD didn't spit out errors or that it was not obvious that it was in fact a hardware problem.  Perhaps the xen hypervisor was hiding the IO errors.  That is one downside of abstracting hardware in virtual machines.  The VM will keep running an instance, but if it never gets to bare metal, then do you really have a VM?  That is an interesting dilemma.

I'm glad you figured it out, since you had me and a few others stumped.  Your setup illustrates the point that there is no single, correct way to set up a linux system.  If it makes sense to you, then that is all that matters.

Me too. I was having some issues with the drive before (Varied). I thought I'd test it on Ubuntu, because I've heard power cycling, partitioning at the end of the drive instead of the front can solve some of these issues, and to be completely honest, Ubuntu, nor Xen-Hypervisor error'ed at all, ever, about the drive. It even let me install some programs, then it stopped letting me I guess at some point. I thought it was a bit peculiar that every Live/OS, including my favorite CentOS wouldn't partition. So I loaded up 12.10 live, did that dd= command that is suppose to replace all bytes with 0's? Well, it rebooted like nothing happened, even after doing that in 2 pass AND random, so I knew it had to be my hard drive at that point. That and doing fsck, gparted, all returned some error like it couldn't do anything. 

Wasn't necessarily a wild goose chase, even though I appreciated you did in fact answer me, it is a forum, and free support after all. I ignored it, and went on to do my other tests. Though any support is better than no support, I tend to ignore the non-beneficial. I don't expect you to know how many read/writes are left on all my hard drives like some tech psychic. Haha. Thanks for everything though.

---

