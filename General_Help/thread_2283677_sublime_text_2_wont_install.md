---
title: "sublime text 2 wont install"
date: 2015-06-23
forum: General Help
---

### Post by Ty_Scheun on 2015-06-23
I am trying to install Sublime Text 2 after trying to install VS Code. I keep getting this:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  0ad-data 0ad-data-common fonts-texgyre hyphen-en-us libao-common libao4
  libboost-filesystem1.54.0 libenet2a libgloox11 libgtkglext1 liblua5.1-0
  libmozjs185-1.0 libnvtt2 libosmesa6 libreoffice-help-en-gb
  libreoffice-help-en-us libreoffice-l10n-en-gb libreoffice-l10n-en-za
  libsoundtouch0 libtinyxml2.6.2 libwxbase3.0-0 libwxgtk3.0-0 mythes-en-au
  mythes-en-us openoffice.org-hyphenation tex-common
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  sublime-text
0 upgraded, 1 newly installed, 0 to remove and 181 not upgraded.
Need to get 0 B/9,670 B of archives.
After this operation, 51.2 kB of additional disk space will be used.
Preconfiguring packages ...
Please report to author unsupported platform 'armv7l'.
(Reading database ... 140278 files and directories currently installed.)
Preparing to unpack .../sublime-text_2.0.2-1~webupd8~3_all.deb ...
Please report to author unsupported platform 'armv7l'.
Please report to author unsupported platform 'armv7l'.
Downloading...
--2015-06-23 18:43:07--  https://c758482.ssl.cf2.rackcdn.com/Sublime%20Text%202.0.2.tar.bz2
Resolving c758482.ssl.cf2.rackcdn.com (c758482.ssl.cf2.rackcdn.com)... 23.79.47.162
Connecting to c758482.ssl.cf2.rackcdn.com (c758482.ssl.cf2.rackcdn.com)|23.79.47.162|:443... connected.
HTTP request sent, awaiting response... 200 OK


    The file is already fully retrieved; nothing to do.


Download done.
Removing outdated cached downloads...
sha256sum mismatch Sublime Text 2.0.2.tar.bz2
Sublime Text is NOT installed.
dpkg: error processing archive /var/cache/apt/archives/sublime-text_2.0.2-1~webupd8~3_all.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/sublime-text_2.0.2-1~webupd8~3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

Any help would be appreciated

After trying to install VS Code, I have resolved to Sublime Text 2. But that wouldnt install either. Here is the report:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  0ad-data 0ad-data-common fonts-texgyre hyphen-en-us libao-common libao4
  libboost-filesystem1.54.0 libenet2a libgloox11 libgtkglext1 liblua5.1-0
  libmozjs185-1.0 libnvtt2 libosmesa6 libreoffice-help-en-gb
  libreoffice-help-en-us libreoffice-l10n-en-gb libreoffice-l10n-en-za
  libsoundtouch0 libtinyxml2.6.2 libwxbase3.0-0 libwxgtk3.0-0 mythes-en-au
  mythes-en-us openoffice.org-hyphenation tex-common
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  sublime-text
0 upgraded, 1 newly installed, 0 to remove and 181 not upgraded.
Need to get 0 B/9,670 B of archives.
After this operation, 51.2 kB of additional disk space will be used.
Preconfiguring packages ...
Please report to author unsupported platform 'armv7l'.
(Reading database ... 140278 files and directories currently installed.)
Preparing to unpack .../sublime-text_2.0.2-1~webupd8~3_all.deb ...
Please report to author unsupported platform 'armv7l'.
Please report to author unsupported platform 'armv7l'.
Downloading...
--2015-06-23 18:43:07--  https://c758482.ssl.cf2.rackcdn.com/Sublime%20Text%202.0.2.tar.bz2
Resolving c758482.ssl.cf2.rackcdn.com (c758482.ssl.cf2.rackcdn.com)... 23.79.47.162
Connecting to c758482.ssl.cf2.rackcdn.com (c758482.ssl.cf2.rackcdn.com)|23.79.47.162|:443... connected.
HTTP request sent, awaiting response... 200 OK


    The file is already fully retrieved; nothing to do.


Download done.
Removing outdated cached downloads...
sha256sum mismatch Sublime Text 2.0.2.tar.bz2
Sublime Text is NOT installed.
dpkg: error processing archive /var/cache/apt/archives/sublime-text_2.0.2-1~webupd8~3_all.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/sublime-text_2.0.2-1~webupd8~3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by jamesisin on 2015-06-23
Use a repository instead of a tarball.

Sublime Text 3 (or 2):

> sudo add-apt-repository ppa:webupd8team/sublime-text-3
sudo apt-get update
sudo apt-get install sublime-text-installer

[From my BuildUbu page.]("http://jamesisin.com/a_high-tech_blech/index.php/buildubu/")

---

### Post by Ty_Scheun on 2015-06-23
I have tried that but it still keeps on replying the same thing

---

### Post by pissedoffdude on 2015-06-23
Hi,

From that output, we see:
Please report to author unsupported platform 'armv7l'.

Upon googling arm and sublime, it's unsupported:
[http://askubuntu.com/questions/472188/how-to-install-sublime-text-on-ubuntu-chromebook](http://askubuntu.com/questions/472188/how-to-install-sublime-text-on-ubuntu-chromebook)
[https://sublimetext.userecho.com/topic/100806-armv7-or-armv6-version-of-sublime-text-2-for-linux/](https://sublimetext.userecho.com/topic/100806-armv7-or-armv6-version-of-sublime-text-2-for-linux/)

You'll have to try a different text editor since sublime doesn't support the arm architecture

---

### Post by jamesisin on 2015-06-23
Bummer.  I like gedit pretty well.

[Customize!]("https://www.google.com/search?client=opera&q=customize+gedit&sourceid=opera&ie=UTF-8&oe=UTF-8")

---

### Post by ajgreeny on 2015-06-23
Please do not start multiple-threads on the same subject.  It makes it difficult to follow and dilutes the answers given.

Threads merged.

---

### Post by pissedoffdude on 2015-06-23
I wouldn't get your hopes too down.  Linux text editors are awesome.  I can't guarantee it'll work for arm, but notepad qq's worth giving a shot if it runs.  I've heard good things about 'atom' as well since it's really similar to sublime.

---

