---
title: "ColdFusion (and ZendStudio) install problems on Edgy"
date: 2006-12-01
forum: General Help
---

### Post by xenzero on 2006-12-01
When I install ColdFusion on Edgy, I was getting the following error

nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

which I resolved by doing:

cp coldfusion*.bin cf.bak
cat cf.bak |sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > cf.bin
./cf.bin

But now I get the following:

An internal LaunchAnywhere application error has occured and this application cannot proceed. (LAX)

Stack Trace:
java.lang.IllegalArgumentException: Malformed \uxxxx encoding.
        at java.util.Properties.loadConvert(Properties.java:387)
        at java.util.Properties.load(Properties.java:336)
        at com.zerog.common.java.util.PropertiesUtil.loadProperties(DashoA8113)
        at com.zerog.lax.LAX.<init>(DashoA8113)
        at com.zerog.lax.LAX.main(DashoA8113)

Any ideas?  From what I can tell from the forums, a similar issue affects ZendStudio.

This issue didn't affect Dapper in my experience.

---

### Post by ericdfields on 2007-03-27
here's my error:

```

eric@eric-desktop:~$ sudo ./coldfuion-702-lin.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

exec: 2319: /tmp/install.dir.13902/Linux/resource/jre/bin/java: not found

```

I'm about to try this fix below:

> **xenzero said:**
> 

cp coldfusion*.bin cf.bak
cat cf.bak |sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > cf.bin
./cf.bin



Any prerequisites to this? I haphazardly tried something similar the other day and it didn't work, so i dropped it attempting again now...

---

### Post by SmakDaddy on 2007-05-16
I'm getting the same error.  I've followed the instructions to a T and still can't get passed the "exec: 2319: /tmp/install.dir.13902/Linux/resource/jre/bin/java: not found" error.

Ubuntu 7.04, CF 7.02 and Apache 2

Anyone out there found a fix for this?  I'm the noobest of noobs when it comes to Linux....

---

### Post by bigbadken on 2007-06-12
I ran into this problem as well.  Here's exactly what I had to do to get this working in Ubuntu 7.04 with CF 7.02.  The coldfusion-702-lin.bin file was saved in my /home/bigbadken directory.

Commands:
```

mv coldfusion-702-lin.bin coldfusion-702-lin.bin.bak
cat coldfusion-702-lin.bin.bak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > coldfusion-702-lin.bin
chmod a+x coldfusion-702-lin.bin

```Terminal output during install:
```

bigbadken@bigbadken-desktop:~$ sudo ./coldfusion-702-lin.bin 
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.8462/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
bigbadken@bigbadken-desktop:~$ mv coldfusion-702-lin.bin coldfusion-702-lin.bin.bakbigbadken@bigbadken-desktop:~$ cat coldfusion-702-lin.bin.bak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > coldfusion-702-lin.bin
bigbadken@bigbadken-desktop:~$ chmod a+x ./coldfusion-702-lin.bin
bigbadken@bigbadken-desktop:~$ sudo ./coldfusion-702-lin.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

Preparing CONSOLE Mode Installation...

===============================================================================
Choose Locale...
----------------

  ->1- English

CHOOSE LOCALE BY NUMBER: 
......etc

```

Another tip FWIW:  You'll need to use "sudo" to properly start the server, despite what the installer says.

Running..
```
/opt/jrun4/bin/jrun -start cfusion
```
... will cause "500 null" errors when you try to configure the server, but running... 
```
sudo /opt/jrun4/bin/jrun -start cfusion
```
...works like a charm.

---

