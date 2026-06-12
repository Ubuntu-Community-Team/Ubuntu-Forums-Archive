---
title: "Re: Problems employing find, mtime, exec and cp to copy files newer than a certain da"
date: 2012-11-23
forum: General Help
---

### Post by RoosterHam on 2012-11-23
So an old thread, but I have found myself in a similar situation this week.

I needed to copy only files newer than 6 months ago, but preserve them within the original directory structure, and do all such via scp/ssh.

One convenient feature is that the directories would contain the same time stamp as the oldest file or directory within that directory (a new subdirectory created for each day at the beginning of that day).

Here's what worked for me:

1. created a file for 'find' to refer to using '-newer' option ( i realised later that i could have just pointed to a file in a directory from 6 months prior )
2. 'touch'ed the "reference.file" so its time stamp was 6 months ago
3. ran >> find /some/dir/local -t d -newer /where/is/reference.file -print0 | xargs -I{} -0 scp -r {} [EMAIL="account@remote.host"]account@remote.host[/EMAIL]:/some/dir/

Could I do this any better?

---

### Post by wildmanne39 on 2012-11-23
Moved to own thread!

---

### Post by erind on 2012-11-23
> **RoosterHam said:**
> So an old thread, but I have found myself in a similar situation this week.

I needed to copy only files newer than 6 months ago, but preserve them within the original directory structure, and do all such via scp/ssh.

One convenient feature is that the directories would contain the same time stamp as the oldest file or directory within that directory (a new subdirectory created for each day at the beginning of that day).

Here's what worked for me:

1. created a file for 'find' to refer to using '-newer' option ( i realised later that i could have just pointed to a file in a directory from 6 months prior )
2. 'touch'ed the "reference.file" so its time stamp was 6 months ago
3. ran >> find /some/dir/local -t d -newer /where/is/reference.file -print0 | xargs -I{} -0 scp -r {} [EMAIL="account@remote.host"]account@remote.host[/EMAIL]:/some/dir/

Could I do this any better?

I'd use **rsync** over **scp**, as it has more useful options, it can copy over ssh and offers a cleaner way to read from std input (*--files-from* option) :

```
cd /some/dir/local

find** .** -newer /where/is/reference.file -print0 | rsync -av0 --files-from=- **.** -e ssh account@remote.host:/destination/dir/
```If you want to plug the full path into find's command line use the code below:

```
find /some/dir/local -newer /where/is/reference.file -print0 | rsync -av0 --files-from=- / -e ssh [EMAIL="account@remote.host"]account@remote.host[/EMAIL]:/destination/dir/

```Be aware though that in this way the copied output will be buried few depths below the destination directory i.e. */full/path/dest/dir/full/path/some/local/dir* instead of */full/path/dest/dir/local_dir* of the first code. 
Anyway in both cases the relative directory structure is preserved, but I'd really go with the first code.

---

### Post by RoosterHam on 2012-11-26
Great tip erind. Unfortunately, in the environment that this situation has arisen rsync is not available. all administration is done via ssh/scp. Samba and NFS payloads are also tightly controlled.

I also prefer rsync in my own network, especially in any situation that I want to preserve directory structure. I just use scp for single file or non recursive directory content copying.

---

### Post by erind on 2012-11-26
You can try *tar *or *cpio *over *ssh*:

```
cd /some/dir/local

find . -newer reference.file -print0 | tar --null --files-from=- -cvf - | ssh -C user@remote.host tar -C /destination/dir/ -xf -
```With cpio:

```
cd /some/dir/local

find . -newer reference.file -print0 | cpio -o -0Hnewc | ssh -C user@remote.host "cd /destination/dir ; cpio -i0dvum"
```In both cases permissions and timestamps are preserved.

Now as far as *find+scp* is concerned, there's really not much choice other than:

[LIST]
[*] create locally a tar file from find's output, (  *find . -print0 | tar --null --files-from=- -cvf dirball.tar*  ),
[*] cp the tar file over,
[*] ssh and untar on the other side, which is basically what the first code is doing.
[/LIST]

---

