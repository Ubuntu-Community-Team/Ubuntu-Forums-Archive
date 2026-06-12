---
title: "Lost data ?"
date: 2007-07-20
forum: General Help
---

### Post by jonathonblake on 2007-07-20
I've been deleting duplicate files on my system.

Roughly 40 GB of data that I did not delete is now producing messages such as the following:
Couldn't display "/home/jonathon/My Documents/my CDs/e-Sword/1corinthianschart1.jpg".

Size is "unknown", File Type is "unknown". Date modified is "unknown". Permissions are "unknown".
doing "ls -al" at the command line indicates that the file directories are drw-rw-rw-.
Trying to cd into the directory results in a "permission denied" error.

"sudo cd"  gives me a "command not found" error. :(

Any suggestions on what to do to retrieve that data?

xan

jonathon

---

### Post by dougfractal on 2007-07-20
how did you delete your file graphically or commandline?
 ```
du -sh ~/ 
```   disk usage

What format is your filesytem (ext3,...)

have you rebooted?

---

### Post by jonathonblake on 2007-07-20
[QUOTE=dougfractal]How did you delete your file graphically or commandline?[/quote]

For the most part graphically.  I deleted some fonts, and one or two directories using "rm -R *".   As best as I can remember, I didn't do that in any of the affected directories ---they were done using the "Delete" option from the mouse.  I did not use the "Delete to Trash" or whatever that second option is.

>  ```
du -sh ~/ 
``` 

That command ends with the line **43905704   /home/jonathon/**
All of the affected directories list "permission denied".  

System Monitor claims 12.7 GB free.   
The system monitor claim is why I hope I can restore that data.

> What format is your filesytem (ext3,...)

Whatever the default Ubuntu filesystem is.  

> have you rebooted?
Since I did the deletions?  yes.
Since I found I couldn't access the files?  No.

xan

jonathon

---

### Post by bollix47 on 2007-07-20
If you want to use cd use the following:

```
sudo su
cd directoryname
```

type exit when you are finished to leave root

---

### Post by dougfractal on 2007-07-20
ls -l /home/jonathon/My\ Documents/my\ CDs/e-Sword/1corinthianschart1.jpg
is it a symlink?

sudo du -sh /home/jonathon

sudo chown -R jonathon:jonathon /home/jonathon/*

good luck
Doug

---

### Post by az on 2007-07-20
> **jonathonblake said:**
> I've been deleting duplicate files on my system.

Roughly 40 GB of data that I did not delete is now producing messages such as the following:
Couldn't display "/home/jonathon/My Documents/my CDs/e-Sword/1corinthianschart1.jpg".

Size is "unknown", File Type is "unknown". Date modified is "unknown". Permissions are "unknown".
doing "ls -al" at the command line indicates that the file directories are drw-rw-rw-.
Trying to cd into the directory results in a "permission denied" error.

"sudo cd"  gives me a "command not found" error. :(

Any suggestions on what to do to retrieve that data?

xan

jonathon

Perhaps you have a borked filesystem, or worse, a dying hard drive.  If you are getting weird behaviour from your drive, I would suggest you unmount it immediately and try to recover data non-invasively.

See here:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by dagnabit dang doohickey on 2007-07-21
Directories need execute permissions:
chmod +x directoryname

You may also want to consider removing the write permissions for others:
chmod o-w directoryname

To do this with one command:
chmod 775 directoryname

---

### Post by jonathonblake on 2007-07-21
[QUOTE=dougfractal]ls -l /home/jonathon/My\ Documents/my\ CDs/e-Sword/1corinthianschart1.jpg
is it a symlink?[/quote]

No.

> sudo chown -R jonathon:jonathon /home/jonathon/*

Thanks.  After running that half a dozen times, the files came back.  :)

xan

jonathon

---

