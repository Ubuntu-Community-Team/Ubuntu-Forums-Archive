---
title: "Google Chrome No Longer Opening 24 January 2021 . . ."
date: 2021-01-24
forum: General Help
---

### Post by tamjk on 2021-01-24
It started this morning.
Although Chrome is very much a #2 browser by me, I use it now and again.
But this morning it just wouldn't open. I saw the fan swirl for a while and then . . . nothing.

I uninstalled and reinstalled via:

```
$ sudo apt update
$ wget [https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb)
--2021-01-24 12:13:53--  [https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb)
Resolving dl.google.com (dl.google.com)... 74.125.193.190, 74.125.193.91, 74.125.193.136, ...
Connecting to dl.google.com (dl.google.com)|74.125.193.190|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 72800524 (69M) [application/x-debian-package]
Saving to: &#8216;google-chrome-stable_current_amd64.deb&#8217;

google-chrome-stabl 100%[===================>]  69.43M  7.17MB/s    in 10s     

2021-01-24 12:14:07 (6.71 MB/s) - &#8216;google-chrome-stable_current_amd64.deb&#8217; saved [72800524/72800524]

$ sudo dpkg -i google-chrome-stable_current_amd64.deb
Selecting previously unselected package google-chrome-stable.
(Reading database ... 259677 files and directories currently installed.)
Preparing to unpack google-chrome-stable_current_amd64.deb ...
Unpacking google-chrome-stable (88.0.4324.96-1) ...
Setting up google-chrome-stable (88.0.4324.96-1) ...
update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/x-www-browser (x-www-browser) in auto mode
update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode
update-alternatives: using /usr/bin/google-chrome-stable to provide /usr/bin/google-chrome (google-chrome) in auto mode
Processing triggers for bamfdaemon (0.5.3+18.04.20180207.2-0ubuntu2) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for man-db (2.9.1-1) ...

Then I tried starting Chrome from the CLI

$ google-chrome
/usr/bin/google-chrome: line 8: /usr/bin/readlink: Permission denied
/usr/bin/google-chrome: line 10: /usr/bin/dirname: Permission denied
/usr/bin/google-chrome: line 45: /usr/bin/cat: Permission denied
/usr/bin/google-chrome: line 45: /usr/bin/cat: Success
/usr/bin/google-chrome: line 46: /usr/bin/cat: Permission denied
/usr/bin/google-chrome: line 46: /usr/bin/cat: Success

And nothing happens . . . 

I copy below the lines 8 & 10 of /usr/bin/google-chrome:

1 #!/bin/bash
2 #
3 # Copyright (c) 2011 The Chromium Authors. All rights reserved.
4 # Use of this source code is governed by a BSD-style license that can be
5 # found in the LICENSE file.
6
7 # Let the wrapped binary know that it has been run through the wrapper.
8 export CHROME_WRAPPER="`readlink -f "$0"`"
9
10 HERE="`dirname "$CHROME_WRAPPER"`"
```

Not sure what's wrong here.

---

### Post by mIk3_08 on 2021-01-24
Try to Restart your system then open the chrome again. maybe there is something that has not loaded properly during the start of your system.

---

### Post by tamjk on 2021-01-27
Not much help, Mike_08.
Issue is the same, restart, reinstall.

---

### Post by CelticWarrior on 2021-01-27
It seems to be a permissions issue. Have you changed something regarding permissions?

---

### Post by mIk3_08 on 2021-01-28
Yeah CelticWarrior is right this could be permissions. Try to change it.

---

