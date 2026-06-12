---
title: "Can't startup Skype"
date: 2013-04-27
forum: General Help
---

### Post by Hyper Tails on 2013-04-27
Hey guys, I've recently installed Ubuntu 13.04 (64-bit), and it's been so-far-so-good.

I installed Skype on it as well, I was able to use it on earlier versions of Ubuntu, but every time I tried to load it up, it will not start up.

I looked up answers to my problem on Google, and none of them worked for me.

Any help will be thanked.

---

### Post by Thee on 2013-04-27
When you start Skype from terminal what does it say?

---

### Post by Hyper Tails on 2013-04-27
```
liam@liam-Z68P-DS3:~$ skype
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/mesa/libGL.so.1' from LD_PRELOAD cannot be preloaded: ignored.
Segmentation fault (core dumped)

```

I followed some instructions on the internet as well.

---

### Post by Thee on 2013-04-27
Try running this:

```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so:/usr/lib/i386-linux-gnu/mesa/libGL.so.1 skype
```

---

### Post by Hyper Tails on 2013-04-27
> **Thee said:**
> Try running this:

```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so:/usr/lib/i386-linux-gnu/mesa/libGL.so.1 skype
```

```
liam@liam-Z68P-DS3:~$ LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so:/usr/lib/i386-linux-gnu/mesa/libGL.so.1 skype
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/mesa/libGL.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/mesa/libGL.so.1' from LD_PRELOAD cannot be preloaded: ignored.
Segmentation fault (core dumped)
liam@liam-Z68P-DS3:~$ 

```

Here is my results.

---

### Post by Gizfreak on 2013-04-27
Take a look at [my thread about Skype]("http://ubuntuforums.org/showthread.php?t=2138838") and maybe you'll understand why Skype doesn't support Linux anymore.

---

### Post by stevedude on 2013-04-27
This is a known bug regarding Ubuntu 13.04 and proprietary NVidia or AMD Drivers. I had the same issue. Go to [http://www.webupd8.org/2013/04/fix-skype-not-working-in-ubuntu-1304.html](http://www.webupd8.org/2013/04/fix-skype-not-working-in-ubuntu-1304.html) and follow the instructions. It worked for me.

---

### Post by Odzinic on 2013-05-02
> **stevedude said:**
> This is a known bug regarding Ubuntu 13.04 and proprietary NVidia or AMD Drivers. I had the same issue. Go to [http://www.webupd8.org/2013/04/fix-skype-not-working-in-ubuntu-1304.html](http://www.webupd8.org/2013/04/fix-skype-not-working-in-ubuntu-1304.html) and follow the instructions. It worked for me.
I attempted this fix using AMD 13.3 beta driver on 13.04 and I still got this error:

```
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/mesa/libGL.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/mesa/libGL.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/mesa/libGL.so.1' from LD_PRELOAD cannot be preloaded: ignored.
Segmentation fault
```

---

### Post by melal on 2013-05-02
> **Odzinic said:**
> I attempted this fix using AMD 13.3 beta driver on 13.04 and I still got this error:

```
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/mesa/libGL.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/mesa/libGL.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/mesa/libGL.so.1' from LD_PRELOAD cannot be preloaded: ignored.
Segmentation fault
```

The reason of your problem is current version of libqtwebkit4 library. Just rollback to older version 2.2.1-4ubuntu1 of libqtwebkit4.

for 64-bit system:
```

cd /tmp
wget http://launchpadlibrarian.net/112036076/libqtwebkit4_2.2.1-4ubuntu1_amd64.deb
sudo dpkg -i libqtwebkit4_2.2.1-4ubuntu1_amd64.deb
```

for 32-bit system:
```

cd /tmp
wget http://launchpadlibrarian.net/112036044/libqtwebkit4_2.2.1-4ubuntu1_i386.deb
sudo dpkg -i libqtwebkit4_2.2.1-4ubuntu1_i386.deb
```

After installation your problem will be resolved.

---

### Post by timgood on 2013-05-02
Recent Skype update has solved this problem.

---

### Post by melal on 2013-05-03
> **timgood said:**
> Recent Skype update has solved this problem.

It's not true. Infact Ubuntu developers changed bash-script for "updated" Skype launching by adding to startup bash-script the following line:

```
export LD_PRELOAD="/usr/lib/i386-linux-gnu/mesa/libGL.so.1${LD_PRELOAD:+:}$LD_PRELOAD"
```

This line just forces libGL.so.1 library load and no more. The update will have no effects for those users who use, for example, NVidia official drivers installed from *.run files from official NVidia web-site. Such a users met already (see above) the following problem:

```
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/mesa/libGL.so.1' from LD_PRELOAD cannot be preloaded: ignored. 
```

There are two ways to solve this issue. First one is described by me above. It's rolling back to older version of libqtwebkit4 library. The second and more correct way is to force Skype to use libGL.so.1 library from libgl1-mesa-glx package. You can do this as described below.

Download libgl1-mesa-glx 9.1.1-0ubuntu3 32-bit package to your home directory:

```

cd
wget http://launchpadlibrarian.net/137709980/libgl1-mesa-glx_9.1.1-0ubuntu3_i386.deb

```

Unpack downloaded libgl1-mesa-glx_9.1.1-0ubuntu3_i386.deb package to a new created directory:

```

mkdir ~/mesa-skype
dpkg -x libgl1-mesa-glx_9.1.1-0ubuntu3_i386.deb ~/mesa-skype

```

Create new directory mesa-skype inside /usr/lib/i386-linux-gnu/

```

sudo mkdir -p /usr/lib/i386-linux-gnu/mesa-skype

```

Copy everything from ~/mesa-skype/usr/lib/i386-linux-gnu/mesa to /usr/lib/i386-linux-gnu/mesa-skype:

```

sudo cp ~/mesa-skype/usr/lib/i386-linux-gnu/mesa/* /usr/lib/i386-linux-gnu/mesa-skype/

```

Edit bash-script /usr/bin/skype using your favorite text editor, for instance, nano:

```

sudo nano /usr/bin/skype

```

Change line from

```
/usr/lib/i386-linux-gnu/mesa/libGL.so.1${LD_PRELOAD:+:}$LD_PRELOAD
```

to

```
/usr/lib/i386-linux-gnu/mesa-skype/libGL.so.1${LD_PRELOAD:+:}$LD_PRELOAD
```

and save changes

That's all. Described changes force Skype to use libGL.so.1 library from libgl1-mesa-glx package and the issue will be resolved. At the same time this changes affect Skype only, but not NVidia or fglrx drivers.

---

### Post by cthlhu1987 on 2013-05-03
> **melal said:**
> It's not true. Infact Ubuntu developers changed bash-script for "updated" Skype launching by adding to startup bash-script the following line:

```
export LD_PRELOAD="/usr/lib/i386-linux-gnu/mesa/libGL.so.1${LD_PRELOAD:+:}$LD_PRELOAD"
```

This line just forces libGL.so.1 library load and no more. The update will have no effects for those users who use, for example, NVidia official drivers installed from *.run files from official NVidia web-site. Such a users met already (see above) the following problem:

```
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/mesa/libGL.so.1' from LD_PRELOAD cannot be preloaded: ignored. 
```

There are two ways to solve this issue. First one is described by me above. It's rolling back to older version of libqtwebkit4 library. The second and more correct way is to force Skype to use libGL.so.1 library from libgl1-mesa-glx package. You can do this as described below.

Download libgl1-mesa-glx 9.1.1-0ubuntu3 32-bit package to your home directory:

```

cd
wget http://launchpadlibrarian.net/137709980/libgl1-mesa-glx_9.1.1-0ubuntu3_i386.deb

```

Unpack downloaded libgl1-mesa-glx_9.1.1-0ubuntu3_i386.deb package to a new created directory:

```

mkdir ~/mesa-skype
dpkg -x libgl1-mesa-glx_9.1.1-0ubuntu3_i386.deb ~/mesa-skype

```

Create new directory mesa-skype inside /usr/lib/i386-linux-gnu/

```

sudo mkdir -p /usr/lib/i386-linux-gnu/mesa-skype

```

Copy everything from ~/mesa-skype/usr/lib/i386-linux-gnu/mesa to /usr/lib/i386-linux-gnu/mesa-skype:

```

sudo cp ~/mesa-skype/usr/lib/i386-linux-gnu/mesa/* /usr/lib/i386-linux-gnu/mesa-skype/

```

Edit bash-script /usr/bin/skype using your favorite text editor, for instance, nano:

```

sudo nano /usr/bin/skype

```

Change line from

```
/usr/lib/i386-linux-gnu/mesa/libGL.so.1${LD_PRELOAD:+:}$LD_PRELOAD
```

to

```
/usr/lib/i386-linux-gnu/mesa-skype/libGL.so.1${LD_PRELOAD:+:}$LD_PRELOAD
```

and save changes

That's all. Described changes force Skype to use libGL.so.1 library from libgl1-mesa-glx package and the issue will be resolved. At the same time this changes affect Skype only, but not NVidia or fglrx drivers.

:guitar: :guitar: :guitar:
OH YEAH BABY IT WORKED!!!! a THOUSAND THANKS!!!!!!!!!!!11

---

### Post by Odzinic on 2013-05-03
> **melal said:**
> It's not true. Infact Ubuntu developers changed bash-script for "updated" Skype launching by adding to startup bash-script the following line:

```
export LD_PRELOAD="/usr/lib/i386-linux-gnu/mesa/libGL.so.1${LD_PRELOAD:+:}$LD_PRELOAD"
```

This line just forces libGL.so.1 library load and no more. The update will have no effects for those users who use, for example, NVidia official drivers installed from *.run files from official NVidia web-site. Such a users met already (see above) the following problem:

```
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/mesa/libGL.so.1' from LD_PRELOAD cannot be preloaded: ignored. 
```

There are two ways to solve this issue. First one is described by me above. It's rolling back to older version of libqtwebkit4 library. The second and more correct way is to force Skype to use libGL.so.1 library from libgl1-mesa-glx package. You can do this as described below.

Download libgl1-mesa-glx 9.1.1-0ubuntu3 32-bit package to your home directory:

```

cd
wget http://launchpadlibrarian.net/137709980/libgl1-mesa-glx_9.1.1-0ubuntu3_i386.deb

```

Unpack downloaded libgl1-mesa-glx_9.1.1-0ubuntu3_i386.deb package to a new created directory:

```

mkdir ~/mesa-skype
dpkg -x libgl1-mesa-glx_9.1.1-0ubuntu3_i386.deb ~/mesa-skype

```

Create new directory mesa-skype inside /usr/lib/i386-linux-gnu/

```

sudo mkdir -p /usr/lib/i386-linux-gnu/mesa-skype

```

Copy everything from ~/mesa-skype/usr/lib/i386-linux-gnu/mesa to /usr/lib/i386-linux-gnu/mesa-skype:

```

sudo cp ~/mesa-skype/usr/lib/i386-linux-gnu/mesa/* /usr/lib/i386-linux-gnu/mesa-skype/

```

Edit bash-script /usr/bin/skype using your favorite text editor, for instance, nano:

```

sudo nano /usr/bin/skype

```

Change line from

```
/usr/lib/i386-linux-gnu/mesa/libGL.so.1${LD_PRELOAD:+:}$LD_PRELOAD
```

to

```
/usr/lib/i386-linux-gnu/mesa-skype/libGL.so.1${LD_PRELOAD:+:}$LD_PRELOAD
```

and save changes

That's all. Described changes force Skype to use libGL.so.1 library from libgl1-mesa-glx package and the issue will be resolved. At the same time this changes affect Skype only, but not NVidia or fglrx drivers.

This worked. Thank you.

---

### Post by Shrek01 on 2013-05-03
Thx melal.

---

### Post by pecico on 2013-05-06
> **melal said:**
> The reason of your problem is current version of libqtwebkit4 library. Just rollback to older version 2.2.1-4ubuntu1 of libqtwebkit4.

for 64-bit system:
```

cd /tmp
wget http://launchpadlibrarian.net/112036076/libqtwebkit4_2.2.1-4ubuntu1_amd64.deb
sudo dpkg -i libqtwebkit4_2.2.1-4ubuntu1_amd64.deb
```

for 32-bit system:
```

cd /tmp
wget http://launchpadlibrarian.net/112036044/libqtwebkit4_2.2.1-4ubuntu1_i386.deb
sudo dpkg -i libqtwebkit4_2.2.1-4ubuntu1_i386.deb
```

After installation your problem will be resolved.


This solution works for me (Ubuntu 13.04, 32 bit, proprietary nvidia driver)!!!
Thank you very much!

---

### Post by lovebluesky2009 on 2013-05-06
seen from others
type in terminal
```
sudo -s
mv /usr/bin/skype /usr/bin/skype-bin
gedit /usr/bin/skype
```

copy the following code to gedit
```
#!/bin/sh
export LD_PRELOAD=/usr/lib/i386-linux-gnu/mesa/libGL.so.1
exec skype-bin
```

save and run in terminal
```
chmod 0755 /usr/bin/skype
```

just for 64 bit

---

### Post by melal on 2013-05-06
> **lovebluesky2009 said:**
> seen from others
type in terminal
```
sudo -s
mv /usr/bin/skype /usr/bin/skype-bin
gedit /usr/bin/skype
```

copy the following code to gedit
```
#!/bin/sh
export LD_PRELOAD=/usr/lib/i386-linux-gnu/mesa/libGL.so.1
exec skype-bin
```

save and run in terminal
```
chmod 0755 /usr/bin/skype
```

just for 64 bit

1. Nobody needs to do this as this fix is part of official skype deb-package from ubuntu repositories since latest update. Just install or update skype from official ubuntu repos.
2. This fix doesn't work at those users who installed proprietary nvidia or amd drivers from *.run files from official NVidia and AMD web-sites. Such a users can fix problem using described above method: [http://ubuntuforums.org/showthread.php?t=2139649&p=12631036#post12631036](http://ubuntuforums.org/showthread.php?t=2139649&p=12631036#post12631036)

---

### Post by badbod on 2013-05-10
+1 for Melal, worked great for me too! Using AMD propriety drivers 13.4 on ubuntu 13.04 x86_64 (amd64)

---

### Post by mmstick on 2013-05-15
Doesn't work on Ubuntu 13.10. Still broken.

---

### Post by carlosalvet on 2013-05-17
lovebluesky2009 wrote about a several steps for the skype error.

I did the steps to change the library and now The Ubuntu Software Center throws me an error of library incompability and can't install anything untill the depends were resolved.

How can I roll back the last changes?

```

cd /tmp
wget http://launchpadlibrarian.net/112036076/libqtwebkit4_2.2.1-4ubuntu1_amd64.deb
sudo dpkg -i libqtwebkit4_2.2.1-4ubuntu1_amd64.deb

```

I run the Ubuntu Software Center and throws an error and ask me for repair, at least the repair fails and throws

```

(Reading database ... 222134 files and directories currently installed.)
Preparing to replace libqtwebkit4:amd64 2.2.1-4ubuntu1 (using .../libqtwebkit4_2.3.0-0ubuntu2_amd64.deb) ...
Unpacking replacement libqtwebkit4:amd64 ...
dpkg: error processing /var/cache/apt/archives/libqtwebkit4_2.3.0-0ubuntu2_amd64.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libqtwebkit4/copyright', which is different from other instances of package libqtwebkit4:amd64
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 /var/cache/apt/archives/libqtwebkit4_2.3.0-0ubuntu2_amd64.deb
Error in function: 
dpkg: error processing libqtwebkit4:amd64 (--configure):
 package libqtwebkit4:amd64 2.2.1-4ubuntu1 cannot be configured because libqtwebkit4:i386 is at a different version (2.3.0-0ubuntu2)
dpkg: error processing libqtwebkit4:i386 (--configure):
 package libqtwebkit4:i386 2.3.0-0ubuntu2 cannot be configured because libqtwebkit4:amd64 is at a different version (2.2.1-4ubuntu1)


```

Some body can help me please?

---

### Post by carlosalvet on 2013-05-17
I did the steps to change the library and now The Ubuntu Software Center throws me an error of library incompability and can't install anything untill the depends were resolved.

How can I roll back the last changes?

```

cd /tmp
wget http://launchpadlibrarian.net/112036076/libqtwebkit4_2.2.1-4ubuntu1_amd64.deb
sudo dpkg -i libqtwebkit4_2.2.1-4ubuntu1_amd64.deb

```

---

### Post by melal on 2013-05-18
> **carlosalvet said:**
> I did the steps to change the library and now The Ubuntu Software Center throws me an error of library incompability and can't install anything untill the depends were resolved.

How can I roll back the last changes?

```

cd /tmp
wget http://launchpadlibrarian.net/112036076/libqtwebkit4_2.2.1-4ubuntu1_amd64.deb
sudo dpkg -i libqtwebkit4_2.2.1-4ubuntu1_amd64.deb

```

Post kindly output of:

```

uname -m

```

and

```

dpkg --list | grep libqtwebkit4

```

---

