---
title: "Icon nano trouble"
date: 2017-05-12
forum: General Help
---

### Post by jsc12345 on 2017-05-12
Hi, Everyone!
I've recently installed a Macbuntu Icon pack, but not all the icons are to my liking. So, I started by changing the libreoffice icon (The current icon was Word) to the pages icon. Following that success, I tried to change the Google Chrome icon to that of Safari, which, sort of failed. I put in this code: ```
sudo nano /usr/share/applications/chrome.desktop
``` and then I downloaded a Safari image off the web. So then I put ```
icon=/home/****/Pictures/Safari.png
``` (Just put the stars there for privacy purposes). But now it's got this weird icon which is like a notebook with an A made out of two pencils and a ruler.
Can someone explain this?

---

### Post by Perfect Storm on 2017-05-12
Try with **menulibre** it's bit easier that way.

---

### Post by jsc12345 on 2017-05-12
> **Artificial Intelligence said:**
> Try with **menulibre** it's a bit easier that way. I don't really want to install anything. I just want to knowwhat's wrong so I can fix it.

---

### Post by deadflowr on 2017-05-12
Not sure the icon= works
Shouldn't it be Icon= with a capital I.
Sounds like the path setting is incorrect and the application is using the default "unknown" icon,
much like as if you used Ubuntu's normal icons and the icon would show the Ubuntu unknown icon, which is the grey box with a question mark in the middle.

---

### Post by jsc12345 on 2017-05-12
> **deadflowr said:**
> Not sure the icon= works
Shouldn't it be Icon= with a capital I.
Sounds like the path setting is incorrect and the application is using the default "unknown" icon,
much like as if you used Ubuntu's normal icons and the icon would show the Ubuntu unknown icon, which is the gray box with a question mark in the middle.
Well, I did copy it directly from the file explorer

---

### Post by howefield on 2017-05-12
Try putting the icon in the ~/.local/share/icons/ folder.

Then use..

```
sudo -H nautilus
```

to open the file manager and navigate to /usr/share/applications/ and right click on the chrome desktop and select properties, click on the chrome icon in the properties dialogue window and replace with the one you put in your home folder as above.

---

### Post by deadflowr on 2017-05-12
> **jsc12345 said:**
> Well, I did copy it directly from the file explorer

Sorry, I meant the full line was incorrect
instead of it reading
```
icon=/home/****/Pictures/Safari.png
```
it should read as
```
Icon=/home/****/Pictures/Safari.png
```
,also it is better to copy the file to your home's .local/share/applications folder. (/home/*&^%/.local/share/applications)
Files in /usr/share/applications can get overwritten by updates, and can cause it to lose whatever changes you make to them.
Files in the home  folder do not get overwritten by updates, so any changes you make to them will stay forever.
(Also since you have write ability to your own home folder, copying from /usr to your home folder does not require root/sudo; just right click and select copy to copy it, no root needed, if that make sense)

---

### Post by jsc12345 on 2017-05-13
> **howefield said:**
> Try putting the icon in the ~/.local/share/icons/ folder.

Then use...

```
sudo -H nautilus
```

to open the file manager and navigate to /usr/share/applications/ and right click on the chrome desktop and select properties, click on the chrome icon in the properties dialogue window and replace with the one you put in your home folder as above.When I 
when I try to move it it just says permission denided

Icon just went completely blank!

---

### Post by howefield on 2017-05-13
> **jsc12345 said:**
> when I try to move it it just says permission denided

Please be a little more explanatory, what exactly did you do to get you the error ?

---

### Post by jsc12345 on 2017-05-13
I tried to move it and it said "error moving file: permission denied

---

### Post by deadflowr on 2017-05-13
Move what?  And from where to where?
Easier to use copy, imo.

---

### Post by jsc12345 on 2017-05-13
> **deadflowr said:**
> Move what? And from where to where?
Easier to use copy, imo.
I have a MacBuntuOS package, so I TRIED to copy it into usr/share/icons/MacBuntuOS/applications/
Did I do anything wrong?

---

### Post by deadflowr on 2017-05-13
> **jsc12345 said:**
> I have a MacBuntuOS package, so I TRIED to copy it into usr/share/icons/MacBuntuOS/applications/
Did I do anything wrong?

Yes
You cannot move or copy into the system folder "/usr" without sudo/root.
You can however copy from /usr into your own home folder.
This is because you do not have the proper write permissions to write into system folders.
(Not without running with sudo or as root)

Though, I am not sure what the plan is for moving it into the icons folder. 
Or what is meant by package?

---

### Post by jsc12345 on 2017-05-13
> **deadflowr said:**
> Yes
You cannot move or copy into the system folder "/usr" without sudo/root.
You can, however, copy from /usr into your own home folder.
This is because you do not have the proper write permissions to write into system folders.
(Not without running with sudo or as root)

Though, I am not sure what the plan is for moving it into the icons folder. 
Or what is meant by package?
So what do I do? (Code please)

---

### Post by deadflowr on 2017-05-13
Sorry, was about to add this help page explaining rootsudo:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

as to what code needs to be run, depends on what the package is, really.

---

### Post by jsc12345 on 2017-05-13
> **deadflowr said:**
> Sorry, was about to add this help page explaining rootsudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

as to what code needs to be run, depends on what the package is, really.
But I know about sudo. Can you PLEASE just give me step-by-step directions?

---

### Post by deadflowr on 2017-05-13
What's the package?
Is it a .deb package or something else?

---

### Post by jsc12345 on 2017-05-14
> **deadflowr said:**
> What's the package?
Is it a .deb package or something else?
I installed it via apt-repository

---

### Post by deadflowr on 2017-05-14
I was able to play around with MacBuntu-OS icons on my 17.10 development (gnome shell) release and got the safari icon for chrome by doing these things:
1) copy the google-chrome.desktop file from /usr/share/applications to /home/me/.local/share/applications
terminal command to do that was
```
cp /usr/share/applications/google-chrome.desktop ~/.local/share/applications
```
then open the file in gedit.
(.desktop files are launchers and do not open like a regular text file would, so to open you need to either open gedit first and use the open feature, then search for the file; or simply drag and drop it from the Files app into gedit.)
I then rename the Icon=line from 
```
Icon=google-chrome
```
to 
```
Icon=web-browser
```
and saved the file.

And the icon in the launch bar and in the search menu changed automatically to the safari icon, or what one could describe as the safari icon.

As you used apt to add the icon package I would assume the icons are properly stored in the /usr/share/icons folder, which is fine.

see if any of this is helpful...

---

### Post by jsc12345 on 2017-05-15
> **deadflowr said:**
> I was able to play around with MacBuntu-OS icons on my 17.10 development (gnome shell) release and got the safari icon for chrome by doing these things:
1) copy the google-chrome.desktop file from /usr/share/applications to /home/me/.local/share/applications
terminal command to do that was
```
cp /usr/share/applications/google-chrome.desktop ~/.local/share/applications
```
then open the file in gedit.
(.desktop files are launchers and do not open like a regular text file would, so to open you need to either open gedit first and use the open feature, then search for the file; or simply drag and drop it from the Files app into gedit.)
I then rename the Icon=line from 
```
Icon=google-chrome
```
to 
```
Icon=web-browser
```
and saved the file.

And the icon in the launch bar and in the search menu changed automatically to the safari icon, or what one could describe as the safari icon.

As you used apt to add the icon package I would assume the icons are properly stored in the /usr/share/icons folder, which is fine.

see if any of this is helpful... It didn't work. Is it because A. I deleted the Ubuntu web browser or B. Because The file directory in which icons are stored is /usr/share/icons/MacBuntu-OS/apps/128.

---

### Post by deadflowr on 2017-05-15
Post the output of the .desktop file as it is now.
It can help to know what it looks like currently, perhaps something you've done to it has remained and is causing the problems.

And the /usr/share/icons folder is system-wide and all apps will be able to use whatever icons are within, so that's not the problem.
(Unless you've fiddle with the folders permissions or something)

---

### Post by jsc12345 on 2017-05-18
> **deadflowr said:**
> Post the output of the .desktop file as it is now.
It can help to know what it looks like currently, perhaps something you've done to it has remained and is causing the problems.

And the /usr/share/icons folder is system-wide and all apps will be able to use whatever icons are within, so that's not the problem.
(Unless you've fiddled with the folders permissions or something)What do you mean, output?

---

### Post by deadflowr on 2017-05-18
> **jsc12345 said:**
> What do you mean, output?

What the contents of the .desktop file look like.

---

### Post by jsc12345 on 2017-05-19
> **deadflowr said:**
> What the contents of the .desktop file look like.```
[Desktop Entry]Version=1.0
Name=Google Chrome
# Only KDE 4 seems to use GenericName, so we reuse the KDE strings.
# From Ubuntu's language-pack-kde-XX-base packages, version 9.04-20090413.
GenericName=Web Browser
GenericName[ar]=&#1605;&#1578;&#1589;&#1601;&#1581; &#1575;&#1604;&#1588;&#1576;&#1603;&#1577;
GenericName[bg]=&#1059;&#1077;&#1073; &#1073;&#1088;&#1072;&#1091;&#1079;&#1098;&#1088;
GenericName[ca]=Navegador web
GenericName[cs]=WWW prohlíže&#269;
GenericName[da]=Browser
GenericName[de]=Web-Browser
GenericName[el]=&#928;&#949;&#961;&#953;&#951;&#947;&#951;&#964;&#942;&#962; &#953;&#963;&#964;&#959;&#973;
GenericName[en_GB]=Web Browser
GenericName[es]=Navegador web
GenericName[et]=Veebibrauser
GenericName[fi]=WWW-selain
GenericName[fr]=Navigateur Web
GenericName[gu]=&#2741;&#2759;&#2732; &#2732;&#2765;&#2736;&#2750;&#2697;&#2717;&#2736;
GenericName[he]=&#1491;&#1508;&#1491;&#1508;&#1503; &#1488;&#1497;&#1504;&#1496;&#1512;&#1504;&#1496;
GenericName[hi]=&#2357;&#2375;&#2348; &#2348;&#2381;&#2352;&#2366;&#2313;&#2332;&#2364;&#2352;
GenericName[hu]=Webböngész&#337;
GenericName[it]=Browser Web
GenericName[ja]=&#12454;&#12455;&#12502;&#12502;&#12521;&#12454;&#12470;
GenericName[kn]=&#3228;&#3262;&#3250; &#3253;&#3264;&#3221;&#3277;&#3255;&#3221;
GenericName[ko]=&#50937; &#48652;&#46972;&#50864;&#51200;
GenericName[lt]=Žiniatinklio naršykl&#279;
GenericName[lv]=T&#299;mek&#316;a p&#257;rl&#363;ks
GenericName[ml]=&#3381;&#3398;&#3372;&#3405; &#3372;&#3405;&#3376;&#3404;&#3384;&#3376;&#3405;*
GenericName[mr]=&#2357;&#2375;&#2348; &#2348;&#2381;&#2352;&#2366;&#2314;&#2332;&#2352;
GenericName[nb]=Nettleser
GenericName[nl]=Webbrowser
GenericName[pl]=Przegl&#261;darka WWW
GenericName[pt]=Navegador Web
GenericName[pt_BR]=Navegador da Internet
GenericName[ro]=Navigator de Internet
GenericName[ru]=&#1042;&#1077;&#1073;-&#1073;&#1088;&#1072;&#1091;&#1079;&#1077;&#1088;
GenericName[sl]=Spletni brskalnik
GenericName[sv]=Webbläsare
GenericName[ta]=&#2951;&#2979;&#3016;&#2991; &#2953;&#2994;&#3006;&#2997;&#3007;
GenericName[th]=&#3648;&#3623;&#3655;&#3610;&#3648;&#3610;&#3619;&#3634;&#3623;&#3660;&#3648;&#3595;&#3629;&#3619;&#3660;
GenericName[tr]=Web Taray&#305;c&#305;
GenericName[uk]=&#1053;&#1072;&#1074;&#1110;&#1075;&#1072;&#1090;&#1086;&#1088; &#1058;&#1077;&#1085;&#1077;&#1090;
GenericName[zh_CN]=&#32593;&#39029;&#27983;&#35272;&#22120;
GenericName[zh_HK]=&#32178;&#38913;&#28687;&#35261;&#22120;
GenericName[zh_TW]=&#32178;&#38913;&#28687;&#35261;&#22120;
# Not translated in KDE, from Epiphany 2.26.1-0ubuntu1.
GenericName[bn]=&#2451;&#2527;&#2503;&#2476; &#2476;&#2509;&#2480;&#2494;&#2441;&#2460;&#2494;&#2480;
GenericName[fil]=Web Browser
GenericName[hr]=Web preglednik
GenericName[id]=Browser Web
GenericName[or]=&#2835;&#2893;&#2860;&#2887;&#2860; &#2860;&#2893;&#2864;&#2878;&#2825;&#2844;&#2864;
GenericName[sk]=WWW prehliada&#269;
GenericName[sr]=&#1048;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090; &#1087;&#1088;&#1077;&#1075;&#1083;&#1077;&#1076;&#1085;&#1080;&#1082;
GenericName[te]=&#3118;&#3129;&#3134;&#3108;&#3122; &#3077;&#3112;&#3149;&#3125;&#3143;&#3127;&#3135;
GenericName[vi]=B&#7897; duy&#7879;t Web
# Gnome and KDE 3 uses Comment.
Comment=Access the Internet
Comment[ar]=&#1575;&#1604;&#1583;&#1582;&#1608;&#1604; &#1573;&#1604;&#1609; &#1575;&#1604;&#1573;&#1606;&#1578;&#1585;&#1606;&#1578;
Comment[bg]=&#1044;&#1086;&#1089;&#1090;&#1098;&#1087; &#1076;&#1086; &#1080;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;
Comment[bn]=&#2439;&#2472;&#2509;&#2463;&#2494;&#2480;&#2472;&#2503;&#2463;&#2463;&#2495; &#2437;&#2509;&#2479;&#2494;&#2453;&#2509;&#2488;&#2503;&#2488; &#2453;&#2480;&#2497;&#2472;
Comment[ca]=Accedeix a Internet
Comment[cs]=P&#345;ístup k internetu
Comment[da]=Få adgang til internettet
Comment[de]=Internetzugriff
Comment[el]=&#928;&#961;&#972;&#963;&#946;&#945;&#963;&#951; &#963;&#964;&#959; &#916;&#953;&#945;&#948;&#943;&#954;&#964;&#965;&#959;
Comment[en_GB]=Access the Internet
Comment[es]=Accede a Internet.
Comment[et]=Pääs Internetti
Comment[fi]=Käytä internetiä
Comment[fil]=I-access ang Internet
Comment[fr]=Accéder à Internet
Comment[gu]=&#2695;&#2690;&#2719;&#2736;&#2728;&#2759;&#2719; &#2701;&#2709;&#2765;&#2744;&#2759;&#2744; &#2709;&#2736;&#2763;
Comment[he]=&#1490;&#1497;&#1513;&#1492; &#1488;&#1500; &#1492;&#1488;&#1497;&#1504;&#1496;&#1512;&#1504;&#1496;
Comment[hi]=&#2311;&#2306;&#2335;&#2352;&#2344;&#2375;&#2335; &#2340;&#2325; &#2346;&#2361;&#2369;&#2306;&#2330; &#2360;&#2381;&#2341;&#2366;&#2346;&#2367;&#2340; &#2325;&#2352;&#2375;&#2306;
Comment[hr]=Pristup Internetu
Comment[hu]=Internetelérés
Comment[id]=Akses Internet
Comment[it]=Accesso a Internet
Comment[ja]=&#12452;&#12531;&#12479;&#12540;&#12493;&#12483;&#12488;&#12395;&#12450;&#12463;&#12475;&#12473;
Comment[kn]=&#3207;&#3202;&#3231;&#3248;&#3277;&#3240;&#3270;&#3231;&#3277; &#3205;&#3240;&#3277;&#3240;&#3265; &#3242;&#3277;&#3248;&#3253;&#3271;&#3254;&#3263;&#3256;&#3263;
Comment[ko]=&#51064;&#53552;&#45367; &#50672;&#44208;
Comment[lt]=Interneto prieiga
Comment[lv]=Piek&#316;&#363;t internetam
Comment[ml]=&#3335;&#3368;&#3405;&#3377;&#3376;&#3405;**&#3368;&#3398;&#3377;&#3405;&#3377;&#3405; &#3334;&#3349;&#3405;*&#3384;&#3384;&#3405; &#3354;&#3398;&#3375;&#3405;&#3375;&#3393;&#3349;
Comment[mr]=&#2311;&#2306;&#2335;&#2352;&#2344;&#2375;&#2335;&#2350;&#2343;&#2381;&#2351;&#2375; &#2346;&#2381;&#2352;&#2357;&#2375;&#2358; &#2325;&#2352;&#2366;
Comment[nb]=Gå til Internett
Comment[nl]=Verbinding maken met internet
Comment[or]=&#2823;&#2851;&#2893;&#2847;&#2864;&#2893;&#2856;&#2887;&#2847;&#2893; &#2858;&#2893;&#2864;&#2860;&#2887;&#2870; &#2837;&#2864;&#2856;&#2893;&#2852;&#2881;
Comment[pl]=Skorzystaj z internetu
Comment[pt]=Aceder à Internet
Comment[pt_BR]=Acessar a internet
Comment[ro]=Accesa&#355;i Internetul
Comment[ru]=&#1044;&#1086;&#1089;&#1090;&#1091;&#1087; &#1074; &#1048;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;
Comment[sk]=Prístup do siete Internet
Comment[sl]=Dostop do interneta
Comment[sr]=&#1055;&#1088;&#1080;&#1089;&#1090;&#1091;&#1087;&#1080;&#1090;&#1077; &#1048;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;&#1091;
Comment[sv]=Gå ut på Internet
Comment[ta]=&#2951;&#2979;&#3016;&#2991;&#2980;&#3021;&#2980;&#3016; &#2949;&#2979;&#3009;&#2965;&#3009;&#2980;&#2994;&#3021;
Comment[te]=&#3079;&#3074;&#3103;&#3120;&#3149;&#3112;&#3142;&#3103;&#3149;*&#3112;&#3137; &#3078;&#3093;&#3149;&#3128;&#3142;&#3128;&#3149; &#3098;&#3142;&#3119;&#3149;&#3119;&#3074;&#3105;&#3135;
Comment[th]=&#3648;&#3586;&#3657;&#3634;&#3606;&#3638;&#3591;&#3629;&#3636;&#3609;&#3648;&#3607;&#3629;&#3619;&#3660;&#3648;&#3609;&#3655;&#3605;
Comment[tr]=&#304;nternet'e eri&#351;in
Comment[uk]=&#1044;&#1086;&#1089;&#1090;&#1091;&#1087; &#1076;&#1086; &#1030;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;&#1091;
Comment[vi]=Truy c&#7853;p Internet
Comment[zh_CN]=&#35775;&#38382;&#20114;&#32852;&#32593;
Comment[zh_HK]=&#36899;&#32218;&#21040;&#32178;&#38555;&#32178;&#36335;
Comment[zh_TW]=&#36899;&#32218;&#21040;&#32178;&#38555;&#32178;&#36335;
Exec=/usr/bin/google-chrome-stable %U
Terminal=false
Icon='/home/john/Pictures/Safari.png'    
Type=Application
Categories=Network;WebBrowser;
MimeType=text/html;text/xml;application/xhtml_xml;image/webp;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;
Actions=NewWindow;NewPrivateWindow;


[Desktop Action NewWindow]
Name=New Window
Name[am]=&#4768;&#4850;&#4661; &#4632;&#4661;&#4782;&#4725;
Name[ar]=&#1606;&#1575;&#1601;&#1584;&#1577; &#1580;&#1583;&#1610;&#1583;&#1577;
Name[bg]=&#1053;&#1086;&#1074; &#1087;&#1088;&#1086;&#1079;&#1086;&#1088;&#1077;&#1094;
Name[bn]=&#2472;&#2468;&#2497;&#2472; &#2441;&#2439;&#2472;&#2509;&#2465;&#2507;
Name[ca]=Finestra nova
Name[cs]=Nové okno
Name[da]=Nyt vindue
Name[de]=Neues Fenster
Name[el]=&#925;&#941;&#959; &#928;&#945;&#961;&#940;&#952;&#965;&#961;&#959;
Name[en_GB]=New Window
Name[es]=Nueva ventana
Name[et]=Uus aken
Name[fa]=&#1662;&#1606;&#1580;&#1585;&#1607; &#1580;&#1583;&#1740;&#1583;
Name[fi]=Uusi ikkuna
Name[fil]=New Window
Name[fr]=Nouvelle fenêtre
Name[gu]=&#2728;&#2741;&#2752; &#2741;&#2751;&#2690;&#2721;&#2763;
Name[hi]=&#2344;&#2312; &#2357;&#2367;&#2306;&#2337;&#2379;
Name[hr]=Novi prozor
Name[hu]=Új ablak
Name[id]=Jendela Baru
Name[it]=Nuova finestra
Name[iw]=&#1495;&#1500;&#1493;&#1503; &#1495;&#1491;&#1513;
Name[ja]=&#26032;&#35215;&#12454;&#12452;&#12531;&#12489;&#12454;
Name[kn]=&#3257;&#3274;&#3256; &#3253;&#3263;&#3202;&#3233;&#3274;
Name[ko]=&#49352; &#52285;
Name[lt]=Naujas langas
Name[lv]=Jauns logs
Name[ml]=&#3370;&#3393;&#3364;&#3391;&#3375; &#3381;&#3391;&#3368;&#3405;*&#3361;&#3403;
Name[mr]=&#2344;&#2357;&#2368;&#2344; &#2357;&#2367;&#2306;&#2337;&#2379;
Name[nl]=Nieuw venster
Name[no]=Nytt vindu
Name[pl]=Nowe okno
Name[pt]=Nova janela
Name[pt_BR]=Nova janela
Name[ro]=Fereastr&#259; nou&#259;
Name[ru]=&#1053;&#1086;&#1074;&#1086;&#1077; &#1086;&#1082;&#1085;&#1086;
Name[sk]=Nové okno
Name[sl]=Novo okno
Name[sr]=&#1053;&#1086;&#1074;&#1080; &#1087;&#1088;&#1086;&#1079;&#1086;&#1088;
Name[sv]=Nytt fönster
Name[sw]=Dirisha Jipya
Name[ta]=&#2986;&#3009;&#2980;&#3007;&#2991; &#2970;&#3006;&#2995;&#2992;&#2990;&#3021;
Name[te]=&#3093;&#3149;&#3120;&#3146;&#3108;&#3149;&#3108; &#3125;&#3135;&#3074;&#3105;&#3147;
Name[th]=&#3627;&#3609;&#3657;&#3634;&#3605;&#3656;&#3634;&#3591;&#3651;&#3627;&#3617;&#3656;
Name[tr]=Yeni Pencere
Name[uk]=&#1053;&#1086;&#1074;&#1077; &#1074;&#1110;&#1082;&#1085;&#1086;
Name[vi]=C&#7917;a s&#7893; M&#7899;i
Name[zh_CN]=&#26032;&#24314;&#31383;&#21475;
Name[zh_TW]=&#38283;&#26032;&#35222;&#31383;
Exec=/usr/bin/google-chrome-stable


[Desktop Action NewPrivateWindow]
Name=New Incognito Window
Name[ar]=&#1606;&#1575;&#1601;&#1584;&#1577; &#1580;&#1583;&#1610;&#1583;&#1577; &#1604;&#1604;&#1578;&#1589;&#1601;&#1581; &#1575;&#1604;&#1605;&#1578;&#1582;&#1601;&#1610;
Name[bg]=&#1053;&#1086;&#1074; &#1087;&#1088;&#1086;&#1079;&#1086;&#1088;&#1077;&#1094; „&#1080;&#1085;&#1082;&#1086;&#1075;&#1085;&#1080;&#1090;&#1086;“
Name[bn]=&#2472;&#2468;&#2497;&#2472; &#2459;&#2470;&#2509;&#2478;&#2476;&#2503;&#2486;&#2496; &#2441;&#2439;&#2472;&#2509;&#2465;&#2507;
Name[ca]=Finestra d'incògnit nova
Name[cs]=Nové anonymní okno
Name[da]=Nyt inkognitovindue
Name[de]=Neues Inkognito-Fenster
Name[el]=&#925;&#941;&#959; &#960;&#945;&#961;&#940;&#952;&#965;&#961;&#959; &#947;&#953;&#945; &#945;&#957;&#974;&#957;&#965;&#956;&#951; &#960;&#949;&#961;&#953;&#942;&#947;&#951;&#963;&#951;
Name[en_GB]=New Incognito window
Name[es]=Nueva ventana de incógnito
Name[et]=Uus inkognito aken
Name[fa]=&#1662;&#1606;&#1580;&#1585;&#1607; &#1580;&#1583;&#1740;&#1583; &#1581;&#1575;&#1604;&#1578; &#1606;&#1575;&#1588;&#1606;&#1575;&#1587;
Name[fi]=Uusi incognito-ikkuna
Name[fil]=Bagong Incognito window
Name[fr]=Nouvelle fenêtre de navigation privée
Name[gu]=&#2728;&#2741;&#2752; &#2715;&#2753;&#2730;&#2752; &#2741;&#2751;&#2690;&#2721;&#2763;
Name[hi]=&#2344;&#2312; &#2327;&#2369;&#2346;&#2381;&#2340; &#2357;&#2367;&#2306;&#2337;&#2379;
Name[hr]=Novi anoniman prozor
Name[hu]=Új Inkognitóablak
Name[id]=Jendela Penyamaran baru
Name[it]=Nuova finestra di navigazione in incognito
Name[iw]=&#1495;&#1500;&#1493;&#1503; &#1495;&#1491;&#1513; &#1500;&#1490;&#1500;&#1497;&#1513;&#1492; &#1489;&#1505;&#1514;&#1512;
Name[ja]=&#26032;&#12375;&#12356;&#12471;&#12540;&#12463;&#12524;&#12483;&#12488; &#12454;&#12451;&#12531;&#12489;&#12454;
Name[kn]=&#3257;&#3274;&#3256; &#3205;&#3228;&#3277;&#3230;&#3262;&#3236; &#3253;&#3263;&#3202;&#3233;&#3275;
Name[ko]=&#49352; &#49884;&#53356;&#47551; &#52285;
Name[lt]=Naujas inkognito langas
Name[lv]=Jauns inkognito rež&#299;ma logs
Name[ml]=&#3370;&#3393;&#3364;&#3391;&#3375; &#3381;&#3399;&#3383; &#3370;&#3405;&#3376;&#3354;&#3405;&#3355;&#3368;&#3405;&#3368; &#3381;&#3391;&#3368;&#3405;*&#3361;&#3403;
Name[mr]=&#2344;&#2357;&#2368;&#2344; &#2327;&#2369;&#2346;&#2381;&#2340; &#2357;&#2367;&#2306;&#2337;&#2379;
Name[nl]=Nieuw incognitovenster
Name[no]=Nytt inkognitovindu
Name[pl]=Nowe okno incognito
Name[pt]=Nova janela de navegação anónima
Name[pt_BR]=Nova janela anônima
Name[ro]=Fereastr&#259; nou&#259; incognito
Name[ru]=&#1053;&#1086;&#1074;&#1086;&#1077; &#1086;&#1082;&#1085;&#1086; &#1074; &#1088;&#1077;&#1078;&#1080;&#1084;&#1077; &#1080;&#1085;&#1082;&#1086;&#1075;&#1085;&#1080;&#1090;&#1086;
Name[sk]=Nové okno inkognito
Name[sl]=Novo okno brez beleženja zgodovine
Name[sr]=&#1053;&#1086;&#1074;&#1080; &#1087;&#1088;&#1086;&#1079;&#1086;&#1088; &#1079;&#1072; &#1087;&#1088;&#1077;&#1075;&#1083;&#1077;&#1076;&#1072;&#1114;&#1077; &#1073;&#1077;&#1079; &#1072;&#1088;&#1093;&#1080;&#1074;&#1080;&#1088;&#1072;&#1114;&#1072;
Name[sv]=Nytt inkognitofönster
Name[ta]=&#2986;&#3009;&#2980;&#3007;&#2991; &#2990;&#2993;&#3016;&#2984;&#3007;&#2994;&#3016;&#2970;&#3021; &#2970;&#3006;&#2995;&#2992;&#2990;&#3021;
Name[te]=&#3093;&#3149;&#3120;&#3146;&#3108;&#3149;&#3108; &#3077;&#3100;&#3149;&#3102;&#3134;&#3108; &#3125;&#3135;&#3074;&#3105;&#3147;
Name[th]=&#3627;&#3609;&#3657;&#3634;&#3605;&#3656;&#3634;&#3591;&#3651;&#3627;&#3617;&#3656;&#3607;&#3637;&#3656;&#3652;&#3617;&#3656;&#3619;&#3632;&#3610;&#3640;&#3605;&#3633;&#3623;&#3605;&#3609;
Name[tr]=Yeni Gizli pencere
Name[uk]=&#1053;&#1086;&#1074;&#1077; &#1074;&#1110;&#1082;&#1085;&#1086; &#1074; &#1088;&#1077;&#1078;&#1080;&#1084;&#1110; &#1072;&#1085;&#1086;&#1085;&#1110;&#1084;&#1085;&#1086;&#1075;&#1086; &#1087;&#1077;&#1088;&#1077;&#1075;&#1083;&#1103;&#1076;&#1091;
Name[vi]=C&#7917;a s&#7893; &#7849;n danh m&#7899;i
Name[zh_CN]=&#26032;&#24314;&#38544;&#36523;&#31383;&#21475;
Name[zh_TW]=&#26032;&#22686;&#28961;&#30165;&#24335;&#35222;&#31383;
Exec=/usr/bin/google-chrome-stable --incognito
```

---

### Post by deadflowr on 2017-05-19
Remove the quotes from the Icon= path

---

### Post by jsc12345 on 2017-05-19
> **deadflowr said:**
> Remove the quotes from the Icon= path
I will try but I think last time I did it had bad results.

---

### Post by deadflowr on 2017-05-19
Make sure it's one continuous line
Icon=/path
no space after the = sign.

---

### Post by jsc12345 on 2017-05-19
> **deadflowr said:**
> Make sure it's one continuous line
Icon=/path
no space after the = sign. do I need to put in ```
Icon=/Path
``` or is that just an example?

---

### Post by deadflowr on 2017-05-19
Just a generic example.
(unless you happen to have an image called Path in the top level of the file system...)

---

### Post by jsc12345 on 2017-05-19
ok

---

### Post by jsc12345 on 2017-05-19
Nothing happened

---

### Post by deadflowr on 2017-05-19
This is unity desktop, right?
check the dash search for chrome.
did that change?

---

### Post by jsc12345 on 2017-05-19
It's Gnome but I searched for it in Activities and it didn't work.

---

