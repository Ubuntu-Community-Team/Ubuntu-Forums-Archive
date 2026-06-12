---
title: "Problem with backing up using tar"
date: 2007-05-06
forum: General Help
---

### Post by herbster on 2007-05-06
I am using Simple Backup to back up to .tar, but my last few full backups have been exceeding 4.5gb and now I'm at 5.1gb, and I have consistently been burning to DVD-RW, so this poses a problem for me.

Is there a way to make a .tar spread into 4.5gb volumes? So it would be like 4.5gb, then 700mb split.

Or how else can I do it so that I can spread it across? Or is this not a good idea?

Someone please clarify this for me I'm kind of scared at not having my backup process figured out hehe :)

---

### Post by mlind on 2007-05-06
I guess you can use **split** for splitting the tar archive in pieces and use cat to construct the full archive again.
I've only used cpio for backup purposes and haven't had need to split the backup across volumes.

If you do regulary backups, you may want to do incremental backups to save space, preferably with a tool that automates this stuff.
Something like backuppc or bacula maybe.

---

### Post by Slim Odds on 2007-05-06
How about using some compression?

Like gz or bz?

---

### Post by herbster on 2007-05-06
I am using Simple Backup, it outputs a files.tgz and it does incremental backups (I have it set to do them).

mlind,

How do you use cpio, what is the command you use to make your backups with it?

Oh and I am going to try split, so if I am to restore I would just use cat to restore the archives off the DVDs onto my drive? I'm unclear as to exactly how I could restore let's say files.tgz spread across 2 DVDs??

---

### Post by mlind on 2007-05-06
I reckon google gives better answers about cpio backups than I. Here's couple results I found
[http://www.debian.org/doc/manuals/reference/ch-tips.en.html#s8.3.5](http://www.debian.org/doc/manuals/reference/ch-tips.en.html#s8.3.5)
[http://osr507doc.sco.com/en/OSUserG/_Creating_a_cpio_backup.html](http://osr507doc.sco.com/en/OSUserG/_Creating_a_cpio_backup.html)
[http://bradthemad.org/tech/notes/cpio_directory.php](http://bradthemad.org/tech/notes/cpio_directory.php)

cpio is considered better than tar if you're doing backups from your entire filesystem as it can handle "special" files better. If you just backup your home directory, tar is okay.

Here's how archive a directory and split the archive (gzipped and splitted as 10MB chunks)
```

tar czvf - /path/to/directory | split -b 10m - backup.tar.gz

```

To extract the full archive
```

cat backup.tar.gz* | tar xzvf -

```

Here's a nice article about doing incremental backups with tar
[http://chxo.com/be2/tar_backup_to_ntfs.html](http://chxo.com/be2/tar_backup_to_ntfs.html)


/edit
as you already have the backup archive, just split it
```

split -d -b 10m mybackup.tar.gz part.tar.gz

```

To restore the archive and extract it
```

cat foo.tar.gz* | tar xzvf -

```

---

### Post by Slim Odds on 2007-05-06
> **herbster said:**
> I am using Simple Backup, it outputs a files.tgz and it does incremental backups (I have it set to do them).


You might want to check if it has the option to use bzip2. You'll get much better compression.

---

