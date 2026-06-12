---
title: "Cant find a program I installed??"
date: 2012-12-22
forum: General Help
---

### Post by listerdl on 2012-12-22
Hi I downloaded Dragon Disk which is a FTP/ SSH client.

It was a deb file and really easy to install - it was loaded through the Ubuntu software and it seemed to install fine.

I cant find it though??

I have looked in /usr/ and /opt/ and applications but it just isnt there??

In the Ubuntu Software Center it is listed as "installed" and labelled as dgtools - short for Dragon Tools...

This is the file name: dgtools_1.3.1-0ubuntu_i386.deb

This is the Dragon Disk site: [http://www.dragondisk.com/](http://www.dragondisk.com/)

Thanks for any help to locate this!

---

### Post by chadk5utc on 2012-12-22
from a terminal type
> sudo whereis whateverfilename.extension
modify to suit

---

### Post by listerdl on 2012-12-22
> **chadk5utc said:**
> from a terminal type

modify to suit

Thanks for your help. So I guess in my instance it would be:

```
sudo whereis dgtools_1.3.1-0ubuntu_i386.deb
```

:o

I'd do it now but im not by that machine anymore. When I am ill update this post for other people. Thx

---

### Post by zombifier25 on 2012-12-23
> **listerdl said:**
> Thanks for your help. So I guess in my instance it would be:

```
sudo whereis dgtools_1.3.1-0ubuntu_i386.deb
```

:o

I'd do it now but im not by that machine anymore. When I am ill update this post for other people. Thx

First off, I doubt "sudo" is needed. Secondly, the command "whereis" is used to find the location of the command and the man files.

The website states that the command to launch it is "dragondisk".

---

### Post by vasa1 on 2012-12-23
You could also try "locate".
So, in a terminal, run:
locate **whatever**
where whatever will be the app you're looking for.

I'm not sure that sudo is needed for locate or whereis. I use sudo only when normal commands fail.

Quoting from [LOCATE FIND AND WHEREIS]("http://linux-sxs.org/utilities/locate.html"):
> just to point out the differences between locate, find, and whereis:

whereis: will search only particular paths to find binaries and or manpages. The manpages tells you where whereis looks.

locate: locate uses a database created by an updatedb to efficiently locate files. Works great, assuming your database is updated often enough to be reasonable upto date. Most boxes using locate have the updatedb occuring in cron.

find: find is perhaps one of the most powerful commands there is. For just locating a file/program of a particular name, it'll definitely be slower than locate or whereis ...

---

### Post by stinkeye on 2012-12-23
As a test, I installed the **dragondisk_1.0.5-0ubuntu_amd64.deb**
in Quantal and it appears in the dash when searching for dragon.
DragonDisk also appears in the old menu under the Internet section, when running a gnome classic session, .
Both launch a DragonDisk gui.

The **/usr/share/applications/dragondisk.desktop** file shows the exec command
is **/usr/bin/dragondisk** or just **dragondisk** in terminal.

The other download of **dgtools** on the same page, installs the Command line sync tool ...**dgsync**.
Terminal...
```
dgsync --help
```

So it appears there are 2 downloads...
[LIST]
[*]dragondisk (gui)
[*]dgtools (command line **dgsync**)
[/LIST]
If you want the gui you need to download the **dragondisk_1.0.5-0ubuntu_i386.deb** file.

---

### Post by tonyp13 on 2012-12-23
Hello,
DragonDisk is not a FTP/SSH Client but an Amazon S3 Client.

Tony

---

### Post by rnerwein on 2012-12-23
> **tonyp13 said:**
> Hello,
DragonDisk is not a FTP/SSH Client but an Amazon S3 Client.

Tony
hi
cd /
sudo find . -name "***dragondisk*"**
will give you everything you want
cheers

---

### Post by listerdl on 2012-12-23
> **stinkeye said:**
> As a test, I installed the **dragondisk_1.0.5-0ubuntu_amd64.deb**
in Quantal and it appears in the dash when searching for dragon.
DragonDisk also appears in the old menu under the Internet section, when running a gnome classic session, .
Both launch a DragonDisk gui.

The **/usr/share/applications/dragondisk.desktop** file shows the exec command
is **/usr/bin/dragondisk** or just **dragondisk** in terminal.

The other download of **dgtools** on the same page, installs the Command line sync tool ...**dgsync**.
Terminal...
```
dgsync --help
```

So it appears there are 2 downloads...
[LIST]
[*]dragondisk (gui)
[*]dgtools (command line **dgsync**)
[/LIST]
If you want the gui you need to download the **dragondisk_1.0.5-0ubuntu_i386.deb** file.

Thanks very much for pointing something that I should have realized! Yes I just needed to download the GUI. 

Thanks to everyone.

---

