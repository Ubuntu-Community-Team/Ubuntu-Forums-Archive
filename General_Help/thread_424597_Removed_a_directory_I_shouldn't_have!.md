---
title: "Removed a directory I shouldn't have!"
date: 2007-04-26
forum: General Help
---

### Post by lotacus on 2007-04-26
I was manually removing BloGTk by finding references using search. Because of the structure of the results it presents I got a bit confuses, but anyways, did this:

sudo rm -r /usr/share/app-install/desktop

sudo rm -r /var/lib/dpkg/info

forgetting to add BloGTK.desktop because I read the results as if this directory was owned by the application. Stupid me.

anyways, now I am having some serious warnings when adding/removing and using apt-get.

```
[SIZE="1"]dpkg: serious warning: files list file for package `kdelibs4-dev' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `iptables' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libwnck18' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libqthreads-12' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `kcoloredit' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libsasl2-dev' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `bash' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libpcre3-dev' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `make' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `util-linux' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `ekiga' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xkbutils' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libkrb53' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libiso9660-4' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libxcursor1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libglitz1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libdvbpsi4' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xfonts-utils' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xserver-xorg-input-kbd' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `update-manager' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libmeanwhile1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgnome-mag2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libmusicbrainz4c2a' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libksieve0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `ttf-indic-fonts' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `avahi-daemon' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `lame' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libdvdplay0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgii1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgnome2-dev' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `ksirtet' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `kpilot' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `reiserfsprogs' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `po-debconf' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libneon25' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-uno' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gstreamer0.10-x' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `ubuntu-minimal' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `popularity-contest' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xrefresh' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libpt-plugins-v4l2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `kmilo' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `m4' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libmad0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `kmrml' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `hplip' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libfontenc1' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `kdeaddons' missing, assuming package has no files currently installed.[/SIZE]

```

That's just a small snippet. I know that it is near impossible to undelete using ext3 filesystem, but wondering if there is any way to fix this problem? Such as some sort of fix command for dpkg to re-index?

---

