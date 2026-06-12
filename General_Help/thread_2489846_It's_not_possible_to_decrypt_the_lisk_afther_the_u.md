---
title: "It's not possible to decrypt the lisk afther the updute"
date: 2023-08-11
forum: General Help
---

### Post by dimebagplug on 2023-08-11
hello
System Ubuntu
, I'm looking for help with logging in to the system or advice on how to pull files from an encrypted drive.
The system was encrypted during the installation of the system with the built-in LUKS encryption.
After the context menu of the update was displayed, and I updated the system to the next version, not through the terminal and commands, the computer at the first start and my attempt to enter the password for the system and disk, it does not work, it simply cannot move further, because it writes that the password is incorrect.
My guesses are that the system was updated incorrectly and packages could mix because of this there was a problem with the inability to decrypt the disk.
through the live system, there were attempts to directly open the disk through the following commands, but nothing happened

sudo cryptsetup luksOpen --test-passphrase /dev/sdb3
sudo cryptsetup luksHeaderBackup /dev/sdb3 --header-backup-file luksHeader.bin
sudo cryptsetup luksOpen --test-passphrase luksHeader.bin
sudo cryptsetup luksOpen /dev ubuntu --debug
sudo cryptsetup luksHeaderRestore /dev/sdb3 --header-backup-file luksHeader.bin

[https://imgur.com/a/kMssL26](https://imgur.com/a/kMssL26)

---

### Post by MAFoElffen on 2023-08-11
> **dimebagplug said:**
> 
```

sudo cryptsetup luksOpen --test-passphrase /dev/sdb3  [COLOR=#ff0000]## Do  not  activate device, just verify passphrase. No mapping name was supplied, so would prompt.[/COLOR]
sudo cryptsetup luksHeaderBackup /dev/sdb3 --header-backup-file luksHeader.bin [COLOR=#ff0000]## Stores a binary backup of the LUKS header and ke***** area.[/COLOR]
sudo cryptsetup luksOpen --test-passphrase luksHeader.bin  [COLOR=#ff0000]## [/COLOR]
sudo cryptsetup luksOpen /dev ubuntu --debug [COLOR=#ff0000]## Note -- Incorrect format of command... ???[/COLOR]
sudo cryptsetup luksHeaderRestore /dev/sdb3 --header-backup-file luksHeader.bin [COLOR=#ff0000] ## Dangerous. Overwrite header from a working backup file.[/COLOR]

```

Ouch. Let me try to understand just what you did... Hopefully it is still recoverable. In the key slots, I am assuming you only have a single passphrase entered(?)

Those commands would have assumed that you had already backed up the LUKS container header to a file called luksHeader.bin previous to this. 

What is the output of this from a LiveUSB 
```

lsblk -e7 -o name,label,size,fstype,model

```
It sounds like you did not have backups of the data... Right

---

### Post by dimebagplug on 2023-08-11
That's right, only one password, which was entered when the system was created. There were no keys or restore points. These are the commands I entered to try and repair

---

### Post by dimebagplug on 2023-08-11
[https://imgur.com/a/NB6bDLN](https://imgur.com/a/NB6bDLN)

---

### Post by dimebagplug on 2023-08-11
The name of the disk is different, do not pay attention, since my system was installed on two, external and internal, where they were divided into system files and home

---

### Post by MAFoElffen on 2023-08-11
> **dimebagplug said:**
> The name of the disk is different, do not pay attention, since my system was installed on two, external and internal, where they were divided into system files and home
Please explain that so i know which disks I am looking at in relation to what they contain...

Maybe more:
```

sudo blkid | grep 'TYPE=\"crypto_LUKS\"'
DISKS=$(sudo blkid | awk '/crypto_LUKS/ {print $1} ' | sed 's/\://g')
for disk in ${DISKS[@]}; do sudo cryptsetup luksDump $disk; done

```

---

