---
title: "synchronizing"
date: 2007-07-01
forum: General Help
---

### Post by jocheem67 on 2007-07-01
Is there such a tool?

I'd like to put my music ( home folder ) onto a vfat backup disk, preferably using a synchronize tool. Can do it by hand ofcourse but maybe there's an automated solution??? Other way round would be nice too....

---

### Post by PaulFr on 2007-07-01
Have you looked at **grsync** package (project home page is at **[http://www.opbyte.it/grsync](http://www.opbyte.it/grsync)**) ?

---

### Post by soxs on 2007-07-01
Well.. you could simply use:
cp -Rvf /input/dir /target

I am doing backups myself this way. (Note: option -v is not necessary)

No necessite of using a sync tool at all.

---

### Post by jocheem67 on 2007-07-01
Okay thanks, gonna try the command first, and maybe then the tool.


Cheers!

---

### Post by PaulFr on 2007-07-01
FYI, some info for you:
1. The difference between **rsync** and **cp** is this: rsync actually compares the source and destination directories to find what is different and only copies the difference. cp blindly copies all the files over without any comparison. This obviously makes a big difference when you have oodles and oodles of files to sync :-)
2. **grsync** is merely a GUI wrapper around the rsync command (see **[http://rsync.samba.org](http://rsync.samba.org)** for more details about the rsync command).
3. You can convert any command to run automatically by using **cron** and the **crontab** command.
Hope this helps.

---

### Post by lingnoi on 2007-07-02
I want to rsync my user directory on my laptop with the user directory on my Desktop via ssh.

Can anyone help me figure out what command I need to type? Thanks :)

---

### Post by jocheem67 on 2007-07-02
Thanks again, installed the grsync tool. 
Well actually there may be a problem here, as my usb-disk is ntfs-formatted. I'm not sure yet if this tool can cope with non linux filesystems....we'll see about that.

cheers...

---

### Post by PaulFr on 2007-07-02
In response to lingnoi,

From the man page for rsync, in the examples section, comes the following:```
rsync -az -e ssh --delete <local_directory> <remote-host>:"<remote-directory>"
``` where -e indicates the remote shell command.

If you need to login with a different user name on the destination machine, then ```
rsync -az -e "ssh -l <ssh-user>" --delete <local_directory> <remote-host>:"<remote-directory>"
```

A useful resource for rsync usage is **[http://sial.org/howto/rsync/](http://sial.org/howto/rsync/)**

---

### Post by jocheem67 on 2007-07-02
Synchronizing between a ntfs and an ext3 disk is actually working okay....

---

### Post by Brian96 on 2007-07-25
In the grsync user interface, what does the "Delete on destination" option mean? Does that mean that a file is missing from the source folder it will delete it on the destination folder?

EDIT; Never mind. I just discovered that hovering over each option provides a pop-up description.

---

