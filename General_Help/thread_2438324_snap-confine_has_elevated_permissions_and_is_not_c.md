---
title: "snap-confine has elevated permissions and is not confined but should be. Refusing to"
date: 2020-03-10
forum: General Help
---

### Post by back-ache on 2020-03-10
I am running the latest version (19.10) of Ubuntu of a live USB stick with persistence which I plan to use as a casual development system.

I tried installing eclipse with snap which didn't work so install Microsoft code from the app store

But...when I try to launch it I get

snap-confine has elevated permissions and is not confined but should be. Refusing to continue to avoid permission escalation attacks

The solutions offered by google haven't done the trick. Whats the proper answer? I don't want to wipe the stick and start afresh, but it is an option :-(

---

### Post by Impavidus on 2020-03-10
"Latest version" isn't very clear. Do you mean the latest LTS version (18.04), the latest released version (19.10) or the current development version (20.04)?

Anyway, if it's a live usb, it's not a full system. You can have a live usb with persistence (you didn't specify), on which you can install some things and keep them after a reboot, but it's a bit limited. I expect that's the cause of your problem. Note that I never use snap packages or anything Microsoft and that I only use live usbs to install or fix Ubuntu.

---

### Post by back-ache on 2020-03-10
I hoped that wasn't the case, I want to keep my work (on Windows) and play (open source contributions) separate :-(

Currently I am using a USB3 stick and Ubuntu 19.10 (AMD64)

The performance is great though the Sandisk gets almost to hot to touch

---

### Post by TheFu on 2020-03-10
> Anyway, if it's a live usb, it's not a full system. You can have a live usb with persistence (you didn't specify), on which you can install some things and keep them after a reboot, but it's a bit limited. I expect that's the cause of your problem. **Note that I never use snap packages or anything Microsoft and that I only use live usbs to install or fix Ubuntu**.

Same for me.

I do use virtual machines, extensively, and have since around 2006.  VMs today are more than good for almost any sort of development, except Java or FPS games.  Heck, I do webapp development on a chromebook with 4G of RAM and 20G storage for the webapp server stuff. My development runs inside a KVM VM on the chromebook.

USB will always be slower and have queuing issues for storage access. The USB storage protocol just isn't made to host a complete, multi-threaded, multi-tasking OS where 20 different processes all need to access USB storage areas. USB storage is fine for emergencies and for uses where just a few processes will need access - like backups or media streaming, but not for an OS daily use.  For that, we need the SATA command set - like eSATA.  IMHO.

Or just use a VM.

If you plan to do Java development, get the fastest Core i7 or Ryzen 9xxx and 64GB of RAM, 2x NVMe SSD storage and hope that's fast enough.  Java is a dog/slow/hungry for CPU and RAM.  For Python, C, Perl, Ruby, Rust, Go, development, pretty much any chromebook or better system can be used.

I've tried to use snaps a few times. They always fail. Seems the snap dev team doesn't think anyone should use storage that isn't in their HOME directory. This design failure has forced me to use AppImages, which are slow, clunky too.  Played with flatpaks, they didn't work. Seems some dependencies weren't included by the package teams - which sorta defeats the reason for using flatpaks, right?

---

### Post by back-ache on 2020-03-10
I do want to stick with USB, maybe I could boot to a baremetal VM host and then to a VM (though that one on my opensource project then require a vm for its container maybe an issue)

The languages I plan on using are just python and javascript and for database postgres and mongo

oh why does life have to be so complicated :-)

---

### Post by CelticWarrior on 2020-03-10
You can have a full install in an USB drive. Not the same thing as a live version with or without persistence and, of course, much less "portable". Live media is not to be used as a daily driver.

---

### Post by TheFu on 2020-03-10
> **back-ache said:**
>  
oh why does life have to be so complicated :-)

The answer to that question always seems to be *MS-Windows*.

VMs actually make life much easier.  We can try out almost any OS inside a VM with effectively zero risk to the hostOS, especially if we don't perform risky online behaviors and use NAT networking from the VM.  I've found the flexibility provided by virtualization to be so great that my daily use desktop is actually a VM since around 2010.  I don't have any monster computers with $1000 CPUs and 32GB or RAM either.  I ran 15 VMs on a Core2 Duo from 2008 and 16GB of RAM for almost a decade. Then I moved some to a Core i5-750 (1st gen i5).  None of my systems, even today, have more than 16GB of RAM.  Linux just doesn't waste RAM like Windows does.

Here's the free RAM, buffers, swap on a web-app server running nextcloud, wallabag, and ZNC:
```
$ free -h
              total        used        free      shared  buff/cache   available
Mem:           992M        **299M**        350M         45M        342M        455M
Swap:          1.0G        162M        859M

```
300MB of RAM used for all those webapps.

Here's my VPN server:
```
$ free -h
              total        used        free      shared  buff/cache   available
Mem:           992M         **56M**        270M         10M        664M        742M
Swap:          1.0G          0B        1.0G

```
Under 60MB of RAM used.  This is an Ubuntu 16.04 server, BTW. Fully patched.
Linux servers are highly efficient.  It will take some time to get over that warped MSFT-thinking bias.

However, that isn't to say that all Ubuntu Servers are this efficient:
```
$ free 
             total       used       free     shared    buffers     cached
Mem:       1220136     **971808**     248328          0     183460     342688
-/+ buffers/cache:     445660     774476
Swap:            0          0          0
```
That's a Ruby on Rails webapp server using almost 1GB of RAM. It is a hog.

USB for an OS really should be avoided.  Go ahead and run that way for a few months, you'll see.  The portability you seem to want just doesn't really work out for non-trivial setups.

The required storage for a Linux VM isn't like MS-Windows either. My VMs use direct LVM allocations. Each of these below are allocations for a single VM, each:
```
NAME                                SIZE TYPE FSTYPE      MOUNTPOINT
&#9474; &#9500;&#9472;hadar--vg-lv--srv--1910          10G lvm              
&#9474; &#9500;&#9472;hadar--vg-lv--zcs45--1604        25G lvm              
&#9474; &#9500;&#9472;hadar--vg-lv--blog44--1604     16.2G lvm              
&#9474; &#9500;&#9472;hadar--vg-lv--vpn09--1604       7.5G lvm              
&#9474; &#9500;&#9472;hadar--vg-lv--spam3              10G lvm              
&#9474; &#9500;&#9472;hadar--vg-test--1804             10G lvm              
&#9474; &#9500;&#9472;hadar--vg-lv--lubuntu11--1604    31G lvm              
&#9474; &#9500;&#9472;hadar--vg-lv--xen41--1604      12.5G lvm      
```        
I give servers the storage they need.  10G is about the lower end size.  Adding more storage is really easy thanks to LVM. Right-sized storage ripples throughout our infrastructure. It impacts backup storage, backup timeframes, disaster recovery, off-site backups.  Basically, having the correct amount, and no more, is important.

Anyways, VMs are central to every programmer, IT person, and enterprise since around 2005.  Not knowing and being comfortable with VMs isn't a good idea these days.

---

