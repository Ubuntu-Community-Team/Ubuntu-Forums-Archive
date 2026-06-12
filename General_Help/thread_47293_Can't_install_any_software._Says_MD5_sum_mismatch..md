---
title: "Can't install any software. Says MD5 sum mismatch."
date: 2005-07-08
forum: General Help
---

### Post by duffmckagan on 2005-07-08
I just can't install anything on my Hoary now.
i am really stuck up.
I am following the Ubuntu Unofficial guide.

apt-get gives an error saying that the software can't be installed due to a MD5 sum mismatch.

This is what i get when trying to install a software.

```

amit@Quantum:~$ sudo apt-get install gftp
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gftp-common gftp-gtk gftp-text
The following NEW packages will be installed:
  gftp gftp-common gftp-gtk gftp-text
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 118kB/515kB of archives.
After unpacking 3871kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com hoary/universe gftp-text 2.0.18-2 [118kB]
Fetched 118kB in 25s (4585B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gftp/gftp-text_2.0.18-2_i386.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

I tried 
**sudo dpkg --clear-avail** but no use

My sources.list file has the same repositories like those in the Unofficial ubuntu guide.

---

### Post by linuxfanatic1024 on 2005-07-08
I had that exact same problem when I started using Ubuntu. I fixed it by changing to another country's mirrors.

I replaced all instances of [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) with [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/)

I have no idea what causes those errors, but you can try other Ubuntu download mirrors.

Good luck!

--Dan

---

### Post by cobelloy on 2005-07-08
same here, apt-get was fine, now I can't get stuff. is it maybe a temporary repository issue?

---

### Post by duffmckagan on 2005-07-08
Well i really think so.

I did 

apt-get update

But no use of doing that yet.

I think it is something temporary.
But can't say until a Mod or the Admin says this.

Thank you.

---

### Post by GMachine_24 on 2005-07-08
I am having the same problems attempting to install help files for The Gimp. I changed the repository files based on gb.ubuntu etc. and just got other errors.

---

