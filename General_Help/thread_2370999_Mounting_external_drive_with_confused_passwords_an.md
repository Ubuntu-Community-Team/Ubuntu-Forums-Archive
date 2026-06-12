---
title: "Mounting external drive with confused passwords and encryption"
date: 2017-09-09
forum: General Help
---

### Post by Mark_in_Hollywood on 2017-09-09
I have had, a backup of /home on an external drive. The backup set was created by Ubuntu's "Backups" and for the rest of this post and further posts, I'll call it deja-dup to disambiguate.

The deja-dup has been used for several versions of Ubuntu, starting as far back as 12.04. The log-in password and the deja-dup password were the same. That is to say, to run deja-dup or restore from deja-dup a password is to be entered.

Now for the confusing part. Upon buying an ssd to put 16.04 on, I selected the install-time encryption. I wrote down the 32 character passphrase. Somehow, or other, the external device holding deja-dup's /home (copy), has been encrypted. I know this to be a fact because when the drive is powered up, and mounted, and the Access-Private-Data is called (or ran), the drive mounts in /media/mark (mark is the user name). The files on the external drive all have filenames starting with something like encrypfs_fnek . . . 

Now, oddly, deja-dup has no way to have a password changed. So, when some circumstances required a new password, (say 14.04), the deja-dup password had to be the one first ever used. I have that password.

Now for the next confusing part. After installing 16.04 on an ssd, I blew up that drive, or at least it's encryption. GParted could not delete the partitions (yes I was using a LiveISO.)  By drive, I mean the equivalent of Windws' C:. I have never see the proper nomenclature for a Linux C: (and yes, I know Linux doesn't use C: as a name). By drive I mean that storage device that is attached by (in my case) a SATA cable onto the computer's motherboard. The "Main" drive. I installed a replacement ssd. I re-installed 16.04 with install time encryption. I wrote down the (second, different) thirty-two character passphrase that I was told to do during the installation of 16.04.

So, now I have an external device holding the original deja-dup created backup of /home. But I cannot unlock it. I have 3 passwords or 2 passphrases and 1 password. I can mount the external drive.  Responses from earlier posts about my problem here reveal that the **data** is encrypted, (and here I'm guessing) as opposed to a or the partition being encrypted.

What do I do to recover (unlock, unencrpt, de-crypt) the files or objects (what you may call them).

---

### Post by TheFu on 2017-09-10
Ubuntu offers 2 different types of encryption.  dm-crypt and encryptfs.  
1) dm-crypt/LUKS is used for whole partition encryption.  It is relatively fast and is NOT tied to any specific userid.
2) encryptfs is normally used to encrypt HOME directories on a per-user basis.  It is slow and leaks information about the files unencrypted information.

Sounds like your original foreray into encryption used encryptfs.  I found no good way to backup data stored in that manner automatically and disabled it after a few months of testing.  I want 100% automatic, nightly, backups.  If I have to point-n-click at something to make a backup, that is a total failure.

deja-dup is based on duplicity.  duplicity is in the style of a backup system from 1970.  Weekly full backups and daily incremental backups would be the recommended method.  Constantly performing daily incremental backups for over 15-30 days would not be recommended with that tool. At some point, it is important to re-do the full backup.  The key really is not to have corruption because a full backup wasn't performed recently enough. [https://askubuntu.com/questions/625521/duplicity-deja-dup-full-backup-frequency](https://askubuntu.com/questions/625521/duplicity-deja-dup-full-backup-frequency)
If I were doing this, using this tool, I'd make a daily incremental backups and a full every 2 weeks.

I don't use deja dup for a number of reasons.

---

### Post by mterry2 on 2017-09-10
@TheFu, deja-dup does make occasional full backup checkpoints. But only every three months, which is less often than you'd like. But that likely isn't Mark's issue.

@Mark, are you able to see files on the backup drive? Ideally a *lot* of files that start with the name "duplicity-"

---

### Post by TheFu on 2017-09-10
I think the OP has encryptfs HOME encryption + duplicity encryption.  [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

I could have the exact name of the file system type wrong. There are a few options encfs, encryptfs, ecryptfs (I think).  The key is to mount the encrypted HOME first, then use the deja-dup password to restore the files. This is 2 steps.

---

### Post by Mark_in_Hollywood on 2017-09-11
mterry2 - there are a "lot of files", viz.:

 ```
root@Lexington:/media/mark/9deada4e-82ad-45fa-a1c6-a8e68d8b41f5/.ecryptfs/mark/.Private# ls
ECRYPTFS_FNEK_ENCRYPTED.FabE1bS80hpzR-T9b2YaJ-w2BGeT-W36kEE3.4Rufguc3sk-COzcqRrZx3YrzG3mse-mVvhOJhibbWAc7MnHxMrxALJS5l6Qv2c2uwJaBcQeAiAF-r7SMqmfp200xOp84ApA-WU-9s86iq2-
```

These "files" show in Properties are about 150gig. That is the size of the deja-dup backup, prior to that drive or data getting either LUKS or dm-crypt locked. I know this as I look at the size of the backup-set created by deja-dup every once in a while. And did so before starting a new OS install.

So, I'm asking, which comes first in this setup, the deja-dup or encryption passphrase? I must first unwrap (unlock? terminology ambiguation) the device/data/partition with the passphrase, and then further unlock the same with the password that deja-dup uses?

FWIW, the duplicity filenames were on that drive until the first ssd locked up and was replaced by a second ssd. I apologize at this point. I panicked about my /home. By the time of the attaching the 2nd ssd, the filenames on the external sata seem to have been encrypted, whereas, prior to that, the filenames were the deja-dup "duplicity" style. 

When the 2nd ssd had 16.04 installed, and I tried to run deja-dup's restore, it reported nothing backup-set to restore from. That is when I discovered that the other encryption was in force. The duplicity named files were on the sata external drive that has been used for several iterations of Ubuntu to backup the /home. From 12.04 to 16.04 if my memory serves me correctly. Since that time, I am able to mount the device, but the passphrase (32 character string) does not unlock it. Or at least I am not able to understand how to how unlock it. That does not mean I didn't use the unlock command at the cli; I did. It doesn't unlock, which is why I'm uncertain as to whether the deja-dup password must be applied first before the passphrase can work.

One last thing, I cannot, due to panicking, recall whether the files that hold the backup, are or are not encrypted with the login (computer power up time password, which is NOT the LUKS or dm-crypt encryption passphrase. That is, if the passphrase encryption is unwrapped or unlocked, the files may show as regular files, not a string of duplicity filename files.

---

### Post by mterry2 on 2017-09-12
@Mark, you said "I must first unwrap (unlock? terminology ambiguation) the device/data/partition with the passphrase, and then further unlock the same with the password that deja-dup uses?"

And yes, that's what you need to do. Decrypt the partition, then once you have a bunch of duplicity-* files, you can use deja-dup.

I'm not sure how to help with decrypting the partition though, sorry.

---

### Post by TheFu on 2017-09-12
post #4 has the link he needs.

---

### Post by Mark_in_Hollywood on 2017-09-12
While the bytes on the external drive are the files that deja-dup made a backup set of, they are not an encrypted /home as I read the Community Page at Post #4, as TheFu notes. What "encryption" there is comes from Ubuntu's backup in-built backup system, called Backups (based on Duplicity). While those bytes must be a sub-folder of root, they aren't a directory, such as /home. As each drive must be partitioned, the external sata has ext4 filesystem and the entire device is but one partition.

From a while ago, while working on this:

```
root@Lexington:/media/mark/9deada4e-82ad-45fa-a1c6-a8e68d8b41f5/.ecryptfs/mark/.Private# ecryptfs-mount-private
ERROR: Encrypted private directory is not setup properly
```

Reading the pages of [EncryptedPrivateDirectory]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Data_Manually") has not helped me to understand what is locked or wrapped. I have tried several times to follow what is there, but I'm not understanding whether I do or do not have an encrypted partition, folder, directory, as deja-dup doesn't make files like gedit or printing/saving a page of a URL would.

---

### Post by TheFu on 2017-09-12
See the part that says ".ecryptfs" - that is a huge hint that you need to mount that encrypted storage BEFORE you can get to any of the files stored there.

If the encryption cannot be decrypted and mounted (probably happens at the same time), then you cannot get access to the backup files.  Whenever using encryption, haven't a know-you-can-restore backup is absolutely mandatory.  Even more so with dm-crypt/LUKS.

So, right now, you need to solve the **ERROR: Encrypted private directory is not setup properly** issue before worrying at all about duplicity/deja-whatever.   [https://askubuntu.com/questions/613691/cant-access-my-home-directory-encrypted-private-directory-is-not-setup-properl](https://askubuntu.com/questions/613691/cant-access-my-home-directory-encrypted-private-directory-is-not-setup-properl) might be a solution.  It worked for someone else.  Seems the CWD matters greatly to the ecryptfs-mount-private command. 
There is an article about this here: [https://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](https://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/) - they are fairly reputable, provided the distro and version are close.

---

### Post by Mark_in_Hollywood on 2017-09-15
Results from LiveISO session.

Running sudo fdisk -l while external /home is powered up up freezes. So no /dev/sdXX is viewable.

Opening Natuilus file manager panel icon of external /home. I cannot see the icon: Access-Private-Data (yes, CTRL-H shows hid folders.)
I have been able to run the Access-Private-Data in prior LiveISO sessions.

In terminal running blkid: shows that external /home is not mounted.

This has not happened before.

sudo mount -a

and blkid again shows no ext /home.

running "disks" shows ext /home mounted as /dev/sdc1

```
file:///media/ubuntu/9deada4e-82ad-45fa-a1c6-a8e68d8b41f5
```


Returned to deferredIOs post despite forgoing

```
udisks --mount /dev/sdc1
```

terminal returns: command not found

```
sudo apt update
```

ran, and next:

```
ubuntu@ubuntu:~$ sudo apt install udisks

E: Unable to locate package udisks
```

--- next ---

Continuing with deferredIOs post despite foregoing:

```
ubuntu@ubuntu:/media/ubuntu/9deada4e-82ad-45fa-a1c6-a8e68d8b41f5$ ls
lost+found  mark  username

ubuntu@ubuntu:/media/ubuntu/9deada4e-82ad-45fa-a1c6-a8e68d8b41f5$ cd /media/ubuntu/9deada4e-82ad-45fa-a1c6-a8e68d8b41f5/mark
bash: cd: /media/ubuntu/9deada4e-82ad-45fa-a1c6-a8e68d8b41f5/mark: Permission denied
```

Continuing with deferredIOs post:

```
ubuntu@ubuntu:/media/ubuntu/9deada4e-82ad-45fa-a1c6-a8e68d8b41f5$ sudo ecryptfs-recover-private .Private/
INFO: Searching for encrypted private directories (this might take a while)...
find: ‘/run/user/999/gvfs’: Permission denied
find: File system loop detected; ‘/sys/kernel/debug/pinctrl’ is part of the same file system loop as ‘/sys/kernel/debug’.
```

Stop deferredIOs post. Continue with 

Accessing encrypted home from LiveCD
[https://answers.launchpad.net/ecryptfs/+question/114209](https://answers.launchpad.net/ecryptfs/+question/114209)


```
mark@Lexington:/$ sudo ecryptfs-add-passphrase --fnek
[sudo] password for mark: 
Passphrase: 
Inserted auth tok with sig [de0357543abe6969] into the user session keyring
Inserted auth tok with sig [8a0b80df2b4e58a7] into the user session keyring
```

```
ubuntu@ubuntu:~$ sudo mount -t ecryptfs /media/ubuntu/9deada4e-82ad-45fa-a1c6-a8e68d8b41f5/mark/.Private /mnt
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32
 2) blowfish: blocksize = 8; min keysize = 16; max keysize = 56
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16
Selection [aes]: aes
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 16
Enable plaintext passthrough (y/n) [n]: n
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [de0357543abe6969]: 8a0b80df2b4e58a7
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=8a0b80df2b4e58a7
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=de0357543abe6969
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [de0357543abe6969] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : yes
Successfully appended new sig to user sig cache file
Error mounting eCryptfs: [-2] No such file or directory
Check your system logs; visit <http://ecryptfs.org/support.html>

```

Please recall that I do have two passphrases. One from the first SSD install and another from the second SSD install. I used the second passphrase. I didn't try the first (older) one. Would Ubuntu's "Backups" (deja-dup) have a username? Also, "disks" shows GPT, but also says Microsoft Basic Data.

---

