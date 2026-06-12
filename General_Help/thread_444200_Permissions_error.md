---
title: "Permissions error"
date: 2007-05-15
forum: General Help
---

### Post by the.dark.lord on 2007-05-15
A friend of mine installed Ubuntu Feisty Fawn (7.04), and has a strange error with it. First- he has two HDDs. 
1st HDD- Ubuntu
2nd HDD- Files 

He has Read Only permissions for the second HDD (owner:unknown,  error when tried to change:SORRY,COULDNT CHANGE THE PERMISSIONS OF "PRASH(2nd HDD)"). Help please.

Thanks.

---

### Post by taurus on 2007-05-15
What filesystem is that second harddrive?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by the.dark.lord on 2007-05-15
> **taurus said:**
> What filesystem is that second harddrive?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

Thanks for replying. He tells me it is NTFS.

---

### Post by kb2wdi on 2007-05-15
This is common issue with FAT and NTFS partitions.

you need to add "ro,uid=1000,gid=1000" to the mount options in "/etc/fstab" file to change owner and group from <root> to normal account.

---

### Post by taurus on 2007-05-15
For ntfs filesystem, you need to use ntfs-eg driver before you can write to it.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by the.dark.lord on 2007-05-16
Thanks for the replies, people. He got it working now :)

---

