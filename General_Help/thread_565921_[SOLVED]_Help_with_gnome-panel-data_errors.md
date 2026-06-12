---
title: "[SOLVED] Help with gnome-panel-data errors"
date: 2007-10-02
forum: General Help
---

### Post by Poene on 2007-10-02
```

peter@peter-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up gnome-panel-data (2.18.1-0ubuntu3.1) ...
/usr/share/gconf/schemas/panel-object.schemas:637: parser error : ParsePI: PI long space expected
&#65533;&#65533;&#2330;&#2381;&#2330; &#2340;&#2361;&#2325;&#2379; &#2346;&#2381;&#2351;&#2366;&#2344;&#2354;&#2325;&#2379; &#2346;&#2352;&#2367;&#2330;&#2366;&#2351;&#2325;&#2404;<?long
                                                                               ^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : ParsePI: PI long never end ...

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag long line 637

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag locale line 635

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag schema line 398

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag schemalist line 4

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag gconfschemafile line 2

^
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 1:2.18.1-0ubuntu3.1); however:
  Package gnome-panel-data is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-panel-data
 gnome-panel
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

I get an error code 1.  Is there a way I can fix this?

System Specs:
Ubuntu AMD64 7.04
AMD Athlon Athlon 64 4600+
2GB DDR RAM
250 GB Seagate HDD IDE Master
200 GB Maxtor HDD IDE Slave
200 GB Maxtor HDD SATA Master
ECS Motherboard
ATI X1950 PRO

---

### Post by Poene on 2007-10-02
Now I get this error when doing it.
```
 peter@peter-desktop:~/Desktop$ sudo apt-get update
Get:1 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Get:2 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release
Get:4 http://security.ubuntu.com feisty-security Release [50.9kB]   
Hit http://us.archive.ubuntu.com feisty-updates Release                 
Hit http://us.archive.ubuntu.com feisty/main Packages                    
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources  
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Get:5 http://security.ubuntu.com feisty-security/main Packages [78.8kB]
Get:6 http://security.ubuntu.com feisty-security/restricted Packages [5992B]
Get:7 http://security.ubuntu.com feisty-security/main Sources [14.2kB]
Get:8 http://security.ubuntu.com feisty-security/restricted Sources [953B]
Get:9 http://security.ubuntu.com feisty-security/universe Packages [36.2kB]
Get:10 http://security.ubuntu.com feisty-security/universe Sources [5036B]
Get:11 http://security.ubuntu.com feisty-security/multiverse Packages [5412B]
Get:12 http://security.ubuntu.com feisty-security/multiverse Sources [1052B]
Fetched 199kB in 2s (82.3kB/s)  
Reading package lists... Done
peter@peter-desktop:~/Desktop$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/available' near line 14910 package `libsasl2-modules':
 `Suggests' field, invalid package name `libsasl2-modules-gssapi=mit': character `=' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)
peter@peter-desktop:~/Desktop$ 

```

Help please!

---

### Post by p_quarles on 2007-10-02
Try this:
```
sudo apt-get autoremove --purge
```
then
```
sudo apt-get update
```
and then
```
sudo apt-get install -f
```
I'm not saying this will fix anything, but if you post whatever errors you get it might be a clue to the problem.

---

### Post by Poene on 2007-10-02
I tried the steps you recommended and this is my terminal.

```

peter@peter-desktop:~$ sudo apt-get autoremove --purge
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
dpkg: parse error, in file `/var/lib/dpkg/available' near line 14910 package `libsasl2-modules':
 `Suggests' field, invalid package name `libsasl2-modules-gssapi=mit': character `=' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)
peter@peter-desktop:~$ sudo apt-get update
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Get:2 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Hit http://us.archive.ubuntu.com feisty Release
Hit http://security.ubuntu.com feisty-security/main Packages        
Hit http://us.archive.ubuntu.com feisty-updates Release
Hit http://security.ubuntu.com feisty-security/restricted Packages  
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
peter@peter-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
dpkg: parse error, in file `/var/lib/dpkg/available' near line 14910 package `libsasl2-modules':
 `Suggests' field, invalid package name `libsasl2-modules-gssapi=mit': character `=' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by p_quarles on 2007-10-02
Cool. I think I know what the problem is. Try this:
```
gksudo gedit /var/lib/dpkg/available
```
Use the "go to line" tool to move forward to line 14910 and change
```
libsasl2-modules-gssapi=mit
```
to
```
libsasl2-modules-gssapi-mit
```
I'm crossing my fingers, but I *think* that will fix the problem. I just looked at my own packages-available cache, and the latter is the correct name of that package.

---

### Post by Poene on 2007-10-02
Okay. That got rid of the line error. Now I'm back to stage one again with the gnome-panel-data error code (1).

```
 peter@peter-desktop:~$ gksudo gedit /var/lib/dpkg/available
peter@peter-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up libbeecrypt6 (4.1.2-6build1) ...

Setting up librpm4 (4.4.1-14build1) ...

Setting up rpm (4.4.1-14build1) ...

Setting up alien (8.65) ...
Setting up gnome-panel-data (2.18.1-0ubuntu3.1) ...
/usr/share/gconf/schemas/panel-object.schemas:637: parser error : ParsePI: PI long space expected
&#65533;&#65533;&#2330;&#2381;&#2330; &#2340;&#2361;&#2325;&#2379; &#2346;&#2381;&#2351;&#2366;&#2344;&#2354;&#2325;&#2379; &#2346;&#2352;&#2367;&#2330;&#2366;&#2351;&#2325;&#2404;<?long
                                                                               ^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : ParsePI: PI long never end ...

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag long line 637

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag locale line 635

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag schema line 398

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag schemalist line 4

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag gconfschemafile line 2

^
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 1:2.18.1-0ubuntu3.1); however:
  Package gnome-panel-data is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
Setting up libpng3 (1.2.15~beta5-1ubuntu1) ...
Setting up libxml1 (1.8.17-14build1) ...

Errors were encountered while processing:
 gnome-panel-data
 gnome-panel
E: Sub-process /usr/bin/dpkg returned an error code (1)
peter@peter-desktop:~$ 

```

I appreciate the help btw!

---

### Post by p_quarles on 2007-10-02
No problem. Happy to help when I can.

Anyway: always run "apt-get update" before doing an upgrade. So, first, try running those two commands again, and if that doesn't work, give this one another try:
```
sudo apt-get install -f
```
If *that* doesn't work, try:
```
sudo dpkg -C
```
and post the results here.

---

### Post by Poene on 2007-10-02
Here is my terminal output:

```
 peter@peter-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up gnome-panel-data (2.18.1-0ubuntu3.1) ...
/usr/share/gconf/schemas/panel-object.schemas:637: parser error : ParsePI: PI long space expected
&#65533;&#65533;&#2330;&#2381;&#2330; &#2340;&#2361;&#2325;&#2379; &#2346;&#2381;&#2351;&#2366;&#2344;&#2354;&#2325;&#2379; &#2346;&#2352;&#2367;&#2330;&#2366;&#2351;&#2325;&#2404;<?long
                                                                               ^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : ParsePI: PI long never end ...

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag long line 637

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag locale line 635

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag schema line 398

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag schemalist line 4

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag gconfschemafile line 2

^
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 1:2.18.1-0ubuntu3.1); however:
  Package gnome-panel-data is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-panel-data
 gnome-panel
E: Sub-process /usr/bin/dpkg returned an error code (1)
peter@peter-desktop:~$ sudo dpkg -C
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 gnome-panel          launcher and docking facility for GNOME 2

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 gnome-panel-data     common files for GNOME 2 panel

peter@peter-desktop:~$ 

```

---

### Post by Poene on 2007-10-02
sudo apt-get update
sudo apt-get upgrade

have the same error

---

### Post by p_quarles on 2007-10-02
Okay, run the following two commands:
```
sudo dpkg --configure gnome-panel
sudo dpkg --configure gnome-panel-data
```
Again, post any errors back here.

---

### Post by Poene on 2007-10-02
Terminal Output:

```

peter@peter-desktop:~$ sudo dpkg --configure gnome-panel
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 1:2.18.1-0ubuntu3.1); however:
  Package gnome-panel-data is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-panel
peter@peter-desktop:~$ sudo dpkg --configure gnome-panel-data
Setting up gnome-panel-data (2.18.1-0ubuntu3.1) ...
Failed to load file "/var/lib/gconf/defaults/%gconf-tree-en_GB.xml": Error on line 1009 char 80: Element 'losal_schema' was closed, but the currently open element is 'local_schema'
Failed to load file "/var/lib/gconf/defaults/%gconf-tree-az.xml": Line 1598 character 1: Attribute "short_dusc" is invalid on <local_schema> element in this context
/usr/share/gconf/schemas/panel-object.schemas:637: parser error : ParsePI: PI long space expected
&#65533;&#65533;&#2330;&#2381;&#2330; &#2340;&#2361;&#2325;&#2379; &#2346;&#2381;&#2351;&#2366;&#2344;&#2354;&#2325;&#2379; &#2346;&#2352;&#2367;&#2330;&#2366;&#2351;&#2325;&#2404;<?long
                                                                               ^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : ParsePI: PI long never end ...

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag long line 637

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag locale line 635

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag schema line 398

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag schemalist line 4

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag gconfschemafile line 2

^
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gnome-panel-data
peter@peter-desktop:~$ 

```

---

### Post by p_quarles on 2007-10-02
Boy, this one just isn't going down without a fight. Sigh.

First off, try this:
```
sudo apt-get build-dep gnome-panel
```
and then run the dpkg commands again. I don't think that will work, but it's worth a try because it's simpler than the next step.

Which is:
```
gksudo gedit /usr/share/gconf/schemas/panel-object.schemas
```
Then, go to the line numbers mentioned in the error message and look for any differences as to how they are formatted vs. how nearby lines are formatted. (btw, I don't use Gnome, so I'm kinda working blind here; it's possible that those numbers don't refer to lines).

---

### Post by Poene on 2007-10-02
Terminal Output:

```

 [747kB]
Get:61 http://us.archive.ubuntu.com feisty/main libglade2-dev 1:2.6.0-3 [134kB]
Get:62 http://us.archive.ubuntu.com feisty/main libgconf2-dev 2.18.0.1-0ubuntu1 [288kB]
Get:63 http://us.archive.ubuntu.com feisty/main libgpg-error-dev 1.4-2build1 [34.4kB]
Get:64 http://us.archive.ubuntu.com feisty/main libgcrypt11-dev 1.2.3-2build1 [245kB]
Get:65 http://us.archive.ubuntu.com feisty/main libtasn1-3-dev 0.3.6-2build1 [314kB]
Get:66 http://us.archive.ubuntu.com feisty/main libopencdk8-dev 0.5.9-2build1 [135kB]
Get:67 http://us.archive.ubuntu.com feisty/main liblzo-dev 1.08-3 [109kB]      
Get:68 http://us.archive.ubuntu.com feisty/main libgnutls-dev 1.4.4-3build1 [393kB]
Get:69 http://us.archive.ubuntu.com feisty/main libsepol1-dev 1.14-2build1 [581kB]
Get:70 http://us.archive.ubuntu.com feisty/main libselinux1-dev 1.32-3ubuntu1 [224kB]
Get:71 http://us.archive.ubuntu.com feisty/main libgnomevfs2-dev 1:2.18.1-0ubuntu1 [568kB]
Get:72 http://us.archive.ubuntu.com feisty/main libesd0-dev 0.2.36-3ubuntu4 [26.6kB]
Get:73 http://us.archive.ubuntu.com feisty/main libgnome2-dev 2.18.0-0ubuntu1 [119kB]
Get:74 http://us.archive.ubuntu.com feisty/main libbonoboui2-dev 2.18.0-0ubuntu1 [330kB]
Get:75 http://us.archive.ubuntu.com feisty/main libdbus-glib-1-dev 0.73-1 [186kB]
Get:76 http://us.archive.ubuntu.com feisty/main libgnome-keyring-dev 0.8.1-0ubuntu1 [58.2kB]
Get:77 http://us.archive.ubuntu.com feisty/main libjpeg62-dev 6b-13 [195kB]    
Get:78 http://us.archive.ubuntu.com feisty/main libgnomeui-dev 2.17.92-0ubuntu1 [475kB]
Get:79 http://us.archive.ubuntu.com feisty/main libstartup-notification0-dev 0.9-1 [26.9kB]
Get:80 http://us.archive.ubuntu.com feisty/main libgnome-desktop-dev 1:2.18.1-0ubuntu1 [86.7kB]
Get:81 http://us.archive.ubuntu.com feisty/main libgnome-menu-dev 2.18.0-0ubuntu3 [80.8kB]
Get:82 http://us.archive.ubuntu.com feisty/main liblaunchpad-integration-dev 0.1.13 [10.5kB]
Get:83 http://us.archive.ubuntu.com feisty/main liblpint-bonobo-dev 0.1.13 [8560B]
Get:84 http://us.archive.ubuntu.com feisty/main libwnck-dev 2.18.0-0ubuntu1 [192kB]
Get:85 http://us.archive.ubuntu.com feisty/main libxmu-dev 2:1.0.2-1ubuntu2 [58.3kB]
Get:86 http://us.archive.ubuntu.com feisty/main patchutils 0.2.31-3 [102kB]    
Get:87 http://us.archive.ubuntu.com feisty/main sharutils 1:4.2.1-15 [114kB]   
Fetched 26.9MB in 2m44s (163kB/s)                                              
Extracting templates from packages: 100%
Selecting previously deselected package x11proto-core-dev.
(Reading database ... 107213 files and directories currently installed.)
Unpacking x11proto-core-dev (from .../x11proto-core-dev_7.0.10-1_all.deb) ...
Selecting previously deselected package libice-dev.
Unpacking libice-dev (from .../libice-dev_2%3a1.0.3-1build1_amd64.deb) ...
Selecting previously deselected package libsm-dev.
Unpacking libsm-dev (from .../libsm-dev_2%3a1.0.2-1build1_amd64.deb) ...
Selecting previously deselected package libxau-dev.
Unpacking libxau-dev (from .../libxau-dev_1%3a1.0.3-1_amd64.deb) ...
Selecting previously deselected package libxdmcp-dev.
Unpacking libxdmcp-dev (from .../libxdmcp-dev_1%3a1.0.2-1_amd64.deb) ...
Selecting previously deselected package x11proto-input-dev.
Unpacking x11proto-input-dev (from .../x11proto-input-dev_1.4.1-1_all.deb) ...
Selecting previously deselected package x11proto-kb-dev.
Unpacking x11proto-kb-dev (from .../x11proto-kb-dev_1.0.3-2ubuntu1_all.deb) ...
Selecting previously deselected package xtrans-dev.
Unpacking xtrans-dev (from .../xtrans-dev_1.0.3-1_all.deb) ...
Selecting previously deselected package libx11-dev.
Unpacking libx11-dev (from .../libx11-dev_2%3a1.1.1-1ubuntu3_amd64.deb) ...
Selecting previously deselected package x11proto-render-dev.
Unpacking x11proto-render-dev (from .../x11proto-render-dev_2%3a0.9.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxrender-dev.
Unpacking libxrender-dev (from .../libxrender-dev_1%3a0.9.1-3_amd64.deb) ...
Selecting previously deselected package x11proto-xext-dev.
Unpacking x11proto-xext-dev (from .../x11proto-xext-dev_7.0.2-5ubuntu1_all.deb) ...
Selecting previously deselected package x11proto-fixes-dev.
Unpacking x11proto-fixes-dev (from .../x11proto-fixes-dev_1%3a4.0-0.1ubuntu2_all.deb) ...
Selecting previously deselected package libxfixes-dev.
Unpacking libxfixes-dev (from .../libxfixes-dev_1%3a4.0.3-1_amd64.deb) ...
Selecting previously deselected package libxcursor-dev.
Unpacking libxcursor-dev (from .../libxcursor-dev_1%3a1.1.8-1_amd64.deb) ...
Selecting previously deselected package libxext-dev.
Unpacking libxext-dev (from .../libxext-dev_2%3a1.0.3-1build1_amd64.deb) ...
Selecting previously deselected package libexpat1-dev.
Unpacking libexpat1-dev (from .../libexpat1-dev_1.95.8-3.4build1_amd64.deb) ...
Selecting previously deselected package zlib1g-dev.
Unpacking zlib1g-dev (from .../zlib1g-dev_1%3a1.2.3-13ubuntu4_amd64.deb) ...
Selecting previously deselected package libfreetype6-dev.
Unpacking libfreetype6-dev (from .../libfreetype6-dev_2.2.1-5ubuntu1.1_amd64.deb) ...
Selecting previously deselected package libfontconfig1-dev.
Unpacking libfontconfig1-dev (from .../libfontconfig1-dev_2.4.2-1ubuntu1_amd64.deb) ...
Selecting previously deselected package libxft-dev.
Unpacking libxft-dev (from .../libxft-dev_2.1.12-1_amd64.deb) ...
Selecting previously deselected package libxi-dev.
Unpacking libxi-dev (from .../libxi-dev_2%3a1.1.0-1build1_amd64.deb) ...
Selecting previously deselected package x11proto-xinerama-dev.
Unpacking x11proto-xinerama-dev (from .../x11proto-xinerama-dev_1.1.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxinerama-dev.
Unpacking libxinerama-dev (from .../libxinerama-dev_2%3a1.0.1-4build1_amd64.deb) ...
Selecting previously deselected package libxmu-headers.
Unpacking libxmu-headers (from .../libxmu-headers_2%3a1.0.2-1ubuntu2_all.deb) ...
Selecting previously deselected package x11proto-randr-dev.
Unpacking x11proto-randr-dev (from .../x11proto-randr-dev_1.2.1-1_all.deb) ...
Selecting previously deselected package libxrandr-dev.
Unpacking libxrandr-dev (from .../libxrandr-dev_2%3a1.2.0-3ubuntu1_amd64.deb) ...
Selecting previously deselected package x11proto-resource-dev.
Unpacking x11proto-resource-dev (from .../x11proto-resource-dev_1.0.2-4ubuntu1_all.deb) ...
Selecting previously deselected package libxres-dev.
Unpacking libxres-dev (from .../libxres-dev_2%3a1.0.1-2_amd64.deb) ...
Selecting previously deselected package libxt-dev.
Unpacking libxt-dev (from .../libxt-dev_1%3a1.0.5-1_amd64.deb) ...
Selecting previously deselected package m4.
Unpacking m4 (from .../m4_1.4.8-1build1_amd64.deb) ...
Selecting previously deselected package autoconf.
Unpacking autoconf (from .../autoconf_2.61-3_all.deb) ...
Selecting previously deselected package autotools-dev.
Unpacking autotools-dev (from .../autotools-dev_20060920.1_all.deb) ...
Selecting previously deselected package automake1.7.
Unpacking automake1.7 (from .../automake1.7_1.7.9-9_all.deb) ...
Selecting previously deselected package cdbs.
Unpacking cdbs (from .../cdbs_0.4.48ubuntu1_all.deb) ...
Selecting previously deselected package gnome-pkg-tools.
Unpacking gnome-pkg-tools (from .../gnome-pkg-tools_0.9.3_all.deb) ...
Selecting previously deselected package intltool.
Unpacking intltool (from .../intltool_0.35.5-0ubuntu2_all.deb) ...
Selecting previously deselected package libart-2.0-dev.
Unpacking libart-2.0-dev (from .../libart-2.0-dev_2.3.17-1_amd64.deb) ...
Selecting previously deselected package libglib2.0-dev.
Unpacking libglib2.0-dev (from .../libglib2.0-dev_2.12.11-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libatk1.0-dev.
Unpacking libatk1.0-dev (from .../libatk1.0-dev_1.18.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libaudiofile-dev.
Unpacking libaudiofile-dev (from .../libaudiofile-dev_0.2.6-6ubuntu3_amd64.deb) ...
Selecting previously deselected package libavahi-common-dev.
Unpacking libavahi-common-dev (from .../libavahi-common-dev_0.6.17-0ubuntu3_amd64.deb) ...
Selecting previously deselected package libdbus-1-dev.
Unpacking libdbus-1-dev (from .../libdbus-1-dev_1.0.2-1ubuntu4_amd64.deb) ...
Selecting previously deselected package libavahi-client-dev.
Unpacking libavahi-client-dev (from .../libavahi-client-dev_0.6.17-0ubuntu3_amd64.deb) ...
Selecting previously deselected package libavahi-glib-dev.
Unpacking libavahi-glib-dev (from .../libavahi-glib-dev_0.6.17-0ubuntu3_amd64.deb) ...
Selecting previously deselected package libidl-dev.
Unpacking libidl-dev (from .../libidl-dev_0.8.7-0.1ubuntu2_amd64.deb) ...
Selecting previously deselected package liborbit2-dev.
Unpacking liborbit2-dev (from .../liborbit2-dev_1%3a2.14.7-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libpopt-dev.
Unpacking libpopt-dev (from .../libpopt-dev_1.10-3build1_amd64.deb) ...
Selecting previously deselected package libbonobo2-dev.
Unpacking libbonobo2-dev (from .../libbonobo2-dev_2.18.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libpng12-dev.
Unpacking libpng12-dev (from .../libpng12-dev_1.2.15~beta5-1ubuntu1_amd64.deb) ...
Selecting previously deselected package libcairo2-dev.
Unpacking libcairo2-dev (from .../libcairo2-dev_1.4.2-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libpango1.0-dev.
Unpacking libpango1.0-dev (from .../libpango1.0-dev_1.16.2-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libgtk2.0-dev.
Unpacking libgtk2.0-dev (from .../libgtk2.0-dev_2.10.11-0ubuntu3_amd64.deb) ...
Selecting previously deselected package libgnomecanvas2-dev.
Unpacking libgnomecanvas2-dev (from .../libgnomecanvas2-dev_2.14.0-3ubuntu2_amd64.deb) ...
Selecting previously deselected package libxml2-dev.
Unpacking libxml2-dev (from .../libxml2-dev_2.6.27.dfsg-1ubuntu3_amd64.deb) ...
Selecting previously deselected package libglade2-dev.
Unpacking libglade2-dev (from .../libglade2-dev_1%3a2.6.0-3_amd64.deb) ...
Selecting previously deselected package libgconf2-dev.
Unpacking libgconf2-dev (from .../libgconf2-dev_2.18.0.1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libgpg-error-dev.
Unpacking libgpg-error-dev (from .../libgpg-error-dev_1.4-2build1_amd64.deb) ...
Selecting previously deselected package libgcrypt11-dev.
Unpacking libgcrypt11-dev (from .../libgcrypt11-dev_1.2.3-2build1_amd64.deb) ...
Selecting previously deselected package libtasn1-3-dev.
Unpacking libtasn1-3-dev (from .../libtasn1-3-dev_0.3.6-2build1_amd64.deb) ...
Selecting previously deselected package libopencdk8-dev.
Unpacking libopencdk8-dev (from .../libopencdk8-dev_0.5.9-2build1_amd64.deb) ...
Selecting previously deselected package liblzo-dev.
Unpacking liblzo-dev (from .../liblzo-dev_1.08-3_amd64.deb) ...
Selecting previously deselected package libgnutls-dev.
Unpacking libgnutls-dev (from .../libgnutls-dev_1.4.4-3build1_amd64.deb) ...
Selecting previously deselected package libsepol1-dev.
Unpacking libsepol1-dev (from .../libsepol1-dev_1.14-2build1_amd64.deb) ...
Selecting previously deselected package libselinux1-dev.
Unpacking libselinux1-dev (from .../libselinux1-dev_1.32-3ubuntu1_amd64.deb) ...
Selecting previously deselected package libgnomevfs2-dev.
Unpacking libgnomevfs2-dev (from .../libgnomevfs2-dev_1%3a2.18.1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libesd0-dev.
Unpacking libesd0-dev (from .../libesd0-dev_0.2.36-3ubuntu4_amd64.deb) ...
Selecting previously deselected package libgnome2-dev.
Unpacking libgnome2-dev (from .../libgnome2-dev_2.18.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libbonoboui2-dev.
Unpacking libbonoboui2-dev (from .../libbonoboui2-dev_2.18.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libdbus-glib-1-dev.
Unpacking libdbus-glib-1-dev (from .../libdbus-glib-1-dev_0.73-1_amd64.deb) ...
Selecting previously deselected package libnspr-dev.
Unpacking libnspr-dev (from .../libnspr-dev_2%3a1.firefox2.0.0.6+1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libedataserver1.2-dev.
Unpacking libedataserver1.2-dev (from .../libedataserver1.2-dev_1.10.1-0ubuntu1.1_amd64.deb) ...
Selecting previously deselected package libebook1.2-dev.
Unpacking libebook1.2-dev (from .../libebook1.2-dev_1.10.1-0ubuntu1.1_amd64.deb) ...
Selecting previously deselected package libecal1.2-dev.
Unpacking libecal1.2-dev (from .../libecal1.2-dev_1.10.1-0ubuntu1.1_amd64.deb) ...
Selecting previously deselected package libedataserverui1.2-dev.
Unpacking libedataserverui1.2-dev (from .../libedataserverui1.2-dev_1.10.1-0ubuntu1.1_amd64.deb) ...
Selecting previously deselected package libgnome-keyring-dev.
Unpacking libgnome-keyring-dev (from .../libgnome-keyring-dev_0.8.1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libjpeg62-dev.
Unpacking libjpeg62-dev (from .../libjpeg62-dev_6b-13_amd64.deb) ...
Selecting previously deselected package libgnomeui-dev.
Unpacking libgnomeui-dev (from .../libgnomeui-dev_2.17.92-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libstartup-notification0-dev.
Unpacking libstartup-notification0-dev (from .../libstartup-notification0-dev_0.9-1_amd64.deb) ...
Selecting previously deselected package libgnome-desktop-dev.
Unpacking libgnome-desktop-dev (from .../libgnome-desktop-dev_1%3a2.18.1-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libgnome-menu-dev.
Unpacking libgnome-menu-dev (from .../libgnome-menu-dev_2.18.0-0ubuntu3_amd64.deb) ...
Selecting previously deselected package liblaunchpad-integration-dev.
Unpacking liblaunchpad-integration-dev (from .../liblaunchpad-integration-dev_0.1.13_amd64.deb) ...
Selecting previously deselected package liblpint-bonobo-dev.
Unpacking liblpint-bonobo-dev (from .../liblpint-bonobo-dev_0.1.13_amd64.deb) ...
Selecting previously deselected package libwnck-dev.
Unpacking libwnck-dev (from .../libwnck-dev_2.18.0-0ubuntu1_amd64.deb) ...
Selecting previously deselected package libxmu-dev.
Unpacking libxmu-dev (from .../libxmu-dev_2%3a1.0.2-1ubuntu2_amd64.deb) ...
Selecting previously deselected package patchutils.
Unpacking patchutils (from .../patchutils_0.2.31-3_amd64.deb) ...
Selecting previously deselected package sharutils.
Unpacking sharutils (from .../sharutils_1%3a4.2.1-15_amd64.deb) ...
[B]Setting up gnome-panel-data (2.18.1-0ubuntu3.1) ...
Failed to load file "/var/lib/gconf/defaults/%gconf-tree-ka.xml": Error on line 741 char 85: Invalid UTF-8 encoded text
/usr/share/gconf/schemas/panel-object.schemas:637: parser error : ParsePI: PI long space expected
&#65533;&#65533;&#2330;&#2381;&#2330; &#2340;&#2361;&#2325;&#2379; &#2346;&#2381;&#2351;&#2366;&#2344;&#2354;&#2325;&#2379; &#2346;&#2352;&#2367;&#2330;&#2366;&#2351;&#2325;&#2404;<?long
                                                                               ^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : ParsePI: PI long never end ...

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag long line 637

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag locale line 635

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag schema line 398

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag schemalist line 4

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag gconfschemafile line 2

^
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 1:2.18.1-0ubuntu3.1); however:
  Package gnome-panel-data is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured[/B]
Setting up x11proto-core-dev (7.0.10-1) ...
Setting up libice-dev (1.0.3-1build1) ...
Setting up libsm-dev (1.0.2-1build1) ...
Setting up libxau-dev (1.0.3-1) ...
Setting up libxdmcp-dev (1.0.2-1) ...
Setting up x11proto-input-dev (1.4.1-1) ...
Setting up x11proto-kb-dev (1.0.3-2ubuntu1) ...
Setting up xtrans-dev (1.0.3-1) ...
Setting up libx11-dev (1.1.1-1ubuntu3) ...
Setting up x11proto-render-dev (0.9.2-4ubuntu1) ...
Setting up libxrender-dev (0.9.1-3) ...
Setting up x11proto-xext-dev (7.0.2-5ubuntu1) ...
Setting up x11proto-fixes-dev (4.0-0.1ubuntu2) ...
Setting up libxfixes-dev (4.0.3-1) ...
Setting up libxcursor-dev (1.1.8-1) ...
Setting up libxext-dev (1.0.3-1build1) ...
Setting up libexpat1-dev (1.95.8-3.4build1) ...

Setting up zlib1g-dev (1.2.3-13ubuntu4) ...
Setting up libfreetype6-dev (2.2.1-5ubuntu1.1) ...

Setting up libfontconfig1-dev (2.4.2-1ubuntu1) ...
Setting up libxft-dev (2.1.12-1) ...
Setting up libxi-dev (1.1.0-1build1) ...
Setting up x11proto-xinerama-dev (1.1.2-4ubuntu1) ...
Setting up libxinerama-dev (1.0.1-4build1) ...
Setting up libxmu-headers (1.0.2-1ubuntu2) ...
Setting up x11proto-randr-dev (1.2.1-1) ...
Setting up libxrandr-dev (1.2.0-3ubuntu1) ...
Setting up x11proto-resource-dev (1.0.2-4ubuntu1) ...
Setting up libxres-dev (1.0.1-2) ...
Setting up libxt-dev (1.0.5-1) ...
Setting up m4 (1.4.8-1build1) ...

Setting up autoconf (2.61-3) ...

Setting up autotools-dev (20060920.1) ...
Setting up automake1.7 (1.7.9-9) ...

Setting up cdbs (0.4.48ubuntu1) ...

Setting up gnome-pkg-tools (0.9.3) ...

Setting up intltool (0.35.5-0ubuntu2) ...
Setting up libart-2.0-dev (2.3.17-1) ...
Setting up libglib2.0-dev (2.12.11-0ubuntu1) ...
Setting up libatk1.0-dev (1.18.0-0ubuntu1) ...
Setting up libaudiofile-dev (0.2.6-6ubuntu3) ...
Setting up libavahi-common-dev (0.6.17-0ubuntu3) ...
Setting up libdbus-1-dev (1.0.2-1ubuntu4) ...
Setting up libavahi-client-dev (0.6.17-0ubuntu3) ...
Setting up libavahi-glib-dev (0.6.17-0ubuntu3) ...
Setting up libidl-dev (0.8.7-0.1ubuntu2) ...
Setting up liborbit2-dev (2.14.7-0ubuntu1) ...
Setting up libpopt-dev (1.10-3build1) ...
Setting up libbonobo2-dev (2.18.0-0ubuntu1) ...
Setting up libpng12-dev (1.2.15~beta5-1ubuntu1) ...
Setting up libcairo2-dev (1.4.2-0ubuntu1) ...
Setting up libpango1.0-dev (1.16.2-0ubuntu1) ...
Setting up libgtk2.0-dev (2.10.11-0ubuntu3) ...
Setting up libgnomecanvas2-dev (2.14.0-3ubuntu2) ...
Setting up libxml2-dev (2.6.27.dfsg-1ubuntu3) ...
Setting up libglade2-dev (2.6.0-3) ...

Setting up libgconf2-dev (2.18.0.1-0ubuntu1) ...

Setting up libgpg-error-dev (1.4-2build1) ...
Setting up libgcrypt11-dev (1.2.3-2build1) ...
Setting up libtasn1-3-dev (0.3.6-2build1) ...

Setting up libopencdk8-dev (0.5.9-2build1) ...

Setting up liblzo-dev (1.08-3) ...
Setting up libgnutls-dev (1.4.4-3build1) ...
Setting up libsepol1-dev (1.14-2build1) ...
Setting up libselinux1-dev (1.32-3ubuntu1) ...
Setting up libgnomevfs2-dev (2.18.1-0ubuntu1) ...
Setting up libesd0-dev (0.2.36-3ubuntu4) ...
Setting up libgnome2-dev (2.18.0-0ubuntu1) ...
Setting up libbonoboui2-dev (2.18.0-0ubuntu1) ...
Setting up libdbus-glib-1-dev (0.73-1) ...
Setting up libnspr-dev (1.firefox2.0.0.6+1-0ubuntu1) ...
Setting up libedataserver1.2-dev (1.10.1-0ubuntu1.1) ...
Setting up libebook1.2-dev (1.10.1-0ubuntu1.1) ...
Setting up libecal1.2-dev (1.10.1-0ubuntu1.1) ...
Setting up libedataserverui1.2-dev (1.10.1-0ubuntu1.1) ...
Setting up libgnome-keyring-dev (0.8.1-0ubuntu1) ...
Setting up libjpeg62-dev (6b-13) ...
Setting up libgnomeui-dev (2.17.92-0ubuntu1) ...
Setting up libstartup-notification0-dev (0.9-1) ...
Setting up libgnome-desktop-dev (2.18.1-0ubuntu1) ...
Setting up libgnome-menu-dev (2.18.0-0ubuntu3) ...
Setting up liblaunchpad-integration-dev (0.1.13) ...
Setting up liblpint-bonobo-dev (0.1.13) ...
Setting up libwnck-dev (2.18.0-0ubuntu1) ...

Setting up libxmu-dev (1.0.2-1ubuntu2) ...
Setting up patchutils (0.2.31-3) ...
Setting up sharutils (4.2.1-15) ...

Errors were encountered while processing:
 gnome-panel-data
 gnome-panel
E: Sub-process /usr/bin/dpkg returned an error code (1)
E: Failed to process build dependencies
**peter@peter-desktop:~$ sudo dpkg --configure gnome-panel**
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 1:2.18.1-0ubuntu3.1); however:
  Package gnome-panel-data is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-panel
**peter@peter-desktop:~$ sudo apt-get build-dep gnome-panel**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up gnome-panel-data (2.18.1-0ubuntu3.1) ...
/usr/share/gconf/schemas/panel-object.schemas:637: parser error : ParsePI: PI long space expected
&#65533;&#65533;&#2330;&#2381;&#2330; &#2340;&#2361;&#2325;&#2379; &#2346;&#2381;&#2351;&#2366;&#2344;&#2354;&#2325;&#2379; &#2346;&#2352;&#2367;&#2330;&#2366;&#2351;&#2325;&#2404;<?long
                                                                               ^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : ParsePI: PI long never end ...

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag long line 637

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag locale line 635

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag schema line 398

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag schemalist line 4

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag gconfschemafile line 2

^
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 1:2.18.1-0ubuntu3.1); however:
  Package gnome-panel-data is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-panel-data
 gnome-panel
E: Sub-process /usr/bin/dpkg returned an error code (1)
E: Failed to process build dependencies
peter@peter-desktop:~$ sudo dpkg --configure gnome-panel-data
Setting up gnome-panel-data (2.18.1-0ubuntu3.1) ...
/usr/share/gconf/schemas/panel-object.schemas:637: parser error : ParsePI: PI long space expected
&#65533;&#65533;&#2330;&#2381;&#2330; &#2340;&#2361;&#2325;&#2379; &#2346;&#2381;&#2351;&#2366;&#2344;&#2354;&#2325;&#2379; &#2346;&#2352;&#2367;&#2330;&#2366;&#2351;&#2325;&#2404;<?long
                                                                               ^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : ParsePI: PI long never end ...

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag long line 637

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag locale line 635

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag schema line 398

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag schemalist line 4

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag gconfschemafile line 2

^
[B]dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gnome-panel-data[/B]
**peter@peter-desktop:~$ gksudo gedit /usr/share/gconf/schemas/panel-object.schemas** 
```

Below is a screenshot of my schema file. I have no idea what I am looking at.

---

### Post by p_quarles on 2007-10-02
After looking at the screenshot, I have no idea what I'm looking at either, except that it doesn't look right. 

Do you happen to have any Chinese or eastern European language packs installed? 

If not, then it looks like gconf (which is basically the configuration registry for the Gnome desktop) is completely foo-bared. 

The following might help, and won't hurt anything if it doesn't:
```
sudo dpkg-reconfigure gconf
sudo dpkg-reconfigure gconf2
```
Beyond that, like I said I don't use Gnome, so my advice would be to wait for someone who does to step in here. 

By the way, I noticed that one of your earlier error messages said something about Alien and RPM -- what package(s) did you install using that?

---

### Post by Poene on 2007-10-02
> **p_quarles said:**
> After looking at the screenshot, I have no idea what I'm looking at either, except that it doesn't look right. 

Do you happen to have any Chinese or eastern European language packs installed? 

If not, then it looks like gconf (which is basically the configuration registry for the Gnome desktop) is completely foo-bared. 

The following might help, and won't hurt anything if it doesn't:
```
sudo dpkg-reconfigure gconf
sudo dpkg-reconfigure gconf2
```
Beyond that, like I said I don't use Gnome, so my advice would be to wait for someone who does to step in here. 

By the way, I noticed that one of your earlier error messages said something about Alien and RPM -- what package(s) did you install using that?

The two commands above don't work. 
```
 peter@peter-desktop:~$ sudo dpkg-reconfigure gconf
Package `gconf' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: gconf is not installed
peter@peter-desktop:~$ 

```

I have the basic install; if that comes with Chinese or Eastern European language packs. Does the basic install come with language packs? If it does not, then my gnome is really FUBAR.

I used Alien and RPM to try and install 64-bit flash. I was getting the gnome-panel-error prior to that though. In fact, the gnome-panel-data error is the reason why I can't install Flash to begin with nor can I run Azureus.

**Thanks so much for helping though!** I wouldn't even know where to start looking to be honest.

---

### Post by p_quarles on 2007-10-02
And you tried the same command with gconf2? Got the same error? (I'm assuming yes).

The basic English-language installation definitely does not come with gconf files in Chinese. So, yes, Gnome is corrupt.

I wasn't aware that there was a 64-bit version of Flash available -- are you sure it's a legitimate package?  

Anyway, try:
```
sudo apt-get install -f --reinstall ubuntu-desktop
```
Like I said, your best bet is to wait a day or two to see if someone else can help you with this. Of course, if you can back up your data and reinstall, that will probably be the fastest solution. 

By the way: I'm running 32-bit Ubuntu on a 64-bit system, and it works fine. Running the 64-bit OS is only really helpful if you have huge amounts of RAM and need to be able to use it. If you do reinstall, I'd strongly recommend going with the 32-bit OS.

---

### Post by Poene on 2007-10-03
```
peter@peter-desktop:~$ sudo apt-get install -f --reinstall ubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 18.1kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com feisty/main ubuntu-desktop 1.43 [18.1kB]
Fetched 18.1kB in 0s (23.9kB/s)     
(Reading database ... 111608 files and directories currently installed.)
Preparing to replace ubuntu-desktop 1.43 (using .../ubuntu-desktop_1.43_amd64.deb) ...
Unpacking replacement ubuntu-desktop ...
Setting up gnome-panel-data (2.18.1-0ubuntu3.1) ...
/usr/share/gconf/schemas/panel-object.schemas:637: parser error : ParsePI: PI long space expected
&#65533;&#65533;&#2330;&#2381;&#2330; &#2340;&#2361;&#2325;&#2379; &#2346;&#2381;&#2351;&#2366;&#2344;&#2354;&#2325;&#2379; &#2346;&#2352;&#2367;&#2330;&#2366;&#2351;&#2325;&#2404;<?long
                                                                               ^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : ParsePI: PI long never end ...

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag long line 637

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag locale line 635

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag schema line 398

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag schemalist line 4

^
/usr/share/gconf/schemas/panel-object.schemas:5437: parser error : Premature end of data in tag gconfschemafile line 2

^
dpkg: error processing gnome-panel-data (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-panel-data (= 1:2.18.1-0ubuntu3.1); however:
  Package gnome-panel-data is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-panel-data
 gnome-panel
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
peter@peter-desktop:~$ 

```

I can't afford to reinstall right now, since I need a computer to use for class. The only reason I'm running 64-bit right now is because I can't get the 32-bit Ubuntu to run.

---

### Post by p_quarles on 2007-10-03
Sorry I couldn't help. It sounds like the computer is running, at least, so if you can wait and reinstall during a break, that should fix these problems. 

Good luck, in any case.

---

### Post by Poene on 2007-10-03
> **p_quarles said:**
> Sorry I couldn't help. It sounds like the computer is running, at least, so if you can wait and reinstall during a break, that should fix these problems. 

Good luck, in any case.

Thanks for the honest effort. Much appreciated.

---

### Post by Poene on 2007-10-03
All that tweaking and fiddling messed up my OS so bad, I had to reinstall it haha. The good thing though is that I managed to get a clean install. SOLVED!

---

