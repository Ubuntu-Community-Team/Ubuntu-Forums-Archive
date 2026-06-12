---
title: "Copying an EFS file from NTFS partition"
date: 2007-11-10
forum: General Help
---

### Post by clever on 2007-11-10
I am running Gutsy but I still have some files on an NTFS partition.  I can mount the partition and access most files just fine, but I am trying to be able to access the EFS encrypted files.

Specifically, I am trying to be able to use a Windows XP session running in VirtualBox to read and decrypt the files.  I exported my EFS encryption key from the original XP installation and I have imported the keys into the VirtualBox XP.  No problem there.  So I figure if I can just move the encrypted files into a place where the virtual XP can see them, then it would be able to decrypt them.

The problem is that I can't copy the encrypted files off the NTFS partition.  Say I have two files that I want to copy to my VirtualBox shared folder (where the XP session would be able to see the files).  One is un-encrypted cleartext, and the other is an encrypted file:
```

$ ls -l /mnt/oldwin
total 5
-rwxrwxrwx 1 root root 32 2007-11-10 12:53 clear.txt
-rwxrwxrwx 1 root root 41 2007-11-10 12:54 enc.txt

```

This works fine for the un-encrypted file:
```

$ sudo cp /mnt/oldwin/clear.txt /home/me/VirtualBoxShare

```

But when I try the same thing for the encrypted file, I get a permission denied error:
```

$ sudo cp /mnt/oldwin/enc.txt /home/me/VirtualBoxShare
cp: cannot open `/mnt/oldwin/enc.txt' for reading: Permission denied

```

Note that I am trying to do this as root so I don't know why I get permission problems.

I realize that I won't be able to read the contents of the encrypted file from Gutsy, but I didn't think I would have a problem with just moving the file around.  Is there any way to make this work that you guys can suggest?

---

