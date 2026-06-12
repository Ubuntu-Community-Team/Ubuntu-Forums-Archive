---
title: "hello my friends"
date: 2020-06-19
forum: General Help
---

### Post by touficabboud4 on 2020-06-19
hello everyone here my case:i'm a university student who need windows to use softwares related to my courses but i found myself more comfortable using ubuntu and i found many alternatives to help me like using ubuntu as my main os and use windows in a virtual machine or dual boot windows and ubuntu. what do you suggest me?

---

### Post by TheFu on 2020-06-19
If you don't game or need for Windows to have direct access to the GPU, then put Windows into a virtual machine. It is safer and you don't need to run it all the time.  Dual boot should be avoided as much as possible since it is very inconvenient, breaks our workflow when we have to reboot into the other OS for 5 minutes of stuff, losing our place in the other OS and every Windows update to the boot stuff will probably break the boot for Ubuntu.

```
$ uptime 
 09:17:18 up 20 days,
```
That's a desktop computer as VM host running ... 
```
$ virsh list
 Id    Name                           State
----------------------------------------------------
 1     blog44-1604                    running
 2     regulus                        running
 3     vpn09-1604                     running
 4     spam3                          running
 5     xen41-1604                     running
 6     zcs45-16.04                    running
 10    WinUlt                         running
```
a few VMs. It also has a few lxd containers running:
```
$ lxc list
+--------+---------+---------------------+------+------------+-----------+
|  NAME  |  STATE  |        IPV4         | IPV6 |    TYPE    | SNAPSHOTS |
+--------+---------+---------------------+------+------------+-----------+
| pihole | RUNNING | 172.22.22.80 (eth0) |      | PERSISTENT | 0         |
+--------+---------+---------------------+------+------------+-----------+
| spam1  | RUNNING |                     |      | PERSISTENT | 0         |
+--------+---------+---------------------+------+------------+-----------+
```

I'm actually using regulus as my workstation now. If I had to boot each of these separately, I'd never get anything done. I used to run 15 VMs on a desktop with 8GB of RAM.  Due to all the bloat, now these need 16G, but 2+G of that is used for buffers and I'm not as tight on sizing RAM for each VM as I was before.

---

### Post by touficabboud4 on 2020-06-19
i've never uses a virtual machine on the long term ,it is helpful or just a pain?

---

### Post by TheFu on 2020-06-19
> **touficabboud4 said:**
> i've never uses a virtual machine on the long term ,it is helpful or just a pain?

It depends. I moved my desktop into a VM in 2008 and have never regretted it. 

It is accessible from anywhere and not tied to any specific hardware. Running full screen, I forget that it is using a VM.  That was on a 1st-generation Core2 Duo 6600.  Until a few months ago, that VM had been upgraded from 10.04 --> 12.04 --> 14.04 --> 16.04. As my hardware got faster, I'd move the VM over. Never needed a reinstall.  It was initially a 32-bit install until April this year. For 20.04, I needed to switch to 64-bit as Canonical has ended support for the 32-bit OS. It was my only 32-bit Linux server or desktop remaining on x86 hardware. 

In 2008, I would make a full backup just by copying the VM file over every week, so if anything bad happened, the other file could be swapped in.  A few years later, I was running VMs for customers and needed a better way to backup many VMs. I needed daily, versioned, automatic backups for their business VMs. The file-copy method was taking too long and used way, way, too much storage. Spent a few months researching backup tools and trialed about 10 of them. Around 2012, found a great backup tool that takes just a few minutes and does all the other stuff needed. Still using that tool today.  Most daily backups are 2-7 minutes.  90 days of backups for 24G of data is ...
```
Thu Mar 19 00:07:04 2020         46.5 MB           28.6 GB
Wed Mar 18 00:07:05 2020          109 MB           28.7 GB
Tue Mar 17 00:07:04 2020         64.5 MB           **28.8 GB**
```
I keep media files on network storage, not local.  5G of data to get 90 days of backups?!  What?  Why wouldn't people want that?

Dual boot is much more hassle than using a virtual machine unless you must have direct access to the GPU.  I don't most of the time. These days, KVM+spice is pretty impressive, though it won't touch a real GPU for performance, people do use it for CAD.  I'm generally not sitting behind the computer running my VMs, so the access is remote over the LAN or internet. I use **x2go** for access rather than Spice because x2go is secure from anywhere in the world and includes a ssh tunnel for the connection and credentials.

I do have a Windows laptop from 2010 that has a dual-boot install, but it hasn't booted Linux in probably 8 yrs. It hasn't left my rack in 8 yrs either. It is just too much hassle to boot into Ubuntu for that machine.  Also have a Windows VM for financial programs - stocks, analysis, and finances.  That VM used to be a Windows Media Center until MSFT ended free schedule data.  I've moved to another solution that I coded up in bash and perl over a few weekends.

Dual boot stuff ... what will you do if Ubuntu fails to boot after a Windows update?  Can you quickly fix that problem in 5-10 minutes and get working again?  After all, Windows updates whenever it wants. We have no control anymore. How do you deal with backups? A VM provides simple options like snapshots that you can go reset to that point.  Do a snapshot before any major change, run with it for a week, then decide if you want to keep it or not. There are conditions where  snapshots aren't possible, but those are non-defaults for most hypervisors.

Begin by making a list of all the things you do on each OS.  How many actually **need** a fast GPU under Windows? For me, the list that needs a fast GPU is 1 thing - video editing.  Nothing else does.  You're needs are definitely different. Make the list.

---

