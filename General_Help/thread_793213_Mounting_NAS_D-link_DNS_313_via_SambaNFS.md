---
title: "Mounting NAS D-link DNS 313 via Samba/NFS"
date: 2008-05-13
forum: General Help
---

### Post by mjavorek on 2008-05-13
Hi,

I have bought an Ethernet NAS box D-link DNS-313 which is providing the Samba protocol. I'm not sure (and unfortunately I can't find so detailed specification) if it is providing also the NFS protocol. But very similar and famous DNS-323 is (but also bigger and more expensive).

When I mount this box from Win XP, no problems, I can copy many gigs and be connected many hours without any problem. But when connected from Ubuntu (via samba), connection falls down unexpectedly very often, gnome get freeze then, must remount and try again, but never reach - let say 10 minutes without interruption.

I'm mounting the disk in fstab when booting, network disk (NAS) is running all the time. Mapping line for samba looks like:

//10.0.0.12/Volume_1 /mnt/mamut smbfs username=,password= 0 0

(disk has not restricted access, therefore no user and password)

I have also tried to mount the disk as NFS volume:

10.0.0.12:Volume_1 /mnt/mamut nfs rw,hard,intr 0 0

but it doesn't work, mount is complaining: 
mount.nfs: mount to NFS server '10.0.0.12' failed: System Error: Connection refused

so it maybe looks like the DNS-313 has no NFS, which is a little bit pity, because DNS-313 is also running on Linux and two Linux machines are talking using MS protocol, but better than nothing...

Can anybody help with the samba? Is there anything I should setup better or upgrade in my Ubuntu? Somewhere missing comma or semicolon? ;-) 

Kernel version: 2.6.22-14-generic
Ubuntu version: 7.10 gutsy

Thanks a lot.
Martin

---

### Post by mjavorek on 2008-05-19
I have solved it for my self. 

So, for those, which will find this thread and will have similar problems - of course, it's a problem of the NAS box, not Ubuntu. So, follow the forum thread here:
[http://forum.dsmg600.info/viewtopic.php?pid=15051](http://forum.dsmg600.info/viewtopic.php?pid=15051). 

Solution is not to use a Samba, but install and run a NFS on the box and NFS is running with Ubuntu without problems. I'm using automount now and it is working perfectly.

---

### Post by johncarter on 2008-08-26
this works for me.
//192.168.2.105/volume_1 /media/nas5 cifs nounix,uid=root,noperm,gid=nasusers,file_mode=0777,dir_mode=0777 0 0

---

### Post by Napo2179 on 2009-02-21
Hello,

I am under Ubuntu Intrepid 8.10. I tried to connect the DNS 313 (Dlink) with Wifi Acces.
I did not wish to modify the NAS so I found this solution.

1.Creation of a user on DNS 313 : steph
Configure the MS workgroup as WATERLOO (or any other name)
2.Install with Synaptic the packages : smbget and smbfs.
3.Creation of a media directory : 
in terminal :  mkdir /media/nas0
4.Put the following lines in /etc/fstab :
In terminal : sudo gedit /etc/fstab

# NAS
//192.168.0.169/volume_1 /media/nas0 cifs workgroup=WATERLOO,username=steph 0 0

5.Reboot

After the reboot, when you connect to the Wifi network the NAS will mount automatically.

Let me know if it works for you.

---

### Post by crockettoo on 2009-06-09
Thanks, that worked for me! 8.04 LTS.

---

