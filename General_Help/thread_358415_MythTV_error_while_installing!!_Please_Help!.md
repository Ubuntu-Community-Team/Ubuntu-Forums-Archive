---
title: "MythTV error while installing!! Please Help!"
date: 2007-02-10
forum: General Help
---

### Post by billdotson on 2007-02-10
When I configure the mythtv directory it won't configure correctly

presbp@PresLinux:~/Desktop/mythtv-0.20$ ./configure

 *** WARNING *** 
 Your CPU was not detected properly:
   uname -m: i686
   uname -p: unknown
 model name: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
      flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm

 If you are using a recent CVS checkout, 
 please e-mail the above to [email]mythtv-users@mythtv.org[/email]
 With the subject "configure did not detect my cpu"

cat: /etc/ld.so.conf.d/*.conf: No such file or directory
cat: /etc/ld.so.conf.d/*.conf: No such file or directory
cat: /etc/ld.so.conf.d/*.conf: No such file or directory
cat: /etc/ld.so.conf.d/*.conf: No such file or directory
cat: /etc/ld.so.conf.d/*.conf: No such file or directory
cat: /etc/ld.so.conf.d/*.conf: No such file or directory
cat: /etc/ld.so.conf.d/*.conf: No such file or directory
# Basic Settings
Compile type     release
Compiler cache   no
DistCC           no
Install prefix   /usr/local
CPU              x86 (model name        : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz)
Big Endian       no
MMX enabled      yes

# Input Support
Joystick menu    yes
lirc support     no
Apple Remote     no
Video4Linux sup. yes
ivtv support     yes
FireWire support no
DVB support      no [/usr/include]
DBox2 support    yes
HDHomeRun sup.   yes
CRC Ip Rec sup.  yes
FreeBox support  yes

# Sound Output Support
OSS support      yes
ALSA support     no
aRts support     no
JACK support     no
DTS passthrough  no

# Video Output Support
x11 support      yes
xrandr support   yes
xv support       yes
XvMC support     no
XvMC VLD support no
XvMC pro support no
XvMC OpenGL sup. no
Mac accel.       no
OpenGL vsync     no
DirectFB         no

# Misc Features
Frontend         yes
Backend          yes

# Bindings
bindings_perl    no
Creating libs/libmyth/mythconfig.h and libs/libmyth/mythconfig.mak

libs/libmyth/mythconfig.h is unchanged
./configure: 3499: qmake: not found
presbp@PresLinux:~/Desktop/mythtv-0.20$ make
make: *** No targets specified and no makefile found.  Stop.

That is what is going on in the terminal.  Please help.

---

### Post by PilotJLR on 2007-02-10
Why do you want to install this from source???

Unless you have a compelling reason to do so, then just enable universe repo and do a "sudo apt-get install mythtv".
Version .20 is available from the repos now.

---

### Post by billdotson on 2007-02-10
same thing happens then also.  I think what is happening is when it tries to install MythTV-database it is encountering an error such as it cannot access mysql to make a database.

---

### Post by PilotJLR on 2007-02-10
What error do you receive when installing MythTV with apt-get? 

The output from the first post is specific to generating a Makefile; I have never seen that with apt-get.

You will, when using apt-get, need to specify the root password for mysql (just press enter if it's blank, or if apt-get installed mysql for you). Do not using Synaptic package manager... apt-get at the command line!

---

### Post by billdotson on 2007-02-10
presbp@PresLinux:~$ sudo apt-get install mythtv
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libwxgtk2.6-0 libwxbase2.6-0 python-wxversion python-wxgtk2.6
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libdbd-mysql-perl libmyth-0.20 mysql-client mysql-client-5.0 mythtv-backend
  mythtv-common mythtv-database mythtv-frontend
Suggested packages:
  mythweb mythmusic mythweather mythgallery mythdvd mythvideo mythgame
Recommended packages:
  mythtv-doc mythtv-themes xmltv-util mysql-server
The following NEW packages will be installed:
  libdbd-mysql-perl libmyth-0.20 mysql-client mysql-client-5.0 mythtv
  mythtv-backend mythtv-common mythtv-database mythtv-frontend
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/21.6MB of archives.
After unpacking 54.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package libdbd-mysql-perl.
(Reading database ... 160541 files and directories currently installed.)
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_3.0006-1_i386.deb) ...
Selecting previously deselected package libmyth-0.20.
Unpacking libmyth-0.20 (from .../libmyth-0.20_0.20-0.2ubuntu2_i386.deb) ...
Selecting previously deselected package mysql-client-5.0.
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.0.24a-9_i386.deb) ...
Selecting previously deselected package mysql-client.
Unpacking mysql-client (from .../mysql-client_5.0.24a-9_all.deb) ...
Selecting previously deselected package mythtv-common.
Unpacking mythtv-common (from .../mythtv-common_0.20-0.2ubuntu2_all.deb) ...
Selecting previously deselected package mythtv-database.
Unpacking mythtv-database (from .../mythtv-database_0.20-0.2ubuntu2_all.deb) ...
Selecting previously deselected package mythtv-frontend.
Unpacking mythtv-frontend (from .../mythtv-frontend_0.20-0.2ubuntu2_i386.deb) ...
Selecting previously deselected package mythtv-backend.
Unpacking mythtv-backend (from .../mythtv-backend_0.20-0.2ubuntu2_i386.deb) ...
Selecting previously deselected package mythtv.
Unpacking mythtv (from .../mythtv_0.20-0.2ubuntu2_all.deb) ...
Setting up libdbd-mysql-perl (3.0006-1) ...
Setting up libmyth-0.20 (0.20-0.2ubuntu2) ...

Setting up mysql-client-5.0 (5.0.24a-9) ...
Setting up mysql-client (5.0.24a-9) ...
Setting up mythtv-common (0.20-0.2ubuntu2) ...

Setting up mythtv-database (0.20-0.2ubuntu2) ...
Failed to connect to database: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
Setting up mythtv-frontend (0.20-0.2ubuntu2) ...

Setting up mythtv-backend (0.20-0.2ubuntu2) ...
udev active, devices will be created in /dev/.static/dev/
Starting MythTV server: mythbackendSession management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
.

dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.20-0.2ubuntu2); however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-database
 mythtv
E: Sub-process /usr/bin/dpkg returned an error code (1)

As you can see no success with apt-get either

---

### Post by PilotJLR on 2007-02-11
Ok, I see... try this:

```

sudo apt-get update
sudo apt-get install mysql-server
sudo apt-get install mythtv mythtv-themes

```

Please use that order, and don't combine the last two commands!

---

