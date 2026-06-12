---
title: "how to install tar.gz file"
date: 2014-06-01
forum: General Help
---

### Post by offir on 2014-06-01
i have ubuntu 14.04 installed
and ubuntu one

ubuntu one is Shut down in the  end of the month

i want to use copy
[https://www.copy.com/home/]("https://www.copy.com/home/")


I downloaded the installation file[SIZE=3][COLOR="#0000CD"] "copy_agent-1.43.0319.tgz"[/COLOR][/SIZE]
But I do not know how to install it
I know extract the files but where ?
And how to install them ?

---

### Post by bapoumba on 2014-06-01
A few threads you might be interested in :
I installed it from : [http://ubuntuforums.org/showthread.php?t=2217206&page=3&p=12989518#post12989518](http://ubuntuforums.org/showthread.php?t=2217206&page=3&p=12989518#post12989518)
[http://ubuntuforums.org/showthread.php?t=2215788&page=2&p=12989766#post12989766](http://ubuntuforums.org/showthread.php?t=2215788&page=2&p=12989766#post12989766)
[http://ubuntuforums.org/showthread.php?t=2217713](http://ubuntuforums.org/showthread.php?t=2217713)

---

### Post by offir on 2014-06-01
Thanks it worked

I have another question


I was able to install the software according to this guide
[http://thinkonbytes.blogspot.co.il/2014/04/choosing-copy-as-file-syncing-software.html]("http://thinkonbytes.blogspot.co.il/2014/04/choosing-copy-as-file-syncing-software.html")

But I ran into a small problem
I run the program with the icon was at the cairo dock

Now I have no icon
And when I want to to activate the software I need to go to this library
```
/home/offir/.copy_client
```
And click on
CopyAgent

The software does not appear in any of the menus

---

### Post by offir on 2014-06-01
i try to install this on another computer
with ubuntu 12.04
and it  dont work 

when i get to this line
```
sudo apt-get install libappindicator1 libcanberra-gtk-module ; mkdir ~/.icons
```
i get an error

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcanberra-gtk-module is already the newest version.
libappindicator1 is already the newest version.
The following packages were automatically installed and are no longer required:
  menu-xdg menu libtasn1-3-bin eom-common gir1.2-unique-3.0
  language-pack-kde-en python-gtksourceview2 gtk2-engines-pixbuf
  libjpeg-turbo-progs python-mate-desktop libxml-twig-perl
  language-pack-kde-en-base kde-l10n-engb libxml-parser-perl libfam0
  libnet-dbus-perl libgtksourceview2.0-common libgtksourceview2.0-0 libvte9
  libgle3 libgtkmm-2.4-1c2a mate-media-common hddtemp libtie-ixhash-perl
  libjpeg62 libxml-xpath-perl libffmpegthumbnailer4 libmatebluetooth
  libmatewnck libmatewnck-common ffmpegthumbnailer libjpeg-progs libvte-common
  xscreensaver-data acroread-common
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
mkdir: cannot create directory `/home/offir/.icons': File exists

```

how can i fix this ?

---

### Post by bapoumba on 2014-06-01
Indicator : there is a ongoing bug. I do have the icon showing, but some do not (you can see the related thread on the forums from one of my previous links).
For 12.04, I think the install process is the same. If you already have a /home/.icons, this is why it cannot be created again. Here is what I have in mine :
```
bapoumba@SonyBlue:~$ ls ~/.icons/
copy-error.svg   copy-sync1.svg  copy-sync4.svg  copy-sync7.svg
copy-insync.svg  copy-sync2.svg  copy-sync5.svg  copy-sync8.svg
copy-paused.svg  copy-sync3.svg  copy-sync6.svg  copy-update.svg
```

---

### Post by offir on 2014-06-01
Is there a way to fix it

I need the software on the computer with Ubuntu 12.04 more than the computer with Ubuntu 14.04

---

### Post by offir on 2014-06-02
if i delete this Libraries
the install will work ?

---

