---
title: "Handling thousands of small files in FS with largefile4?"
date: 2007-06-25
forum: General Help
---

### Post by kung fu buntu on 2007-06-25
My partition for storing data was formated for ext3 using **largefile4** flag.
This partition will mostly be used to store very large files (> 200MB). However, it will also be used to save hundreds of interesting news from the web (I currently have over 5000 small files).
How do I cope with this?

I suspect the best way is to put them in a tarball. The problem is that I don't know if that is possible in this case, neither how to do it in an efficient way.
(Note: I'm aware of tar -czf, tar -xzf... but that's about it)

I mean, how can I add, remove, update files in an easy way in a tarball?
Is it efficent in terms of speed (I don't care about compression in this case)? Does tar have to scan all the tarball to find/update/delete a file (in this case it's a html file accompanied by a directory with dozens of other files inside).

Thanks

---

### Post by yabbadabbadont on 2007-06-26
You would be much better off shrinking that partition a little and creating a new one using the "news" option (lots of small files).

---

### Post by kung fu buntu on 2007-06-26
Not really an option...

---

### Post by yabbadabbadont on 2007-06-26
Then use dd to create one large file that is big enough to handle all of your small files.  (plus some extra padding for future growth)  Then attach it to a loop device and create a filesystem on it using the news option.  You can then mount this file as a filesystem and read/write to it to your heart's content.  As a bonus, your largefile4 filesystem won't become fragmented.

If you need detailed instructions, I can provide them.

---

### Post by kung fu buntu on 2007-06-27
I'm stuck...

dd if=/dev/zero of=news.HDD bs=4k count=1M **(create 4GB file)**
/sbin/mkfs.ext2 -m 0 -O dir_index,filetype,has_journal,^journal_dev,^resize_inode,^sparse_super -T news -v news.HDD **(make a filesystem)**

sudo mount news.HDD /mnt/hdd -o loop,umask=007
```
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
If I remove the umask flag it works... :(
dmesg:
```
EXT3-fs: Unrecognized mount option "umask=007" or missing value
```


BTW you have said "(plus some extra padding for future growth) ", how can I resize this image?

---

### Post by kung fu buntu on 2007-06-27
Ok, I think I solved **this** problem. It seems ext3 has no option for umask #-o
```
sudo mount news.HDD /mnt/hdd -o loop,defaults,user
```

But now I would like to have this filesystem mounted at startup, or when I login into my X session.
Editing fstab is a no-no because it does not support files as the first entry. So, what is the proper place to add a mount instruction? As well as the matching umount... :-k

Thanks

---

