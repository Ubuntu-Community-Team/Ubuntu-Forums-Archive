---
title: "Can't run Pantheon-Files from terminal"
date: 2018-02-17
forum: General Help
---

### Post by Hasimir on 2018-02-17
For some reason I **can** launch Pantheon-Files from the dash but I **can't** from terminal o_O
If I type **whereis pantheon-files** the result returned is not an error, but it blank, empty.
If I type **pantheon-files** alone I just get the "command not found" error.

The command **apt-cache show pantheon-files** returns this result:
```

Priority: optional
Section: x11
Installed-Size: 3769
Maintainer: Cody Garver <cody@elementary.io>
Architecture: amd64
Version: 0.3.6+r2746+pkg68~daily~ubuntu0.4.1.1
Recommends: contractor, gvfs-backends, exfat-fuse, tumbler-plugins-extra
Depends: gvfs, libpantheon-files-core0 (= 0.3.6+r2746+pkg68~daily~ubuntu0.4.1.1), libpantheon-files-widgets0 (= 0.3.6+r2746+pkg68~daily~ubuntu0.4.1.1), tumbler, dconf-gsettings-backend | gsettings-backend, libc6 (>= 2.4), libcairo2 (>= 1.2.4), libdbusmenu-glib4 (>= 0.4.2), libgdk-pixbuf2.0-0 (>= 2.23.0), libgee-0.8-2 (>= 0.8.3), libglib2.0-0 (>= 2.39.4), libgranite4 (>= 0.5), libgtk-3-0 (>= 3.14), libpango-1.0-0 (>= 1.20.0), libplank1 (>= 0.11.0), libsqlite3-0 (>= 3.5.9), libunity9 (>= 3.4.6), libzeitgeist-2.0-0 (>= 0.9.9)
Filename: pool/main/p/pantheon-files/pantheon-files_0.3.6+r2746+pkg68~daily~ubuntu0.4.1.1_amd64.deb
Size: 616650
MD5sum: d043f8dc9d99735edbf4d9b7cc4f88e2
SHA1: 19e292689db1eb7b12d71f0b3e83713ed0263549
SHA256: fe79b05466bf4276ab12f14da81352ed83241c7fc26a0c450dcfc1332df8021f
Description-en: File manager for the Pantheon desktop
 Pantheon Files is a modern file manager originally
 designed for the Pantheon desktop environment.
 .
 It features:
 - Column view to effortlessly traverse complex folder hierarchies,
 in addition to Icon and Tree views
 - Contextual actions on files and folders provided by Contractor
 - Transparent support for remote servers and network shares
 - Compliance with elementary HIG, e.g. lets you restore closed tabs
 - Session persistence - take up where you left!
Description-md5: bb358b14d09ba232c3c28c30bb165f39

```

Why can't I launch the program?
Where are its files and folders located?

---

### Post by TheFu on 2018-02-17
Until seeing your post, I'd never heard of Pantheon, so I don't have THE answer.

I can offer a few ideas that might be helpful.

Program names don't always match package names. 
I'd do a **man -k pantheon** to see what comes up.

There are also ways to ask APT which files are included in the package.  Let me look that up ... in the manpage.   [https://askubuntu.com/questions/32507/how-do-i-get-a-list-of-installed-files-from-a-package](https://askubuntu.com/questions/32507/how-do-i-get-a-list-of-installed-files-from-a-package) says to use 
$ dpkg-query -L <package_name>
 or
$ dpkg-deb -c <package_name.deb>

---

### Post by Hasimir on 2018-02-17
Thanks for the answer TheFu :)
Pantheon-Files is the file manager of the Pantheon Desktop environment, native to Elementary Linux.
running one of the commands you provided I got this result
```

** dpkg-query -L pantheon-files**
/.
/usr
/usr/lib
/usr/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu/gtk-3.0
/usr/lib/x86_64-linux-gnu/gtk-3.0/modules
/usr/lib/x86_64-linux-gnu/gtk-3.0/modules/libpantheon-filechooser-module.so
/usr/lib/x86_64-linux-gnu/io.elementary.files
/usr/lib/x86_64-linux-gnu/io.elementary.files/plugins
/usr/lib/x86_64-linux-gnu/io.elementary.files/plugins/core
/usr/lib/x86_64-linux-gnu/io.elementary.files/plugins/core/libpantheon-filesctags.so
/usr/lib/x86_64-linux-gnu/io.elementary.files/plugins/core/pantheon-files-ctags.plug
/usr/lib/x86_64-linux-gnu/io.elementary.files/plugins/core/libnetwork-places.so
/usr/lib/x86_64-linux-gnu/io.elementary.files/plugins/core/libpantheon-files-contractor.so
/usr/lib/x86_64-linux-gnu/io.elementary.files/plugins/core/contractor.plug
/usr/lib/x86_64-linux-gnu/io.elementary.files/plugins/core/libpantheon-filestrash.so
/usr/lib/x86_64-linux-gnu/io.elementary.files/plugins/core/pantheon-files-trash.plug
/usr/lib/x86_64-linux-gnu/io.elementary.files/plugins/core/network-places.plug
/usr/bin
/usr/bin/io.elementary.files
/usr/bin/io.elementary.files-daemon
/usr/bin/io.elementary.files-pkexec
/usr/share
/usr/share/io.elementary.files
/usr/share/io.elementary.files/ui
/usr/share/io.elementary.files/ui/directory_view_popup.ui
/usr/share/doc
/usr/share/doc/pantheon-files
/usr/share/doc/pantheon-files/copyright
/usr/share/doc/pantheon-files/changelog.gz
/usr/share/pixmaps
/usr/share/pixmaps/io.elementary.files
/usr/share/pixmaps/io.elementary.files/thumbnail_frame.png
/usr/share/pixmaps/io.elementary.files/poof.png
/usr/share/dbus-1
/usr/share/dbus-1/services
/usr/share/dbus-1/services/io.elementary.files.FileManager1.service
/usr/share/vala
/usr/share/vala/vapi
/usr/share/vala/vapi/pantheon-files-core.deps
/usr/share/vala/vapi/pantheon-files-core.vapi
/usr/share/vala/vapi/pantheon-files-core-C.vapi
/usr/share/vala/vapi/pantheon-files-widgets.deps
/usr/share/vala/vapi/pantheon-files-widgets.vapi
/usr/share/appdata
/usr/share/appdata/io.elementary.files.appdata.xml
/usr/share/polkit-1
/usr/share/polkit-1/actions
/usr/share/polkit-1/actions/io.elementary.files.policy
/usr/share/locale
/usr/share/locale/ur
/usr/share/locale/ur/LC_MESSAGES
/usr/share/locale/ur/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/so
/usr/share/locale/so/LC_MESSAGES
/usr/share/locale/so/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/mo
/usr/share/locale/mo/LC_MESSAGES
/usr/share/locale/mo/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/am
/usr/share/locale/am/LC_MESSAGES
/usr/share/locale/am/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/yi
/usr/share/locale/yi/LC_MESSAGES
/usr/share/locale/yi/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/la
/usr/share/locale/la/LC_MESSAGES
/usr/share/locale/la/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/nb
/usr/share/locale/nb/LC_MESSAGES
/usr/share/locale/nb/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ig
/usr/share/locale/ig/LC_MESSAGES
/usr/share/locale/ig/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/en_AU
/usr/share/locale/en_AU/LC_MESSAGES
/usr/share/locale/en_AU/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/si
/usr/share/locale/si/LC_MESSAGES
/usr/share/locale/si/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/bo
/usr/share/locale/bo/LC_MESSAGES
/usr/share/locale/bo/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/rue
/usr/share/locale/rue/LC_MESSAGES
/usr/share/locale/rue/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/dz
/usr/share/locale/dz/LC_MESSAGES
/usr/share/locale/dz/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/vi
/usr/share/locale/vi/LC_MESSAGES
/usr/share/locale/vi/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/nd
/usr/share/locale/nd/LC_MESSAGES
/usr/share/locale/nd/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/to
/usr/share/locale/to/LC_MESSAGES
/usr/share/locale/to/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ay
/usr/share/locale/ay/LC_MESSAGES
/usr/share/locale/ay/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/an
/usr/share/locale/an/LC_MESSAGES
/usr/share/locale/an/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/cv
/usr/share/locale/cv/LC_MESSAGES
/usr/share/locale/cv/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/se
/usr/share/locale/se/LC_MESSAGES
/usr/share/locale/se/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ast
/usr/share/locale/ast/LC_MESSAGES
/usr/share/locale/ast/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ht
/usr/share/locale/ht/LC_MESSAGES
/usr/share/locale/ht/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/hr
/usr/share/locale/hr/LC_MESSAGES
/usr/share/locale/hr/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/pt
/usr/share/locale/pt/LC_MESSAGES
/usr/share/locale/pt/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ba
/usr/share/locale/ba/LC_MESSAGES
/usr/share/locale/ba/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/dv
/usr/share/locale/dv/LC_MESSAGES
/usr/share/locale/dv/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/cu
/usr/share/locale/cu/LC_MESSAGES
/usr/share/locale/cu/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ty
/usr/share/locale/ty/LC_MESSAGES
/usr/share/locale/ty/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/sn
/usr/share/locale/sn/LC_MESSAGES
/usr/share/locale/sn/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/tr
/usr/share/locale/tr/LC_MESSAGES
/usr/share/locale/tr/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/sd
/usr/share/locale/sd/LC_MESSAGES
/usr/share/locale/sd/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/io
/usr/share/locale/io/LC_MESSAGES
/usr/share/locale/io/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/es
/usr/share/locale/es/LC_MESSAGES
/usr/share/locale/es/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/kr
/usr/share/locale/kr/LC_MESSAGES
/usr/share/locale/kr/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/or
/usr/share/locale/or/LC_MESSAGES
/usr/share/locale/or/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/tw
/usr/share/locale/tw/LC_MESSAGES
/usr/share/locale/tw/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/lg
/usr/share/locale/lg/LC_MESSAGES
/usr/share/locale/lg/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/tt
/usr/share/locale/tt/LC_MESSAGES
/usr/share/locale/tt/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/iu
/usr/share/locale/iu/LC_MESSAGES
/usr/share/locale/iu/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/hi
/usr/share/locale/hi/LC_MESSAGES
/usr/share/locale/hi/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/na
/usr/share/locale/na/LC_MESSAGES
/usr/share/locale/na/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/gu
/usr/share/locale/gu/LC_MESSAGES
/usr/share/locale/gu/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/kn
/usr/share/locale/kn/LC_MESSAGES
/usr/share/locale/kn/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/kl
/usr/share/locale/kl/LC_MESSAGES
/usr/share/locale/kl/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/hu
/usr/share/locale/hu/LC_MESSAGES
/usr/share/locale/hu/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/te
/usr/share/locale/te/LC_MESSAGES
/usr/share/locale/te/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ro
/usr/share/locale/ro/LC_MESSAGES
/usr/share/locale/ro/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/cr
/usr/share/locale/cr/LC_MESSAGES
/usr/share/locale/cr/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/lb
/usr/share/locale/lb/LC_MESSAGES
/usr/share/locale/lb/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ko
/usr/share/locale/ko/LC_MESSAGES
/usr/share/locale/ko/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ku
/usr/share/locale/ku/LC_MESSAGES
/usr/share/locale/ku/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/zh
/usr/share/locale/zh/LC_MESSAGES
/usr/share/locale/zh/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/tn
/usr/share/locale/tn/LC_MESSAGES
/usr/share/locale/tn/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/sg
/usr/share/locale/sg/LC_MESSAGES
/usr/share/locale/sg/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/pi
/usr/share/locale/pi/LC_MESSAGES
/usr/share/locale/pi/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ps
/usr/share/locale/ps/LC_MESSAGES
/usr/share/locale/ps/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/is
/usr/share/locale/is/LC_MESSAGES
/usr/share/locale/is/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/za
/usr/share/locale/za/LC_MESSAGES
/usr/share/locale/za/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/en_GB
/usr/share/locale/en_GB/LC_MESSAGES
/usr/share/locale/en_GB/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/sv
/usr/share/locale/sv/LC_MESSAGES
/usr/share/locale/sv/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/kj
/usr/share/locale/kj/LC_MESSAGES
/usr/share/locale/kj/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ts
/usr/share/locale/ts/LC_MESSAGES
/usr/share/locale/ts/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/eo
/usr/share/locale/eo/LC_MESSAGES
/usr/share/locale/eo/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/my
/usr/share/locale/my/LC_MESSAGES
/usr/share/locale/my/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/aa
/usr/share/locale/aa/LC_MESSAGES
/usr/share/locale/aa/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/as
/usr/share/locale/as/LC_MESSAGES
/usr/share/locale/as/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ms
/usr/share/locale/ms/LC_MESSAGES
/usr/share/locale/ms/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/lt
/usr/share/locale/lt/LC_MESSAGES
/usr/share/locale/lt/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/tk
/usr/share/locale/tk/LC_MESSAGES
/usr/share/locale/tk/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/su
/usr/share/locale/su/LC_MESSAGES
/usr/share/locale/su/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/mi
/usr/share/locale/mi/LC_MESSAGES
/usr/share/locale/mi/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/de
/usr/share/locale/de/LC_MESSAGES
/usr/share/locale/de/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/wa
/usr/share/locale/wa/LC_MESSAGES
/usr/share/locale/wa/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/pa
/usr/share/locale/pa/LC_MESSAGES
/usr/share/locale/pa/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/id
/usr/share/locale/id/LC_MESSAGES
/usr/share/locale/id/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ce
/usr/share/locale/ce/LC_MESSAGES
/usr/share/locale/ce/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/nv
/usr/share/locale/nv/LC_MESSAGES
/usr/share/locale/nv/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ee
/usr/share/locale/ee/LC_MESSAGES
/usr/share/locale/ee/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/fr_CA
/usr/share/locale/fr_CA/LC_MESSAGES
/usr/share/locale/fr_CA/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/fy
/usr/share/locale/fy/LC_MESSAGES
/usr/share/locale/fy/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/gv
/usr/share/locale/gv/LC_MESSAGES
/usr/share/locale/gv/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/wo
/usr/share/locale/wo/LC_MESSAGES
/usr/share/locale/wo/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ki
/usr/share/locale/ki/LC_MESSAGES
/usr/share/locale/ki/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/oj
/usr/share/locale/oj/LC_MESSAGES
/usr/share/locale/oj/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/zh_CN
/usr/share/locale/zh_CN/LC_MESSAGES
/usr/share/locale/zh_CN/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/bi
/usr/share/locale/bi/LC_MESSAGES
/usr/share/locale/bi/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/os
/usr/share/locale/os/LC_MESSAGES
/usr/share/locale/os/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/br
/usr/share/locale/br/LC_MESSAGES
/usr/share/locale/br/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/zh_HK
/usr/share/locale/zh_HK/LC_MESSAGES
/usr/share/locale/zh_HK/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/hz
/usr/share/locale/hz/LC_MESSAGES
/usr/share/locale/hz/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/sa
/usr/share/locale/sa/LC_MESSAGES
/usr/share/locale/sa/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ss
/usr/share/locale/ss/LC_MESSAGES
/usr/share/locale/ss/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ie
/usr/share/locale/ie/LC_MESSAGES
/usr/share/locale/ie/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/bh
/usr/share/locale/bh/LC_MESSAGES
/usr/share/locale/bh/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/af
/usr/share/locale/af/LC_MESSAGES
/usr/share/locale/af/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ta
/usr/share/locale/ta/LC_MESSAGES
/usr/share/locale/ta/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/mk
/usr/share/locale/mk/LC_MESSAGES
/usr/share/locale/mk/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/pt_BR
/usr/share/locale/pt_BR/LC_MESSAGES
/usr/share/locale/pt_BR/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ug
/usr/share/locale/ug/LC_MESSAGES
/usr/share/locale/ug/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ne
/usr/share/locale/ne/LC_MESSAGES
/usr/share/locale/ne/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/nl
/usr/share/locale/nl/LC_MESSAGES
/usr/share/locale/nl/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/da
/usr/share/locale/da/LC_MESSAGES
/usr/share/locale/da/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/bm
/usr/share/locale/bm/LC_MESSAGES
/usr/share/locale/bm/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/lv
/usr/share/locale/lv/LC_MESSAGES
/usr/share/locale/lv/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/om
/usr/share/locale/om/LC_MESSAGES
/usr/share/locale/om/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/bs
/usr/share/locale/bs/LC_MESSAGES
/usr/share/locale/bs/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/yo
/usr/share/locale/yo/LC_MESSAGES
/usr/share/locale/yo/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ak
/usr/share/locale/ak/LC_MESSAGES
/usr/share/locale/ak/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/li
/usr/share/locale/li/LC_MESSAGES
/usr/share/locale/li/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/qu
/usr/share/locale/qu/LC_MESSAGES
/usr/share/locale/qu/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/av
/usr/share/locale/av/LC_MESSAGES
/usr/share/locale/av/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/vo
/usr/share/locale/vo/LC_MESSAGES
/usr/share/locale/vo/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/hy
/usr/share/locale/hy/LC_MESSAGES
/usr/share/locale/hy/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/nr
/usr/share/locale/nr/LC_MESSAGES
/usr/share/locale/nr/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/fj
/usr/share/locale/fj/LC_MESSAGES
/usr/share/locale/fj/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/cs
/usr/share/locale/cs/LC_MESSAGES
/usr/share/locale/cs/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/zu
/usr/share/locale/zu/LC_MESSAGES
/usr/share/locale/zu/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ru
/usr/share/locale/ru/LC_MESSAGES
/usr/share/locale/ru/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ab
/usr/share/locale/ab/LC_MESSAGES
/usr/share/locale/ab/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/he
/usr/share/locale/he/LC_MESSAGES
/usr/share/locale/he/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/sl
/usr/share/locale/sl/LC_MESSAGES
/usr/share/locale/sl/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ff
/usr/share/locale/ff/LC_MESSAGES
/usr/share/locale/ff/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/sq
/usr/share/locale/sq/LC_MESSAGES
/usr/share/locale/sq/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/bg
/usr/share/locale/bg/LC_MESSAGES
/usr/share/locale/bg/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/rn
/usr/share/locale/rn/LC_MESSAGES
/usr/share/locale/rn/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ae
/usr/share/locale/ae/LC_MESSAGES
/usr/share/locale/ae/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ha
/usr/share/locale/ha/LC_MESSAGES
/usr/share/locale/ha/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/gd
/usr/share/locale/gd/LC_MESSAGES
/usr/share/locale/gd/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/rw
/usr/share/locale/rw/LC_MESSAGES
/usr/share/locale/rw/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/az
/usr/share/locale/az/LC_MESSAGES
/usr/share/locale/az/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/fi
/usr/share/locale/fi/LC_MESSAGES
/usr/share/locale/fi/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ka
/usr/share/locale/ka/LC_MESSAGES
/usr/share/locale/ka/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/fa
/usr/share/locale/fa/LC_MESSAGES
/usr/share/locale/fa/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/mn
/usr/share/locale/mn/LC_MESSAGES
/usr/share/locale/mn/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/bn
/usr/share/locale/bn/LC_MESSAGES
/usr/share/locale/bn/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/cy
/usr/share/locale/cy/LC_MESSAGES
/usr/share/locale/cy/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/kg
/usr/share/locale/kg/LC_MESSAGES
/usr/share/locale/kg/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ik
/usr/share/locale/ik/LC_MESSAGES
/usr/share/locale/ik/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/mg
/usr/share/locale/mg/LC_MESSAGES
/usr/share/locale/mg/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/st
/usr/share/locale/st/LC_MESSAGES
/usr/share/locale/st/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/zh_TW
/usr/share/locale/zh_TW/LC_MESSAGES
/usr/share/locale/zh_TW/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/xh
/usr/share/locale/xh/LC_MESSAGES
/usr/share/locale/xh/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ng
/usr/share/locale/ng/LC_MESSAGES
/usr/share/locale/ng/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/gn
/usr/share/locale/gn/LC_MESSAGES
/usr/share/locale/gn/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/tl
/usr/share/locale/tl/LC_MESSAGES
/usr/share/locale/tl/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ml
/usr/share/locale/ml/LC_MESSAGES
/usr/share/locale/ml/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ky
/usr/share/locale/ky/LC_MESSAGES
/usr/share/locale/ky/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ar
/usr/share/locale/ar/LC_MESSAGES
/usr/share/locale/ar/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ks
/usr/share/locale/ks/LC_MESSAGES
/usr/share/locale/ks/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ja
/usr/share/locale/ja/LC_MESSAGES
/usr/share/locale/ja/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/sr
/usr/share/locale/sr/LC_MESSAGES
/usr/share/locale/sr/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/co
/usr/share/locale/co/LC_MESSAGES
/usr/share/locale/co/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ln
/usr/share/locale/ln/LC_MESSAGES
/usr/share/locale/ln/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/uk
/usr/share/locale/uk/LC_MESSAGES
/usr/share/locale/uk/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/gl
/usr/share/locale/gl/LC_MESSAGES
/usr/share/locale/gl/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/fr
/usr/share/locale/fr/LC_MESSAGES
/usr/share/locale/fr/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/lu
/usr/share/locale/lu/LC_MESSAGES
/usr/share/locale/lu/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ca
/usr/share/locale/ca/LC_MESSAGES
/usr/share/locale/ca/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/fo
/usr/share/locale/fo/LC_MESSAGES
/usr/share/locale/fo/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/it
/usr/share/locale/it/LC_MESSAGES
/usr/share/locale/it/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/jv
/usr/share/locale/jv/LC_MESSAGES
/usr/share/locale/jv/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/kk
/usr/share/locale/kk/LC_MESSAGES
/usr/share/locale/kk/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/sr@latin
/usr/share/locale/sr@latin/LC_MESSAGES
/usr/share/locale/sr@latin/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/el
/usr/share/locale/el/LC_MESSAGES
/usr/share/locale/el/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/lo
/usr/share/locale/lo/LC_MESSAGES
/usr/share/locale/lo/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ti
/usr/share/locale/ti/LC_MESSAGES
/usr/share/locale/ti/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/sma
/usr/share/locale/sma/LC_MESSAGES
/usr/share/locale/sma/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/mh
/usr/share/locale/mh/LC_MESSAGES
/usr/share/locale/mh/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/be
/usr/share/locale/be/LC_MESSAGES
/usr/share/locale/be/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/kv
/usr/share/locale/kv/LC_MESSAGES
/usr/share/locale/kv/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/mt
/usr/share/locale/mt/LC_MESSAGES
/usr/share/locale/mt/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ny
/usr/share/locale/ny/LC_MESSAGES
/usr/share/locale/ny/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/et
/usr/share/locale/et/LC_MESSAGES
/usr/share/locale/et/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/oc
/usr/share/locale/oc/LC_MESSAGES
/usr/share/locale/oc/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/th
/usr/share/locale/th/LC_MESSAGES
/usr/share/locale/th/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/no
/usr/share/locale/no/LC_MESSAGES
/usr/share/locale/no/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/jbo
/usr/share/locale/jbo/LC_MESSAGES
/usr/share/locale/jbo/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ga
/usr/share/locale/ga/LC_MESSAGES
/usr/share/locale/ga/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/mr
/usr/share/locale/mr/LC_MESSAGES
/usr/share/locale/mr/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/uz
/usr/share/locale/uz/LC_MESSAGES
/usr/share/locale/uz/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ve
/usr/share/locale/ve/LC_MESSAGES
/usr/share/locale/ve/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/nn
/usr/share/locale/nn/LC_MESSAGES
/usr/share/locale/nn/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/sc
/usr/share/locale/sc/LC_MESSAGES
/usr/share/locale/sc/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/tg
/usr/share/locale/tg/LC_MESSAGES
/usr/share/locale/tg/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/sm
/usr/share/locale/sm/LC_MESSAGES
/usr/share/locale/sm/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/en_CA
/usr/share/locale/en_CA/LC_MESSAGES
/usr/share/locale/en_CA/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/eu
/usr/share/locale/eu/LC_MESSAGES
/usr/share/locale/eu/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/sw
/usr/share/locale/sw/LC_MESSAGES
/usr/share/locale/sw/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ch
/usr/share/locale/ch/LC_MESSAGES
/usr/share/locale/ch/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/sk
/usr/share/locale/sk/LC_MESSAGES
/usr/share/locale/sk/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ckb
/usr/share/locale/ckb/LC_MESSAGES
/usr/share/locale/ckb/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/km
/usr/share/locale/km/LC_MESSAGES
/usr/share/locale/km/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/rm
/usr/share/locale/rm/LC_MESSAGES
/usr/share/locale/rm/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ia
/usr/share/locale/ia/LC_MESSAGES
/usr/share/locale/ia/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ii
/usr/share/locale/ii/LC_MESSAGES
/usr/share/locale/ii/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/kw
/usr/share/locale/kw/LC_MESSAGES
/usr/share/locale/kw/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/ho
/usr/share/locale/ho/LC_MESSAGES
/usr/share/locale/ho/LC_MESSAGES/io.elementary.files.mo
/usr/share/locale/pl
/usr/share/locale/pl/LC_MESSAGES
/usr/share/locale/pl/LC_MESSAGES/io.elementary.files.mo
/usr/share/applications
/usr/share/applications/io.elementary.files.desktop
/usr/share/glib-2.0
/usr/share/glib-2.0/schemas
/usr/share/glib-2.0/schemas/io.elementary.files.gschema.xml

```

Now the terminal command **io.elementary.files** runs an instance of the Pantheon FIles program :D
But... it still won't run as root :(
If I try sudo io.elementary.files the output is:
```

[INFO 01:37:40.856601] Application.vala:154: Files version: 0.3.5
[INFO 01:37:40.856632] Application.vala:156: Kernel version: 4.15.3-041503-generic
No protocol specified
Unable to init server: Could not connect: Connection refused

(io.elementary.files:6978): Gtk-WARNING **: cannot open display: :0

```

What does it mean?

---

### Post by Frogs Hair on 2018-02-17
Try the following.

```
sudo -H pantheon-files
```

---

### Post by TheFu on 2018-02-17
Running most GUI programs as root (w/ sudo) isn't a good idea for a number of reasons.

The main reason is that using *sudo {gui-program}*, keep the regular user's environment, but runs the application as root, leaving root-owned files in a user's (not root's) HOME.  That can be bad and lead to a system that doesn't work when the userid tries to write to a file owned by root that shouldn't be.

As Frogs Hair says, using **sudo -H** will change the HOME environment to use root's HOME, but it won't fix the Xauth file.  Some extra steps are usually needed, though I can't help with them, since I use the shell for file management myself.

Sorry, I'm no more help.

---

### Post by again? on 2018-02-18
Are you using Elementary Loki or have you installed pantheon packages in ubuntu?
In Loki  the commands are **pantheon-files** and for root **pantheon-files-pkexec** which actually executes **pkexec "/usr/bin/pantheon-files**"

So from your "dpkg-query -L pantheon-files" output I would use
```
/usr/bin/io.elementary.files
```
and for root
```
/usr/bin/io.elementary.files-pkexec
```
or
```
pkexec /usr/bin/io.elementary.files
```

Loki is based on Ubuntu 16.04 and with the changes to admin access for graphical applications
not sure if pkexec still works on later Ubuntu releases.
So for root, possibly
```
sudo -H /usr/bin/io.elementary.files
```

---

### Post by Hasimir on 2018-02-18
This is what happens with the -H option :

```

**sudo -H io.elementary.files**
 
[INFO 09:48:53.281253] Application.vala:154: Files version: 0.3.5
[INFO 09:48:53.281296] Application.vala:156: Kernel version: 4.15.3-041503-generic
No protocol specified
Unable to init server: Could not connect: Connection refused

(io.elementary.files:10429): Gtk-WARNING **: cannot open display: :0

```

**@ TheFu** ... don't worry buddy, and thanks for the help so far! :D

**@ guber2** ... I've installed Pantheon Files on to Ubuntu 17.10, it's just too good a file manager to renounce it ;)
But if you or anyone else knows other similar fms, I'm open to change.
Mainly I like the keyboard navigation of folders, the way you can enter and explore folders in new columns just by navigating Left on the keyboard, and then go back by navigating Right. It feels very natural, and it's THE one feature I miss from my days with a MacOs (along with Mac gestures).
Are there any other file managers with this behavior? :)

---

### Post by again? on 2018-02-18
I installed pantheon-files from  the elementary-os/daily ppa in Xubuntu 17.10 and this works to open as root
```
/usr/bin/io.elementary.files-pkexec
```

Your dpkg-query output shows the file exists on your system.

---

### Post by again? on 2018-02-18
> **Hasimir said:**
> **@ guber2** ... I've installed Pantheon Files on to Ubuntu 17.10, it's just too good a file manager to renounce it ;)
But if you or anyone else knows other similar fms, I'm open to change.
Mainly I like the keyboard navigation of folders, the way you can enter and explore folders in new columns just by navigating Left on the keyboard, and then go back by navigating Right. It feels very natural, and it's THE one feature I miss from my days with a MacOs (along with Mac gestures).
Are there any other file managers with this behavior? :)
Not sure but it appears to be the same as nautilus in list view.
You just need to "Allow folders to be expanded" in preferences.

---

### Post by TheFu on 2018-02-18
There are lots of different file managers, going back all the way to Xtree for MS-Dos.  Most have been ported to Linux.  There's a NextStep file manager, for example from the NEXT computers. 

Another thought - 17.10 uses Wayland by default. Not all programs have been ported from Xorg to Wayland.  Before login, you can choose to use xorg instead. Click the "gear" and chose.  Might not help at all. Don't know.

---

### Post by Hasimir on 2018-02-18
Still no joy even with **-pkxec**, same error as before.

on a side note I'm giving Nautilus another try, but maybe I'll open a separate thread to find my dream FM :)

---

### Post by Frogs Hair on 2018-02-18
I may have missed it , but are you in the Ubuntu session or Ubuntu on Xorg ?

---

### Post by Hasimir on 2018-02-18
> **Frogs Hair said:**
> I may have missed it , but are you in the Ubuntu session or Ubuntu on Xorg ?

Dang I forgot to test that!
I usually run the GNOME option. I now tried the GNOME on Xorg option an the -pkxec command works. **Thanks for this!** :D
Still, I'll look for an alternative that doesn't require me to reboot the system in a non-standard (for my habits) configuration just to access run a file manager as root :P

---

### Post by Frogs Hair on 2018-02-18
You can grant session permissions in Wayland with the following. This works for synaptic , nautilus , gufw and other applications.

```
xhost +si:localuser:root
```

---

