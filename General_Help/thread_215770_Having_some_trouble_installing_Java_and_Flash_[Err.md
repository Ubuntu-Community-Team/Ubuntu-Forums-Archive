---
title: "Having some trouble installing Java and Flash [Error msgs]"
date: 2006-07-14
forum: General Help
---

### Post by Daiver on 2006-07-14
I just reformatted my computer and now I have problems getting Java back in.  Please see:

daiver@ulysses:~$ sudo apt-get install sun-java5-jre sun-java5-plugin
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libltdl3 odbcinst1debian1 sun-java5-bin unixodbc
Suggested packages:
  sun-java5-fonts libmyodbc odbc-postgresql libct1
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed:
  libltdl3 odbcinst1debian1 sun-java5-bin sun-java5-jre sun-java5-plugin unixodbc
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.0MB of archives.
After unpacking 84.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libltdl3 1.5.22-2 [168kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main odbcinst1debian1 2.2.11-11build1 [63.8kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main unixodbc 2.2.11-11build1 [269kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse sun-java5-bin 1.5.0-06-1 [22.1MB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse sun-java5-jre 1.5.0-06-1 [7341kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse sun-java5-plugin 1.5.0-06-1 [1334B]
Fetched 30.0MB in 6m59s (71.6kB/s)
Preconfiguring packages ...
Selecting previously deselected package libltdl3.
(Reading database ... 68332 files and directories currently installed.)
Unpacking libltdl3 (from .../libltdl3_1.5.22-2_i386.deb) ...
Selecting previously deselected package odbcinst1debian1.
Unpacking odbcinst1debian1 (from .../odbcinst1debian1_2.2.11-11build1_i386.deb) ...
Selecting previously deselected package unixodbc.
Unpacking unixodbc (from .../unixodbc_2.2.11-11build1_i386.deb) ...
Selecting previously deselected package sun-java5-bin.
Unpacking sun-java5-bin (from .../sun-java5-bin_1.5.0-06-1_i386.deb) ...
sun-dlj-v1-1 license could not be presented
dpkg: error processing /var/cache/apt/archives/sun-java5-bin_1.5.0-06-1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Selecting previously deselected package sun-java5-jre.
Unpacking sun-java5-jre (from .../sun-java5-jre_1.5.0-06-1_all.deb) ...
sun-dlj-v1-1 license could not be presented
dpkg: error processing /var/cache/apt/archives/sun-java5-jre_1.5.0-06-1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Selecting previously deselected package sun-java5-plugin.
Unpacking sun-java5-plugin (from .../sun-java5-plugin_1.5.0-06-1_i386.deb) ...
[COLOR="Navy"]Errors were encountered while processing:
 /var/cache/apt/archives/sun-java5-bin_1.5.0-06-1_i386.deb
 /var/cache/apt/archives/sun-java5-jre_1.5.0-06-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
[COLOR="DarkGreen"]daiver@ulysses:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: gsfonts-x11 but it is not going to be installed
  sun-java5-plugin: Depends: sun-java5-bin (= 1.5.0-06-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
daiver@ulysses:~$ sudo apt-get -f install[/COLOR]
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  sun-java5-bin sun-java5-jre
Suggested packages:
  sun-java5-fonts
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed:
  sun-java5-bin sun-java5-jre
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B/29.5MB of archives.
After unpacking 83.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 68394 files and directories currently installed.)
Unpacking sun-java5-jre (from .../sun-java5-jre_1.5.0-06-1_all.deb) ...
sun-dlj-v1-1 license could not be presented
dpkg: error processing /var/cache/apt/archives/sun-java5-jre_1.5.0-06-1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Unpacking sun-java5-bin (from .../sun-java5-bin_1.5.0-06-1_i386.deb) ...
sun-dlj-v1-1 license could not be presented
dpkg: error processing /var/cache/apt/archives/sun-java5-bin_1.5.0-06-1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java5-jre_1.5.0-06-1_all.deb
 /var/cache/apt/archives/sun-java5-bin_1.5.0-06-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can anyone help me with this?

---

