---
title: "apt/dpkg problem"
date: 2007-03-09
forum: General Help
---

### Post by coolclassic on 2007-03-09
I have a problem with a broken package the errors I get are as follows:

using Adept: This error appears whilst trying to reinstall, install or purge:

"There was an error committing changes. Possibly there was a problem downloading some packages or the commit would break packages".


Using the command line dpkg gives:

dpkg: error processing turboprint (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 turboprint

dpkg: error processing turboprint (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 turboprint

dpkg: error processing turboprint (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 turboprint


I have tried "sudo dpkg --configure -a" with no success
Also I cannot use Adept or the command line to install/delete packages until this problem is solved. 

This problem started when installing a debs turboprint file the install did not complete.

---

### Post by invalid on 2007-03-09
Are you attempting to install a saved .deb file?
What is the exact command you are using, and are you sure the file is in the same directory?
Please also put output in code tags, so we can see it a little more clearly.

---

### Post by coolclassic on 2007-03-12
The command used to install turboprint:

desktop:~/Software$ sudo dpkg -i turboprint_1.95-2_i386.deb   

The error message i received when trying to install is:

Selecting previously deselected package turboprint.
(Reading database ... 167354 files and directories currently installed.)
Preparing to replace turboprint 1.95-2 (using turboprint_1.95-2_i386.deb) ...
/var/lib/dpkg/info/turboprint.prerm: 3: /usr/share/turboprint/lib/uninstall-pre: not found
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 3: /usr/share/turboprint/lib/uninstall-pre: not found
dpkg: error processing turboprint_1.95-2_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/turboprint.postinst: 3: /usr/share/turboprint/lib/install-post: not found
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 turboprint_1.95-2_i386.deb

At this point the install process freezes.

Since this error I have been unable to use apt or adept/synaptic.

To attempt to clear the problem I have tried the folowing commands:

dpkg -r turboprint
dpkg -p turboprint
The errors produced by these commands are listed in my first post
sudo dpkg --configure -a   this has no effect

---

### Post by zvacet on 2007-03-12
It seems that old version is making you trouble.Uninstall all versions(manualy if you have to),and then try to install new version.

---

### Post by coolclassic on 2007-03-14
Thanks zvacet problem solved. I don't know why I never thought of that. Turboprint unistaller doesn't remove everthing, there was some files left over in var /lib/dpkg/info

---

