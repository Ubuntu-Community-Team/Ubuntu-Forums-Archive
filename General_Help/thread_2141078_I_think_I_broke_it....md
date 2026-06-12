---
title: "I think I broke it..."
date: 2013-05-01
forum: General Help
---

### Post by onipar on 2013-05-01
I feel like a real idiot.

I was trying to clean up my computer (ubuntu 12.04 LTS), so I looked up some general "clear cache" commands for the terminal.  I guess I should have known better than to randomly apply changes, but I was in a rush.  Stupid mistake.

Anyway, after restarting, the unity bar as well as the top bar (with settings, volume  etc) were gone.  Nowhere to be found.  I tried searching google and applying some terminal prompts, but nothing is working.

I was hoping there's an easy "restore" thing I can do, or else if someone is familiar with this problem and knows how to fix it?  I'm out of ideas!  :confused:

I don't remember the exact command lines I used, but here are links to pages that I had accessed prior to the problem:
[http://mauriziosiagri.wordpress.com/2012/10/24/clean-and-optimize-ubuntu-12-10-quantal-quetzal/](http://mauriziosiagri.wordpress.com/2012/10/24/clean-and-optimize-ubuntu-12-10-quantal-quetzal/)
[http://www.commandlinefu.com/commands/view/10446/clear-cached-memory-on-ubuntu](http://www.commandlinefu.com/commands/view/10446/clear-cached-memory-on-ubuntu)
[http://ubuntuarena.wordpress.com/2012/12/26/11-tips-to-speed-up-computers-running-ubuntu-12-1012-04linux-mint-13-maya/](http://ubuntuarena.wordpress.com/2012/12/26/11-tips-to-speed-up-computers-running-ubuntu-12-1012-04linux-mint-13-maya/)

I'd appreciate any help, thank you!

---

### Post by zero2xiii on 2013-05-01
Hay,

Can you please give the output of:

```
cat ~/.bash_history
```

So we can see all the commands that might have screwed up  the system?

Thanks

---

### Post by onipar on 2013-05-01
Thanks!  Here you go:

> joey13@Dark-Star:~$ cat ~/.bash_history
./firefox -profilemanager
cd
./thunderbird -profilemanager
CD
cd ./thunderbird -profilemanager
cd ./thunderbird
cd
./thunderbird
thunderbird -P
sudo /usr/share/doc/libdvdread4/install-css.sh
cd~/.thunderbird/
cd .thunderbird p
ls
cd
.terminal -p
cd terminal -P
cd .terminal -P
./thunderbird -profilemanagerP
./thunderbird -P
cd ./thunderbird -P
./thunderbird -profilemanager
./mprime
cd ./mprime
sudo sensors-detect
sudo /home/joey13/mprime
sudo sensors
sudo sensors-detect
service module-init-tools start
sudo /etc/init.d/module-init-tools restart
sudo apt-get autoclean
sudo apt-get clean
deadalive13
sudo /home/joey13/mprime
sudo  /var/log/jockey.log
gedit /var/log/jockey.log
sudo apt-get remove gnome-screensaver
sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra
sudo apt-get purge psych
sudo apt-get remove gnome-screensaver
gksudo gedit /usr/share/applications/gnome-screensaver-preferences.desktop
sudo gedit /usr/share/applications/gnome-screensaver-preferences.desktop
gksudo gedit /usr/share/applications/xscreensaver-preferences.desktop
sudo killall gnome-screensaver
gconftool-2 --type boolean -s /apps/gnome_settings_daemon/screensaver/start_screensaver false
sudo gconftool-2 --type boolean -s /apps/gnome_settings_daemon/screensaver/start_screensaver false
gksudo gedit /usr/share/applications/gnome-screensaver-preferences.desktop
sudo shutdown -r now
sudo shutdown -r now 
sudo apt-get purge gnome-screensaver
sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra
sudo gedit /etc/xdg/autostart/screensaver.desktop
sudo '/media/TODDLER/SSD frimware/SH103_503FW_Lnx.zip' 
sudo'/home/joey13/Desktop/firmware/KINGSTON SSDNow SF Updater L_64Bit' 
deadair13
xtrkcad
update-menus -v
unity -reset
unity reset
restart
cp /var/backups/dpkg.status /var/lib/dpkg/status
sudo dash
sudo firefox
sudo unity
sudo software center
sudo restore
sudo unity
joey13@Dark-Star:~$ 


And just as a follow up, would it be easier (and fix the problem) to simply update to 12.10?  Thanks again!

---

### Post by zero2xiii on 2013-05-01
Hay,

I actually do not see anything that might break unity... It seems you only cleaned apt-get cache and removed gnome screen saver and installed xscreen saver.

However, purging the screen saver might have destroyed some config files shared with unity. Someone might be more on top of that then me.

What happens when you do "unity reset" in terminal?

I highly doubt an "update" will fix it as configuration files are usually kept (one of the big reasons updates usually break the system..).

Hang around a bit. Someone might see something I missed.

Can you please supply the output of this as well, just to see exactly what apt did when you un-installed and installed the screen saver:
```
cat /var/log/apt/term.log
```

Cheers

---

### Post by onipar on 2013-05-01
The screensaver thing was done over a year ago I think, when I was first setting the system up. Unless when I did those purge things it automatically messed with the old screensaver settings and files?  I'll have to get back to you on the other output in a little bit.  thanks again!

Oh, and unity reset didn't seem to do anything that I could see.  :-(

---

### Post by zero2xiii on 2013-05-01
Wow that is random,

okay rather then give the output of:

```
history
```

This might be a more recent, correct out put. (I read the log file up side down #-o)

Or have you done anything in a root shell? Either with SU or SUDO -I? As this will be in a different log.

 EDIT: If you did anything in a root shell please go back to a root shell as you did when running the commands and give the output of "history" for that, but separately please.

Cheers

---

### Post by iiSkeletorii on 2013-05-01
What about a CTRL+ALT+F1 then log in and issue a unity--reset? I noticed you did a unity reset but while still using Unity. Maybe doing it from CLI mode will work better. Use CTRL+ALT+F7 to get back to gui (just in case you didn't know).

---

### Post by Impavidus on 2013-05-01
I see a sudo unity somewhere. Starting unity as root but with your own environment seems a bit risky, but it's not very likely the damage would survive a reboot. Still, it may be a good idea to look for root-owned files in your home directory. Also because you have started firefox with sudo at one time.

Maybe someone can come up with a nice find command to find all root-owned files in your home directory.

---

### Post by zero2xiii on 2013-05-02
Hay,

Shouldn't everything in ~/ be owned by that user? Then you can just run a recursvie chown on the whole home directory to own as user?

I can try and whip up a single liner but I was just wondering..

Cheers

EDIT:
You can start with:
```
ls -l -R | awk '$3=="root" { print $0}'
```

---

### Post by Impavidus on 2013-05-02
You can run a recursive chown, but that won't tell you whether any files were root owned. It doesn't matter much. chown -v would show it, but gives such a lot of output that you'll need to filter it.

And make that command```

ls -l**[COLOR=#ff0000]a[/COLOR]**R | awk '$3=="root" { print $0 }'
```so that it also prints hidden files.

---

### Post by zero2xiii on 2013-05-02
+1,

The A some how slipped my mind. I have an alias set for ls to show all files and colour the output and sort and what what so I can just throw ls in terminal and be done with it.

The attention is in the details ey.. Lol

---

### Post by steeldriver on 2013-05-02
you could also do something like

```
find ~ \( -uid 0 -o -gid 0 \) -ls
```

(find and list attributes of any files or dirs in ~ that are owned by root or whose group is root) or more generally

```
find ~ \( ! -uid $(id -u) -o ! -gid $(id -g) \) -ls
```

(find and list attributes of any files or dirs in ~ whose user or group is not that of the current user)

---

### Post by onipar on 2013-05-03
Hey, sorry for the delay.  Okay, so I tried to unity restart after the cntrl alt f1, but it didn't fix it.  Saw a lot of "error" reads outs on that screen.  Also, I'm sad to say, some of the suggestions are a bit over my head.  I'm not sure of the meaning of "root," for instance.  I did open firefox with "sudo" from a terminal once the unity bar was gone.  Was that a no-no?  Hopefully I'm not screwing things up worse...  Thanks so much for all the help so far; I hope we can figure this out.

 Here's the one output asked for earlier:

> pam@Dark-Star:~$ cat /var/log/apt/term.log

Log started: 2013-05-01  13:31:43
(Reading database ... 550727 files and directories currently installed.)
Preparing to replace libgnutls26:i386 2.12.14-5ubuntu3.2 (using .../libgnutls26_2.12.14-5ubuntu3.3_i386.deb) ...
De-configuring libgnutls26 ...
Unpacking replacement libgnutls26:i386 ...
Preparing to replace libgnutls26 2.12.14-5ubuntu3.2 (using .../libgnutls26_2.12.14-5ubuntu3.3_amd64.deb) ...
Unpacking replacement libgnutls26 ...
Setting up libgnutls26:i386 (2.12.14-5ubuntu3.3) ...
Setting up libgnutls26 (2.12.14-5ubuntu3.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Log ended: 2013-05-01  13:31:54

Log started: 2013-05-01  13:38:30
(Reading database ... 550726 files and directories currently installed.)
Removing ia32-libs ...
Removing ia32-libs-multiarch:i386 ...
Removing bluez-alsa:i386 ...
Removing libesd0:i386 ...
Removing esound-common ...
Removing gstreamer0.10-plugins-good:i386 ...
Removing libsoup-gnome2.4-1:i386 ...
Removing libsoup2.4-1:i386 ...
Removing glib-networking:i386 ...
Removing gstreamer0.10-x:i386 ...
Removing gtk2-engines:i386 ...
Removing gtk2-engines-murrine:i386 ...
Removing gtk2-engines-oxygen:i386 ...
Removing gtk2-engines-pixbuf:i386 ...
Removing ibus-gtk:i386 ...
Removing libaa1:i386 ...
Removing libaio1:i386 ...
Removing libao4:i386 ...
Removing libao-common ...
Removing librsvg2-common:i386 ...
Removing libgail-common:i386 ...
Removing libgail18:i386 ...
Removing libcanberra-gtk-module:i386 ...
Removing libcanberra-gtk0:i386 ...
Removing libgtk2.0-0:i386 ...
Removing libatk1.0-0:i386 ...
Removing libaudiofile1:i386 ...
Removing libavc1394-0:i386 ...
Removing libsdl-ttf2.0-0:i386 ...
Removing libsdl-net1.2:i386 ...
Removing libsdl-mixer1.2:i386 ...
Removing libsdl-image1.2:i386 ...
Removing libsdl1.2debian:i386 ...
Removing libcaca0:i386 ...
Removing libcairo-gobject2:i386 ...
Removing librsvg2-2:i386 ...
Removing libpango1.0-0:i386 ...
Removing libcairo2:i386 ...
Removing libcanberra0:i386 ...
Removing libcap2:i386 ...
Removing libgettextpo0:i386 ...
Removing libcroco3:i386 ...
Removing libcupsimage2:i386 ...
Removing libcurl3:i386 ...
Removing libgconf-2-4:i386 ...
Removing libdbus-glib-1-2:i386 ...
Removing libdv4:i386 ...
Removing libgdbm3:i386 ...
Removing libgdk-pixbuf2.0-0:i386 ...
Removing libgnome-keyring0:i386 ...
Removing libgomp1:i386 ...
Removing libgudev-1.0-0:i386 ...
Removing libibus-1.0-0:i386 ...
Removing libidn11:i386 ...
Removing libiec61883-0:i386 ...
Removing libjasper1:i386 ...
Removing libmad0:i386 ...
Removing libmikmod2:i386 ...
Removing libnss3:i386 ...
Removing libnspr4:i386 ...
Removing libodbc1:i386 ...
Removing libpixman-1-0:i386 ...
Removing libproxy1:i386 ...
Removing libpulse-mainloop-glib0:i386 ...
Removing libpulsedsp:i386 ...
Removing libqt4-opengl:i386 ...
Removing libqt4-svg:i386 ...
Removing libqtwebkit4:i386 ...
Removing libraw1394-11:i386 ...
Removing librtmp0:i386 ...
Removing libshout3:i386 ...
Removing libspeex1:i386 ...
Removing libssl0.9.8:i386 ...
Removing libstdc++5:i386 ...
Removing libtag1c2a:i386 ...
Removing libtag1-vanilla:i386 ...
Removing libtdb1:i386 ...
Removing libunistring0:i386 ...
Removing libvorbisfile3:i386 ...
Removing libwavpack1:i386 ...
Removing libxaw7:i386 ...
Removing libxcb-render0:i386 ...
Removing libxcb-shm0:i386 ...
Removing libxft2:i386 ...
Removing xaw3dg:i386 ...
Removing libxmu6:i386 ...
Removing libxp6:i386 ...
Removing libxss1:i386 ...
Removing libxtst6:i386 ...
Removing libxv1:i386 ...
Removing odbcinst1debian2:i386 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for man-db ...
Processing triggers for gconf2 ...
Processing triggers for install-info ...
Log ended: 2013-05-01  13:39:39

Log started: 2013-05-01  14:38:47
(Reading database ... 550208 files and directories currently installed.)
Preparing to replace linux-libc-dev 3.2.0-40.64 (using .../linux-libc-dev_3.2.0-41.66_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Setting up linux-libc-dev (3.2.0-41.66) ...
Log ended: 2013-05-01  14:38:57

Log started: 2013-05-01  14:45:35
Selecting previously unselected package dconf.
(Reading database ... 550208 files and directories currently installed.)
Unpacking dconf (from .../archives/dconf_0.5.1-2_all.deb) ...
Processing triggers for man-db ...
Setting up dconf (0.5.1-2) ...
Log ended: 2013-05-01  14:45:48

Log started: 2013-05-01  14:48:39
Selecting previously unselected package udo.
(Reading database ... 550219 files and directories currently installed.)
Unpacking udo (from .../archives/udo_6.4.1-1_amd64.deb) ...
Processing triggers for man-db ...
Setting up udo (6.4.1-1) ...
Log ended: 2013-05-01  14:48:44

Log started: 2013-05-01  14:49:46
(Reading database ... 550225 files and directories currently installed.)
Preparing to replace unity 5.18.0-0ubuntu2 (using .../unity_5.18.0-0ubuntu2_amd64.deb) ...
Unpacking replacement unity ...
Processing triggers for man-db ...
Setting up unity (5.18.0-0ubuntu2) ...
Log ended: 2013-05-01  14:49:51

Log started: 2013-05-03  09:35:28
Selecting previously unselected package linux-image-3.2.0-41-generic.
(Reading database ... 550225 files and directories currently installed.)
Unpacking linux-image-3.2.0-41-generic (from .../linux-image-3.2.0-41-generic_3.2.0-41.66_amd64.deb) ...
Done.
Preparing to replace linux-generic 3.2.0.40.48 (using .../linux-generic_3.2.0.41.49_amd64.deb) ...
Unpacking replacement linux-generic ...
Preparing to replace linux-image-generic 3.2.0.40.48 (using .../linux-image-generic_3.2.0.41.49_amd64.deb) ...
Unpacking replacement linux-image-generic ...
Selecting previously unselected package linux-headers-3.2.0-41.
Unpacking linux-headers-3.2.0-41 (from .../linux-headers-3.2.0-41_3.2.0-41.66_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-41-generic.
Unpacking linux-headers-3.2.0-41-generic (from .../linux-headers-3.2.0-41-generic_3.2.0-41.66_amd64.deb) ...
Preparing to replace linux-headers-generic 3.2.0.40.48 (using .../linux-headers-generic_3.2.0.41.49_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
Setting up linux-image-3.2.0-41-generic (3.2.0-41.66) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-41-generic /boot/vmlinuz-3.2.0-41-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-41-generic /boot/vmlinuz-3.2.0-41-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-41-generic /boot/vmlinuz-3.2.0-41-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-41-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-41-generic /boot/vmlinuz-3.2.0-41-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-41-generic /boot/vmlinuz-3.2.0-41-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-41-generic /boot/vmlinuz-3.2.0-41-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-39-generic
Found initrd image: /boot/initrd.img-3.2.0-39-generic
Found linux image: /boot/vmlinuz-3.2.0-38-generic
Found initrd image: /boot/initrd.img-3.2.0-38-generic
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found linux image: /boot/vmlinuz-3.2.0-36-generic
Found initrd image: /boot/initrd.img-3.2.0-36-generic
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found initrd image: /boot/initrd.img-3.2.0-35-generic
Found linux image: /boot/vmlinuz-3.2.0-34-generic
Found initrd image: /boot/initrd.img-3.2.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-33-generic
Found initrd image: /boot/initrd.img-3.2.0-33-generic
Found linux image: /boot/vmlinuz-3.2.0-32-generic
Found initrd image: /boot/initrd.img-3.2.0-32-generic
Found linux image: /boot/vmlinuz-3.2.0-31-generic
Found initrd image: /boot/initrd.img-3.2.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-30-generic
Found initrd image: /boot/initrd.img-3.2.0-30-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-27-generic
Found initrd image: /boot/initrd.img-3.2.0-27-generic
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found linux image: /boot/vmlinuz-3.2.0-25-generic
Found initrd image: /boot/initrd.img-3.2.0-25-generic
Found linux image: /boot/vmlinuz-3.0.0-21-generic
Found initrd image: /boot/initrd.img-3.0.0-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-generic (3.2.0.41.49) ...
Setting up linux-headers-3.2.0-41 (3.2.0-41.66) ...
Setting up linux-headers-3.2.0-41-generic (3.2.0-41.66) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-41-generic /boot/vmlinuz-3.2.0-41-generic
Setting up linux-headers-generic (3.2.0.41.49) ...
Setting up linux-generic (3.2.0.41.49) ...
Log ended: 2013-05-03  09:36:48


> pam@Dark-Star:~$ history
    1  sudo apt-get remove gnome-screensaver
    2  sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra
    3  sudo apt-get remove mystery of mortlake mansion
    4  sudo apt-get remove mystery_of_mortlake_mansion
    5  sudo apt-get remove MortlakeMansion
    6  sudo apt-get remove MortlakeMansion.exe
    7  sude apt-get remove Mystery_of_Mortlake_Mansion
    8  sudo apt-get remove Mystery_of_Mortlake_Mansion
    9  sude apt-get remove Mystery_of_Mortlake_Mansionsudo apt-get remove Mystery_of_Mortlake_Mansion
   10  sudo apt-get remove MysteryofMortlakeMansion
   11  sudo apt-get remove MysteryofMortlakeMansion.exe
   12  sudo apt-get remove MysteryofMortlakeMansion.lnk
   13  sudo add-apt-repository ppa:caffeine-developers/ppa
   14  sudo apt-get remove overlay-scrollbar liboverlay-scrollbar3-0.2-0 liboverlay-scrollbar-0.2-0
   15  sudo add-apt-repository ppa:webupd8team/gnome3
   16  sudo apt-get install gnome-sushi
   17  sudo apt-get install openjdk-7-jre
   18  sudo /etc/init.d/dns-clean
   19  sudo apt-get autoclean
   20  cat /proc/sys/vm/swappiness
   21  sudo apt-get autoremove && sudo apt-get autoclean && sudo apt-get purge && sudo apt-get clean
   22  sudo apt-get check ; sudo apt-get -f install
   23  sudo apt-get install deborphan 
   24  sudo deborphan | xargs sudo apt-get -y remove --purge
   25  and
   26  sudo dpkg --purge `dpkg -l | egrep "^rc" | cut -d ' ' -f3`
   27  sudo apt-get upgrade
   28  sudo apt-get update
   29  unity --reset
   30  dash
   31  sudo firefox
   32  setsid unity
   33  dconf reset -f /org/compiz/
   34  sudo apt-get install dconf
   35  udo apt-get install compizconfig-settings-manager
   36  sudo apt-get install udo
   37  sudo firefox
   38  sudo apt-get -f install && sudo apt-get --reinstall install unity
   39  history
pam@Dark-Star:~$ 


> pam@Dark-Star:~$ cat ~/.bash_history
sudo apt-get remove gnome-screensaver
sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra
sudo apt-get remove mystery of mortlake mansion
sudo apt-get remove mystery_of_mortlake_mansion
sudo apt-get remove MortlakeMansion
sudo apt-get remove MortlakeMansion.exe
sude apt-get remove Mystery_of_Mortlake_Mansion
sudo apt-get remove Mystery_of_Mortlake_Mansion
sude apt-get remove Mystery_of_Mortlake_Mansionsudo apt-get remove Mystery_of_Mortlake_Mansion
sudo apt-get remove MysteryofMortlakeMansion
sudo apt-get remove MysteryofMortlakeMansion.exe
sudo apt-get remove MysteryofMortlakeMansion.lnk
sudo add-apt-repository ppa:caffeine-developers/ppa
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar3-0.2-0 liboverlay-scrollbar-0.2-0
sudo add-apt-repository ppa:webupd8team/gnome3
sudo apt-get install gnome-sushi
sudo apt-get install openjdk-7-jre
sudo /etc/init.d/dns-clean
sudo apt-get autoclean
cat /proc/sys/vm/swappiness
sudo apt-get autoremove && sudo apt-get autoclean && sudo apt-get purge && sudo apt-get clean
sudo apt-get check ; sudo apt-get -f install
sudo apt-get install deborphan 
sudo deborphan | xargs sudo apt-get -y remove --purge
and
sudo dpkg --purge `dpkg -l | egrep "^rc" | cut -d ' ' -f3`
sudo apt-get upgrade
sudo apt-get update
unity --reset
dash
sudo firefox
setsid unity
dconf reset -f /org/compiz/
sudo apt-get install dconf
udo apt-get install compizconfig-settings-manager
sudo apt-get install udo
sudo firefox
sudo apt-get -f install && sudo apt-get --reinstall install unity
pam@Dark-Star:~$ 


---

### Post by onipar on 2013-05-03
Okay, and some other outputs asked for I believe?

> pam@Dark-Star:~$ ls -laR | awk '$3=="root" { print $0 }'
drwxr-xr-x  4 root root    4096 Dec 11  2011 ..
-rw-r--r--  1 root root    62961 May  3 12:05 blocklist.xml
drwxr-xr-x 18 root root     4096 May  3 12:00 Cache
ls: cannot open directory ./.mozilla/firefox/i04g5cet.default/Cache/0: Permission denied
ls: cannot open directory ./.mozilla/firefox/i04g5cet.default/Cache/1: Permission denied
ls: cannot open directory ./.mozilla/firefox/i04g5cet.default/Cache/2: Permission denied
ls: cannot open directory ./.mozilla/firefox/i04g5cet.default/Cache/3: Permission denied
ls: cannot open directory ./.mozilla/firefox/i04g5cet.default/Cache/4: Permission denied
ls: cannot open directory ./.mozilla/firefox/i04g5cet.default/Cache/5: Permission denied
ls: cannot open directory ./.mozilla/firefox/i04g5cet.default/Cache/6: Permission denied
ls: cannot open directory ./.mozilla/firefox/i04g5cet.default/Cache/7: Permission denied
ls: cannot open directory ./.mozilla/firefox/i04g5cet.default/Cache/8: Permission denied
ls: cannot open directory ./.mozilla/firefox/i04g5cet.default/Cache/9: Permission denied
ls: cannot open directory ./.mozilla/firefox/i04g5cet.default/Cache/A: Permission denied
ls: cannot open directory ./.mozilla/firefox/i04g5cet.default/Cache/B: Permission denied
ls: cannot open directory ./.mozilla/firefox/i04g5cet.default/Cache/C: Permission denied
ls: cannot open directory ./.mozilla/firefox/i04g5cet.default/Cache/D: Permission denied
ls: cannot open directory ./.mozilla/firefox/i04g5cet.default/Cache/E: Permission denied
ls: cannot open directory ./.mozilla/firefox/i04g5cet.default/Cache/F: Permission denied
lrwxrwxrwx  1 root root       15 May  3 11:59 lock -> 127.0.1.1:+2371
-rw-------  1 root root     4305 May  3 12:00 prefs.js
drwxr-xr-x  2 root root     4096 May  3 12:03 safebrowsing
-rw-------  1 root root     3928 May  3 12:08 sessionstore.js
drwxr-xr-x 18 root root   4096 May  3 12:00 .
drwx------  4 root root   4096 May  3 12:00 0
drwx------  4 root root   4096 May  3 12:00 1
drwx------  5 root root   4096 May  3 12:00 2
drwx------  3 root root   4096 May  3 12:00 3
drwx------  2 root root   4096 May  3 12:00 4
drwx------  3 root root   4096 May  3 12:00 5
drwx------  2 root root   4096 May  3 12:00 6
drwx------  5 root root   4096 May  3 12:05 7
drwx------  3 root root   4096 May  3 12:00 8
drwx------  3 root root   4096 May  3 12:00 9
drwx------  4 root root   4096 May  3 12:00 A
drwx------  3 root root   4096 May  3 12:08 B
drwx------  3 root root   4096 May  3 12:00 C
-rw-------  1 root root 133884 May  3 12:08 _CACHE_001_
-rw-------  1 root root  67339 May  3 12:06 _CACHE_002_
-rw-------  1 root root 377538 May  3 12:08 _CACHE_003_
-rw-------  1 root root    276 May  3 12:00 _CACHE_MAP_
drwx------  4 root root   4096 May  3 12:00 D
drwx------  3 root root   4096 May  3 12:06 E
drwx------  5 root root   4096 May  3 12:00 F
drwxr-xr-x  2 root root    4096 May  3 12:03 .
-rw-r--r--  1 root root       4 May  3 12:03 classifier.hashkey
-rw-r--r--  1 root root      12 May  3 12:03 goog-malware-shavar.cache
-rw-r--r--  1 root root  811766 May  3 12:03 goog-malware-shavar.pset
-rw-r--r--  1 root root 1748458 May  3 12:03 goog-malware-shavar.sbstore
-rw-r--r--  1 root root      12 May  3 12:03 goog-phish-shavar.cache
-rw-r--r--  1 root root  678016 May  3 12:03 goog-phish-shavar.pset
-rw-r--r--  1 root root  580651 May  3 12:03 goog-phish-shavar.sbstore
-rw-r--r--  1 root root      44 May  3 12:03 test-malware-simple.cache
-rw-r--r--  1 root root      16 May  3 12:03 test-malware-simple.pset
-rw-r--r--  1 root root     232 May  3 12:03 test-malware-simple.sbstore
-rw-r--r--  1 root root      44 May  3 12:03 test-phish-simple.cache
-rw-r--r--  1 root root      16 May  3 12:03 test-phish-simple.pset
-rw-r--r--  1 root root     232 May  3 12:03 test-phish-simple.sbstore
-rw-r--r--  1 root root  34877 May  3 12:00 6a871c402d12edd219f1fca397b607c8.png
-rw-r--r--  1 root root  31189 May  3 12:06 72b3e9eafaf8978c586171d3644273b3.png
-rw-r--r--  1 root root  29173 May  3 12:08 8cff6fc3e14f7638db70b9a0c86cc862.png
-rw-r--r--  1 root root  24980 May  3 12:08 9eee74c44977129069e0d6370e1ee456.png
-rw-r--r--  1 root root  40452 May  3 12:00 c2dad8fb25e6a52d4eff332f8252ef6d.png
-rw-r--r--  1 root root  51186 May  3 12:00 cdc065f85e054c0b7f432bfed0607f1e.png
-rw-r--r--  1 root root  42839 May  1 14:40 0b59e5427e9179cc20fcccd75532f78a.png
-rw-r--r--  1 root root  46327 May  1 14:47 22319446eaf0d5d4909d7b547bb70d94.png
-rw-r--r--  1 root root  34465 May  1 14:34 24f8111decabf3788fee80144e7fa2ac.png
-rw-r--r--  1 root root 107874 May  1 14:44 39b386d529e42c99020c76248bf81d69.png
-rw-r--r--  1 root root  44182 May  1 14:34 4447a278751fb18b431caa92d02b851f.png
-rw-r--r--  1 root root 108998 May  1 14:36 4a0d6199af8e646713f3cae736959dd1.png
-rw-r--r--  1 root root  44731 May  1 14:37 5563dd741659853a6743e61b37067fba.png
-rw-r--r--  1 root root 104654 May  1 14:49 6b42a159caa32925647c05f44b09d4a5.png
-rw-r--r--  1 root root  69654 May  1 14:36 74dc28c0908e982fd95a5115758b0182.png
-rw-r--r--  1 root root  43549 May  1 14:39 7a0c7887000ad3c8aeff4fad39911bb3.png
-rw-r--r--  1 root root  44060 May  1 14:36 849ecb0b1a8f9790917aaed2c4f28e6b.png
-rw-r--r--  1 root root  58382 May  1 14:38 9b3f0aa63042283ca5b61172c7af9acd.png
-rw-r--r--  1 root root  43549 May  1 14:39 b4a85b787f5f2db9ff74e3f6c62e412c.png
-rw-r--r--  1 root root 116857 May  1 14:37 c593e6f4635ae9afc4ef301cac760ba7.png
-rw-r--r--  1 root root 115658 May  1 14:47 d8bd5fccbb9ed63eb32d0d91abbb4338.png
-rw-r--r--  1 root root  44628 May  1 14:49 dbdd812f4d786099ccfa554c70bbf003.png
-rw-r--r--  1 root root  43478 May  1 14:40 dd9b76b871726f21113e772ed1b866a1.png
-rw-r--r--  1 root root    2 May  3 11:59 webapps.json
pam@Dark-Star:~$ 


---

### Post by onipar on 2013-05-03
Again, thank you SO much for taking the time to help with this!

> pam@Dark-Star:~$ find ~ \( -uid 0 -o -gid 0 \) -ls
3803682   44 -rw-r--r--   1 root     root        42839 May  1 14:40 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails-old/0b59e5427e9179cc20fcccd75532f78a.png
3803687   44 -rw-r--r--   1 root     root        44628 May  1 14:49 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails-old/dbdd812f4d786099ccfa554c70bbf003.png
3803670   44 -rw-r--r--   1 root     root        44182 May  1 14:34 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails-old/4447a278751fb18b431caa92d02b851f.png
3803688  104 -rw-r--r--   1 root     root       104654 May  1 14:49 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails-old/6b42a159caa32925647c05f44b09d4a5.png
3803684  116 -rw-r--r--   1 root     root       115658 May  1 14:47 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails-old/d8bd5fccbb9ed63eb32d0d91abbb4338.png
3802096   44 -rw-r--r--   1 root     root        44731 May  1 14:37 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails-old/5563dd741659853a6743e61b37067fba.png
3803726  116 -rw-r--r--   1 root     root       116857 May  1 14:37 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails-old/c593e6f4635ae9afc4ef301cac760ba7.png
3803686   48 -rw-r--r--   1 root     root        46327 May  1 14:47 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails-old/22319446eaf0d5d4909d7b547bb70d94.png
3803742   60 -rw-r--r--   1 root     root        58382 May  1 14:38 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails-old/9b3f0aa63042283ca5b61172c7af9acd.png
3803707   72 -rw-r--r--   1 root     root        69654 May  1 14:36 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails-old/74dc28c0908e982fd95a5115758b0182.png
3803373   44 -rw-r--r--   1 root     root        43549 May  1 14:39 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails-old/7a0c7887000ad3c8aeff4fad39911bb3.png
3803673   36 -rw-r--r--   1 root     root        34465 May  1 14:34 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails-old/24f8111decabf3788fee80144e7fa2ac.png
3803741   44 -rw-r--r--   1 root     root        43549 May  1 14:39 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails-old/b4a85b787f5f2db9ff74e3f6c62e412c.png
3803685  108 -rw-r--r--   1 root     root       107874 May  1 14:44 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails-old/39b386d529e42c99020c76248bf81d69.png
3803674   44 -rw-r--r--   1 root     root        44060 May  1 14:36 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails-old/849ecb0b1a8f9790917aaed2c4f28e6b.png
3803678   44 -rw-r--r--   1 root     root        43478 May  1 14:40 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails-old/dd9b76b871726f21113e772ed1b866a1.png
3803722  108 -rw-r--r--   1 root     root       108998 May  1 14:36 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails-old/4a0d6199af8e646713f3cae736959dd1.png
2621778    4 -rw-r--r--   1 root     root            2 May  3 11:59 /home/pam/.mozilla/firefox/i04g5cet.default/webapps/webapps.json
2492029    0 lrwxrwxrwx   1 root     root           15 May  3 11:59 /home/pam/.mozilla/firefox/i04g5cet.default/lock -> 127.0.1.1:+2371
3801649   32 -rw-r--r--   1 root     root        29173 May  3 12:08 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails/8cff6fc3e14f7638db70b9a0c86cc862.png
3802137   28 -rw-r--r--   1 root     root        25073 May  3 12:09 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails/9eee74c44977129069e0d6370e1ee456.png
3802860   36 -rw-r--r--   1 root     root        34877 May  3 12:00 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails/6a871c402d12edd219f1fca397b607c8.png
3803948   40 -rw-r--r--   1 root     root        40452 May  3 12:00 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails/c2dad8fb25e6a52d4eff332f8252ef6d.png
3801147   32 -rw-r--r--   1 root     root        31189 May  3 12:06 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails/72b3e9eafaf8978c586171d3644273b3.png
3803945   52 -rw-r--r--   1 root     root        51186 May  3 12:00 /home/pam/.mozilla/firefox/i04g5cet.default/thumbnails/cdc065f85e054c0b7f432bfed0607f1e.png
3932544    4 drwxr-xr-x  18 root     root         4096 May  3 12:00 /home/pam/.mozilla/firefox/i04g5cet.default/Cache
3932554    4 drwx------   3 root     root         4096 May  3 12:00 /home/pam/.mozilla/firefox/i04g5cet.default/Cache/8
find: `/home/pam/.mozilla/firefox/i04g5cet.default/Cache/8': Permission denied
3932564  376 -rw-------   1 root     root       381634 May  3 12:09 /home/pam/.mozilla/firefox/i04g5cet.default/Cache/_CACHE_003_
3932546    4 drwx------   4 root     root         4096 May  3 12:00 /home/pam/.mozilla/firefox/i04g5cet.default/Cache/0
find: `/home/pam/.mozilla/firefox/i04g5cet.default/Cache/0': Permission denied
3932549    4 drwx------   3 root     root         4096 May  3 12:00 /home/pam/.mozilla/firefox/i04g5cet.default/Cache/3
find: `/home/pam/.mozilla/firefox/i04g5cet.default/Cache/3': Permission denied
3932552    4 drwx------   2 root     root         4096 May  3 12:00 /home/pam/.mozilla/firefox/i04g5cet.default/Cache/6
find: `/home/pam/.mozilla/firefox/i04g5cet.default/Cache/6': Permission denied
3932550    4 drwx------   2 root     root         4096 May  3 12:00 /home/pam/.mozilla/firefox/i04g5cet.default/Cache/4
find: `/home/pam/.mozilla/firefox/i04g5cet.default/Cache/4': Permission denied
3932561    4 drwx------   5 root     root         4096 May  3 12:00 /home/pam/.mozilla/firefox/i04g5cet.default/Cache/F
find: `/home/pam/.mozilla/firefox/i04g5cet.default/Cache/F': Permission denied
3932557    4 drwx------   3 root     root         4096 May  3 12:08 /home/pam/.mozilla/firefox/i04g5cet.default/Cache/B
find: `/home/pam/.mozilla/firefox/i04g5cet.default/Cache/B': Permission denied
3932556    4 drwx------   4 root     root         4096 May  3 12:00 /home/pam/.mozilla/firefox/i04g5cet.default/Cache/A
find: `/home/pam/.mozilla/firefox/i04g5cet.default/Cache/A': Permission denied
3932551    4 drwx------   3 root     root         4096 May  3 12:00 /home/pam/.mozilla/firefox/i04g5cet.default/Cache/5
find: `/home/pam/.mozilla/firefox/i04g5cet.default/Cache/5': Permission denied
3932560    4 drwx------   3 root     root         4096 May  3 12:06 /home/pam/.mozilla/firefox/i04g5cet.default/Cache/E
find: `/home/pam/.mozilla/firefox/i04g5cet.default/Cache/E': Permission denied
3932547    4 drwx------   4 root     root         4096 May  3 12:00 /home/pam/.mozilla/firefox/i04g5cet.default/Cache/1
find: `/home/pam/.mozilla/firefox/i04g5cet.default/Cache/1': Permission denied
3932562  132 -rw-------   1 root     root       133884 May  3 12:09 /home/pam/.mozilla/firefox/i04g5cet.default/Cache/_CACHE_001_
3932558    4 drwx------   3 root     root         4096 May  3 12:00 /home/pam/.mozilla/firefox/i04g5cet.default/Cache/C
find: `/home/pam/.mozilla/firefox/i04g5cet.default/Cache/C': Permission denied
3932545    4 -rw-------   1 root     root          276 May  3 12:00 /home/pam/.mozilla/firefox/i04g5cet.default/Cache/_CACHE_MAP_
3932555    4 drwx------   3 root     root         4096 May  3 12:00 /home/pam/.mozilla/firefox/i04g5cet.default/Cache/9
find: `/home/pam/.mozilla/firefox/i04g5cet.default/Cache/9': Permission denied
3932559    4 drwx------   4 root     root         4096 May  3 12:00 /home/pam/.mozilla/firefox/i04g5cet.default/Cache/D
find: `/home/pam/.mozilla/firefox/i04g5cet.default/Cache/D': Permission denied
3932553    4 drwx------   5 root     root         4096 May  3 12:05 /home/pam/.mozilla/firefox/i04g5cet.default/Cache/7
find: `/home/pam/.mozilla/firefox/i04g5cet.default/Cache/7': Permission denied
3932563   68 -rw-------   1 root     root        67339 May  3 12:06 /home/pam/.mozilla/firefox/i04g5cet.default/Cache/_CACHE_002_
3932548    4 drwx------   5 root     root         4096 May  3 12:00 /home/pam/.mozilla/firefox/i04g5cet.default/Cache/2
find: `/home/pam/.mozilla/firefox/i04g5cet.default/Cache/2': Permission denied
2492031   20 -rw-------   1 root     root        17372 May  3 12:10 /home/pam/.mozilla/firefox/i04g5cet.default/sessionstore.js
2492032    8 -rw-------   1 root     root         4305 May  3 12:00 /home/pam/.mozilla/firefox/i04g5cet.default/prefs.js
2490535   64 -rw-r--r--   1 root     root        62961 May  3 12:05 /home/pam/.mozilla/firefox/i04g5cet.default/blocklist.xml
3801136    4 drwxr-xr-x   2 root     root         4096 May  3 12:03 /home/pam/.mozilla/firefox/i04g5cet.default/safebrowsing
3802252 1708 -rw-r--r--   1 root     root      1748458 May  3 12:03 /home/pam/.mozilla/firefox/i04g5cet.default/safebrowsing/goog-malware-shavar.sbstore
3801721    4 -rw-r--r--   1 root     root           12 May  3 12:03 /home/pam/.mozilla/firefox/i04g5cet.default/safebrowsing/goog-phish-shavar.cache
3802120  568 -rw-r--r--   1 root     root       580651 May  3 12:03 /home/pam/.mozilla/firefox/i04g5cet.default/safebrowsing/goog-phish-shavar.sbstore
3801740    4 -rw-r--r--   1 root     root           44 May  3 12:03 /home/pam/.mozilla/firefox/i04g5cet.default/safebrowsing/test-phish-simple.cache
3801663    4 -rw-r--r--   1 root     root           12 May  3 12:03 /home/pam/.mozilla/firefox/i04g5cet.default/safebrowsing/goog-malware-shavar.cache
3802125    4 -rw-r--r--   1 root     root           16 May  3 12:03 /home/pam/.mozilla/firefox/i04g5cet.default/safebrowsing/test-malware-simple.pset
3802138    4 -rw-r--r--   1 root     root           16 May  3 12:03 /home/pam/.mozilla/firefox/i04g5cet.default/safebrowsing/test-phish-simple.pset
3802141  796 -rw-r--r--   1 root     root       811766 May  3 12:03 /home/pam/.mozilla/firefox/i04g5cet.default/safebrowsing/goog-malware-shavar.pset
3802143    4 -rw-r--r--   1 root     root          232 May  3 12:03 /home/pam/.mozilla/firefox/i04g5cet.default/safebrowsing/test-malware-simple.sbstore
3802145  664 -rw-r--r--   1 root     root       678016 May  3 12:03 /home/pam/.mozilla/firefox/i04g5cet.default/safebrowsing/goog-phish-shavar.pset
3802151    4 -rw-r--r--   1 root     root           44 May  3 12:03 /home/pam/.mozilla/firefox/i04g5cet.default/safebrowsing/test-malware-simple.cache
3802199    4 -rw-r--r--   1 root     root          232 May  3 12:03 /home/pam/.mozilla/firefox/i04g5cet.default/safebrowsing/test-phish-simple.sbstore
3802203    4 -rw-r--r--   1 root     root            4 May  3 12:03 /home/pam/.mozilla/firefox/i04g5cet.default/safebrowsing/classifier.hashkey
pam@Dark-Star:~$ 


---

### Post by Impavidus on 2013-05-03
I see quite a lot of of root-owned files, all of them in the .mozilla directory. This is caused by running firefox as root. You can solve that part of the problem by running```
sudo chown -R pam:pam .mozilla/
```(pam is your user name, right?)

---

### Post by onipar on 2013-05-03
Pam, yes.  The other user is joey13, but the damage was done under the pam username.  I'll run that code, thanks. The code didn't seem to do anything...

---

### Post by daredent on 2013-05-03
You are not learning, until you break it.   ;)

---

### Post by zero2xiii on 2013-05-03
Hay,

I see something about unity in the apt-get logs:
> Log started: 2013-05-01 14:49:46
 (Reading database ... 550225 files and directories currently installed.)
 Preparing to replace unity 5.18.0-0ubuntu2 (using .../unity_5.18.0-0ubuntu2_amd64.deb) ...
 Unpacking replacement unity ...
 Processing triggers for man-db ...
 Setting up unity (5.18.0-0ubuntu2) ...
 Log ended: 2013-05-01 14:49:51

Which is weird because it "updated" to a 64-bit version, not a higher version? Are you running a 32 or 64 bit install?
If you are unsure please post the output of:

```
uname -a
```

Also I see a LOT of stuff removed, never to be replaced, including some core functioning tools:
> ```
Log started: 2013-05-01 13:38:30
 (Reading database ... 550726 files and directories currently installed.)
 Removing ia32-libs ...
 Removing ia32-libs-multiarch:i386 ...
 Removing bluez-alsa:i386 ...
 Removing libesd0:i386 ...
 Removing esound-common ...
 Removing gstreamer0.10-plugins-good:i386 ...
 Removing libsoup-gnome2.4-1:i386 ...
 Removing libsoup2.4-1:i386 ...
 Removing glib-networking:i386 ...
 Removing gstreamer0.10-x:i386 ...
 Removing gtk2-engines:i386 ...
 Removing gtk2-engines-murrine:i386 ...
 Removing gtk2-engines-oxygen:i386 ...
 Removing gtk2-engines-pixbuf:i386 ...
 Removing ibus-gtk:i386 ...
 Removing libaa1:i386 ...
 Removing libaio1:i386 ...
 Removing libao4:i386 ...
 Removing libao-common ...
 Removing librsvg2-common:i386 ...
 Removing libgail-common:i386 ...
 Removing libgail18:i386 ...
 Removing libcanberra-gtk-module:i386 ...
 Removing libcanberra-gtk0:i386 ...
 Removing libgtk2.0-0:i386 ...
 Removing libatk1.0-0:i386 ...
 Removing libaudiofile1:i386 ...
 Removing libavc1394-0:i386 ...
 Removing libsdl-ttf2.0-0:i386 ...
 Removing libsdl-net1.2:i386 ...
 Removing libsdl-mixer1.2:i386 ...
 Removing libsdl-image1.2:i386 ...
 Removing libsdl1.2debian:i386 ...
 Removing libcaca0:i386 ...
 Removing libcairo-gobject2:i386 ...
 Removing librsvg2-2:i386 ...
 Removing libpango1.0-0:i386 ...
 Removing libcairo2:i386 ...
 Removing libcanberra0:i386 ...
 Removing libcap2:i386 ...
 Removing libgettextpo0:i386 ...
 Removing libcroco3:i386 ...
 Removing libcupsimage2:i386 ...
 Removing libcurl3:i386 ...
 Removing libgconf-2-4:i386 ...
 Removing libdbus-glib-1-2:i386 ...
 Removing libdv4:i386 ...
 Removing libgdbm3:i386 ...
 Removing libgdk-pixbuf2.0-0:i386 ...
 Removing libgnome-keyring0:i386 ...
 Removing libgomp1:i386 ...
 Removing libgudev-1.0-0:i386 ...
 Removing libibus-1.0-0:i386 ...
 Removing libidn11:i386 ...
 Removing libiec61883-0:i386 ...
 Removing libjasper1:i386 ...
 Removing libmad0:i386 ...
 Removing libmikmod2:i386 ...
 Removing libnss3:i386 ...
 Removing libnspr4:i386 ...
 Removing libodbc1:i386 ...
 Removing libpixman-1-0:i386 ...
 Removing libproxy1:i386 ...
 Removing libpulse-mainloop-glib0:i386 ...
 Removing libpulsedsp:i386 ...
 Removing libqt4-opengl:i386 ...
 Removing libqt4-svg:i386 ...
 Removing libqtwebkit4:i386 ...
 Removing libraw1394-11:i386 ...
 Removing librtmp0:i386 ...
 Removing libshout3:i386 ...
 Removing libspeex1:i386 ...
 Removing libssl0.9.8:i386 ...
 Removing libstdc++5:i386 ...
 Removing libtag1c2a:i386 ...
 Removing libtag1-vanilla:i386 ...
 Removing libtdb1:i386 ...
 Removing libunistring0:i386 ...
 Removing libvorbisfile3:i386 ...
 Removing libwavpack1:i386 ...
 Removing libxaw7:i386 ...
 Removing libxcb-render0:i386 ...
 Removing libxcb-shm0:i386 ...
 Removing libxft2:i386 ...
 Removing xaw3dg:i386 ...
 Removing libxmu6:i386 ...
 Removing libxp6:i386 ...
 Removing libxss1:i386 ...
 Removing libxtst6:i386 ...
 Removing libxv1:i386 ...
 Removing odbcinst1debian2:i386 ...
 Processing triggers for libc-bin ...
 ldconfig deferred processing now taking place
 Processing triggers for libglib2.0-0:i386 ...
 Processing triggers for man-db ...
 Processing triggers for gconf2 ...
 Processing triggers for install-info ...
 Log ended: 2013-05-01 13:39:39
```

It seems you updated to a 64bit architecture. But I may be reading this whole log just wrong.

I do not however see where the screen saver was removed. Sigh. Wow. I might just be asleep. It is rather late. Maybe some one with a fresh eye spots something else.

I will look over this in the morning again with a fresh eye.

Cheers for now.

---

### Post by zero2xiii on 2013-05-03
> **Impavidus said:**
> I see quite a lot of of root-owned files, all of them in the .mozilla directory. This is caused by running firefox as root. You can solve that part of the problem by running```
sudo chown -R pam:pam .mozilla/
```(pam is your user name, right?)

Just for interest sake.

I always give chown commands as:

```
chown $(whoami):$(whoami)
```

so there is no way the username can be wrong lol. Just thought I'd share that.

---

### Post by onipar on 2013-05-03
Yeah, it's 64 bit, but just for the sake of being complete, I did the code and it spit this out:
> Linux Dark-Star 3.2.0-41-generic #66-Ubuntu SMP Thu Apr 25 03:27:11 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Thanks again for continuing to look over these logs.  I hope we can figure something out.  Cheers!

---

### Post by zero2xiii on 2013-05-04
Hay,

So I went over the logs again... Still nothing ringing a bell...

Somethings that MIGHT cause your issues.

Why did you run:
```
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar3-0.2-0 liboverlay-scrollbar-0.2-0
```

Also have you installed anything from the PPA you added:
```
sudo add-apt-repository ppa:webupd8team/gnome3
```

And we are going to need the older apt-get logs to see the changes made by the above command.

So to try out now,
Re-install the removed packages (you can remove them again if they do not affect anything):
```
sudo apt-get install overlay-scrollbar liboverlay-scrollbar3-0.2-0 liboverlay-scrollbar-0.2-0
```
To remove them purge them instead of just removing them (perge removes all config files as well):
```
sudo apt-get purge overlay-scrollbar liboverlay-scrollbar3-0.2-0 liboverlay-scrollbar-0.2-0
```

And lastly we need to see your logs directory so we can give the corect command to unpack the correct log file:
```
ls /var/log/apt/
```

This is really strange as I do not see anything thus far that will cause the issues you are describing. If anyone sees anything I might be missing please post it.

Cheers

---

### Post by onipar on 2013-05-04
Honestly, I'm not sure why I ran

sudo apt-get remove overlay-scrollbar liboverlay-scrollbar3-0.2-0 liboverlay-scrollbar-0.2-0

 I also don't think i added anything from the PPA, but again, I'm not sure what that even is!  
I guess I should have mentioned this is my parents' computer, and I'm just trying to fix it for them. 
 So they may have done things on here that I'm not aware of.

The output of that code you posted is sort of strange, but here it is:

> pam@Dark-Star:~$ ls /var/log/apt/
history.log        history.log.4.gz  term.log.10.gz  term.log.5.gz
history.log.10.gz  history.log.5.gz  term.log.11.gz  term.log.6.gz
history.log.11.gz  history.log.6.gz  term.log.12.gz  term.log.7.gz
history.log.12.gz  history.log.7.gz  term.log.1.gz   term.log.8.gz
history.log.1.gz   history.log.8.gz  term.log.2.gz   term.log.9.gz
history.log.2.gz   history.log.9.gz  term.log.3.gz
history.log.3.gz   term.log          term.log.4.gz
pam@Dark-Star:~$ 


EDIT:  Oh, and I ran that code to install the scrollbar, but nothing seemed to happen.  

Just for the sake of being completely informed, I've been making the changes and using firefox in the GNOME desktop, which works fine.  Then I restart and go into Ubuntu desktop to see if the unity bar has reappeared (which it has not).  :(

---

### Post by zero2xiii on 2013-05-05
Hay,

Wow oka it is strange. Really having a hard time finding the cause for this.

Please:
```
zmore /var/log/apt/history.log.1.gz
```
and for completeness:
```
zmore /var/log/apt/history.log.2.gz
```

Please note the output of the above is scrollable. Keep pressing >SPACE< to page scroll untill it exits and then copy the output here.

You can try this before giving the above logs. This might resolve the issue. Please note this resets the settings to default as if it is a fresh install basically.
Before you re-install unity, please try this, it will backup and remove ALL gnome3 related config files. After this, please log out and back in to see what is the outcome of the commands ([found here]("http://askubuntu.com/questions/56313/how-do-i-reset-gnome-to-the-defaults")):
```
mkdir ./.old-gnome-config/ && mv ./.gnome* ./.old-gnome-config/ && mv .gconf* ./.old-gnome-config/ && mv ./.metacity ./.old-gnome-config/ && mv ./.cache ./.old-gnome-config/ && mv ./.dbus ./.old-gnome-config/ && mv ./.dmrc ./.old-gnome-config/ && mv ./.mission-control ./.old-gnome-config/ && mv ./.thumbnails ./.old-gnome-config/   && ~/.config/dconf/* ./.old-gnome-config/
```
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity .cache .dbus .dmrc .mission-control .thumbnails ~/.config/dconf/user ~.compiz*
```

If you feel gutsy and want to try it. You can purge compiz unity and reinstall it following these steps found [here]("http://askubuntu.com/questions/131016/how-can-i-remove-and-re-install-unity"):
```
sudo apt-get remove compizconfig-settings-manager
sudo apt-get remove compiz-fusion-plugins-extra
sudo apt-get remove compiz-plugins-extra
sudo apt-get purge compiz*
```

```
sudo apt-get install unity-2d
sudo apt-get install ubuntu-desktop
sudo apt-get install ubuntu-desktop-2d
sudo apt-get install compizconfig-settings-manager
sudo apt-get install xserver-xgl
sudo apt-get install emerald
sudo apt-get install compiz-fusion-plugins-extra
sudo apt-get install git compiz-plugins-extra
sudo apt-get install compiz-plugins-extra
sudo apt-get install unity
```

Wow.

Well good luck.

---

### Post by onipar on 2013-05-05
I tried that one "mkdir" command to reset gnome and it spit this back out at me:  mv: cannot stat `./.metacity': No such file or directory

I didn't do the second one because I think you meant I was only supoed to do the second one after the first?  And I didn't do the purge compiz thing, but I might after this...

Here are the outputs you wanted:

> am@Dark-Star:~$ zmore /var/log/apt/history.log.1.gz
------> /var/log/apt/history.log.1.gz <------

Start-Date: 2013-04-01  10:19:22
Commandline: aptdaemon role='role-commit-packages' sender=':1.73'
Upgrade: bind9-host:amd64 (9.8.1.dfsg.P1-4ubuntu0.5, 9.8.1.dfsg.P1-4ubuntu0.6), 
dnsutils:amd64 (9.8.1.dfsg.P1-4ubuntu0.5, 9.8.1.dfsg.P1-4ubuntu0.6), libdns81:am
d64 (9.8.1.dfsg.P1-4ubuntu0.5, 9.8.1.dfsg.P1-4ubuntu0.6), libisccc80:amd64 (9.8.
1.dfsg.P1-4ubuntu0.5, 9.8.1.dfsg.P1-4ubuntu0.6), liblwres80:amd64 (9.8.1.dfsg.P1
-4ubuntu0.5, 9.8.1.dfsg.P1-4ubuntu0.6), libbind9-80:amd64 (9.8.1.dfsg.P1-4ubuntu
0.5, 9.8.1.dfsg.P1-4ubuntu0.6), libisccfg82:amd64 (9.8.1.dfsg.P1-4ubuntu0.5, 9.8
.1.dfsg.P1-4ubuntu0.6), geoclue-ubuntu-geoip:amd64 (0.0.2-0ubuntu6, 0.0.2-0ubunt
u6.3), libisc83:amd64 (9.8.1.dfsg.P1-4ubuntu0.5, 9.8.1.dfsg.P1-4ubuntu0.6)
End-Date: 2013-04-01  10:19:44

Start-Date: 2013-04-02  08:21:59
Commandline: aptdaemon role='role-commit-packages' sender=':1.71'
Upgrade: libopenjpeg2:amd64 (1.3+dfsg-4, 1.3+dfsg-4+squeeze1build0.12.04.1)
End-Date: 2013-04-02  08:22:10

Start-Date: 2013-04-03  09:36:53
Commandline: aptdaemon role='role-commit-packages' sender=':1.76'
Upgrade: poppler-utils:amd64 (0.18.4-1ubuntu3, 0.18.4-1ubuntu3.1), libxslt1.1:am
d64 (1.1.26-8ubuntu1.2, 1.1.26-8ubuntu1.3), libxslt1.1:i386 (1.1.26-8ubuntu1.2, 
1.1.26-8ubuntu1.3), libpoppler-glib8:amd64 (0.18.4-1ubuntu3, 0.18.4-1ubuntu3.1),
 libpoppler19:amd64 (0.18.4-1ubuntu3, 0.18.4-1ubuntu3.1)
End-Date: 2013-04-03  09:37:13

Start-Date: 2013-04-06  09:58:33
Commandline: aptdaemon role='role-commit-packages' sender=':1.75'
Upgrade: libswscale2:amd64 (0.8.5-0ubuntu0.12.04.1, 0.8.6-0ubuntu0.12.04.1), lib
avutil-extra-51:amd64 (0.8.5ubuntu0.12.04.1, 0.8.6ubuntu0.12.04.1), firefox-glob
almenu:amd64 (19.0.2+build1-0ubuntu0.12.04.1, 20.0+build1-0ubuntu0.12.04.3), lib
avdevice53:amd64 (0.8.5-0ubuntu0.12.04.1, 0.8.6-0ubuntu0.12.04.1), firefox:amd64
 (19.0.2+build1-0ubuntu0.12.04.1, 20.0+build1-0ubuntu0.12.04.3), libpostproc52:a
md64 (0.8.5-0ubuntu0.12.04.1, 0.8.6-0ubuntu0.12.04.1), firefox-locale-en:amd64 (
19.0.2+build1-0ubuntu0.12.04.1, 20.0+build1-0ubuntu0.12.04.3), libavformat53:amd
64 (0.8.5-0ubuntu0.12.04.1, 0.8.6-0ubuntu0.12.04.1), firefox-gnome-support:amd64
 (19.0.2+build1-0ubuntu0.12.04.1, 20.0+build1-0ubuntu0.12.04.3), libavcodec-extr
a-53:amd64 (0.8.5ubuntu0.12.04.1, 0.8.6ubuntu0.12.04.1)
End-Date: 2013-04-06  09:59:01

Start-Date: 2013-04-09  10:52:37
Commandline: aptdaemon role='role-commit-packages' sender=':1.79'
Install: linux-headers-3.2.0-40:amd64 (3.2.0-40.64), linux-image-3.2.0-40-generi
c:amd64 (3.2.0-40.64), linux-headers-3.2.0-40-generic:amd64 (3.2.0-40.64)
Upgrade: thunderbird-locale-en-gb:amd64 (17.0.4+build1-0ubuntu0.12.04.1, 17.0.5+
build1-0ubuntu0.12.04.1), thunderbird-locale-en-us:amd64 (17.0.4+build1-0ubuntu0
.12.04.1, 17.0.5+build1-0ubuntu0.12.04.1), thunderbird:amd64 (17.0.4+build1-0ubu
ntu0.12.04.1, 17.0.5+build1-0ubuntu0.12.04.1), linux-generic:amd64 (3.2.0.39.47,
 3.2.0.40.48), linux-headers-generic:amd64 (3.2.0.39.47, 3.2.0.40.48), linux-ima
ge-generic:amd64 (3.2.0.39.47, 3.2.0.40.48), thunderbird-globalmenu:amd64 (17.0.
4+build1-0ubuntu0.12.04.1, 17.0.5+build1-0ubuntu0.12.04.1), thunderbird-gnome-su
pport:amd64 (17.0.4+build1-0ubuntu0.12.04.1, 17.0.5+build1-0ubuntu0.12.04.1), li
nux-libc-dev:amd64 (3.2.0-39.62, 3.2.0-40.64), thunderbird-locale-en:amd64 (17.0
.4+build1-0ubuntu0.12.04.1, 17.0.5+build1-0ubuntu0.12.04.1)
End-Date: 2013-04-09  10:54:12

Start-Date: 2013-04-10  13:28:39
Commandline: aptdaemon role='role-commit-packages' sender=':1.84'
Upgrade: nautilus:amd64 (3.4.2-0ubuntu7, 3.4.2-0ubuntu8), network-manager-gnome:
amd64 (0.9.4.1-0ubuntu2.1, 0.9.4.1-0ubuntu2.2), libnm-gtk0:amd64 (0.9.4.1-0ubunt
u2.1, 0.9.4.1-0ubuntu2.2), libdee-1.0-4:amd64 (1.0.10-0ubuntu1, 1.0.10-0ubuntu1.
1), libjack-jackd2-0:amd64 (1.9.8~dfsg.1-1ubuntu1, 1.9.8~dfsg.1-1ubuntu2), libja
ck-jackd2-0:i386 (1.9.8~dfsg.1-1ubuntu1, 1.9.8~dfsg.1-1ubuntu2), bash:amd64 (4.2
-2ubuntu2, 4.2-2ubuntu2.1), gir1.2-gkbd-3.0:amd64 (3.4.0.2-1, 3.4.0.2-1ubuntu0.1
), simple-scan:amd64 (3.4.1-0ubuntu1.1, 3.4.3-0ubuntu1), libnm-gtk-common:amd64 
(0.9.4.1-0ubuntu2.1, 0.9.4.1-0ubuntu2.2), google-chrome-stable:amd64 (26.0.1410.
43-r189671, 26.0.1410.63-r192696), libgnomekbd7:amd64 (3.4.0.2-1, 3.4.0.2-1ubunt
u0.1), flashplugin-installer:amd64 (11.2.202.275ubuntu0.12.04.1, 11.2.202.280ubu
ntu0.12.04.1), nautilus-data:amd64 (3.4.2-0ubuntu7, 3.4.2-0ubuntu8), gir1.2-dee-
1.0:amd64 (1.0.10-0ubuntu1, 1.0.10-0ubuntu1.1), libnautilus-extension1a:amd64 (3
.4.2-0ubuntu7, 3.4.2-0ubuntu8), libgnomekbd-common:amd64 (3.4.0.2-1, 3.4.0.2-1ub
untu0.1)
End-Date: 2013-04-10  13:30:34

Start-Date: 2013-04-17  04:45:36
Commandline: aptdaemon role='role-commit-packages' sender=':1.73'
Upgrade: libsmbclient:amd64 (3.6.3-2ubuntu2.4, 3.6.3-2ubuntu2.5), libpam-winbind
:amd64 (3.6.3-2ubuntu2.4, 3.6.3-2ubuntu2.5), smbclient:amd64 (3.6.3-2ubuntu2.4, 
3.6.3-2ubuntu2.5), libwbclient0:amd64 (3.6.3-2ubuntu2.4, 3.6.3-2ubuntu2.5), samb
a-common:amd64 (3.6.3-2ubuntu2.4, 3.6.3-2ubuntu2.5), libcurl3:amd64 (7.22.0-3ubu
ntu4, 7.22.0-3ubuntu4.1), libcurl3:i386 (7.22.0-3ubuntu4, 7.22.0-3ubuntu4.1), li
bcurl3-nss:amd64 (7.22.0-3ubuntu4, 7.22.0-3ubuntu4.1), libcurl3-gnutls:amd64 (7.
22.0-3ubuntu4, 7.22.0-3ubuntu4.1), samba-common-bin:amd64 (3.6.3-2ubuntu2.4, 3.6
.3-2ubuntu2.5), winbind:amd64 (3.6.3-2ubuntu2.4, 3.6.3-2ubuntu2.5)
End-Date: 2013-04-17  04:46:12

Start-Date: 2013-04-18  05:17:38
Commandline: aptdaemon role='role-commit-packages' sender=':1.122'
Upgrade: libsmbclient:amd64 (3.6.3-2ubuntu2.5, 3.6.3-2ubuntu2.6), libpam-winbind
:amd64 (3.6.3-2ubuntu2.5, 3.6.3-2ubuntu2.6), smbclient:amd64 (3.6.3-2ubuntu2.5, 
3.6.3-2ubuntu2.6), libdrm-radeon1:amd64 (2.4.39-0ubuntu0.1, 2.4.39-0ubuntu0.2), 
libdrm-radeon1:i386 (2.4.39-0ubuntu0.1, 2.4.39-0ubuntu0.2), xserver-xorg-core:am
d64 (1.11.4-0ubuntu10.12, 1.11.4-0ubuntu10.13), xserver-common:amd64 (1.11.4-0ub
untu10.12, 1.11.4-0ubuntu10.13), libwbclient0:amd64 (3.6.3-2ubuntu2.5, 3.6.3-2ub
untu2.6), deja-dup:amd64 (22.0-0ubuntu3, 22.0-0ubuntu4), samba-common:amd64 (3.6
.3-2ubuntu2.5, 3.6.3-2ubuntu2.6), libdrm2:amd64 (2.4.39-0ubuntu0.1, 2.4.39-0ubun
tu0.2), libdrm2:i386 (2.4.39-0ubuntu0.1, 2.4.39-0ubuntu0.2), libdrm-nouveau1a:am
d64 (2.4.39-0ubuntu0.1, 2.4.39-0ubuntu0.2), libdrm-nouveau1a:i386 (2.4.39-0ubunt
u0.1, 2.4.39-0ubuntu0.2), libdrm-intel1:amd64 (2.4.39-0ubuntu0.1, 2.4.39-0ubuntu
0.2), libdrm-intel1:i386 (2.4.39-0ubuntu0.1, 2.4.39-0ubuntu0.2), samba-common-bi
n:amd64 (3.6.3-2ubuntu2.5, 3.6.3-2ubuntu2.6), winbind:amd64 (3.6.3-2ubuntu2.5, 3
.6.3-2ubuntu2.6)
End-Date: 2013-04-18  05:18:51

Start-Date: 2013-04-19  10:17:22
Commandline: aptdaemon role='role-commit-packages' sender=':1.78'
Upgrade: dnsmasq-base:amd64 (2.59-4, 2.59-4ubuntu0.1), language-selector-gnome:a
md64 (0.79.2, 0.79.3), icedtea-netx:amd64 (1.2-2ubuntu1.3, 1.2.3-0ubuntu0.12.04.
1), language-selector-common:amd64 (0.79.2, 0.79.3), apport:amd64 (2.0.1-0ubuntu
17.1, 2.0.1-0ubuntu17.2), icedtea-netx-common:amd64 (1.2-2ubuntu1.3, 1.2.3-0ubun
tu0.12.04.1), icedtea-6-plugin:amd64 (1.2-2ubuntu1.3, 1.2.3-0ubuntu0.12.04.1), o
penssh-client:amd64 (5.9p1-5ubuntu1, 5.9p1-5ubuntu1.1), python-problem-report:am
d64 (2.0.1-0ubuntu17.1, 2.0.1-0ubuntu17.2), icedtea-plugin:amd64 (1.2-2ubuntu1.3
, 1.2.3-0ubuntu0.12.04.1), python-apport:amd64 (2.0.1-0ubuntu17.1, 2.0.1-0ubuntu
17.2), ssh-askpass-gnome:amd64 (5.9p1-5ubuntu1, 5.9p1-5ubuntu1.1), apport-gtk:am
d64 (2.0.1-0ubuntu17.1, 2.0.1-0ubuntu17.2), icedtea6-plugin:amd64 (6b21.2-2ubunt
u1.3, 6b21.2.3-0ubuntu0.12.04.1)
End-Date: 2013-04-19  10:18:09

Start-Date: 2013-04-25  19:34:47
Commandline: aptdaemon role='role-commit-packages' sender=':1.78'
Upgrade: libc-bin:amd64 (2.15-0ubuntu10.3, 2.15-0ubuntu10.4), python-aptdaemon.p
kcompat:amd64 (0.43+bzr805-0ubuntu8, 0.43+bzr805-0ubuntu9), icedtea-netx:amd64 (
1.2.3-0ubuntu0.12.04.1, 1.2.3-0ubuntu0.12.04.2), openjdk-7-jre:amd64 (7u15-2.3.7
-0ubuntu1~12.04.1, 7u21-2.3.9-0ubuntu0.12.04.1), accountsservice:amd64 (0.6.15-2
ubuntu9.5, 0.6.15-2ubuntu9.6), libmysqlclient18:amd64 (5.5.29-0ubuntu0.12.04.2, 
5.5.31-0ubuntu0.12.04.1), libaccountsservice0:amd64 (0.6.15-2ubuntu9.5, 0.6.15-2
ubuntu9.6), libc6-i386:amd64 (2.15-0ubuntu10.3, 2.15-0ubuntu10.4), python-aptdae
mon.gtkwidgets:amd64 (0.43+bzr805-0ubuntu8, 0.43+bzr805-0ubuntu9), xserver-xorg-
video-intel:amd64 (2.17.0-1ubuntu4.3, 2.17.0-1ubuntu4.4), python-aptdaemon:amd64
 (0.43+bzr805-0ubuntu8, 0.43+bzr805-0ubuntu9), icedtea-netx-common:amd64 (1.2.3-
0ubuntu0.12.04.1, 1.2.3-0ubuntu0.12.04.2), icedtea-6-plugin:amd64 (1.2.3-0ubuntu
0.12.04.1, 1.2.3-0ubuntu0.12.04.2), multiarch-support:amd64 (2.15-0ubuntu10.3, 2
.15-0ubuntu10.4), icedtea-plugin:amd64 (1.2.3-0ubuntu0.12.04.1, 1.2.3-0ubuntu0.1
2.04.2), gir1.2-accountsservice-1.0:amd64 (0.6.15-2ubuntu9.5, 0.6.15-2ubuntu9.6)
, aptdaemon:amd64 (0.43+bzr805-0ubuntu8, 0.43+bzr805-0ubuntu9), python-aptdaemon
-gtk:amd64 (0.43+bzr805-0ubuntu8, 0.43+bzr805-0ubuntu9), icedtea-7-jre-jamvm:amd
64 (7u15-2.3.7-0ubuntu1~12.04.1, 7u21-2.3.9-0ubuntu0.12.04.1), openjdk-7-jre-lib
:amd64 (7u15-2.3.7-0ubuntu1~12.04.1, 7u21-2.3.9-0ubuntu0.12.04.1), libc6-dev:amd
64 (2.15-0ubuntu10.3, 2.15-0ubuntu10.4), aptdaemon-data:amd64 (0.43+bzr805-0ubun
tu8, 0.43+bzr805-0ubuntu9), python-aptdaemon.gtk3widgets:amd64 (0.43+bzr805-0ubu
ntu8, 0.43+bzr805-0ubuntu9), libc-dev-bin:amd64 (2.15-0ubuntu10.3, 2.15-0ubuntu1
0.4), libc6:amd64 (2.15-0ubuntu10.3, 2.15-0ubuntu10.4), libc6:i386 (2.15-0ubuntu
10.3, 2.15-0ubuntu10.4), mysql-common:amd64 (5.5.29-0ubuntu0.12.04.2, 5.5.31-0ub
untu0.12.04.1), icedtea6-plugin:amd64 (6b21.2.3-0ubuntu0.12.04.1, 6b21.2.3-0ubun
tu0.12.04.2), openjdk-7-jre-headless:amd64 (7u15-2.3.7-0ubuntu1~12.04.1, 7u21-2.
3.9-0ubuntu0.12.04.1)
End-Date: 2013-04-25  19:36:15

Start-Date: 2013-04-29  07:56:37
Commandline: aptdaemon role='role-commit-packages' sender=':1.71'
Upgrade: unity-scope-video-remote:amd64 (0.3.5-0ubuntu2.1, 0.3.5-0ubuntu2.2), li
nux-firmware:amd64 (1.79.1, 1.79.4)
End-Date: 2013-04-29  07:56:49


> pam@Dark-Star:~$ zmore /var/log/apt/history.log.2.gz
------> /var/log/apt/history.log.2.gz <------

Start-Date: 2013-03-23  04:09:11
Commandline: aptdaemon role='role-commit-packages' sender=':1.70'
Upgrade: libgudev-1.0-0:amd64 (175-0ubuntu9.2, 175-0ubuntu9.3), libgudev-1.0-0:i
386 (175-0ubuntu9.2, 175-0ubuntu9.3), clamav:amd64 (0.97.6+dfsg-1ubuntu0.12.04.1
, 0.97.7+dfsg-1ubuntu0.12.04.1), clamav-base:amd64 (0.97.6+dfsg-1ubuntu0.12.04.1
, 0.97.7+dfsg-1ubuntu0.12.04.1), libclamav6:amd64 (0.97.6+dfsg-1ubuntu0.12.04.1,
 0.97.7+dfsg-1ubuntu0.12.04.1), udev:amd64 (175-0ubuntu9.2, 175-0ubuntu9.3), gir
1.2-gudev-1.0:amd64 (175-0ubuntu9.2, 175-0ubuntu9.3), libudev0:amd64 (175-0ubunt
u9.2, 175-0ubuntu9.3), libudev0:i386 (175-0ubuntu9.2, 175-0ubuntu9.3), clamav-fr
eshclam:amd64 (0.97.6+dfsg-1ubuntu0.12.04.1, 0.97.7+dfsg-1ubuntu0.12.04.1), ipta
bles:amd64 (1.4.12-1ubuntu4, 1.4.12-1ubuntu5)
End-Date: 2013-03-23  04:10:10

Start-Date: 2013-03-26  09:11:33
Commandline: aptdaemon role='role-commit-packages' sender=':1.80'
Upgrade: gwibber-service-identica:amd64 (3.4.2-0ubuntu2.1, 3.4.2-0ubuntu2.2), la
nguage-selector-gnome:amd64 (0.79.1, 0.79.2), accountsservice:amd64 (0.6.15-2ubu
ntu9.4, 0.6.15-2ubuntu9.5), libgoa-1.0-0:amd64 (3.4.0-0ubuntu1, 3.4.0-0ubuntu1.1
), gwibber-service-twitter:amd64 (3.4.2-0ubuntu2.1, 3.4.2-0ubuntu2.2), gwibber-s
ervice-facebook:amd64 (3.4.2-0ubuntu2.1, 3.4.2-0ubuntu2.2), language-selector-co
mmon:amd64 (0.79.1, 0.79.2), libaccountsservice0:amd64 (0.6.15-2ubuntu9.4, 0.6.1
5-2ubuntu9.5), libgwibber2:amd64 (3.4.2-0ubuntu2.1, 3.4.2-0ubuntu2.2), gir1.2-ac
countsservice-1.0:amd64 (0.6.15-2ubuntu9.4, 0.6.15-2ubuntu9.5), libneon27-gnutls
:amd64 (0.29.6-1, 0.29.6-1ubuntu1), gwibber-service:amd64 (3.4.2-0ubuntu2.1, 3.4
.2-0ubuntu2.2), openssl:amd64 (1.0.1-4ubuntu5.7, 1.0.1-4ubuntu5.8), rsyslog:amd6
4 (5.8.6-1ubuntu8, 5.8.6-1ubuntu8.1), gnome-online-accounts:amd64 (3.4.0-0ubuntu
1, 3.4.0-0ubuntu1.1), gwibber:amd64 (3.4.2-0ubuntu2.1, 3.4.2-0ubuntu2.2), libgwi
bber-gtk2:amd64 (3.4.2-0ubuntu2.1, 3.4.2-0ubuntu2.2), libgoa-1.0-common:amd64 (3
.4.0-0ubuntu1, 3.4.0-0ubuntu1.1), libssl1.0.0:amd64 (1.0.1-4ubuntu5.7, 1.0.1-4ub
untu5.8), libssl1.0.0:i386 (1.0.1-4ubuntu5.7, 1.0.1-4ubuntu5.8)
End-Date: 2013-03-26  09:12:34

Start-Date: 2013-03-29  04:01:10
Commandline: aptdaemon role='role-commit-packages' sender=':1.74'
Upgrade: dmsetup:amd64 (1.02.48-4ubuntu7.2, 1.02.48-4ubuntu7.3), libgnome-contro
l-center1:amd64 (3.4.2-0ubuntu0.9, 3.4.2-0ubuntu0.11), lightdm:amd64 (1.2.3-0ubu
ntu1, 1.2.3-0ubuntu2), libdevmapper1.02.1:amd64 (1.02.48-4ubuntu7.2, 1.02.48-4ub
untu7.3), gnome-control-center-data:amd64 (3.4.2-0ubuntu0.9, 3.4.2-0ubuntu0.11),
 gnome-screenshot:amd64 (3.4.1-0ubuntu1, 3.4.1-0ubuntu1.1), libxml2:amd64 (2.7.8
.dfsg-5.1ubuntu4.3, 2.7.8.dfsg-5.1ubuntu4.4), libxml2:i386 (2.7.8.dfsg-5.1ubuntu
4.3, 2.7.8.dfsg-5.1ubuntu4.4), google-chrome-stable:amd64 (25.0.1364.172-r187217
, 26.0.1410.43-r189671), libdevmapper-event1.02.1:amd64 (1.02.48-4ubuntu7.2, 1.0
2.48-4ubuntu7.3), liblvm2app2.2:amd64 (2.02.66-4ubuntu7.2, 2.02.66-4ubuntu7.3), 
gnome-control-center:amd64 (3.4.2-0ubuntu0.9, 3.4.2-0ubuntu0.11), liblightdm-gob
ject-1-0:amd64 (1.2.3-0ubuntu1, 1.2.3-0ubuntu2), libxrandr2:amd64 (1.3.2-2, 1.3.
2-2ubuntu0.1), libxrandr2:i386 (1.3.2-2, 1.3.2-2ubuntu0.1), python-libxml2:amd64
 (2.7.8.dfsg-5.1ubuntu4.3, 2.7.8.dfsg-5.1ubuntu4.4)
End-Date: 2013-03-29  04:02:31


Again, I can't thank you enough for all the help.  At some point, I think I may simply backup the computer and do a fresh install of a newer version of ubuntu.  But I do want to exhaust all options before that.  I guess I'll try purging compiz now.

---

### Post by onipar on 2013-05-05
I also tried the compiz thing, and here is the complete log of that.  Somthing went wrong I think...

> pam@Dark-Star:~$ sudo apt-get remove compizconfig-settings-manager
[sudo] password for pam: 
Sorry, try again.
[sudo] password for pam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compizconfig-settings-manager is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
pam@Dark-Star:~$ sudo apt-get install unity-2d
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unity-2d is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
pam@Dark-Star:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
pam@Dark-Star:~$ sudo apt-get install ubuntu-desktop-2d
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ubuntu-desktop-2d
pam@Dark-Star:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  compiz-plugins compiz-plugins-main
The following NEW packages will be installed:
  compiz-plugins compiz-plugins-main compizconfig-settings-manager
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,894 kB of archives.
After this operation, 11.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
pam@Dark-Star:~$ sudo apt-get install unity-2d
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unity-2d is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
pam@Dark-Star:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
pam@Dark-Star:~$ sudo apt-get install ubuntu-desktop-2d
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ubuntu-desktop-2d
pam@Dark-Star:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  compiz-plugins compiz-plugins-main
The following NEW packages will be installed:
  compiz-plugins compiz-plugins-main compizconfig-settings-manager
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,894 kB of archives.
After this operation, 11.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.
pam@Dark-Star:~$ 


---

### Post by zero2xiii on 2013-05-05
Hay,

No problem on helping you :D. I do love a challenge such as this.

Nothing really "went wrong" with the install. Only the compiz-settings manager failed it seemed (this is not a crucial part anyway, its simply a GUI settings editor for the config files).

However from the output you posted you only tried to remove one component. There are 4 removals you need to do, but you can skip and just try this one:
```
sudo apt-get purge compiz*
```
And then follow the install steps again as you did, where it said each time the package is already the newest version.

BUT before you do that, let us destroy and rebuild the settings locally first before you purge a possibly working install. The output you got when you did the mkdir command simply means basically that folder does not exist to be moved, so you should be safe to run the second command.

Just to be sure, run a recursive ls to be sure the settings did copy (this is the settings of the current gnome setup esentially):
```
ls -Rah ./.old-gnome-config/
```

This should produce an output SIMILAR to this (not EXACTLY):
```

**SNIP**
./.old-gnome-config/.gconf/apps/procman/openfilestree:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/procman/proctree:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox:
.  ..  audioscrobbler  player  plugins  state  ui  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/audioscrobbler:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/player:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins:
.               cd-recorder     jamendo    power-manager  visualizer
..              context         lyrics     pythonconsole  %gconf.xml
artdisplay      daap            magnatune  rblirc
audiocd         generic-player  mmkeys     replaygain
audioscrobbler  ipod            mpris      status-icon
ayatana         iradio          mtpdevice  umusicstore

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/artdisplay:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/audiocd:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/audioscrobbler:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/ayatana:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/cd-recorder:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/context:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/daap:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/generic-player:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/ipod:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/iradio:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/jamendo:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/lyrics:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/magnatune:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/mmkeys:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/mpris:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/mtpdevice:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/power-manager:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/pythonconsole:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/rblirc:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/replaygain:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/status-icon:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/umusicstore:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/plugins/visualizer:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/state:
.  ..  iradio  library  podcast  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/state/iradio:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/state/library:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/state/podcast:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/ui:
.  ..  library  %gconf.xml

./.old-gnome-config/.gconf/apps/rhythmbox/ui/library:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/same-gnome:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/screenruler:
.  ..  %gconf.xml

./.old-gnome-config/.gconf/apps/seahorse:
.  ..  agent  listing  windows  %gconf.xml

**SNIP**
```

This is just to make sure all your config files ARE backed up. Then run the rm (remove) command:
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity .cache .dbus .dmrc .mission-control .thumbnails ~/.config/dconf/user ~.compiz*
```

Now log out and back in and see if everything is reset. (The log in will take a while longer than normal).

I think that is that for the moment. Hope I said everything. Lolz.

Cheers

EDIT:
Oh yes btw. I do not see anything in the apt-get logs that might contribute to the issue so we can safely assume it is either a configuration error or a faulty install (or corrupted install)

---

### Post by onipar on 2013-05-05
Well, I *think* I applied all the codes in the correct order, but the unity bar remains absent from ubuntu!  :-(  

I'm fairly certain there are missing components or invalid installs for both compiz and unity, because I did recieve some errors and warnings that certain directories did not exist along the way.
Not sure if it's time to give up or not, but dang, this seems like it should be a simple fix!  ;-P

Oh, a couple things from the apt-get install list didn't work.  When I did the following, I got a message back saying those "could not be found."
ubuntu-desktop-2d
xserver-xgl
emerald

Also, here are the outputs when I run unity --restart and unity --replace from the terminal:

> pam@Dark-Star:~$ unity --restart
Usage: unity [options]

unity: error: no such option: --restart
pam@Dark-Star:~$ unity --replace
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing composite options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libopengl.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'opengl'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libcompiztoolbox.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'compiztoolbox'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libdecor.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'decor'
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libresize.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'resize'
Initializing place options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libmove.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'move'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libwall.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'wall'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libgrid.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'grid'
Initializing session options...done
Initializing gnomecompat options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libanimation.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'animation'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libfade.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'fade'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunitymtgrabhandles.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unitymtgrabhandles'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libworkarounds.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'workarounds'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libscale.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'scale'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libexpo.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'expo'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libezoom.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'ezoom'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunityshell.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unityshell'
Setting Update "main_menu_key"
Setting Update "run_key"



Though unity --restart does work when I go into cntrl alt f1 to do it.  Still, no dice though.

Oh crap...just noticed something.  After I posted that outpuit above, I tried closing the terminal, but it said "process still running" or something like that.  Everytime I run a unity --restart or --replace, I usually close out once it gets to that last bit that says "Setting Update "run_key"" because nothing seems to happen after that.  Have I been closing the process too soon, and that's why the unity --restart isn't working?  :-/

And sorry, one last question.  When I go to the software manager, I noticed there are options for "unity" and "compiz" to be removed/installed from the software manager.  Are there any particular packages I should try "removing" and then "reinstalling" from there?

---

### Post by zero2xiii on 2013-05-05
Hay,

Well clearly this is no "easy fix" unfortunately.

Something is definitely screwy with compiz. 

Let us try one last compiz reinstall:

first of update the at-get source list:
```
sudo apt-get update
```

Then:

```
sudo apt-get remove compiz*
audo apt-get purge compiz*
```

if that did not work do:
```
sudo apt-get purge compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default compiz-plugins-main compiz-plugins-main-default
```

then install it back:
```
sudo apt-get install compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default compiz-plugins-main compiz-plugins-main-default
```

DO NOT use "apt-get reinstall" for the above as this does not remove all the configuration.

If there are any erros please post the output again.

Sigh if the above also completely fails. A clean re-install might be the best bet. Unless you wish to start and re-examen the problem from scratch :/

Good luck.

---

### Post by onipar on 2013-05-05
Hey, okay.  So I applied all of the changes, and everything seemed to work okay, but when I restarted the computer, "Ubuntu" wasn't even an option under the desktop choices screen.  Then I tried the unity --restart again, and it said unity wasn't uinstalled, so I installed unity.  Then when I tried the unity --restart, and --replace, I got the same errors and problems as last time.  And of course, still no unity bar in ubuntu (which did reappear as a desktop choice after I installed unity).  Here are the errors:

> pam@Dark-Star:~$ unity --restart
Usage: unity [options]

unity: error: no such option: --restart
pam@Dark-Star:~$ unity --replace
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing composite options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libopengl.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'opengl'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libcompiztoolbox.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'compiztoolbox'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libdecor.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'decor'
Initializing vpswitch options...done
Initializing snap options...done
Initializing mousepoll options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libresize.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'resize'
Initializing place options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libmove.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'move'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libwall.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'wall'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libgrid.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'grid'
Initializing session options...done
Initializing gnomecompat options...done
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libanimation.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'animation'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libfade.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'fade'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunitymtgrabhandles.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unitymtgrabhandles'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libworkarounds.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'workarounds'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libscale.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'scale'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libexpo.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'expo'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libezoom.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'ezoom'
compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunityshell.so' : libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Error: Couldn't load plugin 'unityshell'
Setting Update "main_menu_key"
Setting Update "run_key"



So yeah.  If you think it's time to just do a fresh install, let me know.  You've gone above and beyond, thank you!

---

### Post by zero2xiii on 2013-05-06
Hay,

Wow those commands weren't suppose to touch unity, only compiz. It seems something is deffinitly not right there. But I can't even guestimate what it might be anymore at this point... So yea I think a fresh install should be the best option. I recommend a LTS, 12.04. Leave 12.10 and 13.04 until you know you have a working system. (install it side by side with 12.04 and when you are happy just port over your /home partition). On that note, use the manual partitioning and create a separate partition for /home. You only really need a 4GB root mount but I always give my installs a 10-15GB partition for root, /.


So I recommend this structure:

/ = 10-15GB
/boot = 250+MB (no more than 500 really)
/home = all the rest (unless you plan a side by side install, but the partition can always be resized)

All partitioned are ext4 formatted.

One very last ditch effort before your format, have you tried "unity --reset"?

Sorry I can not help you more, but I think we exhausted every possibility. Honestly.

Well cheers and good luck, feel free to open up another thread if the install process is daunting for you :)

---

### Post by onipar on 2013-05-06
Well, thanks for all the help.  I tried the unity --reset one last time, but still no luck.  Looks like it'll be a fresh install.  Thanks again!

---

### Post by zero2xiii on 2013-05-06
My pleasure, sorry we could not fix this one. Would be awesome to know what the cause of this was. Lol.

Have a happy fresh install:guitar:

---

### Post by onipar on 2013-05-09
SOOOOOOOO weird!  

I have an update.

Okay, so after we decided there was nothing to be done, I started backing up data from the computer, and a few days went by.  I didn't have time to do the update.  Today, my dad was on the computer and I saw a Unity bar in GNOME Classic.  So I logged out and logged back into Ubuntu, and the unity bar was back!!!

My dad said he applied an update that had popped up (And yes, I did do all updates that were available when I was trying to fix it).  

I have no idea if that's what fixed it, or WHY the unity bar suddenly reappeared, but it's back!  :-)  

Strangest.  Computer Problem.  Ever.

---

