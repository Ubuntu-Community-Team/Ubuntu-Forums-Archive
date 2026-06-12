---
title: "i need a lot of help beging someone help"
date: 2007-08-23
forum: General Help
---

### Post by gundumfx on 2007-08-23
:confused:well my problem is after i download ubuntu it is my os now an but when i want to hear music like in vlc player an gnome player it freezes an when i wannna watch videos an music in youtube or any web videos or music it freezes they music wont work so what do i do please help an movies that i download if i want to watch it freezes so what now please help i am begging thank you

---

### Post by jakev383 on 2007-08-23
It sounds like you do not have the codecs to watch or listen to that stuff.  I know some people will grumble and thrown rocks, but try installing Automatix ([www.getautomatix.com](www.getautomatix.com)) and getting the codecs that way.

---

### Post by bapoumba on 2007-08-23
> **gundumfx said:**
> :confused:well my problem is after i download ubuntu it is my os now an but when i want to hear music like in vlc player an gnome player it freezes an when i wannna watch videos an music in youtube or any web videos or music it freezes they music wont work so what do i do please help an movies that i download if i want to watch it freezes so what now please help i am begging thank you

Please install **ubuntu-restricted-extras**, all the codecs are there, except libdvdcss2 that you can get from medibuntu repositories. You'll need to have the multiverse repositories enabled.
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by gundumfx on 2007-08-23
> **bapoumba said:**
> Please install **ubuntu-restricted-extras**, all the codecs are there, except libdvdcss2 that you can get from medibuntu repositories. You'll need to have the multiverse repositories enabled.
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

what do i do with the links you gave me ??

---

### Post by p_quarles on 2007-08-23
You click on the links, and follow the instructions on those pages. :)

---

### Post by gundumfx on 2007-08-23
> **p_quarles said:**
> You click on the links, and follow the instructions on those pages. :)

ok i got you thanks for the help but it is still not working do you think if i like reinstall ubuntu again will it work because before it did

---

### Post by bapoumba on 2007-08-24
Please post your sources.list. Open a terminal (> Applications > Terminal) and paste the output to:
```
cat /etc/apt/sources.list
```

---

### Post by gundumfx on 2007-08-24
> **bapoumba said:**
> Please post your sources.list. Open a terminal (> Applications > Terminal) and paste the output to:
```
cat /etc/apt/sources.list
```

ok i did not what do i do ??

---

### Post by bapoumba on 2007-08-24
You just go to the menu Application, then Terminal. This will open a terminal window. You enter:
```
cat /etc/apt/sources.list
```
in the terminal window, and hit <enter>. Then you paste the output (the answer you got) from the terminal window in a reply here.

This will tell us what repositories you have enabled, and if you can install the codecs right away (we'll tell you how) or if you need more steps before that.

---

### Post by gundumfx on 2007-08-24
> **bapoumba said:**
> You just go to the menu Application, then Terminal. This will open a terminal window. You enter:
```
cat /etc/apt/sources.list
```
in the terminal window, and hit <enter>. Then you paste the output (the answer you got) from the terminal window in a reply here.

This will tell us what repositories you have enabled, and if you can install the codecs right away (we'll tell you how) or if you need more steps before that.


well 
after i put that this is what it showed me can i put it # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/) ./
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/) ./

---

### Post by Gremlinzzz on 2007-08-24
first remove the old paste this in terminal
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
then download and save the new to the desktop click the link and get Option 1: .tar.gz
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
now paste these commands in the terminal one line at a time and hit enter
cd Desktop
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/

---

### Post by bapoumba on 2007-08-24
You should be fine.
Open the terminal again, and run
```
sudo apt-get install ubuntu-restricted-extras
```
When prompted, give your password (it will not appear on the screen) and hit <enter>.
This will install all you need.

---

### Post by Gremlinzzz on 2007-08-24
What i have too do to setup mplayer first i uninstall totems plugin.from synaptic package manager.
then i get the deb package for smplayer [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/) plays my dvd movies.
Then i install mplayer plugin using synaptic package manager.
now for the codecs paste commands in terminal
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
now thxs to this forum i add divxs plugins to watch divxs online
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
Thats it and it works great i can watch dvd movie cds and divxs movies and streaming video.

---

### Post by gundumfx on 2007-08-25
> **bapoumba said:**
> You should be fine.
Open the terminal again, and run
```
sudo apt-get install ubuntu-restricted-extras
```
When prompted, give your password (it will not appear on the screen) and hit <enter>.
This will install all you need.
after the whole thing was done it gave me this 
                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-bin &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; Operating System Distributor License for Java v1.1 (DLJ)                  &#8593;  
 &#9474;                                                                           &#9646;  
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618;  
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618;  
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618;  
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618;  
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618;  
 &#9474; TERMS OF THE AGREEMENT.                                                   &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary     &#9618;  
 &#9474;     form, any other machine readable materials including, but not         &#9618;  
 &#9474;     limited to, libraries, source files, header files, and data files),   &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>                                        
 &#9474;                                                                           &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  
                                                                                
what do i do now

---

### Post by bapoumba on 2007-08-26
When you've got that screen with the license agreement, hit <tab> to highlight "OK", then <enter>. The install process will continue.

---

### Post by gundumfx on 2007-08-26
> **bapoumba said:**
> When you've got that screen with the license agreement, hit <tab> to highlight "OK", then <enter>. The install process will continue.

hey how do i fix this problem 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by gundumfx on 2007-08-26
> **bapoumba said:**
> When you've got that screen with the license agreement, hit <tab> to highlight "OK", then <enter>. The install process will continue.


ok for get it well i know how to fix that now 
so now i will do this sudo apt-get install ubuntu-restricted-extras
an press tab right

---

### Post by gundumfx on 2007-08-26
> **bapoumba said:**
> When you've got that screen with the license agreement, hit <tab> to highlight "OK", then <enter>. The install process will continue.

hey i did that command but when you first gave that commnad i put it in terminal but i did not press tad to select ok so now i tryed puting that command an it gave me this

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-bin: Depends: sun-java6-jre (= 6-00-2ubuntu2) but it is not going to be installed
  ubuntu-restricted-extras: Depends: gstreamer0.10-plugins-ugly but it is not going to be installed
                            Depends: gstreamer0.10-plugins-ugly-multiverse but it is not going to be installed
                            Depends: msttcorefonts but it is not going to be installed
                            Depends: sun-java6-plugin but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


so is it ok that i did not press tab last time an press ok

an then i tryed again an then it did the same thing but this time it did not show the argment then an said with out no error it was done

---

### Post by bapoumba on 2007-08-26
Please run
```
sudo apt-get -f install
```

---

### Post by gundumfx on 2007-08-26
> **bapoumba said:**
> Please run
```
sudo apt-get -f install
```


well i put that in my terminal an this is what i got 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglib2.0-dev libxalan110 libstartup-notification0-dev libpng12-dev
  libgdk-pixbuf2 libxerces27
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

so

---

### Post by bapoumba on 2007-08-26
> **gundumfx said:**
> 
so
So, try to play a mp3 ;)

---

### Post by steveneddy on 2007-08-26
You have Fedora installed, too?!

You've got to be kidding?

---

### Post by bapoumba on 2007-08-26
> **steveneddy said:**
> You have Fedora installed, too?!

You've got to be kidding?
What did I miss? :D

---

### Post by gundumfx on 2007-08-26
> **bapoumba said:**
> So, try to play a mp3 ;)

well yea all the stuff works now thanks a lot for your help 

can  you make me a mod in this web

---

### Post by gundumfx on 2007-08-26
> **steveneddy said:**
> You have Fedora installed, too?!

You've got to be kidding?

what do you  mean i have fedora installed too??

---

### Post by gundumfx on 2007-08-28
> **Gremlinzzz said:**
> What i have too do to setup mplayer first i uninstall totems plugin.from synaptic package manager.
then i get the deb package for smplayer [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/) plays my dvd movies.
Then i install mplayer plugin using synaptic package manager.
now for the codecs paste commands in terminal
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)
now thxs to this forum i add divxs plugins to watch divxs online
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
Thats it and it works great i can watch dvd movie cds and divxs movies and streaming video.

well thanks for telling me but i used the staff members way to fix it an it  did work so thanks you to

---

