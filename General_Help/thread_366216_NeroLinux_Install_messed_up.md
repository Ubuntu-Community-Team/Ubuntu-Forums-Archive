---
title: "NeroLinux Install messed up"
date: 2007-02-20
forum: General Help
---

### Post by chandler on 2007-02-20
I have Ubuntu 6.10 and I just tried to install nerolinux.  During the install it messed up... Now whenevr I try to update, install via synaptic, or automatix, I get an error, generally stating: E: The package nerolinux needs to be reinstalled, but I can't find an archive for it.  So I tried to reinstall, but the .deb installer says the file is corrupt or invalid permissions...  I chown 777 the file, and still get the error.  I tried removing it then redownloading through the HTTP mirror.  That didn't work either.  So, now I'm lost.  I really just want it gone, but can't seem to remove it either.

---

### Post by swejuggalo on 2007-02-20
run " sudo dpkg -r nerolinux-2.1.0.4-x86.deb " in terminal if needed. Then download NeroLinux 2.0.0.3 from [ftp://ftp5.usw.nero.com/software/NeroLINUX/](ftp://ftp5.usw.nero.com/software/NeroLINUX/) . All the older versions are here if downgrading is needed. sudo dpkg -i nerolinux-2.1.0.3-x86.deb does the job, or just click and install as usuall. Worked for me after the 2.0.0.4 failed to install....

---

### Post by chggr on 2007-02-20
Why use nerolinux when there is K3b?

I am trying to keep away from not Opensource software and I have never regretted that...

---

### Post by swejuggalo on 2007-02-20
I use both NeroLinux and k3b (the latest version, rc6 and upgrading and testing often). Both has their downsides and upsides.
NeroLinux is simple and small, k3b is big and powerful.
NeroLinux has more or less all functionality built in. k3b needs KDE and uses other software like dvd-rw-tools to do the actual burning (the bugs can come from...eh... everywhere? :)  ).
It is a matter of taste, functionality, old habit from windows, open source or not...
For me it just...hrm... 2 programs is better than 1? :)

---

### Post by chandler on 2007-02-21
Had some errors, but fixed.  Thanks :)




sudo dpkg -r nerolinux-2.1.0.4-x86.deb
Password:
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !




william@williamubuntu:~$ sudo dpkg -r nerolinux
dpkg: error processing nerolinux (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 nerolinux




william@williamubuntu:~$cd Desktop/





william@williamubuntu:~/Desktop$ sudo dpkg -i nerolinux-2.1.0.3-x86.deb
Selecting previously deselected package nerolinux.
(Reading database ... 132838 files and directories currently installed.)
Preparing to replace nerolinux 2.1.0.4-1 (using nerolinux-2.1.0.3-x86.deb) ...
/var/lib/dpkg/info/nerolinux.prerm: 31: Syntax error: "(" unexpected
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 31: function: not found
/var/lib/dpkg/tmp.ci/prerm: 44: RemoveMenuLinks: not found
dpkg: ... it looks like that went OK.
Unpacking replacement nerolinux ...
Setting up nerolinux (2.1.0.3-1) ...
/var/lib/dpkg/info/nerolinux.postinst: 70: function: not found
/var/lib/dpkg/info/nerolinux.postinst: 85: cannot create configure/NeroLINUX.desktop: Directory nonexistent
/var/lib/dpkg/info/nerolinux.postinst: 85: cannot create configure/NeroLINUX.desktop: Directory nonexistent
/var/lib/dpkg/info/nerolinux.postinst: 85: cannot create configure/NeroLINUX.desktop: Directory nonexistent
/var/lib/dpkg/info/nerolinux.postinst: 93: function: not found
/var/lib/dpkg/info/nerolinux.postinst: 103: CreateDesktopFile: not found
Unsupported Linux distribution. Please copy the '.desktop' file manually.
This file is /usr/share/nero/desktop/NeroLINUX.desktop.
/var/lib/dpkg/info/nerolinux.postinst: 109: CreateDesktopFile: not found
Operating System: Debian GNU/Linux version testing/unstable
grep: Unmatched [ or [^
/var/lib/dpkg/info/nerolinux.postinst: 544: 3.1]: not found
/var/lib/dpkg/info/nerolinux.postinst: 544: ShowDefaultLocation: not found

william@williamubuntu:~/Desktop$

---

### Post by chggr on 2007-02-21
> **swejuggalo said:**
> k3b needs KDE and uses other software like dvd-rw-tools to do the actual burning (the bugs can come from...eh... everywhere? :)  ).

K3b does not need KDE! I am using K3b and Gnome...

---

### Post by Hilding on 2007-02-21
I couldn't remove/uninstall nerolinux but when I followed swejuggalo's advice it worked.

---

### Post by swejuggalo on 2007-02-21
Doesn't need KDE?!

Directly from k3bs own page:

"K3b 0.12 Requirements

    * KDE >= 3.2 - KDE is the great window manager, the powerful desktop, the very powerful c++ library K3b is based on, and a lot of programs.
    * QT >= 3.2 KDE 3.2 requires the QT library version 3.2, a cross-platform GUI development toolkit. Since K3b is a threaded application QT needs to be compiled with threading support enabled.
    * cdrecord/mkisofs - Cdrecord creates home-burned CDs with a CD-R/CD-RW recorder.
    * dvd+rw-tools - The DVD+RW-Tools are used to burn and format DVD+R(W) and DVD-R(W) media. For DVD+R Double Layer burning version >= 5.20.4.10.8 is required.
"

In other words, KDE is needed, but not necessarily have too be the active window manger. I use Gnome too. But parts of KDE is needed for k3b too work.

---

### Post by swejuggalo on 2007-02-21
By the way... NeroLinux is now updated from 2.0.0.4 to 2.0.0.4b. It now works to install without any problems (atleast on my Ubuntu, 6.10).

---

