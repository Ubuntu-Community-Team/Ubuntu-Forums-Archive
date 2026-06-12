---
title: "What does &quot;no-follow-recommends&quot; mean?"
date: 2013-11-07
forum: General Help
---

### Post by vasa1 on 2013-11-07
Near the top of [https://wiki.ubuntu.com/Xubuntu/Roadmap/Specifications/Trusty/xubuntu-core](https://wiki.ubuntu.com/Xubuntu/Roadmap/Specifications/Trusty/xubuntu-core) there's mention of "no-follow-recommends":
> Describe Xubuntu/Roadmap/Specifications/Trusty/xubuntu-core here.Task-Per-Derivative: 1 Task-Section: user Task-Description: Xubuntu minimal installation Task-Extended-Description: This task provides minimal packages for Xubuntu desktop environment. Task-Key: xubuntu-core Task-Name: xubuntu-core Task-Seeds: desktop-common

    Feature: **no-follow-recommends** 

Network Services

Basic network services and Windows integration.

    (avahi-autoipd) # IPv4 link-local interface configuration support

    network-man ...
What does "no-follow-recommends" mean in the context?

---

### Post by ian-weisser on 2013-11-07
If I recall correctly, it means to install only required dependencies, not recommended or suggested dependencies.
This keeps the overall install smaller.
Apt tracks those several categories of dependencies. You can see some of the categories in an example:
```
$ apt-cache show unity
Package: unity
Priority: optional
Section: gnome
Installed-Size: 4952
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 7.1.2+13.10.20131014.1-0ubuntu1
Provides: indicator-renderer
[COLOR=#ff0000]Depends: compiz-core, libatk-bridge2.0-0 (>= 2.5.3), libatk1.0-0 (>= 2.2.0), libbamf3-2 (>= 0.5.0), libc6 (>= 2.17), libcairo2 (>= 1.2.4), libdbusmenu-glib4 (>= 0.4.2), libdee-1.0-4 (>= 0.5.2), libgcc1 (>= 1:4.1.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libgl1-mesa-glx | libgl1, libglew1.8 (>= 1.8.0), libglib2.0-0 (>= 2.37.3), libgtk-3-0 (>= 3.1.6), libindicator3-7 (>= 0.4.90), libjson-glib-1.0-0 (>= 0.12.0), libnotify4 (>= 0.7.0), libnux-4.0-0, libpango-1.0-0 (>= 1.22.0), libpangocairo-1.0-0 (>= 1.14.0), libsigc++-2.0-0c2a (>= 2.0.2), libstartup-notification0 (>= 0.2), libstdc++6 (>= 4.8), libunity-core-6.0-8 (= 7.1.2+13.10.20131014.1-0ubuntu1), libunity-misc4 (>= 4.0.2), libunity-protocol-private0 (>= 7.1.2+13.10.20131010), libx11-6 (>= 2:1.2.99.901), libxext6, libxfixes3 (>= 1:5.0.1-1), libxi6 (>= 2:1.7.1.901), libxrender1, libzeitgeist-2.0-0 (>= 0.9.9), session-migration, python:any, compiz, compiz-core-abiversion-20130415, libnux-abiversion-20130718.0, compiz-plugins-default, libglib2.0-bin, nux-tools, dconf-cli, unity-asset-pool (>= 0.8.18), bamfdaemon[/COLOR]
[COLOR=#00ff00]Recommends: gnome-control-center-unity, unity-scope-guayadeque, unity-scope-openclipart, unity-scope-musique, unity-scope-colourlovers, unity-lens-video, unity-scope-clementine, unity-scope-zotero, unity-scope-texdoc, unity-scope-tomboy, unity-scope-yelp, unity-scope-home, unity-scope-gmusicbrowser, unity-scope-audacious, unity-scope-musicstores, unity-scope-manpages, unity-lens-music, unity-lens-files, unity-scope-chromiumbookmarks, unity-lens-friends, unity-lens-applications, unity-scope-gdrive, unity-scope-calculator, unity-scope-devhelp, unity-scope-virtualbox, unity-scope-firefoxbookmarks, unity-lens-photos, unity-scope-gourmet, unity-scope-video-remote, indicator-appmenu, indicator-application, indicator-sound, indicator-bluetooth, indicator-datetime, indicator-keyboard, indicator-messages, indicator-printers, indicator-power, indicator-session, indicator-sync, telepathy-indicator, hud[/COLOR]
[COLOR=#daa520]Breaks: unity-lens-applications (<< 5.12.0-0ubuntu2), unity-lens-files (<< 5.10.0-0ubuntu2), unity-lens-music (<< 6.0.0), unity-lens-video (<< 0.3.6-0ubuntu2)[/COLOR]
Filename: pool/main/u/unity/unity_7.1.2+13.10.20131014.1-0ubuntu1_i386.deb
Size: 1602208
MD5sum: 17424735e9b0512dbf7d67077b462f2c
SHA1: c9e8f5cd9ca694def6d47c376d3d7c0c9b83f39d
SHA256: 45cd601866bfe3e01a10688402799c4338a594ac81ccf11ff2b707f4f4abf91a
Description-en: Interface designed for efficiency of space and interaction.
 Unity is a desktop experience that sings. Designed by Canonical and the Ayatana
 community, Unity is all about the combination of familiarity and the future. We
 bring together visual design, analysis of user experience testing, modern
 graphics technologies and a deep understanding of the free software landscape
 to produce what we hope will be the lightest, most elegant and most delightful
 way to use your PC.
Description-md5: dec4e0049e561b260175a841cf8a6410
Homepage: https://launchpad.net/unity
Description-md5: dec4e0049e561b260175a841cf8a6410
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 9m
Task: ubuntu-desktop, ubuntu-usb, edubuntu-desktop, edubuntu-usb


```

---

### Post by vasa1 on 2013-11-07
I've been using *sudo apt-get install --no-install-recommends package_name*.

I'm wondering if "Feature: no-follow-recommends" is shorthand or dev-speak for "this package will not pull in recommends".

For example, compare installing *xubuntu-desktop* via *sudo apt-get install xubuntu-desktop* and via *sudo apt-get install --no-install-recommends xubuntu-desktop*. The difference is huge. But the point is that the former is the default. So people would get the recommends automatically.

---

