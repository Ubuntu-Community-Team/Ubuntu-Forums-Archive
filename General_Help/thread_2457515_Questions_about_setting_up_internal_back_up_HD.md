---
title: "Questions about setting up internal back up HD"
date: 2021-02-03
forum: General Help
---

### Post by jmichaels29 on 2021-02-03
Question:  What is the .gpg file that Backup app saves as files - are these encrypted files or something?  Any way to tell it just to backup the files as they are instead of making them .gpg ?

---

### Post by TheFu on 2021-02-04
> **jmichaels29 said:**
> Question:  What is the .gpg file that Backup app saves as files - are these encrypted files or something?  Any way to tell it just to backup the files as they are instead of making them .gpg ?

Sure. Use a different backup tool. There are 50 of them, at least.  Don't feel like you have to use the built-in tool.  I think the default tool is Deja Dup, which is based on duplicity.  The strongest aspect for it is that it encrypts the backups, stores all file permissions/ACLs, owner, group, metadata and chunks them up into easy to manage sizes so that cloudy storage can be used.  Ever noticed that the backup chunks are all the same size?  This target file system doesn't matter at all.

I like **rdiff-backup** [https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006) , but there are lots of solutions.  If you are backing up your HOME directory and not everything, then there are lots of tool options. Most will require the target storage have a Linux file system.  NTFS and all the FAT file systems  (exfat, fat32, fat-whatever) cannot be used.
Some other solutions which I know work:
[LIST]
[*]back-in-time [https://www.howtogeek.com/110138/how-to-back-up-your-linux-system-with-back-in-time/](https://www.howtogeek.com/110138/how-to-back-up-your-linux-system-with-back-in-time/)
[*]rsnapshot: rsync + hardlinks for versioned backups (requires Linux file system like ext4)
[*][LIST]
[*][*][https://popey.com/blog/2020/12/straightforward-linux-backups-with-rsnapshot/](https://popey.com/blog/2020/12/straightforward-linux-backups-with-rsnapshot/)
[*][*][https://www.cyberciti.biz/faq/linux-unix-apple-osx-bsd-rsync-copy-hard-links/](https://www.cyberciti.biz/faq/linux-unix-apple-osx-bsd-rsync-copy-hard-links/)
[*][/LIST]
[/LIST]

My 80+ yr old mother used Back-In-Time for a few years without problems.  All these tools are in the Ubuntu repos, so just *sudo apt install* them.

---

