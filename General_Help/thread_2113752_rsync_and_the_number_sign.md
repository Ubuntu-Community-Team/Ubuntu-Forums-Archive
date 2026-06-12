---
title: "rsync and the number sign"
date: 2013-02-08
forum: General Help
---

### Post by QR72 on 2013-02-08
Hi forum,

using Ubuntu 12.10 and running rsync backup to a locally mounted FTP server (/mnt/ftpsrv).

Here the rsync command I am using in my script:
```
rsync -sr --size-only --temp-dir=/var/tmp/rsync --files-from=$LIST_SOURCE --exclude-from=$LIST_EXCLUDE --log-file=$LOG_FILE $SOURCE $TARGET
```The script is working well and backing up all files, except files that contain a number sign (#) in their name.

The errors I am getting are like this one:
```
2013/02/07 23:49:06 [4518] >f+++++++++ Private/Music/Tresor/Tresor.138 - Pacou - State Of Mind/Pacou - State Of Mind - 03 - Format #2.mp3
2013/02/07 23:49:11 [4518] rsync: open "/mnt/darknas/Private/Music/Tresor/Tresor.138 - Pacou - State Of Mind/Pacou - State Of Mind - 03 - Format #2.mp3": No such file or directory (2)
2013/02/07 23:49:11 [4518] rsync: copy "/var/tmp/rsync/.Pacou - State Of Mind - 03 - Format #2.mp3.JgYsbZ" -> "Private/Music/Tresor/Tresor.138 - Pacou - State Of Mind/Pacou - State Of Mind - 03 - Format #2.mp3": No such file or directory (2)

```Now, it is only a couple of files and I could easily rename them, but I would rather like to solve this.  :-)

The source and the target are not local, both are mounted. The source is mounted via SMB and the target via FTP.
I have checked the code pages and they seem to be alright as all special characters are correct on the target.

Any ideas and hints are welcome!

---

### Post by rnerwein on 2013-02-08
> **QR72 said:**
> Hi forum,

using Ubuntu 12.10 and running rsync backup to a locally mounted FTP server (/mnt/ftpsrv).

Here the rsync command I am using in my script:
```
rsync -sr --size-only --temp-dir=/var/tmp/rsync --files-from=$LIST_SOURCE --exclude-from=$LIST_EXCLUDE --log-file=$LOG_FILE $SOURCE $TARGET
```The script is working well and backing up all files, except files that contain a number sign (#) in their name.

The errors I am getting are like this one:
```
2013/02/07 23:49:06 [4518] >f+++++++++ Private/Music/Tresor/Tresor.138 - Pacou - State Of Mind/Pacou - State Of Mind - 03 - Format #2.mp3
2013/02/07 23:49:11 [4518] rsync: open "/mnt/darknas/Private/Music/Tresor/Tresor.138 - Pacou - State Of Mind/Pacou - State Of Mind - 03 - Format #2.mp3": No such file or directory (2)
2013/02/07 23:49:11 [4518] rsync: copy "/var/tmp/rsync/.Pacou - State Of Mind - 03 - Format #2.mp3.JgYsbZ" -> "Private/Music/Tresor/Tresor.138 - Pacou - State Of Mind/Pacou - State Of Mind - 03 - Format #2.mp3": No such file or directory (2)

```Now, it is only a couple of files and I could easily rename them, but I would rather like to solve this.  :-)

The source and the target are not local, both are mounted. The source is mounted via SMB and the target via FTP.
I have checked the code pages and they seem to be alright as all special characters are correct on the target.

Any ideas and hints are welcome!
hi
i guess your problem is the "#". it stays for a comment for the shell. you have to debase it whit "\#". 
you will see if you try: touch "#bla.blu"
and then: rm #bla.blu --> don't works - you get an error message. 
but: rm \#bla.blu --> works
hope this will help you
cheers

---

### Post by QR72 on 2013-02-08
Thanks, sound logic!

But how can I do this? Isn't that a "bug" within rsync? Or how can I interfere with the filenames that rsync is working with internaly?

Any workaround, other than renaming the files?

---

### Post by papibe on 2013-02-08
Hi QR72.

What are the filesystems underneath the network mounts? (source and destination)?

Regards.

---

### Post by QR72 on 2013-02-08
> **papibe said:**
> Hi QR72.

What are the filesystems underneath the network mounts? (source and destination)?

Regards.

Hi papibe,

the source is an APF share (Apple Time Capsule) and the destination is a Synology NAS, which is build on a Linux distribution.

Thanks.

---

### Post by papibe on 2013-02-08
Thanks.

I'm not able to replicate that problem using a remote connection over ext4.

I would do this tests to look for clues:
[LIST]
[*]Make a source file list that only contain the file with the problem.
[*]rsync from APF to local to check if it works.
[*]Idem, rsync from local to local.
[*]Idem, rsync from local to NAS.
[/LIST]
Let us know how it goes.
Regards.

---

### Post by QR72 on 2013-02-09
Great, thanks for checking that and the thumbs up.

It definitely helps to isolate the problem.

Will check that and get back (hopefully) with the solution for others that may experience a similar issue.

---

### Post by rnerwein on 2013-02-09
> **QR72 said:**
> Thanks, sound logic!

But how can I do this? Isn't that a "bug" within rsync? Or how can I interfere with the filenames that rsync is working with internaly?

Any workaround, other than renaming the files?
hi
no that's no bug it is unix/linux. where are the files come from (i bet windoz). but sorry at the moment i got no idea who to solve the problem.
or just a moment change the filenames (hope you ain't loose any).
i will look for a solution.
cheers

---

### Post by SeijiSensei on 2013-02-09
I looked through the extensive list of options for rsync on its man page and found this one:

-s, --protect-args          no space-splitting; wildcard chars only

I don't know if it will affect how files with a pound sign are treated, but you can give it a try.

The best approach is to avoid naming files with that character.  Embedded pound signs in filenames will always cause problems on *nix machines.

---

### Post by rnerwein on 2013-02-10
> **QR72 said:**
> Thanks, sound logic!

But how can I do this? Isn't that a "bug" within rsync? Or how can I interfere with the filenames that rsync is working with internaly?

Any workaround, other than renaming the files?
hi
with the following command you can get rid of the "#" (if it dosen't matter changing the filename).
rename 's/#/X/g' `find . -type f`
this will change all files in the current and subdirectories from e.g. #bla#blu# to XblaXbluX. it will change all # to X.
cheers

---

