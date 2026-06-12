---
title: "CLI Companion installation in Ubuntu 19.04 fails - python-vte missing"
date: 2019-09-13
forum: General Help
---

### Post by tellapu on 2019-09-13
Hello!
Unfortunately the **wonderful terminal tool CLI Companion** [https://launchpad.net/clicompanion](https://launchpad.net/clicompanion) is no longer maintained but I have not found another terminal tool that **can save/store some favourites/bookmarks of often used commands and has GUI.** 

 I tried to install the deb-file in **Ubuntu 19.04** from Launchpad ([https://launchpad.net/clicompanion/1.0/1.3/+download/clicompanion_1.3-1_all.deb](https://launchpad.net/clicompanion/1.0/1.3/+download/clicompanion_1.3-1_all.deb)) and **failed**:
```
 sudo dpkg -i clicompanion_1.3-1_all.deb
```
Selecting previously unselected package clicompanion.
(Reading database ... 242806 files and directories currently installed.)
Preparing to unpack clicompanion_1.3-1_all.deb ...
Unpacking clicompanion (1.3-1) ...
dpkg: dependency problems prevent configuration of clicompanion:
 clicompanion depends on python-vte; however:
  Package python-vte is not installed.

 dpkg: error processing package clicompanion (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus (3.32.0-1ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-4ubuntu1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for man-db (2.8.5-2) ...
Errors were encountered while processing:
 clicompanion

 The "python-vte" package was removed from the main repository and I could not find a PPA for it. Maybe the missing python-vte is the culprit for the installation error. Can anybody help in any way?

Thanks!

---

### Post by dragonfly41 on 2019-09-13
I have installed cli-companion which still runs on Ubuntu 16.04.
However I decided to adopt different tools for the same purpose
to achieve similar functionality.

I do not know if Actiona is available in Ubuntu 19.04.
[https://jmgr.net/](https://jmgr.net/)

It is under category Accessories.
Using the GUI you can create an external ini file to allow command strings to be selected (including variables).
Through the GUI build a sequence of actions (they are Qt objects or widgets) some of which are listed below ...

Windows - Message Box
Windows - Data input
Windows - Multi data input
Device - Key
System - Command
Internal - Code
Internal - Console
Data - Read INI file
Data - Write clipboard

There may be others I have forgotten.


For example

select and build command string
write output to clipboard
launch command gnome-terminal
target gnome-terminal window
paste using Key Shift+Ctrl+V
run using Key Enter

It is quite a versatile tool which you can use for many automation tasks.

At the end you can run built scripts using notation

actexec myscript.ascr


Linux downloads here ...

[https://wiki.actiona.tools/doku.php?id=:en:start](https://wiki.actiona.tools/doku.php?id=:en:start)

Simple script here ...

[https://wiki.actiona.tools/doku.php?id=:en:start](https://wiki.actiona.tools/doku.php?id=:en:start)

[https://wiki.actiona.tools/doku.php?id=en:scripts:helloworld](https://wiki.actiona.tools/doku.php?id=en:scripts:helloworld)


Actions list ...

[https://wiki.actiona.tools/doku.php?id=en:actions](https://wiki.actiona.tools/doku.php?id=en:actions)


You can also write javascript functions in a Codebox.

---

### Post by dragonfly41 on 2019-09-13
[P.S.] Found python-vte here for 18.04

[https://pkgs.org/download/python-vte](https://pkgs.org/download/python-vte)

---

