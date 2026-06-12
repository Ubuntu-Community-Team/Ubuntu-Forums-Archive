---
title: "Symlink question..."
date: 2015-09-16
forum: General Help
---

### Post by KayeNg on 2015-09-16
Hi guys.  Stupid question that I probably already know the answer to, but I just need confirmation.

Several files in the NTFS partition have a total size of 5GB.  If I were to create a symlink to it in the ext4 partition, I assume it would only take a very negligible amount of space from the ext4 partition, right? Since they are only links?  But how much space and where do I see it?

Thanks

---

### Post by howefield on 2015-09-16
> **KayeNg said:**
> Several files in the NTFS partition have a total size of 5GB.  If I were to create a symlink to it in the ext4 partition, I assume it would only take a very negligible amount of space from the ext4 partition, right? Since they are only links?  But how much space and where do I see it?

Yes, negligible amount of space and you could

```
ls -l ~/
```

to see how much, eg

```
hugh@wily-laptop:~$ ls -l ~/
total 12
drwxr-xr-x 2 hugh hugh 4096 Sep  3 20:09 Desktop
lrwxrwxrwx 1 hugh hugh   16 Sep  3 20:13 Documents -> /Data/Documents/
lrwxrwxrwx 1 hugh hugh   16 Sep  3 20:13 Downloads -> /Data/Downloads/
lrwxrwxrwx 1 hugh hugh   12 Sep  3 20:13 Music -> /Data/Music/
lrwxrwxrwx 1 hugh hugh   15 Sep  3 20:13 Pictures -> /Data/Pictures/
drwxr-xr-x 2 hugh hugh 4096 Sep  3 20:09 Public
drwxr-xr-x 2 hugh hugh 4096 Sep  3 20:09 Templates
lrwxrwxrwx 1 hugh hugh   13 Sep  3 20:13 Videos -> /Data/Videos/
hugh@wily-laptop:~$ 
```

---

