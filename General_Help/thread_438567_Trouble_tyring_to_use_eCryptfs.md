---
title: "Trouble tyring to use eCryptfs"
date: 2007-05-09
forum: General Help
---

### Post by tgcUbuntu on 2007-05-09
I am trying to use eCryptfs. I first did: sudo modprobe ecryptfs and then tried the mount:
sudo mount -t ecryptfs ~/secret ~/secret
I got the following error:
mount: wrong fs type, bad option, bad superblock on /home/ted/secret,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
 
The error in dmesg gave this: 4448.098988] Error parsing options; rc = [-22]

I'm using Ubuntu 7.04 which I recently upgraded to. Any idea what I'm doing wrong?

---

### Post by IgnorantGuru on 2007-05-09
I haven't used ecryptfs so I may not be much help, but generally the wrong fs type comes up when the filesystem is missing (not formatted).  Maybe you need to format the container with ecryptfs first?   eg something like mkfs -t ecryptfs /home/ted/secret   ???

---

### Post by mhalcrow on 2007-05-14
There is no need to format anything to use eCryptfs. It stacks right on top of an existing directory.

Do not use sudo. ``su -'', then mount (unless you're set up for user mounts, but it doesn't look like that's what you want). Sudo will screw with your keyring (the key might wind up in the user keyring rather than the root keyring).

Make sure ecryptfs, aes, cbc, ecb, and md5 are all loaded in your kernel.

Post to ecryptfs-users if you're still having problems.

Mike

---

### Post by awry on 2007-05-14
Have you installed the ecryptfs userspace utilities?  

eCryptfs consists of two components: (1) a kernel module, which is included in the stock Feisty kernel; and (2) userspace utilities, which are not yet packaged for ubuntu (request/bug report in [launchpad]("https://bugs.launchpad.net/ubuntu/+bug/114426"))

You must have both components to use eCryptfs.  So you must compile the userspace utilities from the sources, which you can get from [http://ecryptfs.sourceforge.net/](http://ecryptfs.sourceforge.net/), or wait for the ecryptfs userspace utilities to make it into the ubuntu repositories with (hopefully) the next release.

Of course, you can still use dm-crypt as an (albeit less convenient) out-of-the-box encryption mechanism under ubuntu.

Cheers!

---

### Post by tgcUbuntu on 2007-05-28
Thanks for the help. I hadn't installed the userspace utilities. I did the following to get it to work:

I am running the current version of Ubuntu: 7.04

1. Downloaded keyutils-1.2.tar.bz2 from here: [http://people.redhat.com/~dhowells/keyutils](http://people.redhat.com/~dhowells/keyutils)
    Unpacked and installed it: make & sudo make install
2. Downloaded ecryptfs-utils-15.tar.bz2 from: [http://ecryptfs.sourceforge.net/](http://ecryptfs.sourceforge.net/)
    Unpacked then did: ./configure --prefix=/usr
                                         make
                                         sudo make install

3. sudo modprobe ecryptfs    (not sure if this was necessary)
4. sudo mount -t ecryptfs /secret /secret
   At this point the ecryptfs program askes for various information. After answering the questions it mounts the directory.

    I was able to copy a file into the /secret directory, looked at it to see it  unecrypted then I unmounted /secret and then looked at the file again and found it was in fact encrypted. 

I still have a problem however. When I go to remount the directory ecryptfs ends up asking all the initial questions again. I answer them the same way I originally did and it goes ahead and remounts the directory. The file that I put in the /secret directory is still there.

---

### Post by danieljuh on 2008-04-11
has anyone had any further success of using ecryptfs?

im prolly stupid or something similiar, but i end up with:

Required mount option not provided: [ecryptfs_key_bytes=]
Invalid mount options; aborting. rc = [1]
Error mounting eCryptfs; rc = [-1]; strerr = [Operation not permitted]. Check your system logs;


did tgcUbuntu solve the problem he/she had?

---

