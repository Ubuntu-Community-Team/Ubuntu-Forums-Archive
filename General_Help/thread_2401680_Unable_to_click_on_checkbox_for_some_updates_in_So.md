---
title: "Unable to click on checkbox for some updates in Software Updater (Ubuntu 18.04)"
date: 2018-09-21
forum: General Help
---

### Post by charles75 on 2018-09-21
Hi,

I've recently upgraded to Ubuntu 18.04 and noticed that some updates won't allow check box to be ticked.

One example is GNU Debugger. 

There's a 2.9MB update but it's unchecked.

Is this a bug in Software Updater?

Thanks in advance for any help.

---

### Post by coffeecat on 2018-09-21
Support, not chat.

Thread moved to *General Help*.

---

### Post by &amp;KyT$0P# on 2018-09-21
Please post the output from running these commands in Terminal -
```
sudo apt-get update
apt-get -s dist-upgrade
```

---

### Post by charles75 on 2018-09-26
I've attached the output as advised.

Thanks

---

### Post by &amp;KyT$0P# on 2018-09-27
[s]It looks OK to me.  Does your Software Updater still have this issue?[/s]

---

### Post by charles75 on 2018-09-28
Yes the software updater still shows issues in not allowing checkbox selection.
I performed an upgrade from 16.04.
Maybe I should do a clean install.
These are the updates showing the issue.
GNU Debugger - 2.9MB
Application plugin library - 58kB
Application plugin library (introspection files) - 6kB

Thanks for your help.

---

### Post by westie457 on 2018-09-28
What is the output of ```
sudo apt-get upgrade
sudo apt-get -s dist-upgrade
```

---

### Post by &amp;KyT$0P# on 2018-09-28
#-o Sorry, I was very tired when reading the output and missed these lines -
```
The following packages have been kept back:
  gdb gir1.2-peas-1.0 libpeas-1.0-0
```

Could you please post the output of -
```
apt-cache policy gdb gir1.2-peas-1.0 libpeas-1.0-0
```

(It's easier for us to read the output if you copy+paste it in your post, wrapped in code tags, i.e. prefix it with [noparse]```
 and add 
``` at the end[/noparse].)

---

### Post by charles75 on 2018-09-29
Thanks for replying @halogen2.


```

apt-cache policy gdb gir1.2-peas-1.0 libpeas-1.0-0
gdb:
  Installed: 7.11.1-0ubuntu1~16.5
  Candidate: 8.1-0ubuntu3
  Version table:
     8.1-0ubuntu3 500
        500 http://mirror.sov.uk.goscomb.net/ubuntu bionic/main amd64 Packages
 *** 7.11.1-0ubuntu1~16.5 100
        100 /var/lib/dpkg/status
gir1.2-peas-1.0:
  Installed: 1.16.0-1ubuntu2
  Candidate: 1.22.0-2
  Version table:
     1.22.0-2 500
        500 http://mirror.sov.uk.goscomb.net/ubuntu bionic/main amd64 Packages
 *** 1.16.0-1ubuntu2 100
        100 /var/lib/dpkg/status
libpeas-1.0-0:
  Installed: 1.16.0-1ubuntu2
  Candidate: 1.22.0-2
  Version table:
     1.22.0-2 500
        500 http://mirror.sov.uk.goscomb.net/ubuntu bionic/main amd64 Packages
 *** 1.16.0-1ubuntu2 100
        100 /var/lib/dpkg/status

```

---

### Post by &amp;KyT$0P# on 2018-09-29
Looks like you have the 16.04 versions of those packages installed.

Could you please post the output of this command? -
```
apt-get -s install gdb/bionic gir1.2-peas-1.0/bionic libpeas-1.0-0/bionic
```

---

### Post by charles75 on 2018-09-29
apt-get -s install gdb/bionic gir1.2-peas-1.0/bionic libpeas-1.0-0/bionic
```

NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Selected version '8.1-0ubuntu3' (Ubuntu:18.04/bionic [amd64]) for 'gdb'
Selected version '3.6.6-1~18.04' (Ubuntu:18.04/bionic-updates [amd64]) for 'libpython3.6' because of 'gdb'
Selected version '3.6.6-1~18.04' (Ubuntu:18.04/bionic-updates [amd64]) for 'libpython3.6-stdlib' because of 'libpython3.6'
Selected version '3.6.6-1~18.04' (Ubuntu:18.04/bionic-updates [amd64]) for 'libpython3.6-minimal' because of 'libpython3.6-stdlib'
Selected version '1.22.0-2' (Ubuntu:18.04/bionic [amd64]) for 'gir1.2-peas-1.0'
Selected version '1.22.0-2' (Ubuntu:18.04/bionic [amd64]) for 'libpeas-1.0-0' because of 'gir1.2-peas-1.0'
Selected version '1.22.0-2' (Ubuntu:18.04/bionic [amd64]) for 'libpeas-1.0-0'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gdb : Depends: libpython3.6 (>= 3.6.4~rc1) but it is not going to be installed
 libpeas-1.0-0 : Depends: libpython3.6 (>= 3.6.4~rc1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by &amp;KyT$0P# on 2018-10-05
What about this one? -
```
apt-get -s install gdb/bionic gir1.2-peas-1.0/bionic libpeas-1.0-0/bionic libpython3.6/bionic
```

---

### Post by charles75 on 2018-10-06
I think something broke during the upgrade.
May have to re-install from scratch.

```

apt-get -s install gdb/bionic gir1.2-peas-1.0/bionic libpeas-1.0-0/bionic libpython3.6/bionic
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Selected version '8.1-0ubuntu3' (Ubuntu:18.04/bionic [amd64]) for 'gdb'
Selected version '3.6.6-1~18.04' (Ubuntu:18.04/bionic-updates [amd64]) for 'libpython3.6' because of 'gdb'
Selected version '3.6.6-1~18.04' (Ubuntu:18.04/bionic-updates [amd64]) for 'libpython3.6-stdlib' because of 'libpython3.6'
Selected version '3.6.6-1~18.04' (Ubuntu:18.04/bionic-updates [amd64]) for 'libpython3.6-minimal' because of 'libpython3.6-stdlib'
Selected version '1.22.0-2' (Ubuntu:18.04/bionic [amd64]) for 'gir1.2-peas-1.0'
Selected version '1.22.0-2' (Ubuntu:18.04/bionic [amd64]) for 'libpeas-1.0-0'
Selected version '3.6.6-1~18.04' (Ubuntu:18.04/bionic-updates [amd64]) for 'libpython3.6'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libpython3.6 : Depends: libpython3.6-stdlib (= 3.6.6-1~18.04) but 3.6.6-1+xenial1 is to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by &amp;KyT$0P# on 2018-10-06
I think your 16.04 had a PPA providing newer Python 3 versions, and that PPA didn't get fully disabled before you upgraded to 18.04.  A clean reinstall of 18.04 would definitely fix that, but I'm not sure yet whether it's necessary.

Please post the output from this command -
```
apt-get -s install gdb/bionic gir1.2-peas-1.0/bionic libpeas-1.0-0/bionic python3.6/bionic python3.6-minimal/bionic libpython3.6/bionic libpython3.6-minimal/bionic libpython3.6-stdlib/bionic
```

---

### Post by charles75 on 2018-10-07
```

apt-get -s install gdb/bionic gir1.2-peas-1.0/bionic libpeas-1.0-0/bionic python3.6/bionic python3.6-minimal/bionic libpython3.6/bionic libpython3.6-minimal/bionic libpython3.6-stdlib/bionic
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Selected version '8.1-0ubuntu3' (Ubuntu:18.04/bionic [amd64]) for 'gdb'
Selected version '1.22.0-2' (Ubuntu:18.04/bionic [amd64]) for 'gir1.2-peas-1.0'
Selected version '1.22.0-2' (Ubuntu:18.04/bionic [amd64]) for 'libpeas-1.0-0'
Selected version '3.6.6-1~18.04' (Ubuntu:18.04/bionic-updates [amd64]) for 'python3.6'
Selected version '3.6.6-1~18.04' (Ubuntu:18.04/bionic-updates [amd64]) for 'python3.6-minimal'
Selected version '3.6.6-1~18.04' (Ubuntu:18.04/bionic-updates [amd64]) for 'libpython3.6'
Selected version '3.6.6-1~18.04' (Ubuntu:18.04/bionic-updates [amd64]) for 'libpython3.6-minimal'
Selected version '3.6.6-1~18.04' (Ubuntu:18.04/bionic-updates [amd64]) for 'libpython3.6-stdlib'
The following packages were automatically installed and are no longer required:
  evolution-data-server-online-accounts fonts-stix gnome-todo-common hwdata
  libapparmor-perl libapr1 libaprutil1 libaprutil1-dbd-mysql libaprutil1-ldap
  libasprintf0v5 libbabeltrace-ctf1 libbonoboui2-common libboost-system1.58.0
  libcdio-cdda1 libcdio13 libcgmanager0 libevent-2.0-5 libfcitx-gclient0
  libglade2-0 libglew1.13 libgmime-2.6-0 libgnome-desktop-3-12
  libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-common libgtkmm-2.4-1v5
  libgtop-2.0-10 libhud2 libhunspell-1.3-0 libical1a libkeybinder0 libllvm3.8
  libllvm5.0 liblwres141 libmirprotobuf3 libmysqlclient20 libnih-dbus1
  libnm-gtk-common liborbit-2-0 libpackagekit-glib2-16 libprotobuf-lite10
  libprotobuf9v5 libpython3.5 libqmi-glib1 libqt5multimedia5 libqt5opengl5
  libqt5organizer5 libqt5printsupport5 libqt5sensors5 libqt5test5
  libreoffice-gtk libreoffice-gtk2 librhythmbox-core9 libsignon-extension1
  libsignon-qt5-1 libssl-dev libsuitesparseconfig4.4.6 libvpx3 libvte-common
  libvte9 libwebp5 libwebrtc-audio-processing-0 libwebsockets7 libwinpr-crt0.1
  libwinpr-file0.1 libwinpr-interlocked0.1 libwinpr-library0.1
  libwinpr-registry0.1 libwinpr-sysinfo0.1 libx86-1 libxapian22v5 mysql-common
  python-gobject python-gobject-2 python-gtk2 python-keybinder python-notify
  python-vte python3-guacamole python3-pycurl python3-pyparsing
  python3-xlsxwriter rename snap-confine tcpd ubuntu-mobile-icons
  ubuntu-ui-toolkit-theme
Use 'apt autoremove' to remove them.
Suggested packages:
  gdb-doc python3.6-venv python3.6-doc binfmt-support
The following NEW packages will be installed:
  libpython3.6
The following packages will be upgraded:
  gdb gir1.2-peas-1.0 libpeas-1.0-0
The following packages will be DOWNGRADED:
  libpython3.6-minimal libpython3.6-stdlib python3.6 python3.6-minimal
3 upgraded, 1 newly installed, 4 downgraded, 0 to remove and 0 not upgraded.
Inst python3.6 [3.6.6-1+xenial1] (3.6.6-1~18.04 Ubuntu:18.04/bionic-updates [amd64]) []
Inst libpython3.6-stdlib [3.6.6-1+xenial1] (3.6.6-1~18.04 Ubuntu:18.04/bionic-updates [amd64]) []
Inst python3.6-minimal [3.6.6-1+xenial1] (3.6.6-1~18.04 Ubuntu:18.04/bionic-updates [amd64]) []
Inst libpython3.6-minimal [3.6.6-1+xenial1] (3.6.6-1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Inst libpython3.6 (3.6.6-1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Inst gdb [7.11.1-0ubuntu1~16.5] (8.1-0ubuntu3 Ubuntu:18.04/bionic [amd64])
Inst libpeas-1.0-0 [1.16.0-1ubuntu2] (1.22.0-2 Ubuntu:18.04/bionic [amd64])
Inst gir1.2-peas-1.0 [1.16.0-1ubuntu2] (1.22.0-2 Ubuntu:18.04/bionic [amd64])
Conf python3.6 (3.6.6-1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf libpython3.6-stdlib (3.6.6-1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf python3.6-minimal (3.6.6-1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf libpython3.6-minimal (3.6.6-1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf libpython3.6 (3.6.6-1~18.04 Ubuntu:18.04/bionic-updates [amd64])
Conf gdb (8.1-0ubuntu3 Ubuntu:18.04/bionic [amd64])
Conf libpeas-1.0-0 (1.22.0-2 Ubuntu:18.04/bionic [amd64])
Conf gir1.2-peas-1.0 (1.22.0-2 Ubuntu:18.04/bionic [amd64])

```

---

### Post by &amp;KyT$0P# on 2018-10-07
That output looks good.  Try this command to actually apply the change, does it clear up the issue? -
```
sudo apt-get install gdb/bionic gir1.2-peas-1.0/bionic libpeas-1.0-0/bionic python3.6/bionic python3.6-minimal/bionic libpython3.6/bionic libpython3.6-minimal/bionic libpython3.6-stdlib/bionic
```

---

### Post by charles75 on 2018-10-09
Typed the command and no longer see GNU debugger at all in Software Updater.
Will check again when there's an update to see if GNU appears.
Thanks for your help.

---

### Post by &amp;KyT$0P# on 2018-10-09
> **charles75 said:**
> Typed the command and no longer see GNU debugger at all in Software Updater.
That's expected.  The command should have installed the gdb update.

> Thanks for your help.
You're welcome.

---

