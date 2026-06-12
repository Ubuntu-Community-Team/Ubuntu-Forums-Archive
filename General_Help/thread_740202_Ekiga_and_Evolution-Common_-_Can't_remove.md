---
title: "Ekiga and Evolution-Common - Can't remove"
date: 2008-03-30
forum: General Help
---

### Post by jcarlock on 2008-03-30
So I finally decided to try to upgrade to gutsy from feisty...  running sudo apt-get install -f returns the following.

jcarlock@pflp-jc-ln:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  ekiga evolution-common
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 65.5MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 221329 files and directories currently installed.)
Removing ekiga ...
scrollkeeper-update: symbol lookup error: /usr/lib/libxslt.so.1: undefined symbol: xmlXPathCompiledEvalToBoolean
dpkg: error processing ekiga (--remove):
 subprocess post-removal script returned error exit status 127
Removing evolution-common ...
scrollkeeper-update: symbol lookup error: /usr/lib/libxslt.so.1: undefined symbol: xmlXPathCompiledEvalToBoolean
dpkg: error processing evolution-common (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 ekiga
 evolution-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

I get the same results when I try to remove or install ekiga and evolution-common...  What gets me is this line...

scrollkeeper-update: symbol lookup error: /usr/lib/libxslt.so.1: undefined symbol: 

I'd try this but I'm not removing all these applications.  I am more reporting this than anything else since I will probably be wiping and reinstalling in the next few days...  I will check back and give more details if I can.

jcarlock@pflp-jc-ln:~$ sudo apt-get remove scrollkeeper
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  alacarte bug-buddy capplets-data doc-base ekiga evolution-common gedit gnome-app-install gnome-applets gnome-applets-data gnome-control-center gnome-panel gnome-panel-data gnome-session
  gnome-system-monitor gnome-terminal gnome-user-guide gnome-utils gthumb gucharmap language-selector libgnome-settings-daemon-dev nautilus nautilus-cd-burner nautilus-data restricted-manager scrollkeeper
  software-properties-gtk synaptic ubuntu-docs update-manager update-notifier zenity
0 upgraded, 0 newly installed, 33 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 255MB disk space will be freed.
Do you want to continue [Y/n]?Not a chance....

JC

---

### Post by jcarlock on 2008-04-01
Solved!!!!

Took me some time but I started by trying to install ekiga from source....  Went to:

[http://ekiga.org/index.php?rub=5&path=sources/sources](http://ekiga.org/index.php?rub=5&path=sources/sources)

Downloaded the opal and pwlib tar files.  Installed pwlib package, which needs two apps called bison and flex before pwlib will compile.  Next installed the opal tar.

I'm not going to run down how to install a package from source so you'll have to find that on your own, I know its somewhere here on the forums though.

It goes without saying that sudo apt-get install -f works now...  I actually found it was working while trying to fill some dependencies for the ekiga build.

---

