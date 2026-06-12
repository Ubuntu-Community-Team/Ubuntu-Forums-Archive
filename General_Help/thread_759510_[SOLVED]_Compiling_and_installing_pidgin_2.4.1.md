---
title: "[SOLVED] Compiling and installing pidgin 2.4.1"
date: 2008-04-19
forum: General Help
---

### Post by gillza on 2008-04-19
I downloaded the source. Extracted it. Then my installation procedure as follows 

```

sudo dpkg -r pidgin pidgin-data libpurple0
sudo dpkg --purge pidgin pidgin-data libpurple0
sudo apt-get build-dep pidgin

```

build-essentials - has been installed already
Inside the folder with extracted files:

```
**./configure**
```
```
pidgin 2.4.1

Build GTK+ 2.x UI............. : yes
Build console UI.............. : yes
Build for X11................. : yes

Enable Gestures............... : yes
Protocols to build dynamically : bonjour gg irc jabber msnp9 myspace novell oscar qq sametime simple yahoo zephyr
Protocols to link statically.. :

Build with GStreamer support.. : yes
Build with D-Bus support...... : yes
D-Bus services directory...... : /usr/share/dbus-1/services
Build with NetworkManager..... : no
SSL Library/Libraries......... : Mozilla NSS and GnuTLS
Build with Cyrus SASL support. : no
Use kerberos 4 with zephyr.... : no
Use external libzephyr........ : no
Install pixmaps............... : yes
Install translations.......... : yes
Has you....................... : yes

Use XScreenSaver Extension.... : yes
Use X Session Management...... : yes
Use startup notification...... : yes
Build with GtkSpell support... : yes

Build with plugin support..... : yes
Build with Mono support....... : no
Build with Perl support....... : yes
Build with Tcl support........ : yes
Build with Tk support......... : yes

Print debugging messages...... : no

Pidgin will be installed in /usr/bin.

configure complete, now type 'make'

```
```
**make**
```

```
[B]
checkinstall --install=no[/B]
```
```
======================== Installation successful ==========================
grep: /var/tmp/OgoRfIKTIcKEpZkndSjQX/newfile: No such file or directory

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

NOTE: The package will not be installed

Erasing temporary files...OK

Writing backup package...OK

Deleting temp dir...rm: cannot chdir from `/var/tmp/OgoRfIKTIcKEpZkndSjQX/BACKUP/no-backup/usr/share/pixmaps/pidgin' to `tray': Permission denied
rm: cannot chdir from `/var/tmp/OgoRfIKTIcKEpZkndSjQX/BACKUP/no-backup/usr/share/pixmaps/pidgin' to `toolbar': Permission denied
rm: cannot chdir from `/var/tmp/OgoRfIKTIcKEpZkndSjQX/BACKUP/no-backup/usr/share/pixmaps/pidgin' to `animations': Permission denied
rm: cannot chdir from `/var/tmp/OgoRfIKTIcKEpZkndSjQX/BACKUP/no-backup/usr/share/pixmaps/pidgin' to `protocols': Permission denied
rm: cannot chdir from `/var/tmp/OgoRfIKTIcKEpZkndSjQX/BACKUP/no-backup/usr/share/pixmaps/pidgin' to `status': Permission denied
rm: cannot chdir from `/var/tmp/OgoRfIKTIcKEpZkndSjQX/BACKUP/no-backup/usr/share/pixmaps/pidgin' to `emblems': Permission denied
rm: cannot chdir from `/var/tmp/OgoRfIKTIcKEpZkndSjQX/BACKUP/no-backup/usr/share/pixmaps/pidgin' to `dialogs': Permission denied
rm: cannot chdir from `/var/tmp/OgoRfIKTIcKEpZkndSjQX/BACKUP/no-backup/usr/share' to `icons': Permission denied
rm: cannot chdir from `/var/tmp/OgoRfIKTIcKEpZkndSjQX/META/TRANSL/usr/share/pixmaps/pidgin' to `tray': Permission denied
rm: cannot chdir from `/var/tmp/OgoRfIKTIcKEpZkndSjQX/META/TRANSL/usr/share/pixmaps/pidgin' to `toolbar': Permission denied
rm: cannot chdir from `/var/tmp/OgoRfIKTIcKEpZkndSjQX/META/TRANSL/usr/share/pixmaps/pidgin' to `animations': Permission denied
rm: cannot chdir from `/var/tmp/OgoRfIKTIcKEpZkndSjQX/META/TRANSL/usr/share/pixmaps/pidgin' to `protocols': Permission denied
rm: cannot chdir from `/var/tmp/OgoRfIKTIcKEpZkndSjQX/META/TRANSL/usr/share/pixmaps/pidgin' to `status': Permission denied
rm: cannot chdir from `/var/tmp/OgoRfIKTIcKEpZkndSjQX/META/TRANSL/usr/share/pixmaps/pidgin' to `emblems': Permission denied
rm: cannot chdir from `/var/tmp/OgoRfIKTIcKEpZkndSjQX/META/TRANSL/usr/share/pixmaps/pidgin' to `dialogs': Permission denied
rm: cannot chdir from `/var/tmp/OgoRfIKTIcKEpZkndSjQX/META/TRANSL/usr/share' to `icons': Permission denied
 FAILED!


**********************************************************************

 Done. The new package has been saved to

 /home/igor/Desktop/pidgin-2.4.1/pidgin_2.4.1-1_i386.deb
 You can install it in your system anytime using: 

      dpkg -i pidgin_2.4.1-1_i386.deb

**********************************************************************

```
```
[B]
sudo dpkg -i pidgin_2.4.1-1_i386.deb[/B]
```
```
Selecting previously deselected package pidgin.
(Reading database ... 137499 files and directories currently installed.)
Unpacking pidgin (from pidgin_2.4.1-1_i386.deb) ...
dpkg: pidgin: warning - conffile `etc/gconf' is not a plain file or symlink (= `/etc/gconf')
dpkg: pidgin: warning - conffile `etc/gconf/gconf.xml.defaults' is not a plain file or symlink (= `/etc/gconf/gconf.xml.defaults')
Setting up pidgin (2.4.1-1) ...
dpkg: pidgin: warning - conffile `/etc/gconf' is not a plain file or symlink (= `/etc/gconf')
dpkg: pidgin: warning - conffile `/etc/gconf/gconf.xml.defaults' is not a plain file or symlink (= `/etc/gconf/gconf.xml.defaults')

```

And it is not installed... What am I doing wrong here??? 

Thank you for help.

---

### Post by ryanhaigh on 2008-04-19
I cannot offer much advice on the error message other than to look through this thread for solutions as people in it had the same problem you are having:
[http://ubuntuforums.org/showthread.php?t=613049](http://ubuntuforums.org/showthread.php?t=613049)

Another possibility is to simply use the packages from getdeb.net here [http://getdeb.net/app/Pidgin](http://getdeb.net/app/Pidgin) which worked for me (although I reverted because I didn't like the changes in the latest versions).

---

### Post by gillza on 2008-04-19
I was looking for a topic with a **similar** problem and did not find it. I'll search again. I would like to get this to work instead of simply downloading a binary, since I could successfully compile pidgin on my older computer with 7.10.

---

### Post by ryanhaigh on 2008-04-19
I just googled for "conffile `/etc/gconf' is not a plain file or symlink", there were a couple of results (including this thread) but that thread also had some info. One person suggested ditching checkinstall and another said sudo make was required. There was also something about using prefix /usr or something similar for the configure command I think.

---

### Post by gillza on 2008-04-19
> **ryanhaigh said:**
> I just googled for "conffile `/etc/gconf' is not a plain file or symlink", there were a couple of results (including this thread) but that thread also had some info. One person suggested ditching checkinstall and another said sudo make was required. There was also something about using prefix /usr or something similar for the configure command I think.

hmm just looked through it and missed it. I'll try recompiling with 
```
checkinstall --install=no --exclude=/etc/gconf,/usr/bin,/usr/lib

```

EDIT----------------------------------------------
it compiled, and I installed it.

When I try to run it though:
```
pidgin: error while loading shared libraries: libpurple.so.0: cannot open shared object file: No such file or directory
```

Installing libpurple0 removes pidgin from the system...

---

### Post by mc4man on 2008-04-19
you would need a higher ver. of libpurple0 - 2.4.1 which requires a higher ver. of pidgin-data - 2.4.1 (both installed before pidgin)

---

### Post by TenPlus1 on 2008-04-19
Silly answer, but why not goto [www.getdeb.net](www.getdeb.net) and grab the .deb's for Pidgin 2.4.1 and install it from those (after removing current debs from synaptic)...

Pidgin-Data 1st, then LibPurple then Pidgin main...

---

### Post by gillza on 2008-04-19
I will do it if I won't be able to solve this problem.

P.S. From what I understand libpurple source is included in pidgin source package. So I really can't figure our why it is failing.

---

### Post by gillza on 2008-04-19
Well it seems that I have solved the problem in somewhat a non-trivial way.
After playing around with checkinstall and options I decided to remove any traces of pidgin 2.4.1 on my system
```

sudo dpkg -r pidgin pidgin-data libpurple0
sudo dpkg --purge pidgin pidgin-data libpurple0
```

or you can run 

```
sudo apt-get remove pidgin
``` 

Which should remove pidgin, pidgin-data, and libpurple0 alltogether but will leave config files untoched. 
Option -purge can be used with remove to take care of packages and configs, but I did not try it. 

Then I installed the older version of pidgin (2.2.X) from repositories **and repeated the steps above**. For some reason pidgin would not get removed completely without it. 

Dependencies were installed before, so I did not bother with them.

Next I extracted and recompiled pidgin without the use of checkinstall

```
tar -xvf pidgin-2.4.1.tar.bz2
cd ./pidgin-2.4.1/
./configure && make && sudo make install
```

When I tried to run it I got a following error:
```

pidgin: symbol lookup error: pidgin: undefined symbol: purple_account_get_current_error
```

so I removed **~/.purple** folder and tried again.
got following error:

```
pidgin: error while loading shared libraries: libpurple.so.0: cannot open shared object file: No such file or directory
```

To fix this i ran:
```

sudo ln -s /usr/local/lib/libpurple.so /usr/lib/
sudo ln -s /usr/local/lib/libpurple.so.0 /usr/lib/
```

Tried running pidgin again and it loaded up fine :)

---

### Post by kevdog on 2008-04-20
If you still want to try something I believe your 

./configure

statement should be 

./configure --prefix=/usr

This will avoid the use of symbolic links.  Without this statement the default prefix will be /usr/local.  This is the default for all compiled programs unless otherwise specified on the command line.

---

### Post by gillza on 2008-04-20
Thanks, but since it is working now I'd rather not mess with it until the next version comes out. Also on the pidgin web page in the FAQ section I've found a statement that suggest avoiding installing pidgin in /usr.

---

