---
title: "Openoffice... plz... help"
date: 2007-06-25
forum: General Help
---

### Post by Gael05 on 2007-06-25
Hi.... 
I have download the last openoffice 2.2.1, and when I install it, it says:

root@gael-desktop:~/Openoffice/OOF680_m18_native_packed-1_en-US.9161/RPMS# rpm -Uvih *rpm
error: Failed dependencies:
        /bin/basename is needed by jre-1.6.0-fcs.i586
        /bin/cat is needed by jre-1.6.0-fcs.i586
        /bin/cp is needed by jre-1.6.0-fcs.i586
        /bin/gawk is needed by jre-1.6.0-fcs.i586
        /bin/grep is needed by jre-1.6.0-fcs.i586
        /bin/ln is needed by jre-1.6.0-fcs.i586
        /bin/ls is needed by jre-1.6.0-fcs.i586
        /bin/mkdir is needed by jre-1.6.0-fcs.i586
        /bin/mv is needed by jre-1.6.0-fcs.i586
        /bin/pwd is needed by jre-1.6.0-fcs.i586
        /bin/rm is needed by jre-1.6.0-fcs.i586
        /bin/sed is needed by jre-1.6.0-fcs.i586
        /bin/sort is needed by jre-1.6.0-fcs.i586
        /bin/touch is needed by jre-1.6.0-fcs.i586
        /usr/bin/cut is needed by jre-1.6.0-fcs.i586
        /usr/bin/dirname is needed by jre-1.6.0-fcs.i586
        /usr/bin/expr is needed by jre-1.6.0-fcs.i586
        /usr/bin/find is needed by jre-1.6.0-fcs.i586
        /usr/bin/tail is needed by jre-1.6.0-fcs.i586
        /usr/bin/tr is needed by jre-1.6.0-fcs.i586
        /usr/bin/wc is needed by jre-1.6.0-fcs.i586
        /bin/sh is needed by jre-1.6.0-fcs.i586
        /bin/sh is needed by openoffice.org-core10-2.2.1-9161.i586
        libgnomevfs-2.so.0 is needed by openoffice.org-gnome-integration-2.2.1-9161.i586
        libgconf-2.so.4 is needed by openoffice.org-gnome-integration-2.2.1-9161.i586
root@gael-desktop:~/Openoffice/OOF680_m18_native_packed-1_en-US.9161/RPMS# 

I need the two files: libgnomevfs-2.so.0 and libgconf-2.so.4....
Where can I get them and how to...

---

### Post by AlexThomson_NZ on 2007-06-25
Yikes- I assume you are using rpm for a reason rather than synaptic? :) (fedora per-chance?)

Anyways, rpmfind and pbone are great sites for finding these sort of bits and peices, used them a lot back when I used rpm based distros.

---

### Post by stchman on 2007-06-25
> **Gael05 said:**
> Hi.... 
I have download the last openoffice 2.2.1, and when I install it, it says:

root@gael-desktop:~/Openoffice/OOF680_m18_native_packed-1_en-US.9161/RPMS# rpm -Uvih *rpm
error: Failed dependencies:
        /bin/basename is needed by jre-1.6.0-fcs.i586
        /bin/cat is needed by jre-1.6.0-fcs.i586
        /bin/cp is needed by jre-1.6.0-fcs.i586
        /bin/gawk is needed by jre-1.6.0-fcs.i586
        /bin/grep is needed by jre-1.6.0-fcs.i586
        /bin/ln is needed by jre-1.6.0-fcs.i586
        /bin/ls is needed by jre-1.6.0-fcs.i586
        /bin/mkdir is needed by jre-1.6.0-fcs.i586
        /bin/mv is needed by jre-1.6.0-fcs.i586
        /bin/pwd is needed by jre-1.6.0-fcs.i586
        /bin/rm is needed by jre-1.6.0-fcs.i586
        /bin/sed is needed by jre-1.6.0-fcs.i586
        /bin/sort is needed by jre-1.6.0-fcs.i586
        /bin/touch is needed by jre-1.6.0-fcs.i586
        /usr/bin/cut is needed by jre-1.6.0-fcs.i586
        /usr/bin/dirname is needed by jre-1.6.0-fcs.i586
        /usr/bin/expr is needed by jre-1.6.0-fcs.i586
        /usr/bin/find is needed by jre-1.6.0-fcs.i586
        /usr/bin/tail is needed by jre-1.6.0-fcs.i586
        /usr/bin/tr is needed by jre-1.6.0-fcs.i586
        /usr/bin/wc is needed by jre-1.6.0-fcs.i586
        /bin/sh is needed by jre-1.6.0-fcs.i586
        /bin/sh is needed by openoffice.org-core10-2.2.1-9161.i586
        libgnomevfs-2.so.0 is needed by openoffice.org-gnome-integration-2.2.1-9161.i586
        libgconf-2.so.4 is needed by openoffice.org-gnome-integration-2.2.1-9161.i586
root@gael-desktop:~/Openoffice/OOF680_m18_native_packed-1_en-US.9161/RPMS# 

I need the two files: libgnomevfs-2.so.0 and libgconf-2.so.4....
Where can I get them and how to...

To install Openoffice from OO's website you will need to convert the .rpm to .deb.

You need to install alien

sudo apt-get install alien

Then change to the RPMS folder and type the following:

sudo alien --scripts --keep-version -d *.rpm

Once you have converted the packages to .deb then install them along with the debian menus in desktop integration.

---

