---
title: "Disk Encription - Auto unlock at boot"
date: 2023-11-15
forum: General Help
---

### Post by wesbrooks on 2023-11-15
Hi All, been through various website guides but feel like I'm hitting a brick wall on this one. Seemingly simple task. I have an extra drive that I would like to encrypt and use as local copy of my dropbox data. This is what I have tried:

# Formatted partion:
linux:~$ sudo cryptsetup -y -v luksFormat /dev/sdd1

# Opened partion (asks for passphrase):
linux:~$ sudo cryptsetup -v luksOpen /dev/sdd1 dropbox

# Formatted the patition and created mapper:
linux:~$ sudo mkfs.ext4 /dev/mapper/dropbox

# Made mount point:
linux:~$ sudo mkdir -p /mnt/dropbox

# Mount the drive:
linux:~$ mount -v /dev/mapper/dropbox /mnt/dropbox/

# View luks dump:
linux:~$ sudo cryptsetup luksDump /dev/sdd1

# Add a keyfile to the encrypted partition (asks for passphrase):
linux:~$ sudo cryptsetup luksAddKey /dev/sdd1 /etc/crypttab.keyfile

# Unmount the drive:
linux:~$ sudo umount /mnt/dropbox

# Close the drive:
linux:~$ sudo cryptsetup -v luksClose dropbox

# Open the drive:
linux:~$ sudo cryptsetup -v luksOpen /dev/sdd1 dropbox --key-file=/etc/crypttab.keyfile

# Get UUID date for the drive:
linux:~$ blkid /dev/sdd1
/dev/sdd1: UUID="a183cf32-6693-4b46-9eb0-ddb7ff6dd99e" TYPE="crypto_LUKS" PARTUUID="53090a98-d9e6-4777-bad7-6ae32f5a4b7e"

# Open editor and add line:
linux:~$ sudo gedit /etc/crypttab

dropbox   /dev/disk/by-uuid/a183cf32-6693-4b46-9eb0-ddb7ff6dd99e /root/crypttab.keyfile luks

# Open edito and add line:
linux:~$ sudo gedit /etc/fstab

/dev/mapper/dropbox /mnt/dropbox ext4 defaults 0 0

# Test mounting:
linux:~$ sudo mount -av

# Update initramfs:
linux:~$ sudo update-initramfs -c -k $(uname -r)

All the above works, but the log in crashes after adding the main unlock passphase for the ubunutu system. This is 22.04 LTS and was installed using the encryption option. Thanks for any help you can offer. I cobbled the above together from the following links:

[https://www.redhat.com/sysadmin/disk-encryption-luks](https://www.redhat.com/sysadmin/disk-encryption-luks)
[https://askubuntu.com/questions/59487/how-to-configure-lvm-luks-to-autodecrypt-partition](https://askubuntu.com/questions/59487/how-to-configure-lvm-luks-to-autodecrypt-partition)
[https://askubuntu.com/questions/1351911/what-does-regenerate-your-initramfs-mean](https://askubuntu.com/questions/1351911/what-does-regenerate-your-initramfs-mean)

---

### Post by wesbrooks on 2023-11-15
Got it! Writing it down seemed to have helped!

# Get UUID date for the drive:
linux:~$ blkid /dev/sdd1
/dev/sdd1: UUID="a183cf32-6693-4b46-9eb0-ddb7ff6dd99e" TYPE="crypto_LUKS" **PARTUUID="53090a98-d9e6-4777-bad7-6ae32f5a4b7e"**

# Open editor and add line:
linux:~$ sudo gedit /etc/crypttab

dropbox   /dev/disk/**by-partuuid/a183cf32-6693-4b46-9eb0-ddb7ff6dd99e** /root/crypttab.keyfile luks

---

### Post by TheFu on 2023-11-15
Don't use sudo with gui tools.  To edit system files, set your EDITOR environment variable, then use **sudoedit** instead.

Explaining things often points out flaws in our own steps.  No so sure I'd want anything encrypted to unlock automatically myself, but if your purpose for encryption is to make returning storage devices with failures to the storage vendor under warranty and you don't really care about system security, then I suppose it is fine.

---

### Post by wesbrooks on 2023-11-16
Out of curiosity why is using GUIs with sudo advised against?

My understanding:

My system is encrypted, so any keys to automatically unlock the drive can only be accessed if the operator has already got past my main drive encryption. The intention here was to add an additional drive to the system purely as a local copy of remote data. If I didn't have this encrypted then the whole contents would be easily readable should my device have been stolen.

---

### Post by ActionParsnip on 2023-11-16
[https://bencane.com/2012/02/26/sudoedit-securely-allow-users-to-edit-files/](https://bencane.com/2012/02/26/sudoedit-securely-allow-users-to-edit-files/)

---

### Post by TheFu on 2023-11-16
> **wesbrooks said:**
> Out of curiosity why is using GUIs with sudo advised against?

GUI programs often will create settings under the currently running uid.  I've seen where someone would do a fresh install, then use **sudo gedit /etc/some-file-here** and that would create all the setting files under the user's home, not root's.  Doing that would create root-owned directories, files, dbs, etc in a user's home and prevent the user from having any access. This would crash any other programs, like the Gnome DE, so they'd be stuck in a login loop forever. 

non-GUI programs, like vim, don't create settings without a special request. It just doesn't happen, so *sudo nano* or *sudo vim* always turn out to be fine.

But if you set your desired EDITOR into the environment and use **sudoedit**, then any editor, including GUI programs will not cause issues.  The editors never run under another userid when started by sudoedit.  And if the editing isn't running under elevated permissions, then shelling out as root isn't another danger.  Those are a few reasons why it is safer.  There are probably 10 more.

Whenever I see instructions from people using sudo gedit, that makes me wonder what other details they got wrong.  BTW, sudoedit has been around a long time, so we all need to get the word out. Sometimes old-timers don't know about it.

---

### Post by wesbrooks on 2023-11-20
Thanks for the clarifications. I'll read through the link and follow the advice.

Just checking on the other issue that was flagged up. Did my use case for unencrypting the hard drive at boot make sense?

---

### Post by MAFoElffen on 2023-11-20
I do the same in crypttab for storing the keyfile on a USB key, as another level... For booting where I have an encrypted root, then on that drive, store keyfiles to the other encrypted partitions, that are unlocked, then mounted into the filesystem. So the initial USB stored keyfile can be removed, and secured elsewhere...

Security wise, if you are storing the key on a disk that is not encrypted and cannot be secured by physical security, such as with a removable storage, then that sort of is for nothing, right? Because the key is "there" in the clear.

Does that make sense?

---

