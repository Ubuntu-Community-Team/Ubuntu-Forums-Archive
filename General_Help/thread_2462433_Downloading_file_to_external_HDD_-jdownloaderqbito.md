---
title: "Downloading file to external HDD -jdownloader/qbitorrent"
date: 2021-05-20
forum: General Help
---

### Post by Automat2 on 2021-05-20
Hello,
I created a standard user account in my box. I am the "admin".
Before I created this other account, I could use JD/qbitorrent and download the files on the external HDD with no problem.
Now I try to do it and neither app allows me to use this external HDD though "Files" shows it mounted and I can open and transfer files to/from it with no problem.
If I try on changing the download path to qbitorrent, > Could not read contents of /media Permission denied
And the option shuts.
I presumed it was a Permissions issue, but when I check Files > HDD > Properties, I can write/delete files to all items.
Anybody knows what to do to download files directly to the HDD?
Thanks.

---

### Post by TheFu on 2021-05-21
This is a very common issue for people who don't understand Unix permissions.  
Learn them.
Also, external devices can have all sorts of file systems.  Which file system is used will determine the next steps. 
If you are mounting it through clicking on some GUI, then it is highly likely not to be a "real" mount.

So - let's gather some information.
What file system is used?
Connect and access the drive. Run **df -Th -x squashfs -x tmpfs -x devtmpfs** - post the results.  Hope for a native Linux file system. If it isn't, then the only way to set permissions is at mount time, through mount options.  OTOH, native Linux file systems let us use the full POSIX Unix permissions which means we have controls to allow lots of different userids to work together on the same files, directories, and once setup, can forget about this.

Of course, there is a short answer - but it completely throws security away and I will not do that. The required access for the specific accounts to access what they need, but no more, is the goal - always.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) is an overview of Unix/POSIX permissions. Takes about 15 minutes to work through. This needs to be hands-on, not just reading.  Then you'll need 30-45 minutes of trying stuff out with 3 terminals, 3 userids, 2 groups  - try every possible combination of permissions, groups on files and directories. Just do it until the "light bulb" moment happens. Then spend at least 5 more minutes testing to validate what you've learned.

After that, you can learn how to setup directories to allow groups of userids to work together. 
[https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp](https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp) has the steps. This method doesn't work for non-native Linux file systems.

---

### Post by Automat2 on 2021-05-21
Of course I don't 'understand' permissions, otherwise I wouldn't have this issue and wouldn't be asking for a solution for it. However, happy to learn.

Nevertheless, the output is:

> Filesystem     Type     Size  Used Avail Use% Mounted on 
/dev/sda6      ext4     451G   17G  411G   4% / 
/dev/sda1      vfat     511M  5.3M  506M   2% /boot/efi 
/dev/sdb1      fuseblk  1.9T  509G  1.4T  28% /media/jordi/680D790B3A348B65 



It is a native Ubuntu.

---

### Post by TheFu on 2021-05-21
Nobody knows Unix permissions when they start. It will take concentration and effort, but there is an elegance that becomes clear around 20-45 minutes into this effort.

```
/dev/sdb1 **fuseblk** 1.9T 509G 1.4T 28% /media/jordi/**680D790B3A348B65** 
```
says it is NOT a native Linux file system. I'd guess it is NTFS? Perhaps?  Can you confirm?

Are you willing to change to ext4 or xfs or some other native Linux file system?  That would require wiping it and losing any data on it already. Just backup the data, we will be able to put it back later, after changing to ext4.  This is not mandatory, but if you intend to use this storage as the OS backup storage too, the backup tools become much more restricted if you don't.
Of course, you can buy a new HDD, format it as ext4, install it and we can make it the new media disk, but I suspect that isn't exactly ideal. Nobody wants to spend $50 for something they don't want.

If you are going to stay with NTFS, then only mount options will control the user, group and permissions.  Wanting to have multiple different programs to have write access will be difficult without completely removing all real permissions. Someone else will need to help with that. Sorry.

---

### Post by TheFu on 2021-05-21
BTW, is /dev/sdb a 2TB or smaller HDD?  If it is larger, you'll want to change to a GPT partition table anyways to gain access to all the storage it has.

---

