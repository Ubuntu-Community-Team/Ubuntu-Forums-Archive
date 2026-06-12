---
title: "kmix open when starting KDE"
date: 2006-07-06
forum: General Help
---

### Post by vayu on 2006-07-06
After dist-upgrading to Dapper, kmix always starts up in an open window instead of as a system tray applet.   

Actually it will start both as an applet and in the system tray if under settings/configure kmix I set either one of the choices for "Dock into panel" or "Enable system tray volume control". It doesn't matter which, having either one set will have it included in the system tray, which I want, but I don't want it opened as a window in the middle of the desktop everytime I start up KDE.

If I uncheck both those choices it still starts as an open window, it just won't be in the system tray.

There is no entry for it in the Autostart directory.  Anyone know where else KDE start items exist, or a fix for this?

---

### Post by Jucato on 2006-07-06
Hmm... My ~/.kde/Autostart folder contains a KMix file, which is a symlink to /usr/share/applications/kde/KMix.desktop. The contents of that file is this:

> 
[Desktop Entry]
Encoding=UTF-8
Exec=kmix -caption "%c" %i %m
DocPath=kmix/index.html
OnlyShowIn=KDE;
Path=
Type=Application
MimeType=
Terminal=false
Icon=kmix
GenericName=Sound Mixer
GenericName[af]=Klank Menger
GenericName[ar]=&#1605;&#1575;&#1586;&#1580; &#1575;&#1604;&#1589;&#1608;&#1578;
GenericName[bg]=&#1040;&#1091;&#1076;&#1080;&#1086; &#1084;&#1080;&#1082;&#1089;&#1077;&#1088;
GenericName[br]=Mesker ar Son
GenericName[bs]=Zvu&#269;ni mikser
GenericName[ca]=Mesclador de so
GenericName[cs]=Zvukový sm&#283;&#353;ova&#269;
GenericName[cy]=Cymysgydd S&#373;n
GenericName[da]=Lydmikser
GenericName[de]=Lautstärkeregler
GenericName[el]=&#924;&#949;&#943;&#954;&#964;&#951;&#962; &#942;&#967;&#959;&#965;
GenericName[eo]=Sonormiksilo
GenericName[es]=Un mezclador audio
GenericName[et]=Helimikser
GenericName[eu]=Soinu nahasgailua
GenericName[fi]=Äänimikseri
GenericName[fr]=Console de mixage
GenericName[gl]=Mesturador de Son
GenericName[he]=&#1502;&#1506;&#1512;&#1489;&#1500; &#1510;&#1500;&#1497;&#1500;
GenericName[hi]=&#2343;&#2381;&#2357;&#2344;&#2367; &#2350;&#2367;&#2325;&#2381;&#2360;&#2352;
GenericName[hr]=Mikser zvuka
GenericName[hu]=Hangkever&#337;
GenericName[is]=Hljóðblöndun
GenericName[it]=Mixer audio
GenericName[ja]=&#12469;&#12454;&#12531;&#12489;&#12511;&#12461;&#12469;&#12540;
GenericName[km]=&#6016;&#6040;&#6098;&#6040;&#6044;&#6071;&#6034;&#6072;&#8203;&#6043;&#6070;&#6041;&#8203;&#6047;&#6040;&#6098;&#6043;&#6081;&#6020;
GenericName[lt]=Gars&#371; mai&#353;iklis
GenericName[lv]=Ska&#326;as Mik&#353;eris
GenericName[mk]=&#1052;&#1080;&#1082;&#1089;&#1077;&#1090;&#1072; &#1079;&#1072; &#1079;&#1074;&#1091;&#1082;
GenericName[ms]=Pengadun Bunyi
GenericName[nb]=Lydmikser
GenericName[nl]=Geluidsmixer
GenericName[nn]=Lydmiksar
GenericName[pa]=&#2599;&#2625;&#2600;&#2624; &#2606;&#2623;&#2581;&#2616;&#2608;
GenericName[pl]=Ustawienia g&#322;o&#347;no&#347;ci
GenericName[pt]=Mesa de Mistura de Áudio
GenericName[pt_BR]=Mixagem de som
GenericName[ro]=Mixer de sunet
GenericName[ru]=&#1047;&#1074;&#1091;&#1082;&#1086;&#1074;&#1086;&#1081; &#1084;&#1080;&#1082;&#1096;&#1077;&#1088;
GenericName[se]=Jietnamixer
GenericName[sk]=Zvukový mixér
GenericName[sl]=Me&#353;alnik zvoka
GenericName[sr]=&#1047;&#1074;&#1091;&#1095;&#1085;&#1072; &#1084;&#1080;&#1082;&#1089;&#1077;&#1090;&#1072;
GenericName[sr@Latn]=Zvu&#269;na mikseta
GenericName[sv]=Ljudmixer
GenericName[ta]=&#2962;&#2994;&#3007; &#2962;&#2985;&#3021;&#2993;&#3009;&#2970;&#3015;&#2992;&#3021;&#2986;&#3021;&#2986;&#3006;&#2985;&#3021;
GenericName[tg]=&#1054;&#1084;&#1077;&#1093;&#1090;&#1072;&#1082;&#1091;&#1085;&#1072;&#1082;&#1080; &#1054;&#1074;&#1086;&#1079;
GenericName[th]=&#3611;&#3619;&#3633;&#3610;&#3649;&#3605;&#3656;&#3591;&#3612;&#3626;&#3617;&#3648;&#3626;&#3637;&#3618;&#3591;
GenericName[tr]=Ses Kar&#305;&#351;t&#305;r&#305;c&#305;
GenericName[uk]=&#1040;&#1091;&#1076;&#1110;&#1086;&#1084;&#1110;&#1082;&#1096;&#1077;&#1088;
GenericName[uz]=&#1040;&#1091;&#1076;&#1080;&#1086; &#1084;&#1080;&#1082;&#1089;&#1077;&#1088;
GenericName[ven]=Tshitanganisi tsha mubvumo
GenericName[wa]=Maxheu d' sons
GenericName[xh]=Umxubi WokuvakalayoU
GenericName[zh_CN]=&#28151;&#38899;&#22120;
GenericName[zh_HK]=&#32882;&#38899;&#28151;&#38899;&#22120;
GenericName[zh_TW]=&#38899;&#25928;&#28151;&#38899;&#22120;
GenericName[zu]=Umxubi Womsindo
Name=KMix
Name[af]=Kmix
Name[bn]=&#2453;&#2503;-&#2478;&#2495;&#2453;&#2509;&#2488;
Name[ca]=Kmix
Name[eo]=Miksilo
Name[hi]=&#2325;&#2375;-&#2350;&#2367;&#2325;&#2381;&#2360;
Name[lv]=KMiks
Name[sv]=Kmix
Name[ta]=&#2965;&#3015;&#2990;&#3007;&#2965;&#3021;&#3000;&#3021;
Name[tg]=K&#1054;&#1084;&#1077;&#1079;&#1080;&#1096;
Name[ven]=U tanganisa ha K
X-KDE-StartupNotify=true
X-DCOP-ServiceType=Unique
Categories=Qt;KDE;AudioVideo;AudioMixer;


This is from an installation of Dapper (not an upgrade from Breezy).

---

### Post by arvs on 2006-08-27
I had the same problem using Kubuntu Dapper. I think it might have something to do with kmix starting twice, but I'm not sure at all. This is a workaround I wrote. Using this, I only get the volume thingy in the system tray at startup.

do	
```
$ sudo kate /usr/bin/startkde
```
then add this:
```
# Added myself to let kmix go to system tray at startup
dcop kmix kmix-mainwindow#1 hide
```
before these lines:
```
# finally, give the session control to the session manager
# if the KDEWM environment variable has been set, then it will be used as KDE's
# window manager instead of kwin.

```

note: I'm new to linux in general and kde in particular, so you might find a much better/cleaner workaround using this as a starting point.

---

