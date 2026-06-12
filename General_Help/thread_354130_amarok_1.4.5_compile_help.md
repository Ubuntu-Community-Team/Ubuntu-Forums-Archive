---
title: "amarok 1.4.5 compile help"
date: 2007-02-05
forum: General Help
---

### Post by darweth on 2007-02-05
Hello.  I am upping Amarok 1.4.4 to 1.4.5 via source.  I apt-get removed Amarok and all it removed was amarok and amarok-xine.  I kept all the other dependencies.

When I compile 1.4.5 I get this msg:

checking for Qt... configure: error: Qt (>= Qt 3.3 and < 4.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.


What do I need to install to compile it successfully?  If I install those QT libraries, can I delete them after?  They are only needed for compiling???  Because like I said, I only removed Amarok and Amarok-Xine... nothing else.

One last thing... if I intend to use a Creative, iRiver, etc... an MTP device I believe it is called... what packages should I install before compiling?  I believe there is a libmtp-dev package or something.  And perhaps gnomad too?

EDIT::::  actually, i guess gnomad is something that works independently and libmtp-dev is all that is needed for AMAROK to work with said device.

Ahhh!

---

### Post by darweth on 2007-02-05
I installed qt3-dev-tools and it did not resolve the issue.  Any ideas?

---

### Post by jd65pl on 2007-02-05
Try doing this

```
sudo apt-get install linux-headers-$(uname -r)
```

then try re-installing amrok

---

### Post by darweth on 2007-02-05
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.17-10-generic is already the newest version.

---

### Post by TriggerHappyChewie on 2007-02-05
try this:

```
sudo apt-get build-dep amarok
```

I don't think you need the dev package of libmtp to compile.

---

### Post by GoneSouth on 2007-02-06
```
sudo apt-get build-dep amarok
```

Resulted in a "could not resolve dependencies" error message for me. I determined the following dependencies by trial and error (your mileage may vary):

```

sudo bash (i get tired of typing sudo in front of every command)
aptitude install libqt3-headers kdelibs4-dev  libxine-dev libruby1.8-dev libtag1-dev
cd <amarok source dir>
./configure --prefix=`kde-config --prefix`
make
apt-get remove amarok amarok-xine
checkinstall make install

```


Aptitude may suggest to downgrade some package versions to satisfy build dependencies, answer yes to these. Configure checkinstall to have package name amarok and version 2:1.4.5. this will prevent the update manager from trying to "update" your amarok to v1.4.4.

Cheers !

---

