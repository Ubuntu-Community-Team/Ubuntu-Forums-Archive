---
title: "[SOLVED] Help with dpkg error-can't get rid of app"
date: 2007-08-09
forum: General Help
---

### Post by 67GTA on 2007-08-09
I tried to install firefox-alt-widgets with Gdebi and got errors that it could not install. I tried to use synaptic, apt-get remove, and dpkg -r. I tried to uninstall/reinstall firefox and then reinstall widgets. Now the widgets package is broken and will not let me install or uninstall anything because it tries to remove widgets before running any other command. It is marked for removal in synaptic and will not let me "unmark" it. How can I get rid of this thing? Terminal output:

shawnr@shawnr-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  firefox-alt-widgets
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 97094 files and directories currently installed.)
Removing firefox-alt-widgets ...
rm: cannot remove `/usr/lib/mozilla-firefox/res/forms.css': No such file or directory
dpkg: error processing firefox-alt-widgets (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 firefox-alt-widgets
E: Sub-process /usr/bin/dpkg returned an error code (1)


shawnr@shawnr-desktop:~$ sudo apt-get remove firefox-alt-widgets
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  firefox-alt-widgets
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 97094 files and directories currently installed.)
Removing firefox-alt-widgets ...
rm: cannot remove `/usr/lib/mozilla-firefox/res/forms.css': No such file or directory
dpkg: error processing firefox-alt-widgets (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 firefox-alt-widgets
E: Sub-process /usr/bin/dpkg returned an error code (1)


shawnr@shawnr-desktop:~$ sudo dpkg -r firefox-alt-widgets
(Reading database ... 97094 files and directories currently installed.)
Removing firefox-alt-widgets ...
rm: cannot remove `/usr/lib/mozilla-firefox/res/forms.css': No such file or directory
dpkg: error processing firefox-alt-widgets (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 firefox-alt-widgets

---

### Post by ruibernardo on 2007-08-09
> **67GTA said:**
> I tried to install firefox-alt-widgets with Gdebi and got errors that it could not install. I tried to use synaptic, apt-get remove, and dpkg -r.

Can you try this?

```
sudo dpkg -P firefox-alt-widgets
```

---

### Post by ayoli on 2007-08-09
or try this:
```
sudo touch /usr/lib/mozilla-firefox/res/forms.css && sudo dpkg -r firefox-alt-widgets
```

---

### Post by 67GTA on 2007-08-11
Sorry for the slow reply. Since it was complaining about the file not existing, I just copied it from my Ubuntu partition to my Kubuntu partition (I'm using Kubuntu). It seemed to like that:)

---

