---
title: "Software Centre really wierd formatting"
date: 2022-10-13
forum: General Help
---

### Post by mikber18 on 2022-10-13
Hi Guys,

Something strange has happened on my install. 

When I go into the store the formatting has suddenly been squished into the middle of the Store Window. 

It was previously nearly across the length of the screen and now it seems like a bit squished into the centre. 

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291124&stc=1[/IMG]
Any ideas what may have happened. I normally see this span across the width of the screen plus minus a few pixels 

Cheers

---

### Post by MAFoElffen on 2022-10-14
'gnome-software' is no longer a default installed application. Are you using the apt or flatpak version?
```

mafoelffen@Mikes-ThinkPad-T520:~$ apt-cache show gnome-software
Package: gnome-software
Architecture: amd64
Version: 41.5-2ubuntu2
Priority: optional
Section: universe/gnome
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 2904
Depends: appstream, apt-config-icons, gnome-software-common (= 41.5-2ubuntu2), gsettings-desktop-schemas (>= 3.18), libgtk3-perl, packagekit (>= 1.1.11), software-properties-gtk, dconf-gsettings-backend | gsettings-backend, libappstream4 (>= 0.14.0), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.34), libcairo2 (>= 1.12.0), libfwupd2 (>= 1.5.6), libgdk-pixbuf-2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.70.0), libgspell-1-2 (>= 1.8.2), libgtk-3-0 (>= 3.22.29), libgudev-1.0-0 (>= 146), libhandy-1-0 (>= 1.3.90), libjson-glib-1.0-0 (>= 1.5.2), libmalcontent-0-0 (>= 0.6.0), libpackagekit-glib2-18 (>= 1.2.5), libpango-1.0-0 (>= 1.18.0), libpolkit-gobject-1-0 (>= 0.99), libsoup2.4-1 (>= 2.52.0), libxmlb2 (>= 0.3.2)
Recommends: fwupd, gnome-software-plugin-snap
Suggests: apt-config-icons-hidpi, gnome-software-plugin-flatpak
Conflicts: sessioninstaller
Filename: pool/universe/g/gnome-software/gnome-software_41.5-2ubuntu2_amd64.deb
Size: 606094
MD5sum: 381873a0019409dccb5eec1d61780a4b
SHA1: 4756e85917243a7ddd293be57d94cc5f0ebea663
SHA256: bbc42b2544acd0abc581239fa3558d75ae0b6b80fdb75cf5e4f1a887759c515e
SHA512: 7e633bbc138cb201294d6237c117c957a731cfbc5ad7b871449642b53fd7baeaf217ca8a9014e6b4415e3f62586b1a074b393ea2aee1da75836790a5e8d34af9
Homepage: https://wiki.gnome.org/Apps/Software
Description-en: Software Center for GNOME
 Software lets you install and update applications and system extensions.
 .
 Software uses a plugin architecture to separate the frontend from the
 technologies that are used underneath. Currently, a PackageKit plugin provides
 data from a number of traditional packaging systems, such as rpm or apt. An
 appdata plugin provides additional metadata from locally installed data in the
 appdata format.
Description-md5: c18037138f62996f54244e20a5eee15b
Task: xubuntu-desktop, ubuntu-budgie-desktop, ubuntu-budgie-desktop-raspi

Package: gnome-software
Architecture: amd64
Version: 41.5-2
Priority: optional
Section: universe/gnome
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 2904
Depends: appstream, apt-config-icons, gnome-software-common (= 41.5-2), gsettings-desktop-schemas (>= 3.18), libgtk3-perl, packagekit (>= 1.1.11), software-properties-gtk, dconf-gsettings-backend | gsettings-backend, libappstream4 (>= 0.14.0), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.34), libcairo2 (>= 1.12.0), libfwupd2 (>= 1.5.6), libgdk-pixbuf-2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.70.0), libgspell-1-2 (>= 1.8.2), libgtk-3-0 (>= 3.22.29), libgudev-1.0-0 (>= 146), libhandy-1-0 (>= 1.3.90), libjson-glib-1.0-0 (>= 1.5.2), libmalcontent-0-0 (>= 0.6.0), libpackagekit-glib2-18 (>= 1.2.5), libpango-1.0-0 (>= 1.18.0), libpolkit-gobject-1-0 (>= 0.99), libsoup2.4-1 (>= 2.52.0), libxmlb2 (>= 0.3.2)
Recommends: fwupd, gnome-software-plugin-snap
Suggests: apt-config-icons-hidpi, gnome-software-plugin-flatpak
Conflicts: sessioninstaller
Filename: pool/universe/g/gnome-software/gnome-software_41.5-2_amd64.deb
Size: 606380
MD5sum: 90031e6275b317b0521c3873f3fb9342
SHA1: aa14ddc1ea85bd76c8741e31ef01c59cac73bda7
SHA256: 7edac928fc0f5a0ac6fd50db0e69d8003f2ab41ccda1afdc2aa3c2700623132e
SHA512: c05cda8a7987527ebdca3d06798ceb0a4a8f227e6545c158ac0a74ef21aa41fc7563df27cf3fefd481d84af0a5e9a3dbe81216aa68414e18fdfdaafddf23c219
Homepage: https://wiki.gnome.org/Apps/Software
Description-en: Software Center for GNOME
 Software lets you install and update applications and system extensions.
 .
 Software uses a plugin architecture to separate the frontend from the
 technologies that are used underneath. Currently, a PackageKit plugin provides
 data from a number of traditional packaging systems, such as rpm or apt. An
 appdata plugin provides additional metadata from locally installed data in the
 appdata format.
Description-md5: c18037138f62996f54244e20a5eee15b
Task: xubuntu-desktop, ubuntu-budgie-desktop, ubuntu-budgie-desktop-raspi

```
And are you running X11 or Wayland?
```

ps -e | egrep -e 'tty' | egrep -e 'x11|Xorg|wayland' | awk '{print $4}'

```

---

### Post by mikber18 on 2022-10-27
> **MAFoElffen said:**
> 'gnome-software' is no longer a default installed application. Are you using the apt or flatpak version?


I am using the apt version. 



> **MAFoElffen said:**
> And are you running X11 or Wayland?

I have just switched to Wayland to see if it makes a difference but it does not make any change.

---

