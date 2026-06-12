---
title: "k3b won't bun anything: IO error"
date: 2005-07-04
forum: General Help
---

### Post by Román on 2005-07-04
Hi! I'm not sure if k3b is supported, but I've been using it for CD recording. I've also searched through the kubuntu forums but I didn't found anything.

One sad day, k3b just stopped working.

It starts the burnong process and it's only output is 

 ```

IO Error
Removing buffer files

``` 

The Debugging output is:

 ```

Devices
-----------------------
CREATIVE CD-RW RW1210E LCS6 (/dev/hdc, ) at /media/cdrom1 [CD-R; CD-RW; CD-ROM] [Error] [SAO; TAO; RAW; RAW/R96P; RAW/R96R]
ATAPI-CD ROM-DRIVE-56MAX 56AI (/dev/hdb, ) at /media/cdrom0 [CD-ROM] [Error] [None]

System
-----------------------
K3b Version: 0.11.23
KDE Version: 3.4.0
QT Version:  3.3.3
Kernel:	  2.6.10-5-k7

``` 

It looks like it can't reach the drives...

I don't know exactly what caused k3b to stop working.  ¿Does anybody know what  could be the cause?

---

### Post by linuxted on 2005-07-04
> **Román]Hi! I'm not sure if k3b is supported, but I've been using it for CD recording. I've also searched through the kubuntu forums but I didn't found anything.

One sad day, k3b just stopped working.

It starts the burnong process and it's only output is 

 ```

IO Error
Removing buffer files

``` 

The Debugging output is:

 ```

Devices
-----------------------
CREATIVE CD-RW RW1210E LCS6 (/dev/hdc, ) at /media/cdrom1 [CD-R said:**
>  [Error] [SAO; TAO; RAW; RAW/R96P; RAW/R96R]
ATAPI-CD ROM-DRIVE-56MAX 56AI (/dev/hdb, ) at /media/cdrom0 [CD-ROM] [Error] [None]

System
-----------------------
K3b Version: 0.11.23
KDE Version: 3.4.0
QT Version:  3.3.3
Kernel:	  2.6.10-5-k7

``` 

It looks like it can't reach the drives...

I don't know exactly what caused k3b to stop working.  ¿Does anybody know what  could be the cause?


I'm having the same problem and its bumming me out!  I might have to go back to Fedora Core 4 if I can't solve this one

---

### Post by tony_st on 2005-12-18
This is an old post, but for the record: I had the same problem with Hoary.  Hard to find any reference to it, but eventually did at [http://sysadminforum.com/showthread.php?t=272619&goto=nextnewest](http://sysadminforum.com/showthread.php?t=272619&goto=nextnewest)

The solution in my case was that the temporary directory k3b was trying to use was no longer writable on my system (for whatever reason).  You can fix that by assigning a directory k3b can use under Settings/Configure K3b.../Misc. Section

---

### Post by nolan- on 2006-05-02
Nice one Tony, cheers mate.
I've been having IO Errors in k3b ever since I created a temp dir and forgot about it and deleted it.

Magic  :)

---

### Post by TitusDalwards on 2006-05-05
can you checkedh  cdrdao or cdrecord has insatalled on your system?if your problem still occurs can you try gnomebaker.

---

