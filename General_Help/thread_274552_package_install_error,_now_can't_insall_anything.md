---
title: "package install error, now can't insall anything"
date: 2006-10-10
forum: General Help
---

### Post by Jewfro_Macabbi on 2006-10-10
I was trying to install my printer driver, following these instructions:

> Installing

Run the following commands only if you ware very particular you do not want to see any errors from the installation of the mfc420cnlpr package:

rm -f /usr/lib/libbrcompij.so*
ln -s /etc/init.d/cupsys /etc/init.d/cups

The first command removes symlinks that mfc420cnlpr puts in but doesn't remove when it is uninstalled (in case you have already installed and removed this package once). The second command makes it easier for the package that expects /etc/init.d/cups (that Mandriva, Red Hat, Suse provide).

Installation is as simple as running dpkg -i on all the downloaded packages:

dpkg -i mfc420cnlpr-1.0.2-1.i386.deb

which I found here:
[https://help.ubuntu.com/community/PrintersBrotherMfc420cn?highlight=%28lpd%29](https://help.ubuntu.com/community/PrintersBrotherMfc420cn?highlight=%28lpd%29)

Now I cannot install anything, aptitude, apt-get, or synaptic package manager all return errors.

The error from synaptic is:

> E: The package mfc420cnlpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

This is the error when I try to install a new package now using sudo aptitude:

> Writing extended state information... Error!
E: I wasn't able to locate file for the mfc420cnlpr package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?


I tried re-installing the printer driver, didn't help. It will not allow me to remove the package either, gives this error:

> :~$ sudo aptitude remove mfc420cnlpr
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REMOVED:
  mfc420cnlpr
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
dpkg: error processing mfc420cnlpr (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
:~$ Errors were encountered while processing:
 mfc420cnlpr


Help please.

---

### Post by Jussi Kukkonen on 2006-10-10
So, maybe you should try what dpkg suggests -- reinstall the package with 
*dpkg -i mfc420cnlpr-1.0.2-1.i386.deb*... paste the output here.

EDIT: Ah, I see you already did. What was the output?

---

### Post by Jewfro_Macabbi on 2006-10-10
Here's the requested output:

> 
jewfro@Mossada:~$ sudo dpkg -i mfc420cnlpr-1.0.2-1.i386.deb
Selecting previously deselected package mfc420cnlpr.
(Reading database ... 112338 files and directories currently installed.)
Preparing to replace mfc420cnlpr 1.0.2-1 (using mfc420cnlpr-1.0.2-1.i386.deb) ...
Unpacking replacement mfc420cnlpr ...
/var/lib/dpkg/info/mfc420cnlpr.postrm: line 6: /etc/init.d/lpd: is a directory
dpkg: warning - old post-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 6: /etc/init.d/lpd: is a directory
dpkg: error processing mfc420cnlpr-1.0.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 126
/var/lib/dpkg/tmp.ci/postrm: line 6: /etc/init.d/lpd: is a directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 126
Errors were encountered while processing:
 mfc420cnlpr-1.0.2-1.i386.deb
jewfro@Mossada:~$



---

### Post by Jussi Kukkonen on 2006-10-10
Looks like the .deb (more specifically the post-removal script) is somehow broken... One lesson to learn here is "Be wary of third party .debs" -- not that you had much choice if you wanted to use your printer.

You could take a look at */var/lib/dpkg/info/mfc420cnlpr.postrm* (line 6) and fix whatever is wrong there, or paste the contents of that file here so we can take a look at it...

EDIT: Now that I think about it (yeah, I know I should do that before replying), this error is probably not enough to make dpkg go crazy like that -- but let's take it one problem at a time.

---

### Post by Jewfro_Macabbi on 2006-10-10
I'd sucessfully used the rpm version of this driver on a Suse install before. The user docs seemed to indicate sucess, so I tried it. And as you said, I'd like to use my printer.

Here's the output you requested:

> 
#!/bin/sh
# ESP Package Manager v3.7.0
if [ -e /etc/init.d/lprng ]; then
/etc/init.d/lprng restart
elif [ -e /etc/init.d/lpd ]; then
/etc/init.d/lpd restart
fi


---

### Post by Jewfro_Macabbi on 2006-10-10
I kept playing with it. Not being able to install anything certainly wasn't working for me, so I figured if I screw it up any worse I'll re-install. I managed to get aptitude,apt-get,synaptic to stop screaming at me, and to let me install software again. I re-installed the brother driver, and made some symbolic links. Not sure if the printer actually works yet, but at least my system works. Here's what I did:

> 
jewfro@Mossada:~$ sudo dpkg -i --force-all mfc420cnlpr-1.0.2-1.i386.deb
Selecting previously deselected package mfc420cnlpr.
(Reading database ... 112338 files and directories currently installed.)
Preparing to replace mfc420cnlpr 1.0.2-1 (using mfc420cnlpr-1.0.2-1.i386.deb) .. .
Unpacking replacement mfc420cnlpr ...
/var/lib/dpkg/info/mfc420cnlpr.postrm: line 6: /etc/init.d/lpd: is a directory
dpkg: warning - old post-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 6: /etc/init.d/lpd: is a directory
dpkg: error processing mfc420cnlpr-1.0.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 126
/var/lib/dpkg/tmp.ci/postrm: line 6: /etc/init.d/lpd: is a directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 126
Errors were encountered while processing:
 mfc420cnlpr-1.0.2-1.i386.deb
jewfro@Mossada:~$ sudo ln -s /etc/init.d/cupsys /etc/init.d/lpd
ln: creating symbolic link `/etc/init.d/lpd/cupsys' to `/etc/init.d/cupsys': Fil e exists
jewfro@Mossada:~$ sudo ln -s /etc/init.d/cupsys /etc/init.d/lprng
jewfro@Mossada:~$ sudo dpkg -i --force-all mfc420cnlpr-1.0.2-1.i386.deb
(Reading database ... 112338 files and directories currently installed.)
Preparing to replace mfc420cnlpr 1.0.2-1 (using mfc420cnlpr-1.0.2-1.i386.deb) .. .
Unpacking replacement mfc420cnlpr ...
 * Restarting Common Unix Printing System: cupsd                         [ ok ]
Setting up mfc420cnlpr (1.0.2-1) ...
mkdir: cannot create directory `/var/spool/lpd/MFC420CN': No such file or direct ory
chown: cannot access `/var/spool/lpd/MFC420CN': No such file or directory
chgrp: cannot access `/var/spool/lpd/MFC420CN': No such file or directory
chmod: cannot access `/var/spool/lpd/MFC420CN': No such file or directory
 * Restarting Common Unix Printing System: cupsd                         [ ok ]

jewfro@Mossada:~$ sudo ln -s /var/spool/lpd/MFC420CN
jewfro@Mossada:~$  sudo dpkg -i --force-all mfc420cnlpr-1.0.2-1.i386.deb
(Reading database ... 112338 files and directories currently installed.)
Preparing to replace mfc420cnlpr 1.0.2-1 (using mfc420cnlpr-1.0.2-1.i386.deb) .. .
Unpacking replacement mfc420cnlpr ...
 * Restarting Common Unix Printing System: cupsd                         [ ok ]
Setting up mfc420cnlpr (1.0.2-1) ...
mkdir: cannot create directory `/var/spool/lpd/MFC420CN': No such file or direct ory
chown: cannot access `/var/spool/lpd/MFC420CN': No such file or directory
chgrp: cannot access `/var/spool/lpd/MFC420CN': No such file or directory
chmod: cannot access `/var/spool/lpd/MFC420CN': No such file or directory
ln: creating symbolic link `/usr/lib/libbrcompij2.so.1.0' to `/usr/lib/libbrcomp ij2.so.1.0.2': File exists
ln: creating symbolic link `/usr/lib/libbrcompij2.so.1' to `/usr/lib/libbrcompij 2.so.1.0.2': File exists
ln: creating symbolic link `/usr/lib/libbrcompij2.so' to `/usr/lib/libbrcompij2. so.1.0.2': File exists
 * Restarting Common Unix Printing System: cupsd                         [ ok ]

jewfro@Mossada:~$ ls


If I did something horribly wrong, do tell me...

---

