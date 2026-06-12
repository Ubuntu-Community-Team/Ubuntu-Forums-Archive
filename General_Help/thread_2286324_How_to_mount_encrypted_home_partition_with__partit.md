---
title: "How to mount encrypted /home partition with / partition is borked?"
date: 2015-07-11
forum: General Help
---

### Post by kevdog on 2015-07-11
I currently Ubuntu 14.04 LTS installed.  I partitioned my hard drive when I installed as /boot, /, /home and /swap.  The /home partition was set to be encrypted by the installer.  Somehow I've now borked my / partition.  The drive wont boot.  I get a ton of errors about the filesystem being corrupted.  I've run e2fsck a few times, however it doesn't seem to fix the problem.  I'm not necessarily interested in saving the installation as I can reinstall the root partition, however I'd like to preserve all the data on the /home partition.  I've yanked the drive and connected via USB to another linux installation.  I can mount the /boot partition and / partition (with errors) however I can't mount the encrypted /home partition.  Is there any way to manually mount this partition to extract the data to a different drive?  

Here is what I get:[   17.218676] EXT4-fs (sdb3): no journal found

I can mount the partition as read only:
sudo mount -o loop,ro,noexec,noload /dev/sdb3 /mnt/sdb3/

Then I get the following:
[kevdog@MacArch sdb3]$ ls -la
total 32
drwxr-xr-x 5 root   root    4096 Feb  6  2012 .
drwxr-xr-x 3 root   root    4096 Jul 11 03:44 ..
drwxr-xr-x 3 root   root    4096 Jan 10  2012 .ecryptfs
dr-x------ 3 kevdog kevdog  4096 Jan 10  2012 kevdog
drwx------ 3 root   root   16384 Jan 19  2012 lost+found

What do I do now however?

---

### Post by sudodus on 2015-07-11
Directly after the installation of the system with encrypted home (at the first log in (into the installed system)), I think you were offered to save the passphrase for the encrypted home. (This passphrase is *not* the same as the log in password.) If you did that, you should be able to use that passphrase to decrypt the data in your encrypted home. Otherwise you have no chance to decrypt it (with methods available for 'an average end user or even an experienced linux user').

Without that passphrase you need a good backup, and can recover the data by re-installing the system from the backup.

---

### Post by kevdog on 2015-07-11
I take it that is the 32 digit alphanumeric password correct?

[kevdog@MacArch sdb3]$ sudo ecryptfs-recover-private .
INFO: Found [.].
Try to recover this directory? [Y/n]: y
INFO: Could not find your wrapped passphrase file.
INFO: To recover this directory, you MUST have your original MOUNT passphrase.
INFO: When you first setup your encrypted private directory, you were told to record
INFO: your MOUNT passphrase.
INFO: It should be 32 characters long, consisting of [0-9] and [a-f].

Enter your MOUNT passphrase: 
mount: mount(2) failed: No such file or directory
ERROR: Failed to mount private data at [/tmp/ecryptfs.hV4LTR2O]


Hmm yeah.  I got problems since I don't know this anymore.  Question however.   Where is the wrapped passphrase file normal kept?

---

### Post by sudodus on 2015-07-11
Yes.

I don't know where it is stored, but it is stored after encryption anyway.

---

### Post by kevdog on 2015-07-11
Ok  -- Phew -- huge save.

Just some notes in case this happens to someone else.   

Using any linux distro - (Ubuntu Live CD is probably the easiest since it has the required packages, however its possible to do this on Arch for example with the ecryptfs-utils package installed.  Probably other distros have a similar package name.  If using any other distro than Ubuntu live CD, make sure you load the ecryptfs module by doing the following:

```
sudo modprobe ecryptfs
```   (Please note this is referenced on this page: ([https://wiki.archlinux.org/index.php/ECryptfs](https://wiki.archlinux.org/index.php/ECryptfs))
)

Ok
You'll need to either boot from the LiveCD or attach your borked drive via USB using an adapter similar to the Inland USB harddrive adapter ([http://inlandproduct.com/usb20toidesataadapterpartnumber08412.aspx]("http://inlandproduct.com/usb20toidesataadapterpartnumber08412.aspx"))

Once you boot the partitions may or may not show up.  Meaning I did a mount command and saw the /dev/sdb1 and /dev/sdb2 show up.  In my case /dev/sdb1 was the /boot partition and /dev/sdb1 was the / partition, but the home partition that contained the encrypted private directory which was created initially when installing Ubuntu, did not automount.  In my case this was known as /dev/sdb3

In order to mount the /home partition with the encrypted home directory, you can do something similar to this:
```
sudo mkdir /mnt/sda3
sudo mount -o loop,ro,noexec,noload /dev/sdb3 /mnt/sdb3/
```

In my case I had forgotten the 16 alphanumberic password that I was instructed to write down and guard with my life.  So much for guarding!! However its possible to recover this alphanumeric password (if your lucky by doing the following)

```
cd /mnt/sdb3/.ecryptfs/<user_name>/.ecryptfs
```

Hopefully within this directory there should be a file called wrapped-passphrase.  If this file doesn't exist, I can't help you. To recover the 16 digit password, do the following:
```
ecryptfs-unwrap-passphrase ./wrapped-passphrase
```

You'll need to know the original passphrase you wrapped the 16 alphanumeric password with.  If you can't remember this, this process will not work.  This command resulted in something like this:
```
116b053e08564b53b2967e64e509bdc5
```

Please note interestingly the command above worked through using the harddrive connected to my arch installation in a virtual machine, but it didnt work with the ubuntu live install disk.  I have no idea why it did not.  I can not explain this but rather pass this along as information.

Once getting this passphrase, do the following:
```
sudo ecryptfs-add-passphrase --fnek
Passphrase: 116b053e08564b53b2967e64e509bdc5
```

This results with:
```
Inserted auth tok with sig [b69fed2a22932ba4] into the user session keyring
Inserted auth tok with sig [8aad0fb4482edab3] into the user session keyring
```

Please note the two numbers in the bracket above.  You will need to make remember or make note of the second one:8aad0fb4482edab3

No do something similar to the following: (Please note this was taken from this link: [http://askubuntu.com/questions/60601/unwrapping-passphrase-and-inserting-into-the-user-session-keyring-failed]("http://askubuntu.com/questions/60601/unwrapping-passphrase-and-inserting-into-the-user-session-keyring-failed"))
```
sudo mkdir -p /home/kevdog/Private
sudo mount -t ecryptfs /mnt/sdb3/.ecryptfs/kevdog/.Private /home/kevdog/Private

Passphrase: 116b053e08564b53b2967e64e509bdc5
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32 (loaded)
 2) blowfish: blocksize = 16; min keysize = 16; max keysize = 56 (not loaded)
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24 (not loaded)
 4) cast6: blocksize = 16; min keysize = 16; max keysize = 32 (not loaded)
 5) cast5: blocksize = 8; min keysize = 5; max keysize = 16 (not loaded)
Selection [aes]: aes

Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 16

Enable plaintext passthrough (y/n) [n]: n

Enable filename encryption (y/n) [n]: y

{this is the second value from Inserted auth tok...}
Filename Encryption Key (FNEK) Signature: **8aad0fb4482edab3**

Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=8aad0fb4482edab3
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=b69fed2a22932ba4
Mounted eCryptfs
```

Your decrypted contents should then be available at the directory such as /home/kevdog/Private or whatever directory you chose to mount the encrypted directory. Copy and save the contents to a new hard drive, and breathe a sigh of relief.

---

### Post by sudodus on 2015-07-11
Congratulations :KS

And thanks for sharing your solution :-)

Lucky you, that you still remembered the original passphrase: > You'll need to know the original passphrase you wrapped the 16 alphanumeric password with.

---

### Post by sudodus on 2015-07-11
By the way, did you change the login password? And the problems with encrypted home started?

---

### Post by kevdog on 2015-07-12
No I didn't change the login password.  I'm not sure what the cause of the error was.  I know prior to this I updated the kernel however if that truly is the cause of the error I don't know.  The discs Smart Drive error went off, however interestingly, it only effects the system partition and not the other partitions on the disc.  I really don't know

---

### Post by sudodus on 2015-07-13
A new kernel can cause various problems, but it is not likely to bork the file system of the root partition. But it is hard to know for sure what happened.

Maybe the origin of the problem was a hardware failure, that the hard disk drive failed, and some blocks went bad (if the 'discs Smart Drive error' means the S.M.A.R.T. information).

Or was 'only' the file system of the root partition corrupted (only logical errors, not a hardware failure)? Maybe caused by a power failure (that the electric power supply was down long enough to cause a 'hard shutdown').

---

