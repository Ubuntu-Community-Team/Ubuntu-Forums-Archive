---
title: "Broken Package - removal script error"
date: 2006-07-09
forum: General Help
---

### Post by helpdeskdan on 2006-07-09
Installed a defective package; can't replace it with older version.  Can not remove package either.  Any ideas?  

dan@ubuntu:~/Desktop$ sudo dpkg -i --force-all xfonts-dosemu_1.2.2-3build1_all.deb
(Reading database ... 94477 files and directories currently installed.)
Preparing to replace xfonts-dosemu 1.2.2-5ubuntu1 (using xfonts-dosemu_1.2.2-3build1_all.deb) ...
Unpacking replacement xfonts-dosemu ...
usage error: unrecognized option
Usage: update-fonts-dir DIRECTORY ...
       update-fonts-dir { -h | --help }
This program is a wrapper for mkfontdir(1x) that is primarily useful to Debian
package maintainer scripts.  See update-fonts-dir(8) for more information.
Options:
    -h, --help                               display this usage message and exitdpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: error processing xfonts-dosemu_1.2.2-3build1_all.deb (--install):
 there is no script in the new version of the package - giving up
Errors were encountered while processing:
 xfonts-dosemu_1.2.2-3build1_all.deb
dan@ubuntu:~/Desktop$


Thank you for reading this thread.  
-Dan

---

### Post by helpdeskdan on 2006-07-09
If it is of any consequence, I can now no longer install packages due to this error!  I'm dead in the water; I'll have to reinstall from scratch if I can't fix this.

---

### Post by yopnono on 2006-07-10
Have you tried to totally remove/force from synaptic?
And you can always search for the files in the computer, and remove them by hand. And try to install the deb again.

---

### Post by PriceChild on 2006-07-10
Yeah, if you go into synaptic, then put a filter on broken packages... you can remove it from there.

---

### Post by helpdeskdan on 2006-07-10
Thank you kindly for your replies. 

Nothing can remove it - not synaptic, not aptitude, not even dpkg with force-all!  Even if I were to manually remove the files, I believe apt would still think it was installed.  As it thinks the package is broken, no matter what I try to install, it tries to deal with this first.  Then, it exits with a status 2 and will not go on to install whatever I selected.  I'm hosed!

I think what I need is some way to remove it from the apt-cache or something.  I don't care about the files; I'll overwrite them with a new package or compile my own.

---

### Post by helpdeskdan on 2006-07-11
I was able to remove the package by commenting everything out in the removal script in xfonts-dosemu.postrm located in /var/lib/dpkg/info.

#!/bin/sh
#set -e
# Automatically added by dh_installxfonts
#if [ -x "`which update-fonts-dir 2>/dev/null`" ]; then
#update-fonts-dir --x11r7-layout misc;update-fonts-alias misc
#fi
# End automatically added section

Not exactly sure what bypassing update-fonts-dir screwed up, but it's much better than having a hosed system!

---

### Post by elfgoh on 2006-10-28
> **helpdeskdan said:**
> I was able to remove the package by commenting everything out in the removal script in xfonts-dosemu.postrm located in /var/lib/dpkg/info.

#!/bin/sh
#set -e
# Automatically added by dh_installxfonts
#if [ -x "`which update-fonts-dir 2>/dev/null`" ]; then
#update-fonts-dir --x11r7-layout misc;update-fonts-alias misc
#fi
# End automatically added section

Not exactly sure what bypassing update-fonts-dir screwed up, but it's much better than having a hosed system!

Hi, this should be a more elegant solution from [http://ubuntuforums.org/showthread.php?t=213711](http://ubuntuforums.org/showthread.php?t=213711)

Just change 

**update-fonts-dir --x11r7-layout misc**

to 

**update-fonts-dir misc**

HTH

---

