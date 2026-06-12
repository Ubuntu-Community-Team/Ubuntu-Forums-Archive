---
title: "cannot install python-gtk2"
date: 2019-10-04
forum: General Help
---

### Post by psionman on 2019-10-04
I am trying to install gnome-schedule. The ./configure stops with

```
checking for PYGTK... no
configure: error: Package requirements (pygtk-2.0 >= 2.6) were not met:

No package 'pygtk-2.0' found
```

I have python-gtk2 installed, but when I try to reisnatll I get an error:

```
(Reading database ... 437971 files and directories currently installed.)
Preparing to unpack .../python-gtk2_2.24.0-4ubuntu1_amd64.deb ...
Unpacking python-gtk2 (2.24.0-4ubuntu1) over (2.24.0-4ubuntu1) ...
Setting up python-gtk2 (2.24.0-4ubuntu1) ...
Setting up python-gtk2-dev (2.24.0-4ubuntu1) ...
  File "/usr/bin/pyversions", line 20
    except IOError, msg:
                  ^
SyntaxError: invalid syntax
dpkg: error processing package python-gtk2-dev (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 python-gtk2-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up python-gtk2-dev (2.24.0-4ubuntu1) ...
  File "/usr/bin/pyversions", line 20
    except IOError, msg:
                  ^
SyntaxError: invalid syntax
dpkg: error processing package python-gtk2-dev (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
```

What can I do?

---

### Post by Xian on 2019-10-05
What does this get you?

```
[COLOR=#000000]sudo apt-get --reinstall install python-gtk2-dev[/COLOR]
```

---

### Post by psionman on 2019-10-06
> **Xian said:**
> What does this get you?

```
[COLOR=#000000]sudo apt-get --reinstall install python-gtk2-dev[/COLOR]
```

E: Internal Error, No file name for python-gtk2-dev:amd64

---

### Post by Xian on 2019-10-06
Okay you've likely got a broken package that will need this type of fix:

[https://stackoverflow.com/questions/48431372/removing-broken-packages-in-ubuntu?answertab=votes#tab-top](https://stackoverflow.com/questions/48431372/removing-broken-packages-in-ubuntu?answertab=votes#tab-top)

Which is to say you'll need to empty files from /var/lib/dpkg/info

And then issue the command:

```
sudo dpkg --remove --force-remove-reinstreq python-gtk2-dev
```

---

### Post by psionman on 2019-10-07
Thanks

That just leads to loads of missing dpkg errors, ending up with

```
suming package has no files currently installed
dpkg: warning: files list file for package 'libxcb-xkb1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libavahi-core7:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-pygments' missing; assuming package has no files currently installed
(Reading database ... 154 files and directories currently installed.)
Removing python-gtk2-dev (2.24.0-4ubuntu1) ...
  File "/usr/bin/pyversions", line 20
    except IOError, msg:
                  ^
SyntaxError: invalid syntax
dpkg: error processing package python-gtk2-dev (--remove):
 subprocess installed pre-removal script returned error exit status 1
  File "/usr/bin/pyversions", line 20
    except IOError, msg:
                  ^
SyntaxError: invalid syntax
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
```

---

### Post by Xian on 2019-10-07
Believe it or not progress is being made. :)

There are currently at least 3 broken packages to be repaired. 
So you'll need to remove each one from the /var/lib/dpkg/info directory:

For example:

```
sudo rm /var/lib/dpkg/info/libxcb-xkb1*
```

**Do this for each of the broken packages.**


Next issue the command:
```
sudo dpkg --configure -a
```

Finally reinstall each/all of the packages -- for example:

```
sudo apt-get install --reinstall libxcb-xkb1
```

---

### Post by psionman on 2019-10-09
No not 3, hundreds! here's a sample

```
dpkg: warning: files list file for package 'brasero-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libhpmud0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gnome-font-viewer' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'unity-lens-applications' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3.5-dev' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libunity-gtk2-parser0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ruby' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mate-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xdg-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-ipaddress' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsub-name-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxxf86vm-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libieee1284-3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'docker-ce-cli' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'yelp' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'uno-libs3' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'iputils-arping' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ca-certificates' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgstreamer-plugins-good1.0-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkf5sonnet5-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-tlwg-loma' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'texlive' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-tibetan-machine' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'avahi-discover' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaudgui5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpango-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libacl1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libschroedinger-1.0-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'geany-plugin-prj' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'manpages-dev' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtheora0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'unity-greeter' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gstreamer0.10-plugins-base:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'language-selector-gnome' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxfixes-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'openssh-client' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libqt4-test:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libvte9' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libjreen1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ncurses-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dirmngr' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'texlive-generic-recommended' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libyaml-libyaml-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-matplotlib' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libprocps4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwebp5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmpg123-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfile-mimeinfo-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bluez' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-totem-1.0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libopencore-amrwb0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'hicolor-icon-theme' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'acl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libshout3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgs9:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fonts-kacst' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'irqbalance' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'rhythmbox-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libharfbuzz-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'qml-module-qtfeedback:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsecret-1-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dh-python' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'geany-plugin-git-changebar' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libglib2.0-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dconf-gsettings-backend:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libreoffice-style-breeze' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libc6-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libslang2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-decorator' missing; assuming package has no files c
```

---

### Post by Xian on 2019-10-09
There have been some command scripts posted to deal with such issues. 

Here's a link to one such example for you to review:

[https://askubuntu.com/questions/949760/dpkg-warning-files-list-file-for-package-missing?answertab=votes#tab-top](https://askubuntu.com/questions/949760/dpkg-warning-files-list-file-for-package-missing?answertab=votes#tab-top)

---

### Post by psionman on 2019-10-18
I am using the command

> for package in $(sudo apt-get upgrade 2>&1 | grep "warning: files list file for package '" | grep -Po "[^'\n ]+'" | grep -Po "[^']+"); do sudo apt-get install --reinstall "$package"; done

24 hours later it's still running. No feedback. Is this OK?

---

