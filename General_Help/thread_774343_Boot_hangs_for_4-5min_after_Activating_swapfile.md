---
title: "Boot hangs for 4-5min after Activating swapfile"
date: 2008-04-29
forum: General Help
---

### Post by remusc on 2008-04-29
Simptom: At boot time, the system hangs for 2-5 minutes and finally it boots correctly.

Environment:
Ubuntu 7.10 /32 bit/ installed on a new laptop HP Compaq 8710w.
Upgraded last week to 8.04

It worked excelent for the first 2-3 weeks and from 2 weeks I have a problem at the boot. After the 'Activating swapfile file OK' message appears the system waits between 3-5 minutes and after that it continues booting and everything is ok.
I don't have any clue how to find out why it hangs at the stage between 'Activating swapfile ...' and '$Mounting securityfs on ...' and what to do in order to do a normal/quick boot, without reinstalling the system.

In order to get more info, I have tried also to activate the boot log file, but I didn't succeeded (I have the edited /etc/default/bootlogd to enable $BOOTLOGD-ENABLE and in rcS.d it runs as @S20) --> but this is another issue...

Maybe related (1):
* 10 days before I have repartinioned the Swap file from 2GB to 4GB (since I have 4 Gb Ram). Even if I corrected the fstab with the new dev-uuid, 1 day before the 'boot' event the fstab entry for the swap was completely wrong, I reedited with the correct dev-uuid. First, I thought that it hangs at 'Activating Swapfile file' but is prints 'OK' and maybe it hangs due to '$Mounting securityfs ...'.

Maybe related (2):
* 2 days before the booting story, I have switched the eth0 from roaming to fix IP and 2 days later I have switched back eth0 from Fix IP to roaming --> the consequence was that OracleXE is not starting anymmore (even if I have completely reinstalled and restore the orginal etc/hosts); in fact, only the listener does not start correctly. This is a third issue, I have included here, because I thought that it is related to some networking issue and maybe also related to the boot hanging.

The upgrade to 8.04 didn't solve this issue.

Thank you in advance for any support/idea.

---

### Post by ghost_ryder35 on 2008-04-29
> **remusc said:**
> Simptom: At boot time, the system hangs for 2-5 minutes and finally it boots correctly.

Environment:
Ubuntu 7.10 /32 bit/ installed on a new laptop HP Compaq 8710w.
Upgraded last week to 8.04

It worked excelent for the first 2-3 weeks and from 2 weeks I have a problem at the boot. After the 'Activating swapfile file OK' message appears the system waits between 3-5 minutes and after that it continues booting and everything is ok.
I don't have any clue how to find out why it hangs at the stage between 'Activating swapfile ...' and '$Mounting securityfs on ...' and what to do in order to do a normal/quick boot, without reinstalling the system.

In order to get more info, I have tried also to activate the boot log file, but I didn't succeeded (I have the edited /etc/default/bootlogd to enable $BOOTLOGD-ENABLE and in rcS.d it runs as @S20) --> but this is another issue...

Maybe related (1):
* 10 days before I have repartinioned the Swap file from 2GB to 4GB (since I have 4 Gb Ram). Even if I corrected the fstab with the new dev-uuid, 1 day before the 'boot' event the fstab entry for the swap was completely wrong, I reedited with the correct dev-uuid. First, I thought that it hangs at 'Activating Swapfile file' but is prints 'OK' and maybe it hangs due to '$Mounting securityfs ...'.

Maybe related (2):
* 2 days before the booting story, I have switched the eth0 from roaming to fix IP and 2 days later I have switched back eth0 from Fix IP to roaming --> the consequence was that OracleXE is not starting anymmore (even if I have completely reinstalled and restore the orginal etc/hosts); in fact, only the listener does not start correctly. This is a third issue, I have included here, because I thought that it is related to some networking issue and maybe also related to the boot hanging.

The upgrade to 8.04 didn't solve this issue.

Thank you in advance for any support/idea.
i.d.k anything about the problem at hand, but since you have 4gbs of ram unless your doing some major video editing, photo editing, hibernation i would slim that swap down to 2gb (like you had it or even less)  I run with 4gb and I do not run a swap (if you use hibernation you have to have a swap with enough memory to hold your ram cause thats where the hibernation writes the stuff)

---

### Post by ghost_ryder35 on 2008-04-29
install bootchart, and then view the file to see exactly where it is hanging.  It creates a pictured graph in /var/log/bootchart/


This is the graph from my boot
 [[IMG]http://img202.imagevenue.com/loc258/th_87574_boot_122_258lo.jpeg[/IMG]](http://img202.imagevenue.com/img.php?image=87574_boot_122_258lo.jpeg)

---

### Post by remusc on 2008-04-29
> **ghost_ryder35 said:**
> install bootchart, and then view the file to see exactly where it is hanging. 

Many thanks for your quick answer.
A step forward!
I have attached my bootchart picture.
I still cannot understand where is the issue ...

---

### Post by dom.parry on 2008-05-26
Hi There,

Did you ever find a solution to this? I'm having the same problem after a fresh install from windows. It's pretty frustrating. The only way around it so far is to disable swap. and I don't have enough ram for that at only 1GB.

Please let me know.

Thanks
Dom

---

### Post by chrisccoulson on 2008-05-26
remusc: Your problem is excessive disk activity from the bootclean script. This script cleans /tmp out on every boot, and will take a lot of time if /tmp has a lot of files in it. Have you got anything running that is storing a lot of data in /tmp? It might be worth checking how much stuff is stored in /tmp each time before you shut down. If you've got gigabytes of data in it, then bootclean is going to take a long time to clear it out next time you boot. In this case, you need to work out what is writing the data in there

---

### Post by dom.parry on 2008-05-27
Hi All,

I think I've found my problem. My windows disk just needed to be defragmented. Now it all seems happy.

-Dom

---

### Post by remusc on 2008-05-27
> **chrisccoulson said:**
> remusc: Your problem is excessive disk activity from the bootclean script. This script cleans /tmp out on every boot, and will take a lot of time if /tmp has a lot of files in it. Have you got anything running that is storing a lot of data in /tmp? It might be worth checking how much stuff is stored in /tmp each time before you shut down. If you've got gigabytes of data in it, then bootclean is going to take a long time to clear it out next time you boot. In this case, you need to work out what is writing the data in there

Thank you.I have around 4Gb in the tmp.
I will investigate what is there (because I delete it manually and every time after boot, I have again around 4 Gb ...).
I will investigate deepper later on, and I will come back (actually I am using 2 computers, both with Ubuntu 8.04, one in the office/ Intel desktop/ without any problem and the other one / HP laptop/ with this problem).

---

### Post by remusc on 2008-05-27
> **dom.parry said:**
> Hi All,

I think I've found my problem. My windows disk just needed to be defragmented. Now it all seems happy.

-Dom

Thanks. I will try also this ( I have still a Windows partition, but I have used it 1-2 times from the time I have bought the laptop ~3 months ago , basically I didn't used Windows, only repartition and installed Ubuntu)

---

### Post by remusc on 2008-05-27
> **remusc said:**
> Thanks. I will try also this ( I have still a Windows partition, but I have used it 1-2 times from the time I have bought the laptop ~3 months ago , basically I didn't used Windows, only repartition and installed Ubuntu)

I have defragmented the Win partition. The problem persists.

---

### Post by chrisccoulson on 2008-05-27
I wouldn't expect the Windows partition to have any influence over your problem remusc. The issue is definately the 4GB in /tmp. bootclean erases this at boot-time, which is where your 5 minutes goes

---

### Post by remusc on 2008-05-27
> **chrisccoulson said:**
> remusc: Your problem is excessive disk activity from the bootclean script. This script cleans /tmp out on every boot, and will take a lot of time if /tmp has a lot of files in it. Have you got anything running that is storing a lot of data in /tmp? It might be worth checking how much stuff is stored in /tmp each time before you shut down. If you've got gigabytes of data in it, then bootclean is going to take a long time to clear it out next time you boot. In this case, you need to work out what is writing the data in there

I have checked again (several times) and it writes a reasonable 1.9MB (gconfd, keyring, hsperfdata_root, Tracker etc.).

I have checked also the /etc/rcS.d and I have:
@S35mountall.sh
@S36mountallbootclean.sh

I have installed also an utility sysv-rc-conf to see what services are started at boot time/at what level. It appears that bootclean is not started at all.

I wonder what happens if I remove @S36mountallbootclean. Do you think it can solve my issue ?

---

