---
title: "kdenlive permission problem (or kde environment in gnome problem)"
date: 2019-04-01
forum: General Help
---

### Post by monkeybrain20122 on 2019-04-01
This is a bit of a strange issue.

I have compiled  kdenlive-18.12.3 in my Unity(gnome-based) Ubuntu 16.04 box. I built it  in my $HOME without ever invoking sudo. But I am not able to access any  folder from kdenlive because in Kdenlive's file open dialogue they are reported to be  owned by root. In order to compile kdenlive I need up to date KF5, since  kde5 in 16.04 is too old I compiled it myself too in my $HOME (again  without sudo at any time) 

I run kdenlive with a script that loads the kf5 environment:


```
export PREFIX=$HOME/opt/kdenlive
export KF5PREFIX=$HOME/opt/kf5
export LD_LIBRARY_PATH=$PREFIX/lib:$KF5PREFIX/lib:$KF5PREFIX/qt5/lib:$LD_LIBRARY_PATH
export PATH=$PREFIX/bin:$KF5PREFIX/bin:$KF5PREFIX/qt5/bin:$PATH
export   PKG_CONFIG_PATH=$PREFIX/lib/pkgconfig:$PREFIX/share/pkgconfig:$KF5PREFIX/lib/pkgconfig:$KF5PREFIX/qt5/lib/pkgconfig:$KF5PREFIX/share/pkgconfig:$PKG_CONFIG_PATH
export QT5DIR=$KF5PREFIX/opt/qt5

```

Where $HOME/opt/kf5 is where I installed KF5

I  think my problem has to do with some weird permission problem stemming  from running a kde environment (not just a kde app) in a gnome box  (and  my hardrive "ubuntu" shows up as a mounted device in kdenlive's open  file menu)

How do I change the permission within the kde environment? 

Thanks.

---

### Post by monkeybrain20122 on 2019-04-02
I think I misdiagnosed. I am able to open folders inside my $HOME without root from the open file menu, so it is not permission. But the it doesn't show anything in the folder. I think this is the culprit

> kf5.kservice.services: KServiceTypeTrader: serviceType "ThumbCreator" not found
kf5.kservice.services: KServiceTypeTrader: serviceType "ThumbCreator" not found
kf5.kservice.services: KServiceTypeTrader: serviceType "ThumbCreator" not found
kf5.kservice.services: KServiceTypeTrader: serviceType "ThumbCreator" not found
kf5.kio.core: couldn't create slave: "klauncher said: Unknown protocol 'baloosearch'.\n"
kf5.kio.core: couldn't create slave: "klauncher said: Unknown protocol 'baloosearch'.\n"


---

### Post by #&amp;thj^% on 2019-04-02
You should run Kdenlive on a stable platform only. My suggestion:
- Use AppImage 18.08.3 (Or the current version for you). Run the Appimage from the terminal (press CTRL + ALT + T). Move to the AppImage folder and run the .AppImage: ./Kdenlive*.AppImage. 
This is all I can think of to try to help, with the limited information here.
Supported clip MIME types:
```

*,v *.3ga *.3gp *.3gpp *.ac3 *.aif *.aiff *.asc *.avf *.avi *.bdm *.bdmv *.bmp *.clpi *.cpi *.dib *.divx *.doc *.dv *.exr *.f4a
 *.f4v *.flac *.flv *.gif *.icb *.jpe *.jpeg *.jpg *.kdenlive *.kdenlivetitle *.kra *.lrv *.m2t *.m2ts *.m2v *.m4a *.m4v *.mka 
*.mkv *.mlt *.moov *.mov *.mp2 *.mp3 *.mp4 *.mpe *.mpeg *.mpg *.mpga *.mpl *.mpls *.mts *.mxf *.oga *.ogg *.ogv *
.ogx *.opus *.pcx *.png *.ppm *.qt *.qtvr *.rm *.rmj *.rmm *.rms *.rmvb *.rmx *.spl *.svg *.swf *.tga *.tif *.tiff *.tpic *.ts *.
txt *.vda *.vob *.vst *.wav *.webm *.westley *.wmv *.xcf [0-9][0-9][0-9].vdr
```

---

### Post by #&amp;thj^% on 2019-04-03
My install is just a bit different than yours, and went as follows:
To install the latest Kdenlive Appimage version, first, download it from [https://files.kde.org/kdenlive/release/](https://files.kde.org/kdenlive/release/).

Then make it executable with chmod +x in a terminal:
```

sudo chmod +x /home/me/Downloads/kdenlive-18.12.1b-x86_64.appimage
```
Change "me" to your username.
Move it to the /opt directory:

```
sudo mkdir /opt/kdenlive
```
Now move it:
```
sudo mv /home/me/Downloads/kdenlive-18.12.1b-x86_64.appimage /opt/kdenlive/
```
Change "me" to your username.
Download a Kdenlive icon from here:[https://cialu.net/wp-content/uploads/2019/02/kdenlive.png](https://cialu.net/wp-content/uploads/2019/02/kdenlive.png)

Move the icon to the Kdenlive folder:

```
sudo mv /home/me/Downloads/kdenlive.png /opt/kdenlive/kdenlive.png
```
Change "me" to your username
Create an application launcher for Kdenlive Appimage:

```
sudo nano /home/me/.local/share/applications/kdenlive.desktop
```
Change "me" to your username
And populate the file with:
```

[Desktop Entry]
Type=Application
Name=Kdenlive
GenericName=Video editor
Comment=KDE Video editor
Categories=Utility;Video;Editor;
Exec=/opt/kdenlive/kdenlive-18.12.1b-x86_64.appimage
Icon=/opt/kdenlive/kdenlive.png
Name[en_US]=Kdenlive

```
And you’re done.

Launch your latest Kdenlive as any other application.

```
apt policy kdenlive
kdenlive:
  Installed: (none)
  Candidate: 4:18.12.3a-0ubuntu1
  Version table:
     4:18.12.3a-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu disco/universe amd64 Packages

```

---

### Post by monkeybrain20122 on 2019-04-05
Hi, 

I knew about the appimage and have tested it before compiling. The reason I want to compile is that the app image cannot use hardware acceleration (box greyed out)

I think I may be missing some pieces in kf5. Will try it again in a few days and report back.

But thanks for the help though.

---

