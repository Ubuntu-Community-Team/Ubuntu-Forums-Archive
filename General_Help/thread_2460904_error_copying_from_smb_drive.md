---
title: "error copying from smb drive"
date: 2021-04-21
forum: General Help
---

### Post by bertrandb on 2021-04-21
Hello,

I'm using Ubuntu 20.04. I can mount an external drive (from the company) successfully from the file manager using the file manager application (with credentials), with smb:// scheme. I can then browse the content of the network drive.


but when I try to copy (cp) from that drive to the local drive, I get some File Not Found error. The file exists and is correct, because, if instead of cp I use 'file' i can get the description of the file.
Also, this error seems to happen only with large file (my tests are on 80MB files), but smaller pass successfully.


we want to run local programs that use data from the network drive directly, is it a good way to setup (using a smb drive, mounted from Nautilus), or is there any other better way? 


These programs we want to run raise a file reading error as well. actually, a simple open/read python program reproduces it. In detail, this python script will start successfully read some lines (actually almost all lines), and then the exception occurs.


If I copy the file from a windows station, I can get it and read it successfully.


please help me to identify the issue.

---

### Post by ActionParsnip on 2021-04-21
What is the cp command you are issuing as well as an the pwd?

---

### Post by bertrandb on 2021-04-21
this is the command, sorry i have to hide some path.
but basically it is run from home, and the cp command uses the path of gvfs (i have tried to use symbolic link as well, just in case.. no sucess)

```
user@station01:~$ cp /run/user/1004/gvfs/smb-share\:server\=server.net\,share\=shr\$/Path/to/My\ file/test.xml target.xml
cp: error reading '/run/user/1004/gvfs/smb-share\:server\=server.net\,share\=shr\$/Path/to/My\ file/test.xml': No such file or directory
```

---

### Post by SeijiSensei on 2021-04-21
Mount the share into the file system with an entry in /etc/fstab.

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by Morbius1 on 2021-04-21
> user@station01:~$ cp /run/user/1004/gvfs/smb-share\:server\=server.net\,share\=shr\$/Path/to/My\ file/test.xml target.xml
cp: error reading '/run/user/1004/gvfs/smb-share\:server\=server.net\,share\=shr\$/Path/to/My\ file/test.xml': No such file or directory
Are you sure that is the correct gvfs mount point?

If you run the following:
```
ls -al /run/user/1004/gvfs
```
Isn't it something more like: /run/user/1004/gvfs/smb-share:server=server.net,share=shr.....

---

### Post by bertrandb on 2021-04-21
yes, it's a weird path, but this is it. i can list the content with [COLOR=#000000]/run/user/1004/gvfs/smb-share:server=server.net,share=shr.... [/COLOR] and also copy small files from it.

---

### Post by bertrandb on 2021-04-21
[COLOR=#000000]"Mount the share into the file system with an entry in /etc/fstab."
[/COLOR]
thanks, right, doing without using nautilus sharing functionality, i can mount the drive and read file successfully, thanks. may be I will go this way.

I liked the nautilus solution as each user can just mount their drive on their own user folder, with their own credential and with no sudo.
(mulitple users may access that drive, each one may have different auth level).

---

