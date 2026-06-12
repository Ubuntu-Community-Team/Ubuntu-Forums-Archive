---
title: "Removing xserver-common-lts-raring"
date: 2014-02-09
forum: General Help
---

### Post by Jkns on 2014-02-09
Hello,

After upgrading from 12.04 to 13.10 I'm now having problems running updates. After running [FONT=courier new]sudo apt-get update[/FONT] and then [FONT=courier new]sudo apt-get upgrade[/FONT] I get the following:

[FONT=courier new]Removing xserver-common-lts-raring ...
Removing 'diversion of /usr/lib/xorg/protocol.txt to /usr/lib/xorg/protocol-precise.txt by xserver-common-lts-raring'
dpkg-divert: error: rename involves overwriting `/usr/lib/xorg/protocol.txt' with
  different file `/usr/lib/xorg/protocol-precise.txt', not allowed
dpkg: error processing xserver-common-lts-raring (--remove):
 subprocess installed post-removal script returned error exit status 2
No apport report written because MaxReports has already been reached
Errors were encountered while processing:
 xserver-common-lts-raring
E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT]

After looking round I tried [http://askubuntu.com/a/369865](http://askubuntu.com/a/369865) but this is what my **xserver-common-lts-raring.postrm** file looks like:
```

#!/bin/sh -e
set -e

if [ remove = "$1" -o abort-install = "$1" -o disappear = "$1" ]; then
    dpkg-divert --remove --package xserver-common-lts-raring --rename \
        --divert /usr/lib/xorg/protocol-precise.txt \
        /usr/lib/xorg/protocol.txt
fi



exit 0
```

Any ideas how to remove/replace/update xserver-common-lts-raring?

Kind regards,

Jkns

---

### Post by jeanjd63 on 2014-02-09
Hello

You can try :
**sudo  dpkg  -P  --force-all  [COLOR=#000000][FONT=courier new]xserver-common-lts-raring[/FONT][/COLOR]**

---

### Post by Jkns on 2014-02-09
Thanks [**[COLOR=#000000]jeanjd63[/COLOR]**]("http://ubuntuforums.org/member.php?u=1879871"), but that gives a similar message:

[FONT=courier new]Removing xserver-common-lts-raring ...
Removing 'diversion of /usr/lib/xorg/protocol.txt to /usr/lib/xorg/protocol-precise.txt by xserver-common-lts-raring'
dpkg-divert: error: rename involves overwriting `/usr/lib/xorg/protocol.txt' with
  different file `/usr/lib/xorg/protocol-precise.txt', not allowed
dpkg: error processing xserver-common-lts-raring (--purge):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 xserver-common-lts-raring[/FONT]

---

### Post by jeanjd63 on 2014-02-09
You can try to modify the file :
**sudo  gedit  [COLOR=#000000] /var/[/COLOR]lib[COLOR=#000000]/dpkg/info/[/COLOR]xserver-common-lts-raring.[COLOR=#000000]postrm[/COLOR]**

```
[COLOR=#000000][FONT=Ubuntu Mono]#!/bin/sh -e
[/FONT][/COLOR]set -e
[COLOR=#000000][FONT=Ubuntu Mono]exit 0[/FONT][/COLOR]
```

And do :
**sudo  apt-get  autoremove**

---

### Post by Jkns on 2014-02-09
That worked a treat. Thank you very much [**[COLOR=#000000]jeanjd6[/COLOR]**]("http://ubuntuforums.org/member.php?u=1879871").

---

