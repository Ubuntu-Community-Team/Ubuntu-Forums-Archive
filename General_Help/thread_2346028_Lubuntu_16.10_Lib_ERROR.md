---
title: "Lubuntu 16.10 Lib ERROR"
date: 2016-12-10
forum: General Help
---

### Post by fritual on 2016-12-10
Hi,
Q: What method can I use to locate Lubuntu module w/libxine.so.1 Lib embedded in it?

```

fritual@lubuntu:~$ qdvdauthor
qdvdauthor: error while loading shared libraries: libxine.so.1: cannot open shared object file: No such file or directory
fritual@lubuntu:~$ 


```
Yours,
fritual

---

### Post by Dennis N on 2016-12-10
Install the package **apt-file** to identify the package containing a certain library.

After installing, you first update it: 

**sudo apt-file update**

Then search

**sudo apt-file find <file name>**

Example: a program needs libGLU.so.1

```
dmn@Sydney:~$ sudo apt-file find libGLU.so.1
libglu1-mesa: /usr/lib/x86_64-linux-gnu/libGLU.so.1
libglu1-mesa: /usr/lib/x86_64-linux-gnu/libGLU.so.1.3.1

```

I should install libglu1-mesa to get this library.

---

### Post by fritual on 2016-12-10
Dennis,
Following your dialog returned VOID:
```

fritual@lubuntu:~$ sudo apt-file find "libxine.so.1"
[sudo] password for fritual: 
fritual@lubuntu:~$ 


```
Q: What's missing?
Suspect apt-file overlooked a repo.
fritual

---

### Post by Dennis N on 2016-12-10
You should not use the quotation marks. Your command should be:

```
sudo apt-file find libxine.so.1
```

---

### Post by fritual on 2016-12-10
> **Dennis N said:**
> You should not use the quotation marks. Your command should be:

```
sudo apt-file find libxine.so.1
```
Hi,
VOID even w/o quotation marks:
```

fritual@lubuntu:~$ sudo apt-file find libxine.so.1
[sudo] password for fritual: 
fritual@lubuntu:~$ 

```
I'm stumpt, but suspect lubuntu 16:10 HD install and maybe try LiveDVD, next.
fritual

---

### Post by Dennis N on 2016-12-10
I don't have 16.10, but here is the result from 14.04:

```
dmn@Sydney:~$ sudo apt-file find libxine.so.1
libxine1-bin: /usr/lib/libxine.so.1
libxine1-bin: /usr/lib/libxine.so.1.30.2
libxine1-dbg: /usr/lib/debug/usr/lib/libxine.so.1.30.2

```

So the package would be libxine1-bin, but that is not available in 16.10 according to package search. Instead, 16.10 has libxine2-bin
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
[http://packages.ubuntu.com/yakkety/libxine2-bin](http://packages.ubuntu.com/yakkety/libxine2-bin)

---

### Post by fritual on 2016-12-10
> **Dennis N said:**
> I don't have 16.10, but here is the result from 14.04:

```
dmn@Sydney:~$ sudo apt-file find libxine.so.1
libxine1-bin: /usr/lib/libxine.so.1
libxine1-bin: /usr/lib/libxine.so.1.30.2
libxine1-dbg: /usr/lib/debug/usr/lib/libxine.so.1.30.2

```

So the package would be libxine1-bin, but that is not available in 16.10 according to package search. Instead, 16.10 has libxine2-bin
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
[http://packages.ubuntu.com/yakkety/libxine2-bin](http://packages.ubuntu.com/yakkety/libxine2-bin)
Hi,
'libxine2-bin' appears VOID of 'libxine.so.1':
```

fritual@lubuntu:~$ sudo aptitude install libxine2-bin
[sudo] password for fritual:
libxine2-bin is already installed at the requested version (1.2.6-1.2)
libxine2-bin is already installed at the requested version (1.2.6-1.2)
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
                                        
fritual@lubuntu:~$ sudo find -H / -name "*libxine.so.1*"
find: ‘/run/user/1000/gvfs’: Permission denied
fritual@lubuntu:~$

```
Perhaps adding an older version to sources.list:
[URL="http://pogidude.com/2013/how-to-install-packages-for-end-of-life-ubuntu-editions/"]link
[/URL]
fritual

---

### Post by Dennis N on 2016-12-11
> 'libxine2-bin' appears VOID of 'libxine.so.1'

You are right about that. You can use apt-file to see all the files (and where they go) contained in a package:

**sudo apt-file list libxine2-bin**

There is a metapackage **libxine2** that installs **libxine2-bin** and other related packages. Also a **libxine1** metapackage.

From this simulation, it looks like they could both be installed on the same system:

```
dmn@Sydney:~$ apt-get -s install libxine1 libxine2
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libgraphicsmagick3 libiso9660-8 libvcdinfo0 libxine1-bin libxine1-ffmpeg
  libxine1-misc-plugins libxine1-plugins libxine2-bin libxine2-doc
  libxine2-ffmpeg libxine2-misc-plugins libxine2-plugins
Suggested packages:
  graphicsmagick-dbg gxine xine-ui libxine1-doc libxine-doc libxine1-gnome
The following NEW packages will be installed:
  libgraphicsmagick3 libiso9660-8 libvcdinfo0 libxine1 [COLOR="#FF0000"]libxine1-bin[/COLOR]
  libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine2 [COLOR="#FF0000"]libxine2-bin[/COLOR]
  libxine2-doc libxine2-ffmpeg libxine2-misc-plugins libxine2-plugins
0 upgraded, 14 newly installed, 0 to remove and 6 not upgraded.

```
**libxine1** and **libxine2** are BOTH available in 14.04.

---

### Post by fritual on 2016-12-11
> **Dennis N said:**
> You are right about that. You can use apt-file to see all the files (and where they go) contained in a package:

**sudo apt-file list libxine2-bin**

There is a metapackage **libxine2** that installs **libxine2-bin** and other related packages. Also a **libxine1** metapackage.

From this simulation, it looks like they could both be installed on the same system:

```
dmn@Sydney:~$ apt-get -s install libxine1 libxine2
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libgraphicsmagick3 libiso9660-8 libvcdinfo0 libxine1-bin libxine1-ffmpeg
  libxine1-misc-plugins libxine1-plugins libxine2-bin libxine2-doc
  libxine2-ffmpeg libxine2-misc-plugins libxine2-plugins
Suggested packages:
  graphicsmagick-dbg gxine xine-ui libxine1-doc libxine-doc libxine1-gnome
The following NEW packages will be installed:
  libgraphicsmagick3 libiso9660-8 libvcdinfo0 libxine1 [COLOR=#FF0000]libxine1-bin[/COLOR]
  libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine2 [COLOR=#FF0000]libxine2-bin[/COLOR]
  libxine2-doc libxine2-ffmpeg libxine2-misc-plugins libxine2-plugins
0 upgraded, 14 newly installed, 0 to remove and 6 not upgraded.

```
**libxine1** and **libxine2** are BOTH available in 14.04.
Hi,
Back to square one.

[Hotlink]("http://glennmcc.dynu.com/download/qdvdauthor/")
My objective is to convert the above Hotlink 5 TGZ binaries to DEB using alien:
> 
alien -d -c <binary-name>

Next, have Lubuntu install them.  I plead ignorance when dealing with the symlinks/shared libraries that have since surfaced, giving post credence.
fritual

---

