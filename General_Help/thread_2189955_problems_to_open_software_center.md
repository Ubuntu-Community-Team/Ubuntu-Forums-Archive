---
title: "problems to open software center"
date: 2013-11-24
forum: General Help
---

### Post by fragos_jim on 2013-11-24
I am a new user and i need help with software center,that i can't open.
I read many messages and when i tried to open in a terminal window with the command  
[I]
software-center[/I]

then give me this

this programm is not installed. you can install it by running
 *sudo apt-get install software-center*
 
then when i run the above command it return this

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_saucy_main_i18n_Translation-el

what can i do to solve it..?

i use lubuntu 13.10

---

### Post by vasa1 on 2013-11-25
> **fragos_jim said:**
> I am a new user and i need help with software center,that i can't open.
I read many messages and when i tried to open in a terminal window with the command  
[I]
software-center[/I]

then give me this

this programm is not installed. you can install it by running
 *sudo apt-get install software-center*
 
then when i run the above command it return this

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_saucy_main_i18n_Translation-el

what can i do to solve it..?

i use lubuntu 13.10

In Lubuntu, you can start the program from the terminal using this command:
```
lubuntu-software-center
```
You should also see it if you click on the "menu" button and then in one of the submenus (System Tools or Preferences, I don't remember which).

In my opinion, there's no need to install anything else.

```
[10:43 AM] ~ $ apt-cache show lubuntu-software-center
Package: lubuntu-software-center
Priority: extra
Section: universe/python
Installed-Size: 920
Maintainer: Julien Lavergne <gilir@ubuntu.com>
Architecture: all
Version: 0.0.5~bzr161-0ubuntu1
Depends: python (>= 2.7.1-0ubuntu2), python (<< 2.8), python-apt, python-gi, gir1.2-gtk-3.0, gir1.2-notify-0.7, python-pysqlite2, python-aptdaemon, python-aptdaemon.gtk3widgets, python-xdg, app-install-data
Filename: pool/universe/l/lubuntu-software-center/lubuntu-software-center_0.0.5~bzr161-0ubuntu1_all.deb
Size: 132150
MD5sum: 3e688f1e1e2b55401db8cf9c2bb1d44e
SHA1: 360e50dda5d3c37a56a8f88ce5183a4ae830c115
SHA256: 689379d6d489ca1fc72d697768fb949902283ab8ddcb19b1266163b5b9098b0e
Description-en: Utility for browsing, installing, removing applications on Lubuntu
 The Lubuntu Software Center lets you browse and install thousands of
 applications available for Lubuntu. You can view available
 applications by category, or search quickly by name or description.
 You can also examine the applications already installed, and remove
 those you no longer need.
 .
 This center was especially optimised for Lubuntu, but you have access to the
 same free applications than on Ubuntu Software Center.
 .
 To install or remove software using the Center, you need administrator
 access on the computer.
Description-md5: 9d477cb5984a25d8a4fa441f4808c317
Homepage: https://launchpad.net/lubuntu-software-center
Description-md5: 9d477cb5984a25d8a4fa441f4808c317
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Task: lubuntu-desktop

```

---

### Post by Bucky Ball on 2013-11-25
> **vasa1 said:**
> 
In my opinion, there's no need to install anything else.



+1. It's already there. Installed as default with Lubuntu.

---

### Post by fragos_jim on 2013-11-25
i run what you told me and it return this:

[I]DEBUG 2013-11-25 13:51:17,112 __init__ 44 Opening config file
DEBUG 2013-11-25 13:51:17,346 __init__ 44 Opening config file
&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#923;&#953;&#963;&#964;&#974;&#957; &#928;&#945;&#954;&#941;&#964;&#969;&#957;... &#931;&#966;&#940;&#955;&#956;&#945;!
Traceback (most recent call last):
  File "/usr/bin/lubuntu-software-center", line 33, in <module>
    mainfunc()
  File "/usr/lib/python2.7/dist-packages/LSC/main.py", line 678, in lscmain
    app = LscControl()
  File "/usr/lib/python2.7/dist-packages/LSC/main.py", line 60, in __init__
    self.refresh_system_call()
  File "/usr/lib/python2.7/dist-packages/LSC/main.py", line 623, in refresh_system_call
    self.cache = apt_pkg.Cache()
SystemError: E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_saucy_main_i18n_Translation-el, E:&#913;&#948;&#973;&#957;&#945;&#964;&#959; &#964;&#959; &#940;&#957;&#959;&#953;&#947;&#956;&#945; &#942; &#951; &#945;&#957;&#940;&#955;&#965;&#963;&#951; &#964;&#969;&#957; &#955;&#953;&#963;&#964;&#974;&#957; &#960;&#945;&#954;&#941;&#964;&#969;&#957; &#942; &#964;&#959;&#965; &#945;&#961;&#967;&#949;&#943;&#959;&#965; &#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951;&#962;.[/I]

please i need more suggestions to fix it.
Thank you in advance

---

### Post by vasa1 on 2013-11-25
How did you install Lubuntu 13.10? 
Have you ever run *sudo apt-get update* and then *sudo apt-get upgrade*?
Have you edited any files in /etc?
Do other things work properly for you?

---

### Post by Yellow Pasque on 2013-11-25
[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

---

### Post by ian-weisser on 2013-11-25
Software Center is only the symptom.
The package manager (apt) has the real problem.
Software Center and apt-get merely tell the package manager what to do. The same problem will stop both from working.

> **fragos_jim said:**
> 
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_saucy_main_i18n_Translation-el


Open a terminal. Try the following commands in order. If you get an error message, stop and show us the _complete_ output.
```
sudo rm /var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_saucy_main_i18n_Translation-el
sudo apt-get update
sudo apt-get upgrade
```
The first command will delete the broken file.
The second command will, among other actions, reconstruct the broken file.
The final command will check for any other problems. If successful, it will download and install all the upgrades for your release of Ubuntu since that file broke your package manager. If successful, Software Center should work again.

Reference: [http://askubuntu.com/questions/30072/how-do-i-fix-a-problem-with-mergelist-or-status-file-could-not-be-parsed-err](http://askubuntu.com/questions/30072/how-do-i-fix-a-problem-with-mergelist-or-status-file-could-not-be-parsed-err)

---

### Post by fragos_jim on 2013-11-25
**the first command retturn this result**

[I]rm: &#945;&#948;&#965;&#957;&#945;&#956;&#943;&#945; &#948;&#953;&#945;&#947;&#961;&#945;&#966;&#942;&#962; «/var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_saucy_main_i18n_Translation-el»: archive or file does not exist

[/I]**the second command***```
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy InRelease*
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release.gpg                             *
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security InRelease                    *
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy Release                                 *
*&#934;&#941;&#961;&#949;:1 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release.gpg [933 B]           *
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy InRelease                           *
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates InRelease                   *
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports InRelease                 *
*Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy Release.gpg                             *
*&#934;&#941;&#961;&#949;:2 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates Release.gpg [933 B]          *
*Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports Release.gpg                   *
*Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy Release                                 *
*&#934;&#941;&#961;&#949;:3 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates Release [49,6 kB]            *
*Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports Release                       *
*&#934;&#941;&#961;&#949;:4 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy/main Sources                         *
*&#931;&#966;&#940;&#955;&#956;&#945; [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main i386 Packages                       *
*  404  Not Found*
*&#934;&#941;&#961;&#949;:5 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy/restricted Sources                   *
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-el_GR                  *
*&#934;&#941;&#961;&#949;:6 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy/universe Sources                     *
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-el                     *
*&#934;&#941;&#961;&#949;:7 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy/multiverse Sources                   *
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://ppa.launchpad.net](http://ppa.launchpad.net) saucy/main Translation-en                     *
*&#934;&#941;&#961;&#949;:8 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy/main i386 Packages                   *
*&#934;&#941;&#961;&#949;:9 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy/restricted i386 Packages             *
*&#934;&#941;&#961;&#949;:10 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy/universe i386 Packages              *
*&#934;&#941;&#961;&#949;:11 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy/multiverse i386 Packages            *
*&#934;&#941;&#961;&#949;:12 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy/main Translation-el                 *
*&#934;&#941;&#961;&#949;:13 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release [49,6 kB]            *
*Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy/main Translation-en                     *
*Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy/multiverse Translation-el*
*Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy/multiverse Translation-en*
*&#934;&#941;&#961;&#949;:14 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Sources                 *
*Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy/restricted Translation-el               *
*Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy/restricted Translation-en               *
*&#934;&#941;&#961;&#949;:15 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Sources*
*Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy/universe Translation-el                 *
*Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy/universe Translation-en                 *
*&#934;&#941;&#961;&#949;:16 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Sources*
*&#934;&#941;&#961;&#949;:17 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates/main Sources                *
*&#934;&#941;&#961;&#949;:18 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates/restricted Sources          *
*&#934;&#941;&#961;&#949;:19 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates/universe Sources            *
*&#934;&#941;&#961;&#949;:20 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Sources           *
*&#934;&#941;&#961;&#949;:21 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates/multiverse Sources          *
*&#934;&#941;&#961;&#949;:22 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main i386 Packages           *
*&#934;&#941;&#961;&#949;:23 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates/main i386 Packages          *
*&#934;&#941;&#961;&#949;:24 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates/restricted i386 Packages    *
*&#934;&#941;&#961;&#949;:25 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted i386 Packages     *
*&#934;&#941;&#961;&#949;:26 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates/universe i386 Packages      *
*&#934;&#941;&#961;&#949;:27 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe i386 Packages       *
*&#934;&#941;&#961;&#949;:28 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates/multiverse i386 Packages    *
*Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates/main Translation-en             *
*&#934;&#941;&#961;&#949;:29 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse i386 Packages     *
*Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates/multiverse Translation-en       *
*Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates/restricted Translation-en       *
*&#934;&#941;&#961;&#949;:30 [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en*
*Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates/universe Translation-en         *
*&#934;&#941;&#961;&#949;:31 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports/main Sources              *
*&#934;&#941;&#961;&#949;:32 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports/restricted Sources        *
*&#934;&#941;&#961;&#949;:33 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports/universe Sources          *
*&#934;&#941;&#961;&#949;:34 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports/multiverse Sources        *
*&#934;&#941;&#961;&#949;:35 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports/main i386 Packages        *
*&#934;&#941;&#961;&#949;:36 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports/restricted i386 Packages  *
*&#934;&#941;&#961;&#949;:37 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports/universe i386 Packages    *
*&#934;&#941;&#961;&#949;:38 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports/multiverse i386 Packages  *
*Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en        *
*Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports/main Translation-en           *
*Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports/multiverse Translation-en     *
*Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports/restricted Translation-en*
*Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en*
*Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports/universe Translation-en*
*Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en          *
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-el_GR       *
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-el          *
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-el_GR *
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy/main Translation-el_GR              *
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-el*
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy/multiverse Translation-el_GR*
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy/restricted Translation-el_GR*
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy/universe Translation-el_GR*
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-el_GR*
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates/main Translation-el_GR*
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates/main Translation-el*
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates/multiverse Translation-el_GR*
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-el*
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates/multiverse Translation-el*
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates/restricted Translation-el_GR*
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates/restricted Translation-el*
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates/universe Translation-el_GR*
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-el_GR*
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-updates/universe Translation-el     *
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports/main Translation-el_GR    *
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports/main Translation-el*
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-el*
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports/multiverse Translation-el_GR*
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports/multiverse Translation-el*
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports/restricted Translation-el_GR*
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports/restricted Translation-el*
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports/universe Translation-el_GR*
*&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) saucy-backports/universe Translation-el*
*&#924;&#949;&#964;&#945;&#966;&#959;&#961;&#964;&#974;&#952;&#951;&#954;&#945;&#957; 199 kB &#963;&#949; 13s (15,0 kB/s)*
*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; [http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/lubuntu-desktop/ppa/ubuntu/dists/saucy/main/binary-i386/Packages)   404  Not Found*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy_main_source_Sources   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy_restricted_source_Sources   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy_universe_source_Sources   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy_multiverse_source_Sources   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy_main_binary-i386_Packages   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy_restricted_binary-i386_Packages   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy_universe_binary-i386_Packages   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy_multiverse_binary-i386_Packages   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy-updates_main_source_Sources   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy-updates_restricted_source_Sources   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy-updates_universe_source_Sources   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy-updates_multiverse_source_Sources   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy-updates_main_binary-i386_Packages   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy-updates_restricted_binary-i386_Packages   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy-updates_universe_binary-i386_Packages   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy-updates_multiverse_binary-i386_Packages   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy-backports_main_source_Sources   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy-backports_restricted_source_Sources   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy-backports_universe_source_Sources   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy-backports_multiverse_source_Sources   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy-backports_main_binary-i386_Packages   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy-backports_restricted_binary-i386_Packages   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy-backports_universe_binary-i386_Packages   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/gr.archive.ubuntu.com_ubuntu_dists_saucy-backports_multiverse_binary-i386_Packages   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_saucy-security_main_source_Sources   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_saucy-security_restricted_source_Sources   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_saucy-security_universe_source_Sources   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_saucy-security_multiverse_source_Sources   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_saucy-security_main_binary-i386_Packages   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_saucy-security_restricted_binary-i386_Packages   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_saucy-security_universe_binary-i386_Packages   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

*W: &#913;&#960;&#959;&#964;&#965;&#967;&#943;&#945; &#945;&#957;&#940;&#954;&#964;&#951;&#963;&#951;&#962; &#964;&#959;&#965; gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_saucy-security_multiverse_binary-i386_Packages   &#913;&#957;&#972;&#956;&#959;&#953;&#959; MD5Sum*

[I]E: Some index files failed to download. They have been ignored, or old ones used instead.
```


[/I][B]and the third

[/B]*&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#923;&#953;&#963;&#964;&#974;&#957; &#928;&#945;&#954;&#941;&#964;&#969;&#957;... &#931;&#966;&#940;&#955;&#956;&#945;!*
*E: Encountered a section with no Package: header*
*E: Problem with MergeList /var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_saucy_main_i18n_Translation-el*
[I]E: &#913;&#948;&#973;&#957;&#945;&#964;&#959; &#964;&#959; &#940;&#957;&#959;&#953;&#947;&#956;&#945; &#942; &#951; &#945;&#957;&#940;&#955;&#965;&#963;&#951; &#964;&#969;&#957; &#955;&#953;&#963;&#964;&#974;&#957; &#960;&#945;&#954;&#941;&#964;&#969;&#957; &#942; &#964;&#959;&#965; &#945;&#961;&#967;&#949;&#943;&#959;&#965; &#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951;&#962;.

[/I][B]i don't have any idea how to fix this cause i'am new with Lubuntu, so if you can help me solve it.
thanks[/B]

---

### Post by Bashing-om on 2013-11-25
fragos_jim; Hi ! My welcome to the forum .

Is this terminal command:
> 
rm: &#945;&#948;&#965;&#957;&#945;&#956;&#943;&#945; &#948;&#953;&#945;&#947;&#961;&#945;&#966;&#942;&#962; «/var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_saucy_main_i18n _Translation-el»: archive or file does not exist

the same as what ian-weisser directed you to use ?
> 
sudo rm /var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_saucy_main_i18n_Translation-el


Copy and paste the commands for best results.
If that command executes successfully then continue with the other two commands.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2013-11-25
> **fragos_jim said:**
> **the first command retturn this result**

[I]rm: &#945;&#948;&#965;&#957;&#945;&#956;&#943;&#945; &#948;&#953;&#945;&#947;&#961;&#945;&#966;&#942;&#962; «/var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_saucy_main_i18n_Translation-el»: [COLOR=#ff0000]archive or file does not exist
[/COLOR]
[/I]

That's an error message. If you see that again, stop.

Try the first command again. Use tab completion.

Open a terminal and type **sudo rm /var/lib/apt/lists/gr. **and then hit <TAB>.
See how the system autocompleted some of the rest for you?
When it stops, add a few more characters of the filename, and tab <TAB> again.
Keep going until it finds the right file. Then delete it.

After deleting that file, try the second and third commands again.

---

### Post by fragos_jim on 2013-11-25
sorry again but what is the file i need to delete?
and how can i do that?
i assume that when i will ad the extra characters you mentioned, you mean to fill in the line after the *command*

rm /var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_saucy

with the characters from the list that returns me above the command line that came after the first command 
i run when i pressed TAB.Is that correct?

---

### Post by ian-weisser on 2013-11-25
> **fragos_jim said:**
> what is the file i need to delete?
Remember when you run **sudo apt-get update && sudo apt-get upgrade** and the system gives you an error message in return? 
The name of the file is inside that error message.


> **fragos_jim said:**
> how can i do that?
You delete a file with the **rm  **command.
Since this file is owned by root, you must prepend with **sudo**
So the command would be **sudo rm <filename>**


> **fragos_jim said:**
> i assume that when i will ad the extra characters you mentioned, you mean to fill in the line after the *command*

rm /var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_saucy

with the characters from the list that returns me above the command line that came after the first command 
i run when i pressed TAB.Is that correct?
Yes, that's right. Well done.

---

