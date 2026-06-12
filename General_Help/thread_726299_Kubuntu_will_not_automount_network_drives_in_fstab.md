---
title: "Kubuntu will not automount network drives in fstab on boot."
date: 2008-03-16
forum: General Help
---

### Post by Ralphus Maximus on 2008-03-16
Hi. I have a new Kubuntu install on a lappy that serves as my "jukebox" for the game room, running Gutsy 7.10.

I have a wired ethernet interface that appears to load on boot, i.e. I can ssh into the machine before I login to kde.

/etc/network./interfaces
> auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 192.168.1.4
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.1
broadcast 192.168.1.255


I have my networked drives in the fstab.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0f20f457-e8c0-4c43-9ecf-cafeb6eba4bd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=e88fd83a-420c-4a69-ac7a-b28f034096b2 /home           ext3    defaults        0       2
# /dev/sda3
UUID=9a0a740f-5ae6-4ad1-ae8f-719fbcad592f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

192.168.1.5:/mnt/lv-raid/LordVega/Walls /home/lordvega/Walls    nfs     defaults        0 0
192.168.1.5:/mnt/lv-raid                /home/lordvega/Jaelle   nfs     defaults        0 0

192.168.1.3:/mnt/raid/Jaelle            /home/lordvega/Shows    nfs     defaults        0 0
192.168.1.3:/mnt/raid/Music             /home/lordvega/Music    nfs     defaults        0 0
192.168.1.3:/mnt/raid/LordVega          /home/lordvega/LordVega nfs     defaults        0 0
192.168.1.3:/mnt/raid                   /mnt/LordVega           nfs     defaults        0 0



When the lappy boots, I log into KDE, and then I have to issue a mount -a command as root to get the nfs drives to mount. How can I make this automatic without having to resort to a script?

Cheers,
RM

---

### Post by fjgaude on 2008-03-16
I'm not sure but could this be your issue:

>  For  ordinary  mounts  it  will hold (a link to) a block special device
       node (as created by mknod())  for  the  device  to  be  mounted,  like
       &#8216;/dev/cdrom&#8217;   or   &#8216;/dev/sdb7&#8217;.    For   NFS   mounts  one  will  have
       <host>:<dir>, e.g., &#8216;knuth.aeb.nl:/&#8217;.  For procfs, use &#8216;proc&#8217;.

From man mount. Seems host:dir is the item of interest, eh?

---

### Post by Ralphus Maximus on 2008-03-16
> **fjgaude said:**
> I'm not sure but could this be your issue:



From man mount. Seems host:dir is the item of interest, eh?

Thanks for the reply.

I'm comfortable that the fstab entry is correct, I can mount the nfs drives after logging in with a mount -a command from the shell. I'm wondering how I can get the OS to automagically mount them without me having to do it manually. 

As I said, this is a new install. I used to run gentoo, and the nfs drive entries are c&p from the old fstab. 

Cheers,
RM

---

### Post by fjgaude on 2008-03-16
Yes, but... but... shouldn't the fstab have mounted the drives? Seems like the command lines are not right  from what I read in the man pages... I've never tried what you are doing, no way to test without lots of work.

Let us know if you find a solution.

---

### Post by Ralphus Maximus on 2008-03-16
> **fjgaude said:**
> Yes, but... but... shouldn't the fstab have mounted the drives? Seems like the command lines are not right  from what I read in the man pages... I've never tried what you are doing, no way to test without lots of work.

Let us know if you find a solution.

That's the whole problem. The fstab **should** automagically mount the drives, but it doesn't  :confused:

The command **mount -a** tells the OS to run through the fstab and mount anything that is not mounted, according to the fstab entry.

Cheers,
RM

---

### Post by fjgaude on 2008-03-16
Yes, the mount -a does but think what this from man mount pages mean:

>        (i) The command
              mount -a [-t type] [-O optlist]
       (usually  given  in  a bootscript) causes all file systems mentioned in
       fstab (of the proper type  and/or  having  or  not  having  the  proper
       options)  to  be mounted as indicated, except for those whose line con&#8208;
       tains the noauto keyword. Adding the -F option will make mount fork, so
       that the filesystems are mounted simultaneously.

       (ii)  When  mounting  a  file system mentioned in fstab, it suffices to
       give only the device, or only the mount point.

       (iii) Normally, only the superuser can mount  file  systems.   However,
       when  fstab  contains  the user option on a line, anybody can mount the
       corresponding system.

I feel that the fstab lines with the IP has something not right, but I can't put my finger on it. What does the mtab file show before and after you manually do a mount -a?

I wish I could be of more help... just don't have the experience.

---

### Post by Ralphus Maximus on 2008-03-16
> **fjgaude said:**
> Yes, the mount -a does but think what this from man mount pages mean:



I feel that the fstab lines with the IP has something not right, but I can't put my finger on it. What does the mtab file show before and after you manually do a mount -a?

I wish I could be of more help... just don't have the experience.

Mtab shows normal. I used the IP instead of the hostname just to make sure it wasn't an issue trying to resolve the hostnames.

mtab after mount -a
> 
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
/dev/sda2 /home ext3 rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
192.168.1.5:/mnt/lv-raid/LordVega/Walls /home/lordvega/Walls nfs rw,addr=192.168.1.5 0 0
192.168.1.5:/mnt/lv-raid /home/lordvega/Jaelle nfs rw,addr=192.168.1.5 0 0
192.168.1.3:/mnt/raid/Jaelle /home/lordvega/Shows nfs rw,addr=192.168.1.3 0 0
192.168.1.3:/mnt/raid/Music /home/lordvega/Music nfs rw,addr=192.168.1.3 0 0
192.168.1.3:/mnt/raid/LordVega /home/lordvega/LordVega nfs rw,addr=192.168.1.3 0 0
192.168.1.3:/mnt/raid /mnt/LordVega nfs rw,addr=192.168.1.3 0 0


I'll reboot later and take a look at the mtab before.

I appreciate the assistance.

Cheers,
RM

---

### Post by Ralphus Maximus on 2008-03-22
The mtab showed the proper drives mounted before and after the mount -a command.

I did find a workaround, I put "mount -a" in /etc/rc.local.

Should I really have to do this? Shouldn't the OS automagically mount the drives in the fstab on boot?  :confused:

If any devs are peeking in, please advise if I'm missing something or it I should file a bug.

Cheers,
RM

---

### Post by freetree on 2008-03-30
I have the same problem before. After I change the mounting point from my home directory to something like /media/mountdir ( which is created by 'sudo mkdir /media/mountdir'), then the nfs folder can mount automatically at boot. Hope this can solve your problem.

---

