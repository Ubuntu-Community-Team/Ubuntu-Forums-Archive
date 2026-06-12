---
title: "rdiff-backup with &quot;--override-chars-to-quote&quot;"
date: 2007-12-28
forum: General Help
---

### Post by shimrah on 2007-12-28
Hi there,

I'm hoping that someone familiar with rdiff-backup can help me here. This app seems ideal for backing up my files to an external drive that is located on another machine on our home network. 

I'm backing up from an NTFS drive to a FAT32.

I'm able to mount the drive and copy things to it, but when I try to use rdiff-backup to copy files over to it, letters are escaped out with garbled code, presumably because the app is trying to avoid duplicate filenames in a file system -- FAT32 -- that is not case sensitive. However, since I'm backing up from NTFS, this isn't an issue and I would rather it not happen. 

From the MAN, it appears that --override-chars-to-quote should solve the dilemma. But when I do this:

```
sudo rdiff-backup --override-chars-to-quote /media/hda2/my_documents /mnt/myBook/shim_backup/my_documents

```

I get this:

```
Fatal Error: Switches missing or wrong number of arguments
See the rdiff-backup manual page for more information.

```

Any thoughts?

Thanks,
Shimrah

---

### Post by number nine on 2008-04-26
I found the same issue, and I managed to find a solution online. The man page doesn't mention that you need to provide the characters to override. What you are probably looking for is:

```
--override-chars-to-quote ''
```

However using this on my backup (to a vfat partition) gave me:

```
IOError: invalid mode: wb
```

I noticed that the default "chars to quote" was: "A-Z-"*/:<>?\\|;" so I just removed the A-Z and made it:

```
--override-chars-to-quote '-"*/:<>?\\|;'
```

And this seems to work. It's still working properly on files with odd characters in their names but not converting uppercase letters to escape codes.

By the way, I've found very few people on this forum using rdiff-backup, so if you have any issues with it I've found it best to look at the rdiff-backup-users mailing list archives: [http://www.mail-archive.com/rdiff-backup-users@nongnu.org/]("http://www.mail-archive.com/rdiff-backup-users@nongnu.org/")

Hope this helps!

---

