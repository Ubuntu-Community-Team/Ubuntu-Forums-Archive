---
title: "Resize windows partition?"
date: 2013-01-04
forum: General Help
---

### Post by AlessioForlante on 2013-01-04
Hello! Just Formatted the entire HD and put Windows 7 in a 20 gb partition and ubuntu in a 280 one.but then i realized that the windows' one was Way too small and i had to put at least 20 more gb.i burned gparted on a disk,but here's  the problem:
There are 5 partitions,2 from windows and 3 from ubuntu,And the ubuntu ones are in a "group" and i cant manage to make the allocated space get out of there....Help? Thanks

---

### Post by fdrake on 2013-01-04
> **AlessioForlante said:**
> Hello! Just Formatted the entire HD and put Windows 7 in a 20 gb partition and ubuntu in a 280 one.but then i realized that the windows' one was Way too small and i had to put at least 20 more gb.i burned gparted on a disk,but here's  the problem:
There are 5 partitions,2 from windows and 3 from ubuntu,And the ubuntu ones are in a "group" and i cant manage to make the allocated space get out of there....Help? Thanks

you have to use a live cd/usb in order to resize the disk. also the partitions need to be unmonted.

faq:[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)
> 
After shrinking the Windows partition, you should reboot once (or twice) into Windows prior to installing Ubuntu. This allows the Windows system to automatically rescan ...


---

### Post by AlessioForlante on 2013-01-04
i am using the CD one

---

### Post by fdrake on 2013-01-04
> **AlessioForlante said:**
> i am using the CD one

run this command to unmount the drives
```

sudo umount -a

```

---

### Post by AlessioForlante on 2013-01-04
> **fdrake said:**
> run this command to unmount the drives
```

sudo umount -a

```

it says that it is "busy"

---

### Post by fdrake on 2013-01-04
> **AlessioForlante said:**
> it says that it is "busy"

reboot the pc from the cdrom. Do not do anything and run my command first then use gparted

---

### Post by AlessioForlante on 2013-01-04
That's what i did

---

### Post by fdrake on 2013-01-04
output for "mount -l" and "sudo fdisk -l"?

---

### Post by AlessioForlante on 2013-01-04
What you mean? Please be more specific im not very good with linux-

---

### Post by fdrake on 2013-01-04
run these command sin the terminal and post the output here:
```

mount -l
sudo fdisk -l

```

ps:   parli italiano? :D

---

### Post by AlessioForlante on 2013-01-04
Sì
I have to run those commands in Gparted?

---

### Post by fdrake on 2013-01-04
> **AlessioForlante said:**
> Sì
I have to run those commands in Gparted?no nel termianl/console!
premi ctrl+alt+t , copia , incolla press invio.

avevi effettuato quei commandi che ti avo dato prima o no?guarda post #4

---

### Post by AlessioForlante on 2013-01-04
Ah Ma allora sono un Idiota io perchè l'ho scritto tutto in gparted -.-
umount -a mi da ```
 glados@glados-Aspire-5740:~$ sudo umount -a
umount: /run/shm: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /run: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /dev: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
glados@glados-Aspire-5740:~$ 


```

mount -l
```
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/shm type tmpfs (rw,nosuid,nodev)
glados@glados-Aspire-5740:~$ 

```
sudo fdisk -l
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 testine, 63 settori/tracce, 38913 cilindri, totale 625142448 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0x000648fe

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    42695201    21244177    7  HPFS/NTFS/exFAT
/dev/sda3        42696702   625141759   291222529    5  Esteso
/dev/sda5        42696704   619003903   288153600   83  Linux
/dev/sda6       619005952   625141759     3067904   82  Linux swap / Solaris
glados@glados-Aspire-5740:~$ 

```

---

### Post by fdrake on 2013-01-04
> **alessioforlante said:**
> ah ma allora sono un idiota io perchè l'ho scritto tutto in gparted -.-
:D  :D

riaccendi il pc e run command 
```

sudo umount -a

```
poi start con gparted.

---

### Post by AlessioForlante on 2013-01-04
Stessa cosa, mi da sempre busy (da ubuntu) e quando vado su gparted non posso far diventare la partizione di windows piu grande

---

### Post by fdrake on 2013-01-04
> **AlessioForlante said:**
> 
[COLOR="Red"][SIZE="4"]_**glados@glados-Aspire-5740:~$**_[/SIZE][/COLOR] 
[/CODE]
ci credo che ti dice che sei busy.e come dire " taglia il ramo dove sei seduto"; il sistema non te lo permette.... You have to boot from a live cd. Devi far partire il sistema  da un Ubuntu-cd non dal tuo hdd, come fai di solito. Non puoi cambiare la misura del disco se il disco viene usato al momento;
[http://www.youtube.com/watch?v=I5DeLLXd5gs](http://www.youtube.com/watch?v=I5DeLLXd5gs)

---

### Post by AlessioForlante on 2013-01-04
Non va! L'ho avviato dal live cd e mi dice ancora busy (Ho fatto sudo umount -a)

---

### Post by fdrake on 2013-01-04
Parlero in Inglose cosi altri ti possono aiutare e capire. 
I have to go to work , when I come back i'll get back to you.

When it says device is busy it means that a program is using the device.Is any program that you know using the disk of the pc?


 It may be that gparted mounts the device automatically; see here to unmount devices in gparted: [IMG]http://iwebdevel.com/wp-content/uploads/2010/02/Screenshot-dev-sdb-GParted-1.png[/IMG]

it is nothing hard to do we are just miussing  something simple...

---

### Post by ajgreeny on 2013-01-04
Sorry, but I don't speak you language.

I think you will need to click on the swap partition in gparted, and choose "swapoff" because your swap is a logical partition inside sda3.

If any logical partition within the extended sda3 is mounted or in use as swap, you will not be able to work on any other logical partition within the same extended partition.

---

### Post by AlessioForlante on 2013-01-04
Can somuone tell me step  by step what to do? im Just getting confused.
There is no unmount to me

---

### Post by AlessioForlante on 2013-01-05
Bumpp,i need help

---

### Post by ajgreeny on 2013-01-05
Have you run the live CD or USB and done a right click on the swap partition in gparted, and chosen "swapoff"?  You do not unmount a swap partition as it is not mounted in the same way as a normal partition.  However a live system finds and uses swap if it exists on a hard disk, and if it is one of several partitions within an extended partition, you will not be able to edit any of those other partitions while swap is in use. Using swapoff to disable swap should allow you to edit any of the partitions.

PS:  Sorry, but I notice that I forgot to mention the [COLOR=Red]right[/COLOR] click in my last post!

---

### Post by fdrake on 2013-01-05
> **ajgreeny said:**
> Sorry, but I don't speak you language.

I think you will need to click on the swap partition in gparted, and choose "swapoff" because your swap is a logical partition inside sda3.

If any logical partition within the extended sda3 is mounted or in use as swap, you will not be able to work on any other logical partition within the same extended partition.

+1
 good point, I didn't thought about the swap partition being in use:
[IMG]http://gparted-livecd.tuxfamily.org/larry/generalities/big/3-main-3.gif[/IMG]

---

### Post by AlessioForlante on 2013-01-05
Yay,After 6 hours of loading it finished.i did it...i had to make a unused space and then make the linux "group" smaller..:popcorn:
Thanks Everyone

---

### Post by fdrake on 2013-01-05
> **AlessioForlante said:**
> Yay,After 6 hours of loading it finished.i did it...i had to make a unused space and then make the linux "group" smaller..:popcorn:
Thanks Everyone

Glad to hear you solved the problem. Was the swap filesystem the proble? Can you clearify, just curious...

Also make sure to mark the thread as "Solved" so others can read it an use the same solution.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by AlessioForlante on 2013-01-07
Basically i made a unlocated space and then i made the linux "group" smaller....Sorry if you dont understand i dont Recal the names :\

---

