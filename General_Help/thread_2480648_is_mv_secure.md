---
title: "is mv secure?"
date: 2022-11-04
forum: General Help
---

### Post by bitrat2 on 2022-11-04
Hi,

I'm aware that moving a file in ext4, or unix fs generally, shuffles a few inodes about, but doesn't copy any data.  

To what extent can this be relied on?  Say I have a large (~100G) file and move it to a different folder on the same drive, can I assume it will not copy data from the file and leave it on disk?  As there is no smv (secure move) in the secure_deletion toolkit, I'm assuming this is true, but I'd like verification that:

[FONT=courier new]**mv dir1/data dir2** <=> **cp dir1/data dir2 && srm **[/FONT]**[FONT=courier new]dir1/data[/FONT]**


... ignoring for the moment the limitations and caveats mentioned in [FONT=courier new]man srm[/FONT].

Cheers,
bitrat

---

### Post by TheFu on 2022-11-04
'mv' only changes the parent inode within the same file system and adds the child filename to the parent "directory" file.  "Folders" have nothing to do with it.  It is about the file system.

Yes, directories are just files on Unix file systems.  Most things are files, as you know, except a running process. Everything else is a file. ;)

In the 1990s, attempting to 'mv' anything between different file systems would fail, so lots of people had a script to try the mv, check for the $? error, then perform a 'cp' + 'rm -i' ... which is logically what happens when a mv across file systems is requested.

I haven't a clue about 'srm'. Never touched it.

---

### Post by bitrat2 on 2022-11-05
Thanks.  :)

> **TheFu said:**
> "Folders" have nothing to do with it.  It is about the file system.
In my lingo, "folder" is another word for "directory".  Maybe I've spent to much time on other OS's.

---

### Post by TheFu on 2022-11-05
> **bitrat2 said:**
> In my lingo, "folder" is another word for "directory".  Maybe I've spent to much time on other OS's.

"File system" is what is important.

---

### Post by mIk3_08 on 2022-11-06
> **bitrat2 said:**
> Hi,

I'm aware that moving a file in ext4, or unix fs generally, shuffles a few inodes about, but doesn't copy any data.  

To what extent can this be relied on?  Say I have a large (~100G) file and move it to a different folder on the same drive, can I assume it will not copy data from the file and leave it on disk?  As there is no smv (secure move) in the secure_deletion toolkit, I'm assuming this is true, but I'd like verification that:

[FONT=courier new]**mv dir1/data dir2** <=> **cp dir1/data dir2 && srm **[/FONT]**[FONT=courier new]dir1/data[/FONT]**


... ignoring for the moment the limitations and caveats mentioned in [FONT=courier new]man srm[/FONT].

Cheers,
bitrat
I better copy first than moving specially when it come to a large file size. Moving can corrupt a large file when it is disrupted. Regards and cheers

---

### Post by TheFu on 2022-11-06
> **mIk3_08 said:**
> I better copy first than moving specially when it come to a large file size. Moving can corrupt a large file when it is disrupted. Regards and cheers

Only when crossing file systems are bytes actually moved. Sorry if that wasn't made clear.
On the same file system, none of the bits actually change, so using "mv" is 10000x safer, and instantaneous.

---

### Post by mIk3_08 on 2022-11-07
> **TheFu said:**
> Only when crossing file systems are bytes actually moved. Sorry if that wasn't made clear.
On the same file system, none of the bits actually change, so using "mv" is 10000x safer, and instantaneous.
Thanks TheFu for the clarification. Just be sure that it won't be interrupted when moving large files. Else, I'll consider it as corrupted when it is interrupted. Like power cut or etc. Regards and cheers.

---

### Post by TheFu on 2022-11-07
> **mIk3_08 said:**
> Thanks TheFu for the clarification. Just be sure that it won't be interrupted when moving large files. Else, I'll consider it as corrupted when it is interrupted. Like power cut or etc. Regards and cheers.

Moving within the same file system is basically instantaneous. I've never had power flicker at the exact instance.

Moving across file systems is a source copy to a destination file system, the copy finishes, and delete source of the source happens only if the copy didn't create an error.  **Any corruption that might happen is from something else.**  I have huge file moves fail all the time, today, yesterday, this week, last week, last month, last year ...  when the target storage ran out of space.  The source file wasn't deleted and was still there after the failure 100% fine.  I did have to manually remove the incomplete file on the target file system.  this is why using rsync is a better way to copy multiple files or huge files between file systems, then manually remove them from the source.  rsync will pick up where the copy process failed if run again.  But for a single file, I'll use 'mv' almost always.

My systems are either on battery backup (UPS) or the laptops have batteries that will last between 5 minutes and 12 hrs, certainly long enough to deal with a power flicker for almost any file copy I'm doing.  I just kicked off a delayed mirror rsync for about 20TB of media files. This wasn't the first time, but I hadn't dont this in a few days, so any changed files or deleted files that need to be handled in the backup storage got to be handled.  I put a 'time' command before the rsync script .... here's the output from that:

```
real    0m28.348s
user    0m0.944s
sys     0m1.490s
```
So, it took about 30 seconds to check all the files, decide which had changed, which had not changed, which were new and which needed to be deleted in the backup mirror storage, then perform the necessary actions.  The source and target areas are on physically separate storage devices, since backs on the same physical device aren't very useful if it fails.  ;)

But back to the OPs question.  When the file is moved across file system, the source file doesn't get shredded, so the data that was there doesn't get overwritten in a secure way. Depending on the drive usage, it my not be overwritten ever or it might get partially overwritten 3 seconds later. There's no way to know.  If the OP doesn't care about being secure from govt cyber sleuths, then a case could be made to either fill empty storage with zeros or random patterns every day.  This wouldn't be good for SSDs, but for spinning disks, exercising each storage location is one of the best ways to keep disks healthy as long as possible and to get early warnings when a HDD is going to fail.  For ext4, there's a tool that will smartly fill empty storage on an unmounted storage device with a pattern.  I just found it a few days ago, but don't remember the name. It isn't part of a default install. There are claims that it is more efficient than using dd or cp with an ideal blocksize to optimize write performance.  Found it: [https://manpages.ubuntu.com/manpages/bionic/man8/zerofree.8.html](https://manpages.ubuntu.com/manpages/bionic/man8/zerofree.8.html)  The big hassle with using that tool is that the target device for getting zeros needs to be either un-mounted or mounted read-only.  BTW, this tool is useful for sparse virtual machine storage files too.

---

