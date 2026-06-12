---
title: "User-mode-linux on 2.6.10"
date: 2005-06-16
forum: General Help
---

### Post by shmk on 2005-06-16
I'm using Ubuntu Hoary with kernel 2.6.10-5-i386  
 
This is what I do for install:  
- download from ubuntu's repository the package "linux-source-2.6.10" 
- I insert tar.bz2 souce file in a new directory called /usr/src/uml  
- Untar with "tar -xvjf"  
- enter in the dir with the source and digit  
make mrproper ARCH=um  
make xconfig ARCH=um  
make modules ARCH=um  
- at this point download "uml-utilities" 
- and test.  
 
For testing I downloaded from the official uml site Debian-3.0r0  
 
To launch I used: 
/vmlinux ubd0=PERCORSO_FS  
 
But uml exit with this error:  
"Initializing Cryptographic API  
sleeping process XXXX got unexpected signal : 11  
 
actually_do_remove : couldn't open directory '/root/.uml/AbJ9iL', errno = 2  
actually_do_remove : couldn't open directory '/root/.uml/AbJ9iL', errno = 2  
Kernel panic - not syncing: Segfault with no mm"  
OR :  
"Initializing stdio console driver  
sleeping process XXXX got unexpected signal : 11  
 
actually_do_remove : couldn't open directory '/root/.uml/6nKFvh', errno = 2  
actually_do_remove : couldn't open directory '/root/.uml/6nKFvh', errno = 2  
Kernel panic - not syncing: Segfault with no mm"  
 
 
Thinking that I have missed some setting in the compile step on 2.6.x kernel I followed this how-to:  
 
[http://uml.harlowhill.com/index.php/Troubleshooting](http://uml.harlowhill.com/index.php/Troubleshooting)  
Using this settings the error is different: 
 
"VFS: Cannot open root device "devicename" or unknown-block(x,y) Please append a correct "root=" boot option"  
 
I tried to append root=/dev/ubd0 or /dev/ubd/0 or /dev/ubda  
without better results 
 
Someone can give me a hand ?

---

### Post by frodon on 2005-06-16
I don't understand exactly what is your problem, but you can try to run the same command using sudo, or like me install the linux sources using synaptic (really fast and easy !).

---

### Post by shmk on 2005-06-16
[QUOTE=frodon]I don't understand exactly what is your problem, but you can try to run the same command using sudo, or like me install the linux sources using synaptic (really fast and easy !).[/QUOTE]
 - I have downloaded linux-source with synaptic... and with a 56k is not so fast :p

- My problem is that I cannot install "user-mode-linux" AKA "UML"

- I don't need to use SUDO because I made the procedure to automatically have superuser privileges when login with the root user

---

### Post by piedamaro on 2005-06-22
You have an UML kernel, now you need a root filesystem image (it 's usually a file) to boot your kernel on. You can download a uml root_fs of many distribtions from the uml site, but there is no ubuntu prepackaged root_fs. 
You can make your own one,  in fact I've installed ubuntu on uml these days, and I'd like to write an howto about that, but you know...time. :(

ubdX is the devìce used by the _virtual_ machine, you should run it with something like this:
./linux mem=64M ubd0=root_fs  devfs=nomount con=xterm  eth0=tuntap,tap0

root_fs is a file in the current dir where I installed a minimal ubuntu system, con=xterm tells the kernel to boot in a separate xterm.

RTM carefully, there are so many paramaters to boot your UML kernel, and installing or booting an UML machine it's a challenging and enjoyable experience :)
Also take a look at  [http://www.netkit.org/](http://www.netkit.org/)

and (italian):[http://www.tic.fdns.net/tic/html/lab.html](http://www.tic.fdns.net/tic/html/lab.html) 

P.S. "- I don't need to use SUDO because I made the procedure to automatically have superuser privileges when login with the root user"
If it means you login ususally as root, it's a bad habit, really.

Vedo ora che sei italiano, c'è una guida per Debian qui: 
There is a Debian uml guide here (italian):
[http://www.pluto.it/journal/pj0504/uml2.html](http://www.pluto.it/journal/pj0504/uml2.html)
:)

---

### Post by shmk on 2005-06-23
I'm testing with the Debian-3.0r0.ext2 found on official UML site, is it wrong ?
I have to self-made a Ubuntu one ?

Now the error I got is this

```
./linux mem=64M ubd0=root_fs devfs=nomount
Checking for the skas3 patch in the host...not found
Checking for /proc/mm...not found
Checking PROT_EXEC mmap in /tmp...OK
tracing thread pid = 14767
Linux version 2.6.10 (root@ubuntu1) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Thu Jun 23 12:26:17 CEST 2005
Built 1 zonelists
Kernel command line: mem=64M ubd0=root_fs devfs=nomount root=98:0
PID hash table entries: 512 (order: 9, 8192 bytes)
Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
Memory: 61696k available
Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
Checking for host processor cmov support...Yes
Checking for host processor xmm support...No
Checking that ptrace can change system call numbers...OK
Checking syscall emulation patch for ptrace...missing
Checking that host ptys support output SIGIO...Yes
Checking that host ptys support SIGIO on close...No, enabling workaround
Checking for /dev/anon on the host...Not available (open failed with errno 2)
NET: Registered protocol family 16
mconsole (version 2) initialized on /root/.uml/Ur15zu/mconsole
ubd: Synchronous mode
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 4096K size 1024 blocksize
NET: Registered protocol family 2
IP: routing cache hash table of 512 buckets, 4Kbytes
TCP: Hash tables configured (established 4096 bind 8192)
NET: Registered protocol family 1
NET: Registered protocol family 17
Initializing software serial port version 1
elevator: using anticipatory as default io scheduler
 ubda: unknown partition table
Initializing stdio console driver
VFS: Mounted root (ext2 filesystem) readonly.
INIT: version 2.84 booting
Activating swap.
Checking root file system...
fsck 1.27 (8-Mar-2002)
fsck.ext2: No such file or directory while trying to open /dev/ubd/0
/dev/ubd/0:
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


fsck failed.  Please repair manually and reboot.  Please note
that the root file system is currently mounted read-only.  To
remount it read-write:

   # mount -n -o remount,rw /

CONTROL-D will exit from this shell and REBOOT the system.

(none):~#

```

PS: I have a 56k so less I download better is...

---

### Post by piedamaro on 2005-06-23
> I have to self-made a Ubuntu one ?
No, sorry, I've missed the point where you said you are using a debian_fs.

"fsck.ext2: No such file or directory while trying to open /dev/ubd/0"

Probably the root image was created with devfs, however in etc fstab you should have something like this:

proc            /proc          proc    defaults 0       0
/dev/ubd0       /              ext2    defaults,errors=remount-ro 0       1

thus make sure you have the /dev/ubd0 device. 
(if not:  mknod /dev/ubd0 b 98 0  insede the virtual machine)

---

### Post by shmk on 2005-06-30
Boh, I cannot understand if now it's ok... is there a command to test if all uml functions works ?

---

### Post by shmk on 2005-08-16
[QUOTE=shmk]Boh, I cannot understand if now it's ok... is there a command to test if all uml functions works ?[/QUOTE]
 Because after login I'm in the uml console but with "ls" there isn't "normal" linux folders (/usr /home ...) ... is it normal ? The only things I can see with "ls -a" are .profile .bash_history .bashrc
(the various commands like mkdir, rmdir ... functions properly)

---

### Post by shmk on 2005-08-16
[QUOTE=shmk]Because after login I'm in the uml console but with "ls" there isn't "normal" linux folders (/usr /home ...) ... is it normal ? The only things I can see with "ls -a" are .profile .bash_history .bashrc
(the various commands like mkdir, rmdir ... functions properly)[/QUOTE]
 My bad... I was in the wrong folder...

---

