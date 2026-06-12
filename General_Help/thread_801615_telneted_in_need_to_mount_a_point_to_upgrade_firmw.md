---
title: "telneted in need to mount a point to upgrade firmware"
date: 2008-05-20
forum: General Help
---

### Post by sdowney717 on 2008-05-20
I am trying to upgrade the firmware to a dsm320 using telnet.
What I cant seem to do is this.
I can not mount my firmware on the flash drive to a location on the file system of the dsm320.

I put the firmware on the KINGSTON flash drive.
I telnet into the dsm320
Then for the dsm320 to 'see' or 'know' where the large firmware file is located, it looks like you have to create a mount point. 
So, I, from the root of dsm320, move to /tmp
cd /tmp
mkdir compfl
his command says this, BUT
mount / dev/sda1 / tmp / comfl  

I think it should be this, sdc1 is the KINGSTON stick

# mount /dev/sdc1 /tmp/compfl      
mount: Mounting /dev/sdc1 on /tmp/compfl failed: No such file or directory

and it of course does not know what to do. I assume since there is no 
dev sdc1 that the dsm320 would know about!
So while in the telnet session, you cant mount a device to a point on another filesystem?

So what do I do to make it work?

Links to relevant info, which is not perfect to understand, but you can get the general idea.

[http://dsm320.yuku.com/topic/393/t/Telnet-access-to-the-DSM320RD-and-what-to-do-with-it.html](http://dsm320.yuku.com/topic/393/t/Telnet-access-to-the-DSM320RD-and-what-to-do-with-it.html)

[http://translate.google.com/translate?hl=en&langpair=de|en&u=http://dsm320firmwareupdate.pbwiki.com/UpDate&tbb=1](http://translate.google.com/translate?hl=en&langpair=de|en&u=http://dsm320firmwareupdate.pbwiki.com/UpDate&tbb=1)


If I type mount on the telnet screen for the dsm320 then I get this
# mount
/dev/ram0 on / type ext2 (rw)
/mtd_rootfs_dev on /mtd_rootfs type cramfs (ro)
none on /proc type proc (rw)
/dev/ram1 on /tmp type ext2 (rw)


If I type mount on the computer terminal for ubuntu I get

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdc1 on /media/KINGSTON type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

how about something like this?
scott@scott-desktop:~$ sudo mount 192.168.1.100:/dev/sdc1 192.168.1.105:/tmp/compfl
mount.nfs: unrecognized mount point 192.168.1.105:/tmp/compfl
scott@scott-desktop:~$

---

