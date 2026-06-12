---
title: "Program Compiles But Cant Be Found?"
date: 2008-02-07
forum: General Help
---

### Post by #Reistlehr- on 2008-02-07
Alright, so im not a Linux noob, and i know how to compile.

I'm trying to compile gnome-main-menu with some modifications i made to it. 

```

./configure --prefix=/usr/lib
make
sudo make install

```

it doesnt go to /usr/lib like it's supposed to. 

```

/home/mike/.nautilus/metafiles/file:%2F%2F%2Fhome%2Fmike%2FDesktop%2Fgnome-main-menu-0.9.8.svn.20070430.xml
/home/mike/Desktop/gnome-main-menu_0.9.8.svn.20070430.orig.tar.gz
/home/mike/.local/share/gnome-main-menu
/home/mike/.local/share/gnome-main-menu/applications.xbel
/home/mike/.icons/icons_gusty_ubuntu/22x22/places/gnome-main-menu.png
/home/mike/.icons/icons_gusty_ubuntu/48x48/actions/gnome-main-menu.png
/home/mike/.icons/icons_gusty_ubuntu/scalable/places/gnome-main-menu.png
/home/mike/.icons/icons_gusty_zgeg/22x22/places/gnome-main-menu.png
/home/mike/.icons/icons_gusty_zgeg/48x48/actions/gnome-main-menu.png
/home/mike/.icons/icons_gusty_zgeg/scalable/places/gnome-main-menu.png
/home/mike/.config/gnome-main-menu
/home/mike/.config/gnome-main-menu/showable_files_migrated
/var/lib/dpkg/info/gnome-main-menu.list
/var/lib/dpkg/info/gnome-main-menu.postrm
/var/cache/apt/archives/gnome-main-menu_0.9.8.svn.20070430-1ubuntu1_amd64.deb
/usr/lib/share/gnome-main-menu
/usr/share/icons/Tangerine/22x22/places/gnome-main-menu.png
/usr/share/icons/Tangerine/24x24/places/gnome-main-menu.png
/usr/share/icons/Tangerine/16x16/places/gnome-main-menu.png
/usr/share/icons/Tangerine/scalable/places/gnome-main-menu.svg
/usr/share/icons/Tangerine/32x32/places/gnome-main-menu.png
/usr/share/icons/Human/22x22/places/gnome-main-menu.png
/usr/share/icons/Human/24x24/places/gnome-main-menu.png
/usr/share/icons/Human/48x48/places/gnome-main-menu.png
/usr/share/icons/Human/scalable/places/gnome-main-menu.svg
/usr/share/icons/gnome/22x22/places/gnome-main-menu.png
/usr/share/icons/gnome/24x24/places/gnome-main-menu.png
/usr/share/icons/gnome/16x16/places/gnome-main-menu.png
/usr/share/icons/gnome/scalable/places/gnome-main-menu.svg
/usr/share/icons/gnome/32x32/places/gnome-main-menu.png
/usr/local/share/locale/tr/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/es/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/sk/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/ar/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/ro/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/zh_CN/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/id/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/gu/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/nb/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/et/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/ka/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/br/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/mr/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/hu/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/pa/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/da/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/bg/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/nl/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/ja/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/en_US/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/sr/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/xh/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/lo/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/en_GB/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/zu/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/de/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/zh_TW/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/mk/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/he/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/it/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/en_CA/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/ta/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/cy/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/pt_BR/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/en_IGID/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/hr/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/gl/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/pl/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/pt/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/fr/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/vi/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/lt/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/ko/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/km/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/sl/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/bn/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/dz/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/af/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/ru/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/el/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/ca/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/fi/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/uk/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/cs/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/hi/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/sv/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/locale/bs/LC_MESSAGES/gnome-main-menu.mo
/usr/local/share/gnome-main-menu
/usr/local/share/gnome-main-menu/documents.xbel
/usr/local/share/gnome-main-menu/applications.xbel
/usr/local/share/gnome-main-menu/places.xbel
/usr/local/share/gnome-main-menu/empty.ods
/usr/local/share/gnome-main-menu/slab-window.glade
/usr/local/share/gnome-main-menu/system-items.xbel

```

It compiles successfullly, no errors, When i install using the deb, or the repo, it install fine into the same directory, so. Apache PHP and MySQL installed into /usr/local fine when i told it.

I'm working on a gtk theme, and would like the customized menu i configured from it, so any help is apprecriated. thanks!

---

