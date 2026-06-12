---
title: "Permissions wine and hda1"
date: 2008-01-13
forum: General Help
---

### Post by Snader on 2008-01-13
Dear users,

There is a program on my windows partition (hda1) which I run through Wine. Is Wine capable of modifying (or corrupting) the filesystem of hda1? This is worrying me.

If so, then I guess I want to change the permissions for hda1 to read-only. I've already tried to do that by replacing the options with "defaults,umask=007,gid=46,ro", but without succes. Here is the relevent part of my original fstab:
```
# /dev/hda1
UUID=5A046017045FF48B /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
```

Thanks in advance,

Sander

---

### Post by Nexusx6 on 2008-01-13
I seriously doubt it. Wine is just a translation layer, it just translates the program's api calls and whatnot normally meant for Windows into ones that Linux can understand and compute. It doesn't go about modifying much of anything; even if you're running a program off your windows partition, any registry keys that the program tries to install get installed to Wine's reg. 

Honestly chief, you're quite safe ;)

---

### Post by Snader on 2008-01-13
Sounds good and thanks for you quick response. :)

---

### Post by Nexusx6 on 2008-01-13
Not a problem ^^ I just caught your edit to OP - I'm not awesome with fstab by any means, but in the event you do ever want to make your drive Read Only for some reason, I think the proper umask is 222 for read+execute (no write) across Owner|Group|Other.

---

### Post by erpo on 2008-01-13
Know the difference between files and filesystems. No, wine cannot damage the filesystem unless it's run as a user who can write to the block device containing the filesystem and something goes terribly wrong. If your system is set up in the canonical way (with a lower case c), then you're safe in this case.

Wine can write to files on your windows partition if your user account can write to files on your windows partition. There is a small chance of messing up an ini file or something similar if you run programs directly from your windows partition with wine. Unfortunately, there is a larger chance that setting the windows filesystem read-only will result in problems when you try to run an application with wine. Some applications expect to be able to write to files. :)

You might want to try installing your windows applications using wine. Then they will be in /home/you/.wine/drive_c/... and you won't have to worry about problems related to running windows programs from your windows partition.

---

### Post by Snader on 2008-01-13
Excellent, that worked. :) While I got your attention,  I've got one last question. What is the difference (in short) between read and execute?

@erpo: Thanks for your detailed explanation. I'll soon figure out how to install programs with wine, good advice. In the meantime, I'll keep the drive read-only. As Wine is only needed for a simple dictionary program. ;)

Thanks again. :)

---

### Post by Nexusx6 on 2008-01-13
Execute means two things:

When you set a file with execute permissions in Linux, this typically only effects script files (usually ending in a .sh extention). You can think of them as the windows .exe in a sense. The diffrence of R and X here is that while simply reading a script file does nothing except let you see what the script does (you can open them in a text editor), X will let that script run and do its job.

In directory's its different. If a directory as R but no X, you can cd the directory, but you can't actually see what's inside of it, as in, using "ls" to list the contents won't show anything. Its a situation most people will never have to use, but it can some times be useful for SysAdmin's as an extra security bonus who are managing files for a company with many group's and projects.

I'll keep an eye on this thread, but if you need to you can also PM anytime ^^

---

