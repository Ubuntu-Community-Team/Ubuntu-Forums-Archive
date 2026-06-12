---
title: "dpkg -l lists same package name 4 times"
date: 2020-02-07
forum: General Help
---

### Post by Skaperen on 2020-02-07
dpkg -l lists the same package name 4 times:
```

ii  xubuntu-community-wallpapers 18.04.0             all                 Xubuntu community wallpapers
ii  xubuntu-community-wallpapers 18.04.0             all                 Xubuntu community wallpapers (Bionic)
ii  xubuntu-community-wallpapers 18.04.0             all                 Xubuntu community wallpapers (Trusty)
ii  xubuntu-community-wallpapers 18.04.0             all                 Xubuntu community wallpapers (Xenial)

```
as you can see, there are previous LTS' in there.  how do i refer to a specific one?

---

### Post by deadflowr on 2020-02-07
You should have
```
xubuntu-community-wallpapers-trusty
xubuntu-community-wallpapers-xenial
xubuntu-community-wallpapers-bionic
```
as the actual wallpaper packages
```
xubuntu-community-wallpapers 
```
is a metapackage.

On bionic only the bionic one is default.
The other two are suggested only.

Seems likely the console window is too small and therefor is cutting it off the extra part of those packages names.

---

### Post by Skaperen on 2020-02-08
yes, you are right.  dpkg is trimming its columns to make the output fit.  i had 136 columns.  i went up to 172 columns and the longer names came through.  even when outputting to a pipe it uses the same width.

dpkg -l formats based on how many columns it thinks you have based on the COLUMNS environment variable.  it pads its output columns to spread things out, rather that based on what the data actually needs like the ls command does. some of the package descriptions are huge so that may be why it does that.

too bad if you only have 80 columns.

it looks like it does the left columns smarter if COLUMNS=0 is done
```

t2a/forums /home/forums 15> COLUMNS=0 dpkg -l|tail -n22
ii  xubuntu-community-wallpapers           18.04.0                                         all          Xubuntu community wallpapers
ii  xubuntu-community-wallpapers-bionic    18.04.0                                         all          Xubuntu community wallpapers (Bionic)
ii  xubuntu-community-wallpapers-trusty    18.04.0                                         all          Xubuntu community wallpapers (Trusty)
ii  xubuntu-community-wallpapers-xenial    18.04.0                                         all          Xubuntu community wallpapers (Xenial)
ii  xubuntu-core                           2.225                                           amd64        Xubuntu core system
ii  xubuntu-default-settings               18.04.6                                         all          default settings for the Xubuntu desktop
ii  xubuntu-desktop                        2.225                                           amd64        Xubuntu desktop system
ii  xubuntu-docs                           18.04.1                                         all          Xubuntu documentation
ii  xubuntu-icon-theme                     18.04.5                                         all          Xubuntu icon theme
ii  xubuntu-wallpapers                     18.04.5                                         all          Xubuntu wallpapers
ii  xul-ext-ubufox                         3.4-0ubuntu1.17.10.1                            all          Ubuntu modifications for Firefox
ii  xvfb                                   2:1.19.6-1ubuntu4.3                             amd64        Virtual Framebuffer 'fake' X server
ii  xxd                                    2:8.0.1453-1ubuntu1.1                           amd64        tool to make (or reverse) a hex dump
ii  xz-utils                               5.2.2-1.3                                       amd64        XZ-format compression utilities
ii  xzdec                                  5.2.2-1.3                                       amd64        XZ-format compression utilities - tiny decompressors
ii  yelp                                   3.26.0-1ubuntu2                                 amd64        Help browser for GNOME
ii  yelp-xsl                               3.20.1-4                                        all          XSL stylesheets for the yelp help browser
ii  zenity                                 3.28.1-1                                        amd64        Display graphical dialog boxes from shell scripts
ii  zenity-common                          3.28.1-1                                        all          Display graphical dialog boxes from shell scripts (common files)
ii  zip                                    3.0-11build1                                    amd64        Archiver for .zip files
ii  zlib1g:amd64                           1:1.2.11.dfsg-0ubuntu2                          amd64        compression library - runtime
ii  zlib1g-dev:amd64                       1:1.2.11.dfsg-0ubuntu2                          amd64        compression library - development
lt2a/forums /home/forums 16>

```

---

### Post by Skaperen on 2020-02-08
it appears that dpkg only deals with COLUMNS=0 when outputting to a pipe.  so i wrote this little script to list packages:
```

#!/usr/bin/env python3
from os import environ
from subprocess import PIPE,Popen
environ['COLUMNS']='0'
p=Popen(['/usr/bin/dpkg','-l'],stdout=PIPE)
for l in p.stdout:
    print(''.join(chr(c)for c in l),end='')
p.wait()

```

---

