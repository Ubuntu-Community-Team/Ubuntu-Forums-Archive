---
title: "resolving Zend Studio Installer Errors"
date: 2006-10-29
forum: General Help
---

### Post by xaarr on 2006-10-29
hello,

i have spend some time to fix this problem:

```
# sudo ./ZendStudio-5_2_0.bin                    
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
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.6489/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

```


the simple Fix is:

```
# cp ZendStudio-5_2_0.bin ZendStudio-5_2_0.bin.bak

# cat ZendStudio-5_2_0.bin.bak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > ZendStudio-5_2_0.bin

# ZendStudio-5_2_0.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
awk: cmd. line:6: warning: escape sequence `\.' treated as plain `.'

Launching installer...

```
i hope this helps some one...

best regards,
Daniel.

---

### Post by xaarr on 2006-10-30
Hmpf!

now, i can install and start ZDE, but the ZDE-Window is blank.

[IMG]http://www.phpaction.de/screen.png[/IMG]

The Welcome Screen on start and the Tips-on-start are showen correctly.

"Ctrl-O" opens the Open-File dialog, but no Top-Main-Menu or edit-area is visible.

system: ubuntu edgy, xgl, beryl

i have also made an Zend-Trouble-Ticket. But i think its a ubuntu or xgl problem with zde.

PS: ZDE is a java application. the JRE is integrated in the ZDE package.

Has anybody seen this problem with other applications ?

Greetz,
Daniel.

---

### Post by xaarr on 2006-11-01
Now my Zend runs under xgl desktop.

the full patch description for ZDE <= 5.2.0 you can read here:
[http://www.zend.com/support/knowledgebase.php?kbid=184&view_only=1](http://www.zend.com/support/knowledgebase.php?kbid=184&view_only=1)

the patch for runs ZDE <= 5.5.0beta to run under xgl:  (works under ZDE 5.2.0 too, but other line-number)

:~/usr/ZendStudio-5.5.0Beta/bin$ diff ZDE.org ZDE 
1693a1694,1695
> options="$options -Dawt.toolkit=sun.awt.motif.MToolkit"
> 

in words:         Add the line 'options="$options -Dawt.toolkit=sun.awt.motif.MToolkit"' on line 1695 in ZDE start file in /bin/


Source & Description of the xgl solution:
[http://forum.beryl-project.org/topic-3013-search-window-borders-development-environment-remain-visible](http://forum.beryl-project.org/topic-3013-search-window-borders-development-environment-remain-visible)


good luck,
Daniel.


PS: The next problem is solving UTF-8 Problems: all special chars are shown correct on loading utf8 documents, but entering new chars are shown as small rectangles.
    See here: [http://www.phpaction.de/zdeutf8/](http://www.phpaction.de/zdeutf8/)
    it shows like a keyboard-input-Problem ?

---

### Post by xaarr on 2006-11-06
The last tip:

now utf8 works fine in my ZDE:

i changet the LANG environment variable and add LANGUAGE in Ubuntu Edgy (6.10)

# cat /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
#LANG="de_DE@euro"
LANG="de_DE.UTF-8"
LANGUAGE="de_DE:de"

After reboot i can correct enter UTF8 chars !


Hope it helps someone,
Daniel.

---

### Post by zero2one on 2006-11-06
I have a simular problem:
updated from dapper to edgy (6.10)
Zend Studio wont start.

Did the hack from the zend support pages

the lib error is gone but now I have:
```
An internal LaunchAnywhere application error has occured and this application cannot proceed. (LAX)

Stack Trace:
java.lang.IllegalArgumentException: Malformed \uxxxx encoding.
        at java.util.Properties.loadConvert(Unknown Source)
        at java.util.Properties.load(Unknown Source)
        at com.zerog.common.java.util.PropertiesUtil.loadProperties(DashoA8113)
        at com.zerog.lax.LAX.<init>(DashoA8113)
        at com.zerog.lax.LAX.main(DashoA8113)

```

Annyone who has an fix for this.

I tried to install the zend studio client in a fresh kubuntu edgy install in a vmware => no problem.

---

### Post by Galoot on 2006-11-09
Following the directions at [http://www.zend.com/support/knowledgebase.php?kbid=226&view_only=1](http://www.zend.com/support/knowledgebase.php?kbid=226&view_only=1) on a fresh Edgy installation worked like a charm for me.

---

### Post by Tikhon on 2006-11-20
> **zero2one said:**
> I have a simular problem:
updated from dapper to edgy (6.10)
Zend Studio wont start.

Did the hack from the zend support pages

the lib error is gone but now I have:
```
An internal LaunchAnywhere application error has occured and this application cannot proceed. (LAX)

Stack Trace:
java.lang.IllegalArgumentException: Malformed \uxxxx encoding.
        at java.util.Properties.loadConvert(Unknown Source)
        at java.util.Properties.load(Unknown Source)
        at com.zerog.common.java.util.PropertiesUtil.loadProperties(DashoA8113)
        at com.zerog.lax.LAX.<init>(DashoA8113)
        at com.zerog.lax.LAX.main(DashoA8113)

```


I have same problem :(
My locale:
```

$ locale
LANG=ru_UA.UTF-8
LANGUAGE=ru_UA:ru
LC_CTYPE="ru_UA.UTF-8"
LC_NUMERIC="ru_UA.UTF-8"
LC_TIME="ru_UA.UTF-8"
LC_COLLATE="ru_UA.UTF-8"
LC_MONETARY="ru_UA.UTF-8"
LC_MESSAGES="ru_UA.UTF-8"
LC_PAPER="ru_UA.UTF-8"
LC_NAME="ru_UA.UTF-8"
LC_ADDRESS="ru_UA.UTF-8"
LC_TELEPHONE="ru_UA.UTF-8"
LC_MEASUREMENT="ru_UA.UTF-8"
LC_IDENTIFICATION="ru_UA.UTF-8"
LC_ALL=

```

---

### Post by Tikhon on 2006-11-24
My ~/.bashrc had "export PS='something'".
This file not be have export. :\
s/export // - decided this problem

---

### Post by ranfow on 2006-11-24
I also met the some problem:](*,) 

sh ./ZendStudio-5_2_0.bin 
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
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.6857/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory

---

### Post by ranfow on 2006-11-24
Thank you Daniel, I have successful installed, but it can't work, what is the matter?

---

