---
title: "hibernation and automatic fsck"
date: 2007-02-09
forum: General Help
---

### Post by frafu on 2007-02-09
Hello, 

As far as I know, Ubuntu automatically checks the harddisks after the computer has booted x times or after y days have elapsed without a fsck. 

However, what happens if the user hibernates the computer instead of shutting it down: Is a wake from hibernation also counted for the automatic fsck? 

If not, could you please give me an advice on how to make the computer regularly perform an automatic fsck? By using cron? 

If the computer is always running (not shutted down, not hibernated,...) and the y days have elapsed without a fsck, when does it perform the fsck? Will it do the fsck on the next reboot or will it do the fsck even if the system is not rebooted? 

Thanks in advance for any explanation and help. 

Francesco

---

### Post by nickoli_02 on 2007-02-09
If you normally just leave your computer on for long periods of time (days/weeks) you can alter the /etc/fstab file to make it check your mounted hard drives on each boot. Sorry, but I don't remember what the option is. Try searching the forums

---

### Post by dcstar on 2007-02-10
> **frafu said:**
> Hello, 

As far as I know, Ubuntu automatically checks the harddisks after the computer has booted x times or after y days have elapsed without a fsck. 

However, what happens if the user hibernates the computer instead of shutting it down: Is a wake from hibernation also counted for the automatic fsck? 

If not, could you please give me an advice on how to make the computer regularly perform an automatic fsck? By using cron? 
........

Firstly, it is when the drive is **mounted** x times or after x period, look at this for details on how to change things (or do a forum search for the various posts that detail it):
```
man tune2fs
```

---

### Post by frafu on 2007-02-10
Hello, 

First of all, thanks for the replies, especially for pointing out that it is the mounting of the harddisk that matters, and not the booting of the computer: 

> **dcstar said:**
> Firstly, it is when the drive is **mounted** x times or after x period

Consequently, if I am getting it right, there is no difference between completely shutting down the computer and putting it into hibernation for the automatic fsck, because I suppose that the harddisks get 
- unmounted on shutdown and hibernation 
- and afterwards remounted on boot and wake up. 

Can anybody please confirm? 

Thanks in advance.

---

### Post by Rui Pais on 2007-02-10
> **frafu said:**
> Hello, 

First of all, thanks for the replies, especially for pointing out that it is the mounting of the harddisk that matters, and not the booting of the computer: 



Consequently, if I am getting it right, there is no difference between completely shutting down the computer and putting it into hibernation for the automatic fsck, because I suppose that the harddisks get 
- unmounted on shutdown and hibernation 
- and afterwards remounted on boot and wake up. 

Can anybody please confirm? 

Thanks in advance.

i don't think that the fsck routine is done after hibernation. It's not done it with suspend. I don't use hibernation, but as far as i remember it simply get your sessions from a saved recorded from disc, so no start/boot sequence was really involved...

You can add such verification to cron, but that don't seems much necessary. 
As long as you run on a journalized system, the kernel will ensure that everything is ok and data backuped. If you suspect something is wrong you could then reboot and go with a verification of disks. 

Remember that Linux filesystems are very solid, not much prone to errors, specially ext3.


Anyway, just for completeness,  the tune2fs flags are (on an unmounted partition!)
sudo tune2fs -c X -i Y /dev/hdx99
where X is the number of reboots you want the check (0 if none is desired), and/or Y the time interval, like 2M (2 month) or 30d (30 days)

---

### Post by frafu on 2007-02-10
> **Rui Pais said:**
> 
You can add such verification to cron, but that don't seems much necessary. 
As long as you run on a journalized system, the kernel will ensure that everything is ok and data backuped. 


I am in fact using the ext3 filesystem, so I am happy to hear that I don't need to worry much. 

>  
If you suspect something is wrong you could then reboot and go with a verification of disks. 
 
How can I go with a verfication of the disks after reboot? (I don't think that you meant changing the c parameter with tune2fs to 1!?) 

Thanks in advance. 

Francesco

---

### Post by Rui Pais on 2007-02-10
> **frafu said:**
> I am in fact using the ext3 filesystem, so I am happy to hear that I don't need to worry much. 
yes, i have gone several times with abrupt power downs (power at my house sometimes can't hold all machines on...) and i never found any problem even after those bad shutdows (i should get an ups anyway or one of these days i'll eventually get in some trouble...)

> 
 
How can I go with a verfication of the disks after reboot? (I don't think that you meant changing the c parameter with tune2fs to 1!?) 

Thanks in advance. 

Francesco

No i mention 0 as a way to turn check by counts off, just as an information, not a suggestion. 
Its a parameter that can be set on a count base or a time base, both or none. 
I doubt that an healthy OS running will get in any trouble, even less ext3. This is like planes ;) Most of the problems happens on land or starting... not on fly/normal use. 

I usually set mine to count 30 and my time to 4M (on an specific ubuntu version it will check once till next version, i never upgrade, always fresh installs) or even to 0. Since i don't reboot  everyday (usually just suspend) I have a file check more or less in each 2 month... sometimes feel more then necessary...

Of course that's my preferences, you should set according to your needs or how you feel safer and confortable. :) 
c 1 i think it will make it annoying unless you always hibernate and only reboot to make the fsck run. 

Don't forget to set 0 1 for filesystem and 0 2 for other partitions on fstab.
:)

---

