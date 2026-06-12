---
title: "go game"
date: 2015-06-14
forum: General Help
---

### Post by cmcanulty on 2015-06-14
I am having no luck installing qgo (it shows a red box in synaptic yet no missing dependencies) or gopanda2
panda go shows a deb file but won't install for me

[http://www.pandanet.co.jp/English/glgo/download.html]("http://www.pandanet.co.jp/English/glgo/download.html")

I get this error

```
cmcanulty@ubuntu1:~$ sudo dpkg -i glGo-1.4.1.deb
(Reading database ... 676957 files and directories currently installed.)
Preparing to unpack glGo-1.4.1.deb ...
Unpacking glgo (1.4.1) over (1.4.1) ...
Setting up glgo (1.4.1) ...
cmcanulty@ubuntu1:~$ sh glGo.install
sh: 0: Can't open glGo.install
cmcanulty@ubuntu1:~$ sh glGo.install
sh: 0: Can't open glGo.install
cmcanulty@ubuntu1:~$ sudo sh glGo.install
sh: 0: Can't open glGo.install

```

I read these 2 threads and didn't work for me

[http://www.lifein19x19.com/forum/viewtopic.php?f=18&t=11302]("http://www.lifein19x19.com/forum/viewtopic.php?f=18&t=11302")

[http://www.lifein19x19.com/forum/viewtopic.php?f=33&t=10763]("http://www.lifein19x19.com/forum/viewtopic.php?f=33&t=10763")

---

### Post by Steve_Horan on 2015-06-14
Have you tired downloading the .tar file. Unzipping it and running ./glGo.install ? It appears the deb package installed without error what happens when you run the game?

---

### Post by cmcanulty on 2015-06-14
I thought that was what I tried with the code above. I downloaded it to  my home, unpacked it and ran

```
sudo sh glGo.install
```

```
cmcanulty@ubuntu1:~$ sudo sh glGo.install
[sudo] password for cmcanulty: 
sh: 0: Can't open glGo.install
cmcanulty@ubuntu1:~$ 
```

I'm not sure I am doing that correctly though, can you explain?

---

### Post by Steve_Horan on 2015-06-14
Go to your command prompt.

type:
> wget [http://www.pandanet.co.jp/English/glgo/downloads/glGo-1.4.1.tar.gz](http://www.pandanet.co.jp/English/glgo/downloads/glGo-1.4.1.tar.gz)
tar -xvaf glGo-1.4.1.tar.gz
sudo ./glGo.install

Enjoy :)

---

### Post by cmcanulty on 2015-06-14
Here is what I get

```
cmcanulty@ubuntu1:~$ wget [http://www.pandanet.co.jp/English/gl...o-1.4.1.tar.gz](http://www.pandanet.co.jp/English/gl...o-1.4.1.tar.gz)
--2015-06-14 17:47:50--  [http://www.pandanet.co.jp/English/gl...o-1.4.1.tar.gz](http://www.pandanet.co.jp/English/gl...o-1.4.1.tar.gz)
Resolving [www.pandanet.co.jp](www.pandanet.co.jp) ([www.pandanet.co.jp](www.pandanet.co.jp))... 118.151.176.198
Connecting to [www.pandanet.co.jp](www.pandanet.co.jp) ([www.pandanet.co.jp)|118.151.176.198|:80](www.pandanet.co.jp)|118.151.176.198|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2015-06-14 17:47:50 ERROR 404: Not Found.
```

also the link to the source files and install code seems to not open

---

### Post by steeldriver on 2015-06-14
You appear to have copied the hyperlink that @Steve_Horan provided **as text** - complete with the URL "shortenings" [COLOR=#ff0000][SIZE=3]**...**[/SIZE][/COLOR]

Try right-clicking on the link and selecting 'copy link location' then paste *that* after the [FONT=courier new]wget
[/FONT]

---

### Post by cmcanulty on 2015-06-14
OK I tried that and  it seems to think it is installed but doesn't appear in menu or open from terminal

```
cmcanulty@ubuntu1:~$ wget http://www.pandanet.co.jp/English/glgo/downloads/glGo-1.4.1.tar.gz
--2015-06-14 18:14:44--  http://www.pandanet.co.jp/English/glgo/downloads/glGo-1.4.1.tar.gz
Resolving www.pandanet.co.jp (www.pandanet.co.jp)... 118.151.176.198
Connecting to www.pandanet.co.jp (www.pandanet.co.jp)|118.151.176.198|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3246236 (3.1M) [application/x-gzip]
Saving to: ‘glGo-1.4.1.tar.gz.1’

100%[======================================>] 3,246,236    678KB/s   in 4.9s   

2015-06-14 18:14:49 (653 KB/s) - ‘glGo-1.4.1.tar.gz.1’ saved [3246236/3246236]

cmcanulty@ubuntu1:~$ tar -xvaf glGo-1.4.1.tar.gz
glGo.install
glGo.license
glGo.remove
glGo.ss
glGo.sw
cmcanulty@ubuntu1:~$ sudo ./glGo.install 
[sudo] password for cmcanulty: 
Copyright 2003-2006 PANDANET Inc.

This installation script will install the glGo
software version 1.4.1 on your system.

Do you wish to continue? y
PANDA-glGo is copyrighted work: Copyright (c) 2003-2006 PANDANET Inc.
All rights reserved.

The artwork and images are copyrighted work and must not be redistributed.
Copyright (c) 2002-2006, Tweet. All rights reserved.

Permission is granted to download, install and use this software.
Permission of the author must be obtained to redistribute the software.
It is forbidden to decompile and modify the software to alter its behaviour, or
distribute such a modified software.

This software is provided 'as-is', without any express or implied warranty,
without even the implied warranty of merchantability or fitness for a particular
purpose. In no event will the authors be held liable for any damages arising
from the use of this software.

Do you agree with the terms of this license? y
Removing old versions of glGo software...
Copyright 2003-2006 PANDANET Inc.
Removing/restoring installed files...
Checking configuration files...
Removing empty installation directories...
Removal is complete.
Backing up old versions of shared files to be installed...
Creating installation directories...
Installing software...
Updating file permissions...
Running post-install commands...
Installation is complete.
cmcanulty@ubuntu1:~$ glgo
glgo: command not found
cmcanulty@ubuntu1:~$
```

Here in screenshot  synaptic show it as installed but on other screenshot  it says differently and I tried from the settings menu force verrsion but it is greyed out

[ATTACH=CONFIG]262601[/ATTACH][ATTACH=CONFIG]262602[/ATTACH]

---

### Post by Steve_Horan on 2015-06-14
What happens when you type glGO in the cmd line?

---

### Post by cmcanulty on 2015-06-14
I have that at the end of my previous reply it is, weird as I have used this app for years with no issue until now, could some file be broken?

```
Running post-install commands...
Installation is complete.
cmcanulty@ubuntu1:~$ glgo
glgo: command not found
cmcanulty@ubuntu1:~$
```

---

### Post by Steve_Horan on 2015-06-14
gl**G**o <-- linux is case sensitive.

---

### Post by cmcanulty on 2015-06-14
```
cmcanulty@ubuntu1:~$ glGo
glGo: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory
cmcanulty@ubuntu1:~$
```

---

### Post by Steve_Horan on 2015-06-14
Ok we are getting close you are just missing some dependency, of course I am current on a SuSe box atm :-({|=.

Could you provide me the output of:
> ldd glGo

This will provide us a list of dependencies.

---

### Post by cmcanulty on 2015-06-14
```
cmcanulty@ubuntu1:~$ ldd glGo 
ldd: ./glGo: No such file or directory
cmcanulty@ubuntu1:~$ 

```

I am going to bed , have an early day tomorrow. Hopefully can work this out, thank you

---

