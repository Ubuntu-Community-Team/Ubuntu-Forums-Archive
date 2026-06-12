---
title: "Programs not opening"
date: 2020-12-21
forum: General Help
---

### Post by grxgghxrpxr on 2020-12-21
Hello

I have recently installed Ubuntu Budgie on one of my old laptops. I've installed the following programs: Shotwell & Wallch, but when I click on them, the icon appears in the dock for a second then disappears. They worked when I tried out the regular Ubuntu in a VM, but they're just doing this now. I have tried reinstalling them, but it's just doing the same. Why is this & how can I fix it?

Thanks
Gregg

---

### Post by TheFu on 2020-12-21
Basic troubleshooting would be to open a terminal and try running the program from there. Then you'll see any messages with warnings, failures.  First, you need to determine the exact name of the program. I'd try "shotwell". If that didn't work, I'd look in the Shotwell.desktop file for the **Exec= ** line.  I'd use 'locate' to find the desktop file, but I use locate 50x a day. You may not even have it installed.  Some .desktop files are placed into  /usr/share/applications/

---

### Post by ActionParsnip on 2020-12-21
It'll probably be in /usr/share/applications

---

### Post by CatKiller on 2020-12-21
> **TheFu said:**
> If that didn't work, I'd look in the Shotwell.desktop file for the **Exec= ** line.  I'd use 'locate' to find the desktop file, but I use locate 50x a day.
You can generally just drag-and-drop the launcher onto a text editor window to see what it says.

---

### Post by grxgghxrpxr on 2020-12-21
> **TheFu said:**
> Basic troubleshooting would be to open a terminal and try running the program from there. Then you'll see any messages with warnings, failures.  First, you need to determine the exact name of the program. I'd try "shotwell". If that didn't work, I'd look in the Shotwell.desktop file for the **Exec= ** line.  I'd use 'locate' to find the desktop file, but I use locate 50x a day. You may not even have it installed.  Some .desktop files are placed into  /usr/share/applications/

Thank you for this. I've located to /usr/share/applications & found 'shotwell.desktop' & 'shotwell-viewer.desktop'. 
What do I do next?
I typed 'shotwell.desktop' & it said 'command not found'.
Then, I typed 'shotwell-viewer.desktop' & it said the same thing.
Then I typed 'shotwell' & it said 'shotwell: error while loading shared libraries: libraw.so.19: cannot open shared object file: No such file or directory'.

---

### Post by CatKiller on 2020-12-21
> **grxgghxrpxr said:**
> I've located to /usr/share/applications & found 'shotwell.desktop' & 'shotwell-viewer.desktop'. 
What do I do next?
They're just text files that include commands to run. Look at them to see what commands they run, then run those commands in a terminal to see if you get any useful error messages.

---

### Post by ActionParsnip on 2020-12-21
if you run:
```

grep -i exec  /usr/share/applications/shotwell.desktop

```
It will show the command that is actually ran when you click the Shotwell item in the launcher. You can then run this in the terminal and get some useful output. I think you already did this but its good to note this for future reference

---

### Post by grxgghxrpxr on 2020-12-21
> **CatKiller said:**
> They're just text files that include commands to run. Look at them to see what commands they run, then run those commands in a terminal to see if you get any useful error messages.

For Shotwell, it comes up with the following:

[Desktop Entry]
Version=1.0
Name=Shotwell
GenericName=Photo Manager
Comment=Organize your photos
# Translators: Search terms to find this application. Do NOT translate or localize the semicolons! The list MUST also end with a semicolon!
Keywords=album;camera;cameras;crop;edit;enhance;export;gallery;image;images;import;organize;photo;photographs;photos;picture;pictures;photography;print;publish;rotate;share;tags;video;facebook;flickr;picasa;youtube;piwigo;
Exec=shotwell %U
# Translators: Do NOT translate or transliterate this text (this is an icon file name)!
Icon=shotwell
Terminal=false
Type=Application
MimeType=x-content/image-dcf;
Categories=Graphics;Photography;GNOME;GTK;
X-GIO-NoFuse=true
X-GNOME-Gettext-Domain=shotwell
X-GNOME-FullName=Shotwell Photo Manager

What commands should I enter?

---

### Post by TheFu on 2020-12-21
> **grxgghxrpxr said:**
>  
Then I typed 'shotwell' & it said 'shotwell: error while loading shared libraries: libraw.so.19: cannot open shared object file: No such file or directory'.

So it cannot find libraw.so.19 in the expected location.  The first thing I would do it use 'locate' to find where that file was. It isn't on my system, but I don't use shotwell, so that isn't surprising at all.  Then I'd figure out which package installed it and for a re-install of that package.  The **apt** program has a way to provide a filename and get the package it belongs to. I don't have that memorized, so you can look it up as easily as I could.

```
sudo apt install --reinstall {name of that package}
```

Then try to run shotwell again in a terminal.

---

### Post by grxgghxrpxr on 2020-12-21
> **TheFu said:**
> So it cannot find libraw.so.19 in the expected location.  The first thing I would do it use 'locate' to find where that file was. It isn't on my system, but I don't use shotwell, so that isn't surprising at all.  Then I'd figure out which package installed it and for a re-install of that package.  The **apt** program has a way to provide a filename and get the package it belongs to. I don't have that memorized, so you can look it up as easily as I could.

```
sudo apt install --reinstall {name of that package}
```

Then try to run shotwell again in a terminal.

I can't find it :(

---

### Post by grxgghxrpxr on 2020-12-21
I typed 'locate libraw' & this came up:

/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/usr/lib/x86_64-linux-gnu/libraw1394.so.11
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/usr/lib/x86_64-linux-gnu/libraw1394.so.11.1.0
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/librawvideo_plugin.so
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawaud_plugin.so
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawdv_plugin.so
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawvid_plugin.so
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/usr/share/doc/libraw1394-11
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/usr/share/doc/libraw19
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/usr/share/doc/libraw1394-11/changelog.Debian.gz
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/usr/share/doc/libraw1394-11/copyright
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/var/lib/dpkg/info/libraw1394-11:amd64.list
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/var/lib/dpkg/info/libraw1394-11:amd64.md5sums
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/var/lib/dpkg/info/libraw1394-11:amd64.shlibs
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/var/lib/dpkg/info/libraw1394-11:amd64.triggers
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/var/lib/dpkg/info/libraw19:amd64.list
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/var/lib/dpkg/info/libraw19:amd64.md5sums
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/var/lib/dpkg/info/libraw19:amd64.shlibs
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/var/lib/dpkg/info/libraw19:amd64.symbols
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/var/lib/dpkg/info/libraw19:amd64.triggers
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/usr/lib/x86_64-linux-gnu/libraw1394.so.11
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/usr/lib/x86_64-linux-gnu/libraw1394.so.11.1.0
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/librawvideo_plugin.so
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawaud_plugin.so
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawdv_plugin.so
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawvid_plugin.so
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/usr/share/doc/libraw1394-11
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/usr/share/doc/libraw19
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/usr/share/doc/libraw1394-11/changelog.Debian.gz
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/usr/share/doc/libraw1394-11/copyright
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/var/lib/dpkg/info/libraw1394-11:amd64.list
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/var/lib/dpkg/info/libraw1394-11:amd64.md5sums
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/var/lib/dpkg/info/libraw1394-11:amd64.shlibs
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/var/lib/dpkg/info/libraw1394-11:amd64.triggers
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/var/lib/dpkg/info/libraw19:amd64.list
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/var/lib/dpkg/info/libraw19:amd64.md5sums
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/var/lib/dpkg/info/libraw19:amd64.shlibs
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/var/lib/dpkg/info/libraw19:amd64.symbols
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/var/lib/dpkg/info/libraw19:amd64.triggers
/snap/gimp/322/usr/lib/x86_64-linux-gnu/libraw.so.16
/snap/gimp/322/usr/lib/x86_64-linux-gnu/libraw.so.16.0.0
/snap/gimp/322/usr/lib/x86_64-linux-gnu/libraw_r.so.16
/snap/gimp/322/usr/lib/x86_64-linux-gnu/libraw_r.so.16.0.0
/snap/gimp/322/usr/share/doc/libraw1394-11
/snap/gimp/322/usr/share/doc/libraw1394-11/copyright
/snap/kde-frameworks-5-core18/32/usr/lib/x86_64-linux-gnu/libraw1394.so.11
/snap/kde-frameworks-5-core18/32/usr/lib/x86_64-linux-gnu/libraw1394.so.11.1.0
/snap/kde-frameworks-5-core18/32/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/librawvideo_plugin.so
/snap/kde-frameworks-5-core18/32/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawaud_plugin.so
/snap/kde-frameworks-5-core18/32/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawdv_plugin.so
/snap/kde-frameworks-5-core18/32/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawvid_plugin.so
/snap/kde-frameworks-5-qt-5-14-core18/4/usr/lib/x86_64-linux-gnu/libraw1394.so.11
/snap/kde-frameworks-5-qt-5-14-core18/4/usr/lib/x86_64-linux-gnu/libraw1394.so.11.1.0
/snap/kdictionary/4/usr/lib/x86_64-linux-gnu/libraw1394.so.11
/snap/kdictionary/4/usr/lib/x86_64-linux-gnu/libraw1394.so.11.1.0
/snap/kdictionary/4/usr/share/doc/libraw1394-11
/snap/kdictionary/4/usr/share/doc/libraw1394-11/AUTHORS
/snap/kdictionary/4/usr/share/doc/libraw1394-11/NEWS.gz
/snap/kdictionary/4/usr/share/doc/libraw1394-11/README
/snap/kdictionary/4/usr/share/doc/libraw1394-11/README.Debian
/snap/kdictionary/4/usr/share/doc/libraw1394-11/changelog.Debian.gz
/snap/kdictionary/4/usr/share/doc/libraw1394-11/copyright
/snap/krita/61/usr/lib/x86_64-linux-gnu/libraw.so.16
/snap/krita/61/usr/lib/x86_64-linux-gnu/libraw.so.16.0.0
/snap/krita/61/usr/lib/x86_64-linux-gnu/libraw_r.so.16
/snap/krita/61/usr/lib/x86_64-linux-gnu/libraw_r.so.16.0.0
/snap/krita/61/usr/share/doc/libraw1394-11
/snap/krita/61/usr/share/doc/libraw16
/snap/krita/61/usr/share/doc/libraw1394-11/AUTHORS
/snap/krita/61/usr/share/doc/libraw1394-11/NEWS.gz
/snap/krita/61/usr/share/doc/libraw1394-11/README
/snap/krita/61/usr/share/doc/libraw1394-11/README.Debian
/snap/krita/61/usr/share/doc/libraw1394-11/changelog.Debian.gz
/snap/krita/61/usr/share/doc/libraw1394-11/copyright
/snap/krita/61/usr/share/doc/libraw16/changelog.Debian.gz
/snap/krita/61/usr/share/doc/libraw16/copyright
/snap/qt551/31/usr/lib/x86_64-linux-gnu/libraw1394.so.11
/snap/qt551/31/usr/lib/x86_64-linux-gnu/libraw1394.so.11.1.0
/usr/lib/x86_64-linux-gnu/libraw1394.so.11
/usr/lib/x86_64-linux-gnu/libraw1394.so.11.1.0
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/librawvideo_plugin.so
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawaud_plugin.so
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawdv_plugin.so
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawvid_plugin.so
/usr/share/doc/libraw1394-11
/usr/share/doc/libraw19
/usr/share/doc/libraw1394-11/changelog.Debian.gz
/usr/share/doc/libraw1394-11/copyright
/var/cache/apt/archives/libraw1394-11_2.1.2-2_i386.deb
/var/lib/dpkg/info/libraw1394-11:amd64.list
/var/lib/dpkg/info/libraw1394-11:amd64.md5sums
/var/lib/dpkg/info/libraw1394-11:amd64.shlibs
/var/lib/dpkg/info/libraw1394-11:amd64.triggers
/var/lib/dpkg/info/libraw19:amd64.list
/var/lib/dpkg/info/libraw19:amd64.md5sums
/var/lib/dpkg/info/libraw19:amd64.shlibs
/var/lib/dpkg/info/libraw19:amd64.symbols
/var/lib/dpkg/info/libraw19:amd64.triggers

---

### Post by grxgghxrpxr on 2020-12-21
I typed 'locate libraw'

This came up:

/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/usr/lib/x86_64-linux-gnu/libraw1394.so.11
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/usr/lib/x86_64-linux-gnu/libraw1394.so.11.1.0
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/librawvideo_plugin.so
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawaud_plugin.so
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawdv_plugin.so
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawvid_plugin.so
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/usr/share/doc/libraw1394-11
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/usr/share/doc/libraw19
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/usr/share/doc/libraw1394-11/changelog.Debian.gz
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/usr/share/doc/libraw1394-11/copyright
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/var/lib/dpkg/info/libraw1394-11:amd64.list
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/var/lib/dpkg/info/libraw1394-11:amd64.md5sums
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/var/lib/dpkg/info/libraw1394-11:amd64.shlibs
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/var/lib/dpkg/info/libraw1394-11:amd64.triggers
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/var/lib/dpkg/info/libraw19:amd64.list
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/var/lib/dpkg/info/libraw19:amd64.md5sums
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/var/lib/dpkg/info/libraw19:amd64.shlibs
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/var/lib/dpkg/info/libraw19:amd64.symbols
/home/timeshift/snapshots/2020-12-19_18-40-52/localhost/var/lib/dpkg/info/libraw19:amd64.triggers
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/usr/lib/x86_64-linux-gnu/libraw1394.so.11
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/usr/lib/x86_64-linux-gnu/libraw1394.so.11.1.0
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/librawvideo_plugin.so
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawaud_plugin.so
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawdv_plugin.so
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawvid_plugin.so
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/usr/share/doc/libraw1394-11
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/usr/share/doc/libraw19
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/usr/share/doc/libraw1394-11/changelog.Debian.gz
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/usr/share/doc/libraw1394-11/copyright
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/var/lib/dpkg/info/libraw1394-11:amd64.list
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/var/lib/dpkg/info/libraw1394-11:amd64.md5sums
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/var/lib/dpkg/info/libraw1394-11:amd64.shlibs
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/var/lib/dpkg/info/libraw1394-11:amd64.triggers
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/var/lib/dpkg/info/libraw19:amd64.list
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/var/lib/dpkg/info/libraw19:amd64.md5sums
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/var/lib/dpkg/info/libraw19:amd64.shlibs
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/var/lib/dpkg/info/libraw19:amd64.symbols
/home/timeshift/snapshots/2020-12-21_13-00-02/localhost/var/lib/dpkg/info/libraw19:amd64.triggers
/snap/gimp/322/usr/lib/x86_64-linux-gnu/libraw.so.16
/snap/gimp/322/usr/lib/x86_64-linux-gnu/libraw.so.16.0.0
/snap/gimp/322/usr/lib/x86_64-linux-gnu/libraw_r.so.16
/snap/gimp/322/usr/lib/x86_64-linux-gnu/libraw_r.so.16.0.0
/snap/gimp/322/usr/share/doc/libraw1394-11
/snap/gimp/322/usr/share/doc/libraw1394-11/copyright
/snap/kde-frameworks-5-core18/32/usr/lib/x86_64-linux-gnu/libraw1394.so.11
/snap/kde-frameworks-5-core18/32/usr/lib/x86_64-linux-gnu/libraw1394.so.11.1.0
/snap/kde-frameworks-5-core18/32/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/librawvideo_plugin.so
/snap/kde-frameworks-5-core18/32/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawaud_plugin.so
/snap/kde-frameworks-5-core18/32/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawdv_plugin.so
/snap/kde-frameworks-5-core18/32/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawvid_plugin.so
/snap/kde-frameworks-5-qt-5-14-core18/4/usr/lib/x86_64-linux-gnu/libraw1394.so.11
/snap/kde-frameworks-5-qt-5-14-core18/4/usr/lib/x86_64-linux-gnu/libraw1394.so.11.1.0
/snap/kdictionary/4/usr/lib/x86_64-linux-gnu/libraw1394.so.11
/snap/kdictionary/4/usr/lib/x86_64-linux-gnu/libraw1394.so.11.1.0
/snap/kdictionary/4/usr/share/doc/libraw1394-11
/snap/kdictionary/4/usr/share/doc/libraw1394-11/AUTHORS
/snap/kdictionary/4/usr/share/doc/libraw1394-11/NEWS.gz
/snap/kdictionary/4/usr/share/doc/libraw1394-11/README
/snap/kdictionary/4/usr/share/doc/libraw1394-11/README.Debian
/snap/kdictionary/4/usr/share/doc/libraw1394-11/changelog.Debian.gz
/snap/kdictionary/4/usr/share/doc/libraw1394-11/copyright
/snap/krita/61/usr/lib/x86_64-linux-gnu/libraw.so.16
/snap/krita/61/usr/lib/x86_64-linux-gnu/libraw.so.16.0.0
/snap/krita/61/usr/lib/x86_64-linux-gnu/libraw_r.so.16
/snap/krita/61/usr/lib/x86_64-linux-gnu/libraw_r.so.16.0.0
/snap/krita/61/usr/share/doc/libraw1394-11
/snap/krita/61/usr/share/doc/libraw16
/snap/krita/61/usr/share/doc/libraw1394-11/AUTHORS
/snap/krita/61/usr/share/doc/libraw1394-11/NEWS.gz
/snap/krita/61/usr/share/doc/libraw1394-11/README
/snap/krita/61/usr/share/doc/libraw1394-11/README.Debian
/snap/krita/61/usr/share/doc/libraw1394-11/changelog.Debian.gz
/snap/krita/61/usr/share/doc/libraw1394-11/copyright
/snap/krita/61/usr/share/doc/libraw16/changelog.Debian.gz
/snap/krita/61/usr/share/doc/libraw16/copyright
/snap/qt551/31/usr/lib/x86_64-linux-gnu/libraw1394.so.11
/snap/qt551/31/usr/lib/x86_64-linux-gnu/libraw1394.so.11.1.0
/usr/lib/x86_64-linux-gnu/libraw1394.so.11
/usr/lib/x86_64-linux-gnu/libraw1394.so.11.1.0
/usr/lib/x86_64-linux-gnu/vlc/plugins/codec/librawvideo_plugin.so
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawaud_plugin.so
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawdv_plugin.so
/usr/lib/x86_64-linux-gnu/vlc/plugins/demux/librawvid_plugin.so
/usr/share/doc/libraw1394-11
/usr/share/doc/libraw19
/usr/share/doc/libraw1394-11/changelog.Debian.gz
/usr/share/doc/libraw1394-11/copyright
/var/cache/apt/archives/libraw1394-11_2.1.2-2_i386.deb
/var/lib/dpkg/info/libraw1394-11:amd64.list
/var/lib/dpkg/info/libraw1394-11:amd64.md5sums
/var/lib/dpkg/info/libraw1394-11:amd64.shlibs
/var/lib/dpkg/info/libraw1394-11:amd64.triggers
/var/lib/dpkg/info/libraw19:amd64.list
/var/lib/dpkg/info/libraw19:amd64.md5sums
/var/lib/dpkg/info/libraw19:amd64.shlibs
/var/lib/dpkg/info/libraw19:amd64.symbols
/var/lib/dpkg/info/libraw19:amd64.triggers

---

