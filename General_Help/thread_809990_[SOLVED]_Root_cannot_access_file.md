---
title: "[SOLVED] Root cannot access file"
date: 2008-05-27
forum: General Help
---

### Post by Bokonon on 2008-05-27
Hello,

I noticed this during the latest update to gdm.  When aptitude goes to configure gdm I get an error that /var/lib/gdm/.cookie cannot be accessed.

I have tried everything I can think of to modify or get rid of this file, but even as root, I cannot do anything.  I also tried to boot to the recovery CD and get the same errors.

Filesystem is jfs and fsck.jfs reported no errors on the partition.  .cookie2 is a copy of the same file from a similar system.

Hardy 64 bit.

Here is an example of my terminal:

root@m1210e:/var/lib/gdm# ls -ail
ls: cannot access .cookie: Permission denied
total 32
  9140 drwxrwx--T  3 root gdm  8192 2008-05-28 10:32 .
395648 drwxr-xr-x 58 root root 4096 2008-05-27 23:33 ..
 82078 -rw-r-----  1 root root   45 2008-05-28 10:32 :0.Xauth
110712 -rw-r--r--  1 root root   64 2008-05-28 10:32 :0.Xservers
209390 ??????????  ? ?    ?       ?                ? .cookie
442382 -rw-------  1 gdm  gdm    33 2008-05-27 23:32 .cookie2
442383 drwxr-xr-x  2 gdm  gdm    32 2008-05-27 23:32 .fontconfig
 82076 prw-rw----  1 root root    0 2008-05-28 10:32 .gdmfifo
root@m1210e:/var/lib/gdm# rm .cookie
rm: cannot remove `.cookie': Permission denied
root@m1210e:/var/lib/gdm# rm -f .cookie
rm: cannot remove `.cookie': Permission denied
root@m1210e:/var/lib/gdm# chown root.root .cookie
chown: cannot access `.cookie': Permission denied
root@m1210e:/var/lib/gdm# chmod 777 .cookie
chmod: cannot access `.cookie': Permission denied
root@m1210e:/var/lib/gdm#

---

### Post by unutbu on 2008-05-27
Please post
```
sudo lsattr -a /var/lib/gdm/
```

---

### Post by Bokonon on 2008-05-27
weflemi@m1210e:~/workspace/system$ sudo lsattr -a /var/lib/gdm/
------------------ /var/lib/gdm/.
------------------ /var/lib/gdm/..
/var/lib/gdm/.cookie: Permission denied
------------------ /var/lib/gdm/.cookie2
------------------ /var/lib/gdm/.fontconfig
lsattr: Operation not supported While reading flags on /var/lib/gdm/.gdmfifo
------------------ /var/lib/gdm/:0.Xauth
------------------ /var/lib/gdm/:0.Xservers
weflemi@m1210e:~/workspace/system$

I think this is just some crazy fluke that happened during my upgrade and not an indication of disk trouble.  I haven't noticed anything funny other than this.

I have been looking for a way to delete the file by inode.

find . -inode <number> -exec rm {} \;

Does not work.  I get the same permissions error.  That seems to be more for files with crazy characters and does not help me.

sudo cp /dev/null /var/lib/gdm/.cookie 

Also fails.

---

### Post by Bokonon on 2008-05-27
This would be a hack, but is there a place in the gdm config that I could specify a different file than /var/lib/gdm/.cookie ?

That way I should be able to complete the upgrade.

---

### Post by unutbu on 2008-05-27
Sorry, I'm stumped. :(

---

### Post by Bokonon on 2008-05-27
I did some searching for single user mode hoping that would give me access, but stumbled across this.

Basically, it got fixed by running fsck during the boot process.  I saw 3 objects having incorrect links and they were all related to gdm.  The fsck ran fsck.jfs apparently and cleaned up the problems.

sudo aptitude safe-upgrade worked after the clean.

I don't know why my fsck.jfs /dev/sda2 (/ partition on a dual-boot system) from the 'live cd' reported no errors, but running fsck on reboot worked.

For anyone who runs into this problem, here is the thread that helped me.  The 

sudo touch /forcechck 

trick mentioned in the thread worked for me on Hardy. FWIW, the file gets removed automatically, so your next boot after the check will be a normal one.

[http://ubuntuforums.org/showthread.php?t=785219&highlight=single+user+mode]("http://ubuntuforums.org/showthread.php?t=785219&highlight=single+user+mode")

---

