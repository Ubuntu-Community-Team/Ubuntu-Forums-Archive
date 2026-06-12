---
title: "Help! I broke Zip files!"
date: 2007-09-06
forum: General Help
---

### Post by DarkGob on 2007-09-06
I'm not sure what I did but I can no longer open Zip files.  It says there's no application suitable for running them.  Also, the Computer icon on my desktop has turned into nautilus-computer.desktop; it opens in gedit but obviously that's worthless.

What I've done recently:
1) Installed Mathematica 6.0 with the command "bash MathInstaller".
2) Fiddling around with gDesklets.  I'm pretty sure I didn't do anything today that I didn't do when I was fiddling around last night, and I'm...let's say 95% sure this problem is new today.

Any ideas?

---

### Post by jim_p on 2007-09-06
Can you post a screenshot or the code that apears in gedit wehn you open My Computer?

As for the zip files, you can right click a .zip file, go to Properties and the "Open with" tab
and add some program like File-Roller or Ark or TXarchiver, depending which you have installed or like the most.
You dont have to know the exact path to the application, just write it in the box and linux will find it ;)

---

### Post by notwen on 2007-09-06
Right click on any file, go to Properties.  From there go to the Open With tab and select the appropriate application.  As far as your .desktop file, I'm not on my Linux PC at the moment and cannot which application uses *.desktop files by default.

---

### Post by sdowney717 on 2007-09-06
go intoi synaptic and reinstall file roller

an archive manager for GNOME 
File-roller is an archive manager for the GNOME environment. It allows you to:

 * Create and modify archives.
 * View the content of an archive.
 * View a file contained in an archive.
 * Extract files from the archive.

File-roller supports the following formats:
 * Tar (.tar) archives, including those compressed with
   gzip (.tar.gz, .tgz), bzip (.tar.bz, .tbz), bzip2 (.tar.bz2, .tbz2),
   compress (.tar.Z, .taz) and lzop (.tar.lzo, .tzo)
 * Zip archives (.zip)
 * Jar archives (.jar, .ear, .war)
 * 7z archives (.7z)
 * iso9660 CD images (.iso)
 * Lha archives (.lzh)
 * Single files compressed with gzip (.gz), bzip (.bz), bzip2 (.bz2),
   compress (.Z) and lzop (.lzo)

File-roller doesn't perform archive operations by itself, but relies on
standard tools for this.

Homepage: [http://fileroller.sourceforge.net](http://fileroller.sourceforge.net)

---

### Post by DarkGob on 2007-09-06
> **jim_p said:**
> Can you post a screenshot or the code that apears in gedit wehn you open My Computer?

I neglected to mention, the icon has also changed, from the computer icon to a generic "I don't know what kind of file this is" icon.

```
[Desktop Entry]
Encoding=UTF-8
Name=Computer
Name[af]=Rekenaar
Name[ar]=&#1575;&#1604;&#1581;&#1575;&#1587;&#1608;&#1576;
Name[az]=Kompüter
Name[be]=&#1050;&#1072;&#1084;&#1087;&#1091;&#1090;&#1072;&#1088;
Name[bg]=&#1058;&#1086;&#1079;&#1080; &#1082;&#1086;&#1084;&#1087;&#1102;&#1090;&#1098;&#1088;
Name[bn]=&#2453;&#2478;&#2509;&#2474;&#2495;&#2441;&#2463;&#2494;&#2480;
Name[bn_IN]=&#2453;&#2478;&#2509;&#2474;&#2495;&#2441;&#2463;&#2494;&#2480;
Name[br]=Urzhiataer
Name[bs]=Ra&#269;unar
Name[ca]=Ordinador
Name[cs]=Po&#269;íta&#269;
Name[cy]=Cyfrifiadur
Name[da]=Maskine
Name[de]=Computer
Name[dz]=&#3906;&#4019;&#3964;&#3906;&#3851;&#3938;&#3954;&#3906;
Name[el]=&#933;&#960;&#959;&#955;&#959;&#947;&#953;&#963;&#964;&#942;&#962;
Name[en_CA]=Computer
Name[en_GB]=Computer
Name[eo]=Komputilo
Name[es]=Equipo
Name[et]=Arvuti
Name[eu]=Ordenagailua
Name[fa]=&#1705;&#1575;&#1605;&#1662;&#1740;&#1608;&#1578;&#1585;
Name[fi]=Tietokone
Name[fr]=Poste de travail
Name[ga]=Ríomhaire
Name[gl]=Computador
Name[gu]=&#2709;&#2734;&#2765;&#2730;&#2765;&#2735;&#2754;&#2719;&#2736;
Name[he]=&#1502;&#1495;&#1513;&#1489;
Name[hi]=&#2325;&#2350;&#2381;&#2346;&#2381;&#2351;&#2370;&#2335;&#2352;
Name[hr]=Ra&#269;unalo
Name[hu]=Számítógép
Name[hy]=&#1344;&#1377;&#1396;&#1377;&#1391;&#1377;&#1408;&#1379;&#1387;&#1401;
Name[id]=Komputer
Name[it]=Computer
Name[ja]=&#12467;&#12531;&#12500;&#12517;&#12540;&#12479;
Name[ka]=&#4313;&#4317;&#4315;&#4318;&#4312;&#4323;&#4322;&#4308;&#4320;&#4312;
Name[ko]=&#52980;&#54504;&#53552;
Name[ku]=Komputer
Name[lt]=Kompiuteris
Name[lv]=Dators
Name[mg]=solosaina
Name[mi]=Te Rorohiko
Name[mk]=&#1050;&#1086;&#1084;&#1087;&#1112;&#1091;&#1090;&#1077;&#1088;
Name[ml]=&#3349;&#3330;&#3370;&#3405;&#3375;&#3394;&#3359;&#3405;&#3359;&#3376;&#3405;*
Name[mn]=&#1090;&#1086;&#1086;&#1094;&#1086;&#1086;&#1083;&#1091;&#1091;&#1088;
Name[ms]=Komputer
Name[nb]=Datamaskin
Name[ne]=&#2325;&#2350;&#2381;&#2346;&#2381;&#2351;&#2369;&#2335;&#2352;
Name[nl]=Computer
Name[nn]=Datamaskin
Name[nso]=Khomphuthara
Name[or]=&#2837;&#2862;&#2893;&#2858;&#2881;&#2847;&#2864;
Name[pa]=&#2581;&#2672;&#2602;&#2623;&#2570;&#2591;&#2608;
Name[pl]=Komputer
Name[pt]=Computador
Name[pt_BR]=Computador
Name[ro]=Computer
Name[ru]=&#1050;&#1086;&#1084;&#1087;&#1100;&#1102;&#1090;&#1077;&#1088;
Name[sk]=Po&#269;íta&#269;
Name[sl]=Ra&#269;unalnik
Name[sq]=Kompjuteri
Name[sr]=&#1056;&#1072;&#1095;&#1091;&#1085;&#1072;&#1088;
Name[sr@Latn]=Ra&#269;unar
Name[sr@ije]=&#1056;&#1072;&#1095;&#1091;&#1085;&#1072;&#1088;
Name[sv]=Dator
Name[ta]=&#2965;&#2979;&#3007;&#2986;&#3021;&#2986;&#3018;&#2993;&#3007;
Name[te]=&#3093;&#3074;&#3114;&#3149;&#3119;&#3138;&#3103;&#3120;&#3149;
Name[th]=&#3588;&#3629;&#3617;&#3614;&#3636;&#3623;&#3648;&#3605;&#3629;&#3619;&#3660;
Name[tk]=_Kampýuter
Name[tr]=Bilgisayar
Name[uk]=&#1050;&#1086;&#1084;&#1087;'&#1102;&#1090;&#1077;&#1088;
Name[vi]=Máy tính
Name[xh]=Ikhompyutha
Name[zh_CN]=&#35745;&#31639;&#26426;
Name[zh_HK]=&#38651;&#33126;
Name[zh_TW]=&#38651;&#33126;
Name[zu]=Isiga-nyezi
Comment=Browse all local and remote disks and folders accessible from this computer
Comment[ar]=&#1578;&#1589;&#1601;&#1617;&#1581; &#1603;&#1604; &#1575;&#1604;&#1571;&#1602;&#1585;&#1575;&#1589; &#1608;&#1575;&#1604;&#1605;&#1580;&#1604;&#1617;&#1583;&#1575;&#1578; &#1575;&#1604;&#1605;&#1581;&#1604;&#1617;&#1610;&#1577; &#1608;&#1575;&#1604;&#1576;&#1593;&#1610;&#1583;&#1577; &#1575;&#1604;&#1605;&#1578;&#1575;&#1581;&#1577; &#1604;&#1607;&#1584;&#1575; &#1575;&#1604;&#1581;&#1575;&#1587;&#1608;&#1576;
Comment[be]=&#1042;&#1072;&#1085;&#1076;&#1088;&#1072;&#1074;&#1072;&#1094;&#1100; &#1087;&#1072; &#1084;&#1103;&#1089;&#1094;&#1086;&#1074;&#1099;&#1093; &#1110; &#1072;&#1076;&#1076;&#1072;&#1083;&#1077;&#1085;&#1099;&#1093; &#1076;&#1099;&#1089;&#1082;&#1072;&#1093; &#1110; &#1090;&#1101;&#1095;&#1082;&#1072;&#1093;, &#1076;&#1072;&#1089;&#1090;&#1091;&#1087;&#1085;&#1099;&#1093; &#1079; &#1075;&#1101;&#1090;&#1072;&#1075;&#1072; &#1082;&#1072;&#1084;&#1087;&#1091;&#1090;&#1072;&#1088;&#1072;
Comment[bg]=&#1055;&#1088;&#1077;&#1075;&#1083;&#1077;&#1076; &#1085;&#1072; &#1074;&#1089;&#1080;&#1095;&#1082;&#1080; &#1083;&#1086;&#1082;&#1072;&#1083;&#1085;&#1080; &#1080; &#1086;&#1090;&#1076;&#1072;&#1083;&#1077;&#1095;&#1077;&#1085;&#1080; &#1076;&#1080;&#1089;&#1082;&#1086;&#1074;&#1077; &#1080; &#1087;&#1072;&#1087;&#1082;&#1080; &#1076;&#1086;&#1089;&#1090;&#1098;&#1087;&#1085;&#1080; &#1086;&#1090; &#1090;&#1086;&#1079;&#1080; &#1082;&#1086;&#1084;&#1087;&#1102;&#1090;&#1098;&#1088;.
Comment[ca]=Navegueu tots els discs i carpetes locals o remotes accessibles de d'aquest ordinador
Comment[cs]=Procházet všechny místní a vzdálené disky a složky dostupné z tohoto po&#269;íta&#269;e
Comment[da]=Gennemse alle lokale og eksterne diske og mapper der kan tilgås fra denne computer
Comment[de]=Alle lokalen und entfernten Datenträger und Ordner, die verfügbar sind, durchsuchen
Comment[dz]=&#3936;&#3851;&#3923;&#3954;&#3851;&#3906;&#4019;&#3964;&#3906;&#3851;&#3938;&#3954;&#3906;&#3851;&#3936;&#3921;&#3954;&#3851;&#3939;&#3942;&#3851;&#3936;&#3931;&#3956;&#3939;&#3851;&#3942;&#4004;&#4017;&#3964;&#3921;&#3851;&#3936;&#3926;&#3921;&#3851;&#3926;&#3919;&#3956;&#3926;&#3851;&#3924;&#3936;&#3954;&#3851; &#3913;&#3962;&#3851;&#3906;&#3923;&#3942;&#3851;&#3921;&#3908;&#3851;&#3920;&#3906;&#3851;&#3938;&#3954;&#3908;&#3851;&#3906;&#3954;&#3851;&#3916;&#3954;&#3904;&#3942;&#3954;&#3851;&#3921;&#3908;&#3851; &#3942;&#4003;&#3964;&#3921;&#3851;&#3936;&#3931;&#3954;&#3923;&#3851;&#3930;&#3956;&#3851; &#3926;&#3938;&#4001;&#3851;&#3936;&#3930;&#3964;&#3939;&#3851;&#3936;&#3926;&#3921;&#3851;
Comment[en_CA]=Browse all local and remote disks and folders accessible from this computer
Comment[en_GB]=Browse all local and remote disks and folders accessible from this computer
Comment[es]=Examina todos los discos remotos y carpetas accesibles desde este equipo
Comment[et]=Kõikide kohalike ja kaugelasetsevate kaustade ning ketaste sirvimine
Comment[eu]=Arakatu lokaleko disko eta karpetak, eta baita ordenagilu honetatik sarbide daitezkeen urrunekoak ere
Comment[fi]=Selaa tältä tietokoneelta käytettävissä olevia paikallisia ja etäkansioita
Comment[fr]=Parcourir tous les disques locaux et distants ainsi que les dossiers accessibles depuis cet ordinateur
Comment[gl]=Examina todos os discos remotos e cartafoles accesibles neste computador
Comment[gu]=&#2694; &#2709;&#2734;&#2765;&#2730;&#2765;&#2735;&#2754;&#2719;&#2736;&#2734;&#2750;&#2690;&#2725;&#2752; &#2744;&#2753;&#2738;&#2733; &#2732;&#2727;&#2752; &#2744;&#2765;&#2725;&#2750;&#2728;&#2751;&#2709; &#2693;&#2728;&#2759; &#2726;&#2754;&#2736;&#2744;&#2765;&#2725; &#2721;&#2751;&#2744;&#2765;&#2709;&#2763; &#2693;&#2728;&#2759; &#2731;&#2763;&#2738;&#2765;&#2721;&#2736;&#2763; &#2732;&#2765;&#2736;&#2750;&#2697;&#2717; &#2709;&#2736;&#2763;
Comment[he]=&#1506;&#1497;&#1497;&#1503; &#1489;&#1499;&#1500; &#1492;&#1514;&#1497;&#1511;&#1497;&#1493;&#1514; &#1493;&#1492;&#1491;&#1497;&#1505;&#1511;&#1497;&#1501; &#1492;&#1502;&#1511;&#1493;&#1502;&#1497;&#1497;&#1501; &#1493;&#1492;&#1502;&#1512;&#1493;&#1495;&#1511;&#1497;&#1501; &#1492;&#1504;&#1490;&#1497;&#1513;&#1497;&#1501; &#1502;&#1502;&#1495;&#1513;&#1489; &#1494;&#1492;
Comment[hu]=A számítógépr&#337;l elérhet&#337; összes helyi és távoli lemez és mappa tallózása
Comment[it]=Esplora tutti i dischi e cartelle locali e remoti accessibili da questo computer
Comment[ja]=&#12371;&#12398;&#12467;&#12531;&#12500;&#12517;&#12540;&#12479;&#12363;&#12425;&#12450;&#12463;&#12475;&#12473;&#12391;&#12365;&#12427;&#20840;&#12390;&#12398;&#12487;&#12451;&#12473;&#12463;&#12392;&#12501;&#12457;&#12523;&#12480;&#12434;&#21442;&#29031;&#12375;&#12414;&#12377;
Comment[ko]=&#51060; &#52980;&#54504;&#53552;&#50640;&#49436; &#51217;&#44540;&#54624; &#49688; &#51080;&#45716; &#47784;&#46304; &#47196;&#52972; &#48143; &#50896;&#44201; &#46356;&#49828;&#53356;&#50752; &#54260;&#45908;&#47484; &#52286;&#50500;&#48389;&#45768;&#45796;
Comment[lt]=Naršyti visus vietinius ir nutolusius diskus ir aplankus, prieinamus iš šio kompiuterio
Comment[lv]=P&#257;rl&#363;kot visus no š&#299;s maš&#299;nas pieejamos att&#257;lin&#257;tos diskus un mapes
Comment[mk]=&#1056;&#1072;&#1079;&#1075;&#1083;&#1077;&#1076;&#1072;&#1112; &#1075;&#1080; &#1089;&#1080;&#1090;&#1077; &#1083;&#1086;&#1082;&#1072;&#1083;&#1085;&#1080;, &#1076;&#1072;&#1083;&#1077;&#1095;&#1085;&#1080; &#1076;&#1080;&#1089;&#1082;&#1086;&#1074;&#1080; &#1080; &#1087;&#1072;&#1087;&#1082;&#1080; &#1087;&#1088;&#1080;&#1089;&#1090;&#1072;&#1087;&#1083;&#1080;&#1074;&#1080; &#1086;&#1076; &#1086;&#1074;&#1086;&#1112; &#1082;&#1086;&#1084;&#1087;&#1112;&#1091;&#1090;&#1077;&#1088;
Comment[nb]=Bla gjennom alle lokale og eksterne disker og mapper som kan nås fra denne datamaskinen
Comment[nl]=Bladeren door lokale schijven en schijven op afstand
Comment[pa]=&#2616;&#2605; &#2610;&#2635;&#2581;&#2610; &#2565;&#2596;&#2631; &#2608;&#2623;&#2606;&#2635;&#2591; &#2593;&#2623;&#2616;&#2581;&#2622;&#2562; &#2565;&#2596;&#2631; &#2567;&#2616; &#2581;&#2672;&#2602;&#2623;&#2570;&#2591;&#2608; &#2596;&#2635;&#2562; &#2613;&#2608;&#2596;&#2635;&#2562;&#2607;&#2635;&#2583; &#2603;&#2635;&#2610;&#2593;&#2608; &#2598;&#2624; &#2589;&#2610;&#2581;
Comment[pl]=Przegl&#261;danie wszystkich lokalnych i zdalnych dysków oraz folderów dost&#281;pnych z tego komputera
Comment[pt]=Navegar em todos os discos e pastas locais e remotos acessíveis deste computador
Comment[pt_BR]=Navegue todos os discos e pastas locais e remotos acessíveis desse computador
Comment[ru]=&#1055;&#1088;&#1086;&#1089;&#1084;&#1086;&#1090;&#1088;&#1077;&#1090;&#1100; &#1074;&#1089;&#1077; &#1083;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1099;&#1077; &#1080; &#1091;&#1076;&#1072;&#1083;&#1105;&#1085;&#1085;&#1099;&#1077; &#1076;&#1080;&#1089;&#1082;&#1080; &#1080; &#1087;&#1072;&#1087;&#1082;&#1080;, &#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1085;&#1099;&#1077; &#1089; &#1101;&#1090;&#1086;&#1075;&#1086; &#1082;&#1086;&#1084;&#1087;&#1100;&#1102;&#1090;&#1077;&#1088;&#1072;
Comment[sr]=&#1056;&#1072;&#1079;&#1075;&#1083;&#1077;&#1076;&#1072;&#1112; &#1089;&#1074;&#1077; &#1083;&#1086;&#1082;&#1072;&#1083;&#1085;&#1077; &#1080; &#1091;&#1076;&#1072;&#1113;&#1077;&#1085;&#1077; &#1076;&#1080;&#1089;&#1082;&#1086;&#1074;&#1077; &#1080; &#1092;&#1072;&#1089;&#1094;&#1080;&#1082;&#1083;&#1077; &#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1085;&#1077; &#1089;&#1072; &#1086;&#1074;&#1086;&#1075; &#1088;&#1072;&#1095;&#1091;&#1085;&#1072;&#1088;&#1072;
Comment[sr@Latn]=Razgledaj sve lokalne i udaljene diskove i fascikle dostupne sa ovog ra&#269;unara
Comment[sv]=Bläddra bland lokala och fjärrdiskar och mappar som är åtkomliga från den här datorn
Comment[th]=&#3648;&#3619;&#3637;&#3618;&#3585;&#3604;&#3641;&#3604;&#3636;&#3626;&#3585;&#3660;&#3649;&#3621;&#3632;&#3650;&#3615;&#3621;&#3648;&#3604;&#3629;&#3619;&#3660;&#3607;&#3633;&#3657;&#3591;&#3627;&#3617;&#3604;&#3651;&#3609;&#3648;&#3588;&#3619;&#3639;&#3656;&#3629;&#3591;&#3649;&#3621;&#3632;&#3651;&#3609;&#3648;&#3588;&#3619;&#3639;&#3629;&#3586;&#3656;&#3634;&#3618;&#3607;&#3637;&#3656;&#3648;&#3586;&#3657;&#3634;&#3606;&#3638;&#3591;&#3652;&#3604;&#3657;&#3592;&#3634;&#3585;&#3588;&#3629;&#3617;&#3614;&#3636;&#3623;&#3648;&#3605;&#3629;&#3619;&#3660;&#3609;&#3637;&#3657;
Comment[uk]=&#1055;&#1077;&#1088;&#1077;&#1075;&#1083;&#1103;&#1085;&#1091;&#1090;&#1080; &#1074;&#1089;&#1110; &#1083;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1110; &#1090;&#1072; &#1074;&#1110;&#1076;&#1076;&#1072;&#1083;&#1077;&#1085;&#1110; &#1076;&#1080;&#1089;&#1082;&#1080; &#1090;&#1072; &#1090;&#1077;&#1082;&#1080;, &#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1085;&#1110; &#1079; &#1094;&#1100;&#1086;&#1075;&#1086; &#1082;&#1086;&#1084;&#1087;'&#1102;&#1090;&#1077;&#1088;&#1072;
Comment[vi]=Duy&#7879;t m&#7885;i &#273;&#297;a c&#7909;c b&#7897; và &#273;&#297;a t&#7915; xa c&#361;ng nh&#432; các th&#432; m&#7909;c có th&#7875; truy c&#7853;p t&#7915; máy này
Comment[zh_CN]=&#27983;&#35272;&#21487;&#20174;&#26412;&#35745;&#31639;&#26426;&#35775;&#38382;&#30340;&#25152;&#26377;&#26412;&#22320;&#21644;&#36828;&#31243;&#30913;&#30424;&#21644;&#25991;&#20214;&#22841;
Comment[zh_HK]=&#24478;&#26412;&#38651;&#33126;&#28687;&#35261;&#25152;&#26377;&#26412;&#27231;&#21450;&#36960;&#31471;&#30913;&#30879;&#21450;&#36039;&#26009;&#22846;
Comment[zh_TW]=&#24478;&#26412;&#38651;&#33126;&#28687;&#35261;&#25152;&#26377;&#26412;&#27231;&#21450;&#36960;&#31471;&#30913;&#30879;&#21450;&#36039;&#26009;&#22846;
TryExec=nautilus 
Exec=nautilus --no-desktop computer:
Icon=gnome-fs-client
Terminal=false
StartupNotify=true
Type=Application
Categories=GNOME;GTK;Core;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.18.1
X-Ubuntu-Gettext-Domain=nautilus
```

---

### Post by DarkGob on 2007-09-06
So no ideas?  I'd really like to know how I've managed to foul things up so I can a) fix it and 2) make sure it doesn't happen again...

---

### Post by jim_p on 2007-09-07
I think something is wrong with your nautilus.
I made a blank test.desktop file and pasted your text inside and guess what...
It opens up "My computer" as usual and has the icon from the icon theme I have on my pc

I suggest you reinstall nautilus for now

---

### Post by DarkGob on 2007-09-08
> **jim_p said:**
> I think something is wrong with your nautilus.
I made a blank test.desktop file and pasted your text inside and guess what...
It opens up "My computer" as usual and has the icon from the icon theme I have on my pc

I suggest you reinstall nautilus for now

Just tried that now by reinstalling through Synaptic, no change.  I've also discovered that I'm unable to to access any of the filesystems listed under My Computer (which I am still able to access through the Places menu).  For instance, attempting to access a slave drives yields "Couldn't display "computer:///111.8%2520GB%2520Volume.drive". The location is not a folder."

I don't know what the hell I did but clearly things are FUBAR.  Please don't tell me I have to  start from scratch!

---

### Post by octathlon on 2007-09-08
Have you tried logging on as a different user to see if you have the same problems?  That would tell you if it is a system-wide problem or just a problem with  some of your user settings.

---

### Post by DarkGob on 2007-09-08
Well, I don't know what happened, but the problem seems to have entirely fixed itself.  Everything is as it was.  From the looks of it it happened after I logged out then logged back in (which I *never* do).

So, in the words of Emily Litella...never mind.

---

