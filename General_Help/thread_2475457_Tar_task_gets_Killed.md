---
title: "Tar task gets Killed"
date: 2022-05-27
forum: General Help
---

### Post by green-eyed on 2022-05-27
[COLOR=#000000][FONT=Menlo]Im trying to tar and compress a folder for backup. It one on many but they get big (like 12TB) and my ram in around 8GB in a VM but in Ubuntu 20.04 and 22.04 (both clean installs) I try to tar them and compress (with 7zip) and if gets killed. I understand the problem is most likely related to swap but I don't nor will have 12TB of swap. How can I fix this? I cant be the first person to tar and compress more data than swap.

Command
```
tar -cvf - "/media/pool1/Media/Pictures/" | 7z a -mx9 -si /mnt/backup/$(date '+%Y-%m-%d')_Pictures.tar.7z
```[/FONT][/COLOR]

End of output error
```

[COLOR=#000000][FONT=Menlo]/media/pool1/Media/Pictures/Family/2014-01-05/047.JPG[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/media/pool1/Media/Pictures/Family/2014-01-05/049.JPG[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/media/pool1/Media/Pictures/Family/2014-01-05/023.JPG                                                                                                       1003M + [Content]/media/pool1/Media/Pictures/Family/2014-01-05/058.JPG[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Killed[/FONT][/COLOR]

```

---

### Post by TheFu on 2022-05-27
**Don't use tar to backup anything over 250MB.**  Use a better backup tool. There are 20+ of those.  _Tar is a waste of your time._

---

### Post by Impavidus on 2022-05-28
tar is designed for dealing with tape archives. That's where the name comes from. It's certainly capable of creating a 120MB archive on a computer with just 32kB of memory. It was created in 1979, after all. So if you're creating a backup of your pictures on a 20TB tape drive, feel free to use tar, but on a hard drive it may be less suited.

I suspect that your crash may be caused by the compression tool, not by tar itself. tar processes the data in 512 byte blocks, but the compression tool uses larger chunks. You may be able to tune this with command line options. But why use compression at all? It slows the process down and jpeg files are compressed already, so compression won't save you anything.

---

### Post by TheFu on 2022-05-28
To add onto Impavidus' post, GNU tar has compression built-in.  There are bzip and gzip in the tool today.
```
$ tar czvf /mnt/backup/$(date "+%F")_Pictures.tgz  "/media/pool1/Media/Pictures/"
```
Will let the tar code handle compression, but images and most videos are already compressed. Perhaps 1-3% more compression will be possible.

'j' is the bzip2 compression option.
'z' is the gunzip compression option.
Other options for gnutar are in the manpage. There is a way to have tar use a specific compression/decompression tool (with caveats), if one of the 8 other choices doesn't fit.

But I still think tar is a waste of your time for backups.
When backing up to tape, all modern tape drives have hardware compression built-in. They have for 20+ yrs.

---

