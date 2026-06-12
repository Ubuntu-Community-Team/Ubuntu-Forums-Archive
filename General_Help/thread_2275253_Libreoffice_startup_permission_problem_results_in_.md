---
title: "Libreoffice startup permission problem results in fatal error"
date: 2015-04-25
forum: General Help
---

### Post by Ralph L on 2015-04-25
I installed libreoffice4.4 in xubuntu.  It seemed to work.  I did some changing of permissions (I thought only in my Shared_Data partition, but maybe I made an error).  Now when I try to start libreoffice4.4 I get ```
Libreoffice 4.4 - Fatal Error The application cannot be started.  User installation could not be competed.
```  If I bring up terminal and enter ```
sudo libreoffice4.4
``` it starts up with no problem--leading me to think I have a permission problem.  Anybody have any thoughts as to whether this is a permission problem or something else???
I tried uninstalling and re-installing libreoffice, but it did not help.  Probably I didn't get everything removed.  Would someone tell me how to uninstall libreoffice, including every libreoffice file, so I can do a really clean install???

Thank you in advance.

---

### Post by ajgreeny on 2015-04-25
Before you start removing anything tell us exactly what you did when you "did some changing of permissions" of things in your shared data partition.

If you used the terminal to change permissions all the commands used will be logged in the** .bash_history** file in your home (it's hidden normally so you will need to use **Ctrl+H** to show hidden files).  Show us those commands and it might throw some light on what is going on here, which I agree with you does sound like a permissions problem.

---

### Post by Ralph L on 2015-04-25
Thank you very much for your response.  Here is .bash_history:```
cd Downloads
ls
cd ~/Downloads/LibreOffice_4.4.0.x_Linux_x86_deb/DEBS
cd LibreOffice_4.4.2.2_Linux_x86_deb
sudo dpkg -i *.deb
ls
cd DEBS
sudo dpkg -i *.deb
cd desktop-integration
cd ~
cd desktop-integration
ln -s test
ln -s test test.link
pkexec thunar
sudo thunar
ls -la | grep root
sudo chown -R john:john .config

sudo chown -R ralph:ralph .config
sudo chown -R ralph:ralph /home/john
sudo chown -R ralph:ralph /home/ralph
sudo apt-get remove --purge libreoffice*
sudo apt-get purge libreoffice?
cd Download
cd Downloads
LibreOffice_4.4.2.2_Linux_x86_deb
cd LibreOffice_4.4.2.2_Linux_x86_deb
sudo dpkg -i *.deb
cd DEBS
sudo dpkg -i *.deb
libreof
cd ~
soffice
libreoffice
cd Downloads
cd LibreOffice_4.4.2.2_Linux_x86_deb
cd DEBS
cd desktop-integration
env
set
env
XDG_DATA_DIRS=/usr/share/xubuntu:/usr/share/xfce4:/usr/local/share/:/usr/share/:/usr/share
export $XDG_DATA_DIRS=/usr/share/xubuntu:/usr/share/xfce4:/usr/local/share/:/usr/share/:/usr/share:/home/ralph/.local/share/Thunar/sendto/
eng

export $XDG_DATA_DIRS=/usr/share/xubuntu:/usr/share/xfce4:/usr/local/share/:/usr/share/:/usr/share:/home/ralph/
export $XDG_DATA_DIRS=/usr/share/xubuntu:/usr/share/xfce4:/usr/local/share/:/usr/share/:/usr/share:/home/
export $XDG_DATA_DIRS=/usr/share/xubuntu:/usr/share/xfce4:/usr/local/share/:/usr/share/:/usr/share:/home
export $XDG_DATA_DIRS=/usr/share/xubuntu:/usr/share/xfce4:/usr/local/share/:/usr/share/:/usr/share
env
export $XDG_DATA_DIRS=/usr/share/xubuntu:/usr/share/xfce4:/usr/local/share/:/usr/share/
export $XDG_DATA_DIRS="/usr/share/xubuntu:/usr/share/xfce4:/usr/local/share/:/usr/share/"
export test="25"
env
sudo thunar
env
sudo thunar
env
sudo thunar
env
XDG_DATA_DIRS=/usr/share/xubuntu:/usr/share/xfce4:/usr/share/xubuntu:/usr/share/xfce4:/usr/local/share/:/usr/share/:/home/ralph/.local/share/Thunar/sendto/:/usr/share
XDG_DATA_DIRS=/usr/share/xubuntu:/usr/share/xfce4:/usr/share/xubuntu:/usr/share/xfce4:/usr/local/share/:/usr/share/:/home/ralph/.local/share/Thunar/sendto:/usr/share
env
sudo thunar
env
sudo thunar
env
sudo thunar
ls -la | grep root
cd .config
cd libreoffice
cd 4
ls -l
cd ..
ls -l
ls -al
cd ..
ls -al
cd libreoffice
cd 4
cd user
ls -al
cd config
ls -al
cd ~
cd .config
ls -al
cd libreoffice
ls -al
cd~
cd ~
ls -al /etc/{gshadow,shadow,group,passwd}*
cd /
ls -al
cd /home
ls -al
cd ralph
ls -al
libreoffice
libreoffice4.4 --writer %U
sudo libreoffice4.4 --writer %U
sudo libreoffice4.4 --writer
sudo thunar
libreoffice4.4
sudo libreoffice4.4
libreoffice4.4
sudo libreoffice4.4
sudo find name libroffice4.4
sudo find -name libreoffice4.4
sudo find -name "libreoffice4.4"
cd /
sudo find -name "libreoffice4.4"
cd ~
/usr/local/bin/libreoffice4.4
cd /usr/local/bin/libreoffice4.4
cd /usr/local/bin/
sudo libreoffice4.4
libreoffice4.4

```

---

### Post by steeldriver on 2015-04-25
The first time you ran the application with sudo, it probably caused its config files to get owned by root - and now it can't write them when run *without* sudo

Look at the ownership of LibreOffice's config - I think that's at ~/.config/libreoffice, either check them manually or do something like this with 'find'

```

find ~/.config ! -user "$USER" -ls

```

---

### Post by ajgreeny on 2015-04-25
I also query why you messed about installing LO that way when you could much more easily have used the libreoffice ppa.  I have been using it for a long time and it already has LO-4.4.2.2, which is then updated automatically along with every other application from the repos.

---

### Post by Ralph L on 2015-04-26
Here's the output of the "find" you requested.  You are indeed correct that the files are owned by root.  Any idea of how they got that way.  I followed the directions on the Libreoffice web site.  As for why I didn't install them from the repositories, I think the repository ones were older then,  Now I see they say 4.2.7 if I read things correctly.  Any ideas of how to uninstall libreoffice completely and I will reinstall using synaptic.

Thank you very much for your help.  Hope I learned something, but I still don't know why the files ended up belonging to root, but in my directory.


```
ralph@lat1:~$ find ~/.config ! -user "$USER" -ls
132354    4 -rw-r--r--   1 root     root          557 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/autotext/mytexts.bau
131311  412 -rw-r--r--   1 root     root       418450 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/database/biblio/biblio.dbf
182524  600 -rw-r--r--   1 root     root       610825 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/database/biblio/biblio.dbt
182735    4 -rw-r--r--   1 root     root         3759 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/database/evolocal.odb
182487    4 -rw-r--r--   1 root     root         2687 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/database/biblio.odb
182490    4 -rw-r--r--   1 root     root         1124 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/basic/Standard/Module1.xba
182491    4 -rw-r--r--   1 root     root          288 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/basic/Standard/dialog.xlb
182492    4 -rw-r--r--   1 root     root          349 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/basic/Standard/script.xlb
182493    4 -rw-r--r--   1 root     root          339 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/basic/dialog.xlc
182497    4 -rw-r--r--   1 root     root          339 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/basic/script.xlc
182498  156 -rw-r--r--   1 root     root       155895 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/config/standard.sob
182499   16 -rw-r--r--   1 root     root        14420 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/config/web.soc
182500    8 -rw-r--r--   1 root     root         4984 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/config/standard.soe
182988    4 drwxr-xr-x   6 root     root         4096 Apr 24 22:46 /home/ralph/.config/libreoffice/4/user/config/soffice.cfg/modules/StartModule
182993    4 drwxr-xr-x   3 root     root         4096 Apr 24 22:46 /home/ralph/.config/libreoffice/4/user/config/soffice.cfg/modules/StartModule/images
182994    4 drwxr-xr-x   2 root     root         4096 Apr 24 22:46 /home/ralph/.config/libreoffice/4/user/config/soffice.cfg/modules/StartModule/images/Bitmaps
182990    4 drwxr-xr-x   2 root     root         4096 Apr 24 22:46 /home/ralph/.config/libreoffice/4/user/config/soffice.cfg/modules/StartModule/toolbar
182991    4 drwxr-xr-x   2 root     root         4096 Apr 24 22:46 /home/ralph/.config/libreoffice/4/user/config/soffice.cfg/modules/StartModule/statusbar
182989    4 drwxr-xr-x   2 root     root         4096 Apr 24 22:46 /home/ralph/.config/libreoffice/4/user/config/soffice.cfg/modules/StartModule/menubar
182501    4 -rw-r--r--   1 root     root         1708 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/config/styles.sod
182502   32 -rw-r--r--   1 root     root        31320 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/config/scribus.soc
182503   12 -rw-r--r--   1 root     root        11165 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/config/standard.soc
182504    4 -rw-r--r--   1 root     root         2171 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/config/standard.soh
182505    8 -rw-r--r--   1 root     root         5238 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/config/hatching.soh
182506    8 -rw-r--r--   1 root     root         4308 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/config/arrowhd.soe
182507    8 -rw-r--r--   1 root     root         6840 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/config/modern.sog
182508   12 -rw-r--r--   1 root     root        10766 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/config/html.soc
182509   32 -rw-r--r--   1 root     root        30852 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/config/classic.sog
182510    8 -rw-r--r--   1 root     root         5080 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/config/standard.sog
182511    8 -rw-r--r--   1 root     root         4408 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/config/gallery.soc
182512    8 -rw-r--r--   1 root     root         5271 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/config/palette.soc
182513   16 -rw-r--r--   1 root     root        13132 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/config/cmyk.soc
182514    4 -rw-r--r--   1 root     root         2426 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/config/standard.sod
182515    4 -rw-r--r--   1 root     root         2331 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/config/tango.soc
182516    4 -rw-r--r--   1 root     root         2334 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/config/libreoffice.soc
182517   48 -rw-r--r--   1 root     root        48408 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/config/autotbl.fmt
182518    4 -rw-r--r--   1 root     root         2048 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/gallery/sg30.sdv
182519    4 -rw-r--r--   1 root     root          565 Apr 25 00:02 /home/ralph/.config/libreoffice/4/user/gallery/sg30.thm
182595    4 -rw-r--r--   1 root     root            1 Apr 24 22:18 /home/ralph/.config/libreoffice/4/user/extensions/shared/lastsynchronized
182594    4 -rw-r--r--   1 root     root            1 Apr 24 22:18 /home/ralph/.config/libreoffice/4/user/extensions/bundled/lastsynchronized
ralph@lat1:~$ 

```

---

### Post by steeldriver on 2015-04-26
You should be able to fix that from the terminal using

```

sudo chown -R ralph:ralph /home/ralph/.config/libreoffice/

```

---

### Post by Ralph L on 2015-04-27
Steeldriver:  Thanks for the response.  Tried it.  Didn't work.  Still get "The application cannot be started. 
User installation could not be completed. "  I have changed the permissions of several items now and I can't remember all of them.  I think the best thing for me to do is to completely remove libreoffice and start again installing it with synaptic.  I tried removing it with the following, but still found all sorts of files remaining.  Most of what I listed are probably icons, but there could be other folder/files that my "find" didn't find.   Would you tell me how to completely.... remove it?

Also, how do I tell what version synaptic will load from repositories.  I interpreted the 1:4.2.7-0ubuntu1 under latest version in synaptic as being Libreoffice 4.2.7, which would be older than the current Libreoffice 4.4.2.  That played a roll in me loading Libreoffice direct from the Libreoffice web site.

```
sudo apt-get remove --purge libreoffice*
sudo apt-get clean
sudo apt-get autoremove
```

```
ralph@lat1:~$ sudo find / -name 'libreoffice*'
/home/ralph/.config/libreoffice
/home/ralph/.config/libreoffice/4/user/config/libreoffice.soc
/home/ralph/Documents/test folder/libreoffice message
/opt/libreoffice4.4
/usr/share/icons/elementary-xfce/mimes/16/libreoffice-oasis-spreadsheet.png
/usr/share/icons/elementary-xfce/mimes/16/libreoffice-drawing.png
/usr/share/icons/elementary-xfce/mimes/16/libreoffice-oasis-drawing.png
/usr/share/icons/elementary-xfce/mimes/16/libreoffice-oasis-drawing-template.png
/usr/share/icons/elementary-xfce/mimes/16/libreoffice-drawing-template.png
/usr/share/icons/elementary-xfce/mimes/16/libreoffice-database.png
/usr/share/icons/elementary-xfce/mimes/16/libreoffice-oasis-text-template.png
/usr/share/icons/elementary-xfce/mimes/16/libreoffice-oasis-presentation-template.png
/usr/share/icons/elementary-xfce/mimes/16/libreoffice-oasis-presentation.png
/usr/share/icons/elementary-xfce/mimes/16/libreoffice-oasis-spreadsheet-template.png
/usr/share/icons/elementary-xfce/mimes/16/libreoffice-oasis-text.png
/usr/share/icons/elementary-xfce/mimes/16/libreoffice-oasis-database.png
/usr/share/icons/elementary-xfce/mimes/16/libreoffice-extension.png
/usr/share/icons/elementary-xfce/mimes/32/libreoffice-oasis-spreadsheet.png
/usr/share/icons/elementary-xfce/mimes/32/libreoffice-drawing.png
/usr/share/icons/elementary-xfce/mimes/32/libreoffice-oasis-drawing.png
/usr/share/icons/elementary-xfce/mimes/32/libreoffice-oasis-drawing-template.png
/usr/share/icons/elementary-xfce/mimes/32/libreoffice-drawing-template.png
/usr/share/icons/elementary-xfce/mimes/32/libreoffice-database.png
/usr/share/icons/elementary-xfce/mimes/32/libreoffice-oasis-text-template.png
/usr/share/icons/elementary-xfce/mimes/32/libreoffice-oasis-presentation-template.png
/usr/share/icons/elementary-xfce/mimes/32/libreoffice-oasis-presentation.png
/usr/share/icons/elementary-xfce/mimes/32/libreoffice-oasis-spreadsheet-template.png
/usr/share/icons/elementary-xfce/mimes/32/libreoffice-oasis-text.png
/usr/share/icons/elementary-xfce/mimes/32/libreoffice-oasis-database.png
/usr/share/icons/elementary-xfce/mimes/32/libreoffice-extension.png
/usr/share/icons/elementary-xfce/mimes/22/libreoffice-oasis-spreadsheet.png
/usr/share/icons/elementary-xfce/mimes/22/libreoffice-drawing.png
/usr/share/icons/elementary-xfce/mimes/22/libreoffice-oasis-drawing.png
/usr/share/icons/elementary-xfce/mimes/22/libreoffice-oasis-drawing-template.png
/usr/share/icons/elementary-xfce/mimes/22/libreoffice-drawing-template.png
/usr/share/icons/elementary-xfce/mimes/22/libreoffice-database.png
/usr/share/icons/elementary-xfce/mimes/22/libreoffice-oasis-text-template.png
/usr/share/icons/elementary-xfce/mimes/22/libreoffice-oasis-presentation-template.png
/usr/share/icons/elementary-xfce/mimes/22/libreoffice-oasis-presentation.png
/usr/share/icons/elementary-xfce/mimes/22/libreoffice-oasis-spreadsheet-template.png
/usr/share/icons/elementary-xfce/mimes/22/libreoffice-oasis-text.png
/usr/share/icons/elementary-xfce/mimes/22/libreoffice-oasis-database.png
/usr/share/icons/elementary-xfce/mimes/22/libreoffice-extension.png
/usr/share/icons/elementary-xfce/mimes/48/libreoffice-oasis-spreadsheet.png
/usr/share/icons/elementary-xfce/mimes/48/libreoffice-drawing.png
/usr/share/icons/elementary-xfce/mimes/48/libreoffice-oasis-drawing.png
/usr/share/icons/elementary-xfce/mimes/48/libreoffice-oasis-drawing-template.png
/usr/share/icons/elementary-xfce/mimes/48/libreoffice-drawing-template.png
/usr/share/icons/elementary-xfce/mimes/48/libreoffice-database.png
/usr/share/icons/elementary-xfce/mimes/48/libreoffice-oasis-text-template.png
/usr/share/icons/elementary-xfce/mimes/48/libreoffice-oasis-presentation-template.png
/usr/share/icons/elementary-xfce/mimes/48/libreoffice-oasis-presentation.png
/usr/share/icons/elementary-xfce/mimes/48/libreoffice-oasis-spreadsheet-template.png
/usr/share/icons/elementary-xfce/mimes/48/libreoffice-oasis-text.png
/usr/share/icons/elementary-xfce/mimes/48/libreoffice-oasis-database.png
/usr/share/icons/elementary-xfce/mimes/48/libreoffice-extension.png
/usr/share/icons/elementary-xfce/mimes/64/libreoffice-oasis-spreadsheet.png
/usr/share/icons/elementary-xfce/mimes/64/libreoffice-drawing.png
/usr/share/icons/elementary-xfce/mimes/64/libreoffice-oasis-drawing.png
/usr/share/icons/elementary-xfce/mimes/64/libreoffice-oasis-drawing-template.png
/usr/share/icons/elementary-xfce/mimes/64/libreoffice-drawing-template.png
/usr/share/icons/elementary-xfce/mimes/64/libreoffice-database.png
/usr/share/icons/elementary-xfce/mimes/64/libreoffice-oasis-text-template.png
/usr/share/icons/elementary-xfce/mimes/64/libreoffice-oasis-presentation-template.png
/usr/share/icons/elementary-xfce/mimes/64/libreoffice-oasis-presentation.png
/usr/share/icons/elementary-xfce/mimes/64/libreoffice-oasis-spreadsheet-template.png
/usr/share/icons/elementary-xfce/mimes/64/libreoffice-oasis-text.png
/usr/share/icons/elementary-xfce/mimes/64/libreoffice-oasis-database.png
/usr/share/icons/elementary-xfce/mimes/64/libreoffice-extension.png
/usr/share/icons/elementary-xfce/mimes/24/libreoffice-oasis-spreadsheet.png
/usr/share/icons/elementary-xfce/mimes/24/libreoffice-drawing.png
/usr/share/icons/elementary-xfce/mimes/24/libreoffice-oasis-drawing.png
/usr/share/icons/elementary-xfce/mimes/24/libreoffice-oasis-drawing-template.png
/usr/share/icons/elementary-xfce/mimes/24/libreoffice-drawing-template.png
/usr/share/icons/elementary-xfce/mimes/24/libreoffice-database.png
/usr/share/icons/elementary-xfce/mimes/24/libreoffice-oasis-text-template.png
/usr/share/icons/elementary-xfce/mimes/24/libreoffice-oasis-presentation-template.png
/usr/share/icons/elementary-xfce/mimes/24/libreoffice-oasis-presentation.png
/usr/share/icons/elementary-xfce/mimes/24/libreoffice-oasis-spreadsheet-template.png
/usr/share/icons/elementary-xfce/mimes/24/libreoffice-oasis-text.png
/usr/share/icons/elementary-xfce/mimes/24/libreoffice-oasis-database.png
/usr/share/icons/elementary-xfce/mimes/24/libreoffice-extension.png
/usr/share/icons/elementary-xfce/mimes/96/libreoffice-oasis-spreadsheet.png
/usr/share/icons/elementary-xfce/mimes/96/libreoffice-drawing.png
/usr/share/icons/elementary-xfce/mimes/96/libreoffice-oasis-drawing.png
/usr/share/icons/elementary-xfce/mimes/96/libreoffice-oasis-drawing-template.png
/usr/share/icons/elementary-xfce/mimes/96/libreoffice-drawing-template.png
/usr/share/icons/elementary-xfce/mimes/96/libreoffice-oasis-text-template.png
/usr/share/icons/elementary-xfce/mimes/96/libreoffice-oasis-presentation-template.png
/usr/share/icons/elementary-xfce/mimes/96/libreoffice-oasis-presentation.png
/usr/share/icons/elementary-xfce/mimes/96/libreoffice-oasis-spreadsheet-template.png
/usr/share/icons/elementary-xfce/mimes/96/libreoffice-oasis-text.png
/usr/share/icons/elementary-xfce/mimes/96/libreoffice-extension.png
/usr/share/icons/elementary-xfce/apps/16/libreoffice-base.png
/usr/share/icons/elementary-xfce/apps/16/libreoffice-draw.png
/usr/share/icons/elementary-xfce/apps/16/libreoffice-writer.png
/usr/share/icons/elementary-xfce/apps/16/libreoffice-impress.png
/usr/share/icons/elementary-xfce/apps/16/libreoffice-calc.png
/usr/share/icons/elementary-xfce/apps/128/libreoffice-base.png
/usr/share/icons/elementary-xfce/apps/128/libreoffice-draw.png
/usr/share/icons/elementary-xfce/apps/128/libreoffice-writer.png
/usr/share/icons/elementary-xfce/apps/128/libreoffice-impress.png
/usr/share/icons/elementary-xfce/apps/128/libreoffice-calc.png
/usr/share/icons/elementary-xfce/apps/32/libreoffice-base.png
/usr/share/icons/elementary-xfce/apps/22/libreoffice-base.png
/usr/share/icons/elementary-xfce/apps/22/libreoffice-draw.png
/usr/share/icons/elementary-xfce/apps/22/libreoffice-writer.png
/usr/share/icons/elementary-xfce/apps/22/libreoffice-impress.png
/usr/share/icons/elementary-xfce/apps/22/libreoffice-calc.png
/usr/share/icons/elementary-xfce/apps/48/libreoffice-base.png
/usr/share/icons/elementary-xfce/apps/48/libreoffice-draw.png
/usr/share/icons/elementary-xfce/apps/48/libreoffice-writer.png
/usr/share/icons/elementary-xfce/apps/48/libreoffice-impress.png
/usr/share/icons/elementary-xfce/apps/48/libreoffice-calc.png
/usr/share/icons/elementary-xfce/apps/64/libreoffice-base.png
/usr/share/icons/elementary-xfce/apps/64/libreoffice-draw.png
/usr/share/icons/elementary-xfce/apps/64/libreoffice-writer.png
/usr/share/icons/elementary-xfce/apps/64/libreoffice-impress.png
/usr/share/icons/elementary-xfce/apps/64/libreoffice-calc.png
/usr/share/icons/elementary-xfce/apps/24/libreoffice-base.png
/usr/share/icons/elementary-xfce/apps/24/libreoffice-draw.png
/usr/share/icons/elementary-xfce/apps/24/libreoffice-writer.png
/usr/share/icons/elementary-xfce/apps/24/libreoffice-impress.png
/usr/share/icons/elementary-xfce/apps/24/libreoffice-calc.png
/usr/share/icons/HighContrast/48x48/apps/libreoffice-base.png
/usr/share/icons/HighContrast/48x48/apps/libreoffice-draw.png
/usr/share/icons/HighContrast/48x48/apps/libreoffice-startcenter.png
/usr/share/icons/HighContrast/48x48/apps/libreoffice-writer.png
/usr/share/icons/HighContrast/48x48/apps/libreoffice-math.png
/usr/share/icons/HighContrast/48x48/apps/libreoffice-impress.png
/usr/share/icons/HighContrast/48x48/apps/libreoffice-calc.png
/usr/share/icons/HighContrast/16x16/apps/libreoffice-base.png
/usr/share/icons/HighContrast/16x16/apps/libreoffice-draw.png
/usr/share/icons/HighContrast/16x16/apps/libreoffice-startcenter.png
/usr/share/icons/HighContrast/16x16/apps/libreoffice-writer.png
/usr/share/icons/HighContrast/16x16/apps/libreoffice-math.png
/usr/share/icons/HighContrast/16x16/apps/libreoffice-impress.png
/usr/share/icons/HighContrast/16x16/apps/libreoffice-calc.png
/usr/share/icons/HighContrast/256x256/apps/libreoffice-base.png
/usr/share/icons/HighContrast/256x256/apps/libreoffice-draw.png
/usr/share/icons/HighContrast/256x256/apps/libreoffice-startcenter.png
/usr/share/icons/HighContrast/256x256/apps/libreoffice-writer.png
/usr/share/icons/HighContrast/256x256/apps/libreoffice-math.png
/usr/share/icons/HighContrast/256x256/apps/libreoffice-impress.png
/usr/share/icons/HighContrast/256x256/apps/libreoffice-calc.png
/usr/share/icons/HighContrast/24x24/apps/libreoffice-base.png
/usr/share/icons/HighContrast/24x24/apps/libreoffice-draw.png
/usr/share/icons/HighContrast/24x24/apps/libreoffice-startcenter.png
/usr/share/icons/HighContrast/24x24/apps/libreoffice-writer.png
/usr/share/icons/HighContrast/24x24/apps/libreoffice-math.png
/usr/share/icons/HighContrast/24x24/apps/libreoffice-impress.png
/usr/share/icons/HighContrast/24x24/apps/libreoffice-calc.png
/usr/share/icons/HighContrast/32x32/apps/libreoffice-base.png
/usr/share/icons/HighContrast/32x32/apps/libreoffice-draw.png
/usr/share/icons/HighContrast/32x32/apps/libreoffice-startcenter.png
/usr/share/icons/HighContrast/32x32/apps/libreoffice-writer.png
/usr/share/icons/HighContrast/32x32/apps/libreoffice-math.png
/usr/share/icons/HighContrast/32x32/apps/libreoffice-impress.png
/usr/share/icons/HighContrast/32x32/apps/libreoffice-calc.png
/usr/share/icons/HighContrast/22x22/apps/libreoffice-base.png
/usr/share/icons/HighContrast/22x22/apps/libreoffice-draw.png
/usr/share/icons/HighContrast/22x22/apps/libreoffice-startcenter.png
/usr/share/icons/HighContrast/22x22/apps/libreoffice-writer.png
/usr/share/icons/HighContrast/22x22/apps/libreoffice-math.png
/usr/share/icons/HighContrast/22x22/apps/libreoffice-impress.png
/usr/share/icons/HighContrast/22x22/apps/libreoffice-calc.png
/usr/share/icons/Humanity/mimes/256/libreoffice-oasis-database.svg
/usr/share/icons/Humanity/mimes/256/libreoffice-oasis-presentation.svg
/usr/share/icons/Humanity/mimes/256/libreoffice-oasis-spreadsheet.svg
/usr/share/icons/Humanity/mimes/256/libreoffice-oasis-text.svg
/usr/share/icons/Humanity/mimes/256/libreoffice-oasis-drawing.svg
/usr/share/icons/Humanity/mimes/16/libreoffice-oasis-drawing-template.png
/usr/share/icons/Humanity/mimes/16/libreoffice-oasis-database.svg
/usr/share/icons/Humanity/mimes/16/libreoffice-oasis-presentation.svg
/usr/share/icons/Humanity/mimes/16/libreoffice-oasis-web-template.png
/usr/share/icons/Humanity/mimes/16/libreoffice-oasis-spreadsheet.svg
/usr/share/icons/Humanity/mimes/16/libreoffice-oasis-text.svg
/usr/share/icons/Humanity/mimes/16/libreoffice-oasis-text-template.png
/usr/share/icons/Humanity/mimes/16/libreoffice-oasis-drawing.svg
/usr/share/icons/Humanity/mimes/16/libreoffice-oasis-presentation-template.png
/usr/share/icons/Humanity/mimes/16/libreoffice-oasis-master-document.png
/usr/share/icons/Humanity/mimes/16/libreoffice-oasis-formula.png
/usr/share/icons/Humanity/mimes/16/libreoffice-oasis-spreadsheet-template.png
/usr/share/icons/Humanity/mimes/128/libreoffice-oasis-database.svg
/usr/share/icons/Humanity/mimes/128/libreoffice-oasis-presentation.svg
/usr/share/icons/Humanity/mimes/128/libreoffice-oasis-spreadsheet.svg
/usr/share/icons/Humanity/mimes/128/libreoffice-oasis-text.svg
/usr/share/icons/Humanity/mimes/128/libreoffice-oasis-drawing.svg
/usr/share/icons/Humanity/mimes/32/libreoffice-oasis-drawing-template.png
/usr/share/icons/Humanity/mimes/32/libreoffice-oasis-database.svg
/usr/share/icons/Humanity/mimes/32/libreoffice-oasis-presentation.svg
/usr/share/icons/Humanity/mimes/32/libreoffice-oasis-web-template.png
/usr/share/icons/Humanity/mimes/32/libreoffice-oasis-spreadsheet.svg
/usr/share/icons/Humanity/mimes/32/libreoffice-oasis-text.svg
/usr/share/icons/Humanity/mimes/32/libreoffice-oasis-text-template.png
/usr/share/icons/Humanity/mimes/32/libreoffice-oasis-drawing.svg
/usr/share/icons/Humanity/mimes/32/libreoffice-oasis-presentation-template.png
/usr/share/icons/Humanity/mimes/32/libreoffice-oasis-master-document.png
/usr/share/icons/Humanity/mimes/32/libreoffice-oasis-formula.png
/usr/share/icons/Humanity/mimes/32/libreoffice-oasis-spreadsheet-template.png
/usr/share/icons/Humanity/mimes/48/libreoffice-oasis-drawing-template.png
/usr/share/icons/Humanity/mimes/48/libreoffice-oasis-database.svg
/usr/share/icons/Humanity/mimes/48/libreoffice-oasis-presentation.svg
/usr/share/icons/Humanity/mimes/48/libreoffice-oasis-web-template.png
/usr/share/icons/Humanity/mimes/48/libreoffice-oasis-spreadsheet.svg
/usr/share/icons/Humanity/mimes/48/libreoffice-oasis-text.svg
/usr/share/icons/Humanity/mimes/48/libreoffice-oasis-text-template.png
/usr/share/icons/Humanity/mimes/48/libreoffice-oasis-drawing.svg
/usr/share/icons/Humanity/mimes/48/libreoffice-oasis-presentation-template.png
/usr/share/icons/Humanity/mimes/48/libreoffice-oasis-master-document.png
/usr/share/icons/Humanity/mimes/48/libreoffice-oasis-formula.png
/usr/share/icons/Humanity/mimes/48/libreoffice-oasis-spreadsheet-template.png
/usr/share/app-install/desktop/libreoffice-impress:libreoffice-impress.desktop
/usr/share/app-install/desktop/libreoffice-base:libreoffice-base.desktop
/usr/share/app-install/desktop/libreoffice-calc:libreoffice-calc.desktop
/usr/share/app-install/desktop/libreoffice-math:libreoffice-math.desktop
/usr/share/app-install/desktop/libreoffice-draw:libreoffice-draw.desktop
/usr/share/app-install/desktop/libreoffice-writer:libreoffice-writer.desktop
/usr/share/app-install/desktop/libreoffice-common:libreoffice-xsltfilter.desktop
/usr/share/app-install/desktop/libreoffice-common:libreoffice-startcenter.desktop
/usr/share/app-install/icons/libreoffice-math.svg
/usr/share/app-install/icons/libreoffice-writer.svg
/usr/share/app-install/icons/libreoffice-draw.svg
/usr/share/app-install/icons/libreoffice-calc.svg
/usr/share/app-install/icons/libreoffice-base.svg
/usr/share/app-install/icons/libreoffice-startcenter.svg
/usr/share/app-install/icons/libreoffice-impress.svg

```

---

### Post by ajgreeny on 2015-04-27
As you installed using dpkg you will also need to remove using dpkg.

It's a long time since Iused dpkg for anything other than a single package so I can't remember how you would do it for the whole suite of LO installed that way, but it may be ```
sudo dpkg -P libreoffice*
```

As for the version of LO available, as I said, you should use the PPA at [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa) which has the latest version, 4.4.2.2, and can be installed in the normal way with software-center or synaptic, or even [B]sudo apt-get install libreoffice.
[/B]
I also wonder if your chown command have caused any other problems with your /home ownership.  It may be well worth running the command ```
sudo chown -R ralph:ralph /home/ralph
``` to make sure all is yours.

---

### Post by Ralph L on 2015-04-28
ajgreeny:  Thanks again for responding.  You've been very helpful.  
```
sudo dpkg -P libreoffice*
``` didn't work.  It said libreoffice* was not a package, so I removed the *, and then it said that libreoffice wasn't installed, even though there were libreoffice files in several places.  So I deleted everything that "find" found looking for the name "libreoffice", except for the icons (I don't know if the libreoffice icons came with Xunbuntu or were added by Libreoffice--do you know??).  Anyway, after the deletions, I used synaptic to install the ppa you recommended and Libreoffice now seems to work.  I didn't know this ppa existed.
Your saying that if I installed libre office with dpkg I had to uninstall it with dpkg tells me that I don't understand installing, uninstalling, packaging, and linking of apps.  Maybe you can enlighten me a little??  Is it that dpkg fails to update some sort of data base that apt-get and synaptic use that causes dpkg-installed-apps to be un-removable by apt-get and synaptic???  Could you explain that, because in the past I have installed a number of apps using dpkg following the instructions on the web site for the app.  Should I never install something with dpkg???  If so why do app. web sites like [http://www.binarytides.com/better-xubuntu-14-04/](http://www.binarytides.com/better-xubuntu-14-04/) say to install things with dpkg, if it is going to result in problems???  And why does the Libreoffice web site even offer a tar.gz file if it can't be installed correctly???  Also, I have seen Gdebi recommended for installing apps.  Is this another thing that doesn't update the apt-get database, and shouldn't be used???

Any help you could give me with the above questions would be greatly appreciated.  Maybe I could learn something and not make this mistake again.

Thanks again,

---

### Post by deadflowr on 2015-04-28
I've used a little bit more robust dpkg command, using a couple pipes like this
first try the dry-run version
```
dpkg -l | grep libreoffice | awk '/^ii/{print $2}' | xargs sudo apt-get purge -s
```
the output should look something like this
```
The following packages will be REMOVED:  libreoffice-base-core* libreoffice-calc* libreoffice-common*
  libreoffice-core* libreoffice-draw* libreoffice-emailmerge*
  libreoffice-gnome* libreoffice-gtk* libreoffice-help-en-us*
  libreoffice-impress* libreoffice-math* libreoffice-style-human*
  libreoffice-style-tango* libreoffice-writer* lo-menubar* mythes-en-us*
  python-uno*
0 upgraded, 0 newly installed, 17 to remove and 0 not upgraded.
Purg libreoffice-help-en-us [1:3.5.7-0ubuntu8]
Purg libreoffice-writer [1:3.5.7-0ubuntu8]
Purg libreoffice-calc [1:3.5.7-0ubuntu8]
Purg libreoffice-base-core [1:3.5.7-0ubuntu8]
Purg libreoffice-emailmerge [1:3.5.7-0ubuntu8]
Purg python-uno [1:3.5.7-0ubuntu8]
Purg libreoffice-style-tango [1:3.5.7-0ubuntu8]
Purg libreoffice-math [1:3.5.7-0ubuntu8]
Purg libreoffice-impress [1:3.5.7-0ubuntu8]
Purg libreoffice-gnome [1:3.5.7-0ubuntu8]
Purg lo-menubar [0.1.0-0ubuntu4]
Purg libreoffice-gtk [1:3.5.7-0ubuntu8]
Purg libreoffice-draw [1:3.5.7-0ubuntu8]
Purg mythes-en-us [1:3.3.0-2ubuntu3]
Purg libreoffice-core [1:3.5.7-0ubuntu8] [libreoffice-style-human:amd64 ]
Purg libreoffice-common [1:3.5.7-0ubuntu8] [libreoffice-style-human:amd64 ]
Purg libreoffice-style-human [1:3.5.7-0ubuntu8]
```
but it won't remove anything yet, since it uses to -s flag, which means simulate.
You can verfiy that nothing was removed by running the command again but this time exclude the xargs sudo apt-get purge, and run it like so
```
dpkg -l | grep libreoffice | awk '/^ii/{print $2}' 
```
it should show all the packages listed, and those are the packages still installed on the system.

If everything from the simulated test run looks good, then try it for real by removing the -s option.

Post back the output if anything you see looks concerning to you.

---

### Post by Ralph L on 2015-04-29
deadflower
Thanks for the response.  I appreciate it that people are so willing to help.  However, by manually deleting libreoffice stuff, I was able to reinstall it from the ppa (recommended by ajgreeny) and libreoffice now seems to run ok.  However, I am trying to learn something from this experience.  If you have any answers to the questions I asked 2 posts back, I would appreciate them.

Thanks again.

---

### Post by Ralph L on 2015-04-30
There is more to this problem than described above.  After I purged and reinstalled libreoffice.  I did ```
sudo thunar
```  Then, in the root thunar window I had just created, I right clicked and opened /etc/fstab with libreoffice.  This caused the file ~/.config/libreoffice/4/user/registrymodifications.xcu to change owner and group to root!!!!  Then I closed libreoffice and opened it again with sudo libreoffice.  This caused many of the files and folders in ~/.config/libreoffice/4/user/ to change owner and group to root!!!!  Then libreoffice would no longer open without using sudo libreoffice in the Terminal.  Then I did ```
sudo chown -R ralph:ralph /home/ralph/.config/libreoffice/
``` and now libreoffice ran fine again.

Anybody have any idea of why libreoffice wants to change ownership on MY files just because it is run with sudo libreoffice???  Does this mean that one should never run libreoffice under root--either explicitly with ```
sudo libreoffice
```, or implicitly with ```
sudo thunar

``` then clicking on a root file such as /etc/fstab????
Incidentally "sudo thunar" also sometimes results in ~/.config/xfce4/xfconf/xfce-perchannel-xml/thunar.xml changing to root ownership, but then it sometimes inexplicably changes back to being owned by the user.  Being able to edit and change system files (owned by root) with the file manager is important to me.  I'm not good at using the Terminal and find it much easier just to run a root version of the file manager.  I have been doing that for years under older OS's in the Ubuntu line and never had a problem.  I am very inexperienced with xubuntu, so I don't know if it was possible to run a root thunar in the past
The whole thing seems very strange, is very confusing to a dummy like me, and makes me wonder if things are supposed to work that way.

---

### Post by ajgreeny on 2015-04-30
Oh dear !!!
YOU SHOULD **NEVER** **USE sudo**  FOR RUNNING ANY GUI APPLICATION SUCH AS THUNAR OR LIBREOFFICE.

Sorry to appear as if I'm shouting but doing so could be why for you have ended up with these problems of incorrect ownership of folders in ~/.config, as you note has already happened to the some of yours in .config

The developers woud prefer it if we only used a few GUI applications like the update-manager or software-center with root permissions, and if so they should be opened not with **sudo** but **gksudo**, or in more recent versions of Ubuntu with **pkexec** policy rules in place.  This may all sound like gobbledegook to you but it is important.

See **Root-Sudo** in my signature for more details, and for even more background and information see also [http://ubuntuforums.org/showthread.php?t=2225832](http://ubuntuforums.org/showthread.php?t=2225832)

Most importantly, do not use sudo for any GUI applications in future or we may be back here with the same problem from you again soon.

---

