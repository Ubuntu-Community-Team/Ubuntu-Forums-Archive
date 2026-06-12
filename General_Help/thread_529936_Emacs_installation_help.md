---
title: "Emacs installation help"
date: 2007-08-19
forum: General Help
---

### Post by pinesol33 on 2007-08-19
Hi all,
I have managed to get myself into a problem. I had emacs 21 along with many other related packages installed via apt-get, but then I saw that emacs 22.1 was out...I then uninstalled all of my emacs 21 packages via apt-get, and did the whole ./configure, make, make install business for emacs 22.1 and all of that worked fine.
Then I realized there were a few packages I wanted, notably JDE, and I worried (probably incorrectly) that since I installed emacs 22.1 outside of apt-get, other emacs packages  might not register with emacs 22.1. So I decided I wanted emacs 21 again, and I did a very stupid thing. I did a 'whereis emacs' and manually deleted (with rm -r thefolder) all emacs files and folders that came up. 
Now when running apt-get install emacs I get the following: 

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  emacs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/24.8kB of archives.
After unpacking 65.5kB of additional disk space will be used.
Selecting previously deselected package emacs.
(Reading database ... 120249 files and directories currently installed.)
Unpacking emacs (from .../emacs_21.4a+1-2ubuntu1_all.deb) ...
Setting up emacs21 (21.4a+1-2ubuntu1) ...
emacs-install emacs21
install/dictionaries-common: Byte-compiling for emacsen flavour emacs21
>>Error occurred processing debian-ispell.el: File error (("Opening input file" "no such file or directory" "/usr/share/emacs21/site-lisp/dictionaries-common/debian-ispell.el"))
>>Error occurred processing ispell.el: File error (("Opening input file" "no such file or directory" "/usr/share/emacs21/site-lisp/dictionaries-common/ispell.el"))
>>Error occurred processing flyspell.el: File error (("Opening input file" "no such file or directory" "/usr/share/emacs21/site-lisp/dictionaries-common/flyspell.el"))
Done
emacsen-common: Handling install of emacsen flavor emacs21
emacsen-common: byte-compiling for emacs21
cp: cannot stat `/etc/emacs/site-start.d/00debian-vars.el': No such file or directory
emacs-install: /usr/lib/emacsen-common/packages/install/emacsen-common emacs21 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 2.
dpkg: error processing emacs21 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of emacs:
 emacs depends on emacs21 | emacs21-nox; however:
  Package emacs21 is not configured yet.
  Package emacs21-nox is not installed.
dpkg: error processing emacs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacs21
 emacs
E: Sub-process /usr/bin/dpkg returned an error code (1)


..so I figured I would do an 'apt-get remove emacs', but I get the same error there. Also, I took the hint from the error message and tried doing 'apt-get install ispell'...but that tried to install emacs too so I got the same error again. Doing an autoremove command gets rid of all emacs related packages that were successfully installed however... 

Can anyone help me out of the hole I've dug myself?

---

