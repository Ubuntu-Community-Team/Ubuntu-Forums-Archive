---
title: "Weirdness trying to mount 2 luks partitions on boot"
date: 2014-05-20
forum: General Help
---

### Post by ejbiow on 2014-05-20
It seems like it should be fairly easy to open two luks-encrypted partitions at boot with only a single password. I already had an encrypted data partition that I set up with a fresh install of Ubuntu 14.04. I added a second hard drive and wanted it encrypted as well, preferably without having to enter two passwords.  I used [this page]("http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile") as a [guide]("http://ubuntuforums.org/showthread.php?t=2219806").  It suggested using a keyfile on the first encrypted partition.  My steps:

1. Create a keyfile.
sudo dd if=/dev/urandom of=/mnt/server/keyfile bs=1024 count=4
Chmod 0400 it so that only root can read it.  

2. Add the keyfile to LUKS.
cryptsetup luksAddKey /dev/sdc3 /mnt/server/keyfile
I got no errors.

3. Edit my /etc/crypttab
luks-sdc3 UUID=xxxxxxxxx /mnt/server/keyfile  luks,discard,nofail

4. Add an entry to my fstab.
 /dev/mapper/luks-sdc3  /mnt/server/moredata  ext4   defaults  0    2 

On rebooting I found that I plugged in my encryption password, but said it was waiting for tney new encrypted partition (/mnt/server/moredata) to mount. It was pretty clear that it wasn't going to do so, so I hit S a couple of times to boot up anyway.  The new partition wasn't mounted.  I failed to unlock the partition by hand because it said it was already unlocked as /dev/dm-1!  So I remmed out my previous fstab entry for the partition and added:

/dev/dm-1  /mnt/server/moredata  ext4   defaults  0    2 

It seems to work OK.  I don't really mind hitting S a couple of times, but it is not what I expected and was a general PITA to figure out.  Any ideas what I'm doing wrong?

---

