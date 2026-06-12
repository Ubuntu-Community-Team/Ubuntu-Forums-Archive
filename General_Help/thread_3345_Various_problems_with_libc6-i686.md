---
title: "Various problems with libc6-i686"
date: 2004-11-05
forum: General Help
---

### Post by andbert on 2004-11-05
My intention was to install Mplayer.
Synaptic sends me an error message.

In terminal sudo apt-get upgrade gives me:

Reading Package Lists... Done
Building Dependency Tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libc6-i686: PreDepends: libc6 (= 2.3.2.ds1-13ubuntu2) but 2.3.2.ds1-13ubuntu2.2 is installed
E: Unmet dependencies. Try using -f.


Then apt-get -f install gives me:

Reading Package Lists... Done
Building Dependency Tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  libc6-i686
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 2183kB disk space will be freed.
Do you want to continue? [Y/n] y
dpkg: error processing libc6-i686 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 libc6-i686
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any input on how to fix this?

---

### Post by diebels on 2004-11-05
Tried "dist-upgrade" or "check"?

---

### Post by andbert on 2004-11-05
Yeah.
Tried both but none of the commands seem to work.
:-(

---

### Post by FLeiXiuS on 2004-11-05
It appears that the package under the name of DS isn't there.  Have you added the universe to your sources.list?

```
apt-cache search ds
```
or
```
apt-cache search ds1
```

Then if you find one that looks like the missing dependency then you have it.

```
apt-get install FILENAME
```

replace filename with the current file.

---

### Post by diebels on 2004-11-05
That's a tricky one. It's libc6-i686 that's got an security upgrade from  version 2.3.2.ds1-13ubuntu2 to version 2.3.2.ds1-13ubuntu2.2. And mplayer thinks it needs the exact version 2.3.2.ds1-13ubuntu2. It should be happy with a newer version. Not sure how to fix this..

---

### Post by diebels on 2004-11-05
Not sure my prevoius post made any sense. From the output, maybe you have a problem with libc6-i686. That could be serious, so to be safe, check that you have included the official repositories in /etc/apt/sources.list:
```
deb http://archive.ubuntu.com/ubuntu/ warty main
deb http://security.ubuntu.com/ubuntu/ warty-security main
```and do:```
sudo apt-get update && apt-get dist-upgrade
```

---

### Post by wallijonn on 2004-11-05
I have to ask why you're not using SPM's XINE?

If it's just to play DVDs, install SPM's XINE, google search for and download [/COLOR=RED]libdvdcss2_1.2.8-1_i386.deb[/COLOR], extract the files and then copy libdvdcss.so.2 and libdvdcss.so.2.0.7 to /usr/lib. 

presto.

---

### Post by andbert on 2004-11-06
Its not just for DVD, but most video-formats.
None of the replies above did work.
The same error message occured:

 Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.
Errors were encountered while processing:
libc6-i686
E: Sub-process /usr/bin/dpkg returned an error code (1)

I cant even use Synaptic to upgrade packages before the broken libc6-i686 is removed/reinstalled!

Input?

---

