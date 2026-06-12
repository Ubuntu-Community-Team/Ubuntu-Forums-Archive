---
title: "torrents vanish from folder when download completes"
date: 2013-06-04
forum: General Help
---

### Post by mgompert on 2013-06-04
I do not know where to ask for help about this so I am posting this here

this is what happens

I start a torrent of a file, every thing looks normal
at some point the file changes from Filename.extention.part to .fuse_hiddenRANDOMNUMBERSHERE
then when the download finishes the .fuse and the folder it is in vanish. I show hiddne files and they are not there

I changed drives that the downloads go to, to check if it is the drive where files are bing saved. the fiels still vanish.
 I changed torrent programs to see if it is transmission doing some thing weird, the files still vanish
I ahve tried other torrents, they vanish.

I have set transmission to send the files to a network drive to see if some where on my computer some thing is doing this, hoping that the networked files will be immune to the .fuse_hiddenNUMBERS problem, but that is not a solution. I should be able to download files to my local drives.

---

### Post by mgompert on 2013-06-04
ok when downloaded to an external drive they show up and are not deleated. doing to try to download to home folder on local machine and see if it is a permissions issue with the mounted local drives

---

### Post by mgompert on 2013-06-04
Ok so it is only doing it with the drives that are mounted, home  downloads fine, and the network drive (sshfs connected to folder in home  directory) is fine but my mounted drives bigboy and brock will not save  any downloads.

any ideas?

---

### Post by Cheesemill on 2013-06-04
Can you  post the output of ***mount*** so we can see how your drives are mounted.

---

### Post by mgompert on 2013-06-04
/dev/sdb6 on / type ext4 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
/dev/sdb1 on /media/matt/Brock type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfsd-fuse on /run/user/matt/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=matt)
/dev/sda1 on /media/matt/bigboy type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
root@192.168.1.108:/media/TOSHIBA EXT/TV/ on /home/matt/OPENELEC type fuse.sshfs (rw,nosuid,nodev,user=matt)
root@192.168.1.108:/media/ on /home/matt/OPENELECmovies type fuse.sshfs (rw,nosuid,nodev,user=matt)

---

