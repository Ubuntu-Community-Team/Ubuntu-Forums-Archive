---
title: "Startup Programs Executed but not Operational"
date: 2017-01-02
forum: General Help
---

### Post by Maxattax97 on 2017-01-02
[COLOR=#111111][FONT=Ubuntu]So far this problem only persists with qBittorrent and Steam. I have noticed that if I log into Ubuntu soon after it boots up, these programs run perfectly fine and appear in the indicator bar at the top of the screen. But if I hit the power button, leave for ~30 minutes, and return to log in, these programs have visibly been executed (their processes are visible in the System Monitor), but are not accessible from the indicator bar and seem to not be functional.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have noticed that if I kill the processes executed at startup and re-run them, everything will work as expected.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have attempted to log output for each of these programs with little success. qBittorrent logs nothing, and Steam logs this when executed by startup:[/FONT][/COLOR]
```

Running Steam on ubuntu 16.10 64-bit
STEAM_RUNTIME is enabled automatically

```
[COLOR=#111111][FONT=Ubuntu]And when Steam is killed and re-run, this is logged:
[/FONT][/COLOR]```

Running Steam on ubuntu 16.10 64-bit
STEAM_RUNTIME is enabled automatically
Running Steam on ubuntu 16.10 64-bit
STEAM_RUNTIME has been set by the user to:
/home/max/.steam/ubuntu12_32/steam-runtime

```
[COLOR=#111111][FONT=Ubuntu]It is possible I am not logging correctly, so here is the file for [FONT=courier new]/home/max/.config/autostart/steam.desktop[/FONT]. I added a delay of 30 seconds hoping it might fix something, but alas, it did not:
[/FONT][/COLOR]```

[Desktop Entry]
Name=Steam
Comment=Application for managing and playing games on Steam
Exec=bash -c "/usr/games/steam %U > /home/max/steamlog.txt 2>&1"
Icon=steam
Terminal=false
Type=Application
Categories=Network;FileTransfer;Game;
MimeType=x-scheme-handler/steam;
Actions=Store;Community;Library;Servers;Screenshots;News;Settings;BigPicture;Friends;
Keywords=Games

X-GNOME-Autostart-enabled=true
X-GNOME-Autostart-Delay=30

[Desktop Action Store]
Name=Store
Name[de]=Shop
Name[es]=Tienda
Name[fr]=Magasin
Name[it]=Negozio
Name[pt]=Loja
Name[ru]=&#1052;&#1072;&#1075;&#1072;&#1079;&#1080;&#1085;
Name[zh_CN]=&#21830;&#24215;
Name[zh_TW]=&#21830;&#24215;
Exec=steam steam://store

[Desktop Action Community]
Name=Community
Name[es]=Comunidad
Name[fr]=Communauté
Name[it]=Comunità
Name[pt]=Comunidade
Name[ru]=&#1057;&#1086;&#1086;&#1073;&#1097;&#1077;&#1089;&#1090;&#1074;&#1086;
Name[zh_CN]=&#31038;&#21306;
Name[zh_TW]=&#31038;&#32676;
Exec=steam steam://url/SteamIDControlPage

[Desktop Action Library]
Name=Library
Name[de]=Bibliothek
Name[es]=Biblioteca
Name[fr]=Bibliothèque
Name[it]=Libreria
Name[pt]=Biblioteca
Name[ru]=&#1041;&#1080;&#1073;&#1083;&#1080;&#1086;&#1090;&#1077;&#1082;&#1072;
Name[zh_CN]=&#24211;
Name[zh_TW]=&#36938;&#25138;&#24235;
Exec=steam steam://open/games

[Desktop Action Servers]
Name=Servers
Name[de]=Server
Name[es]=Servidores
Name[fr]=Serveurs
Name[it]=Server
Name[pt]=Servidores
Name[ru]=&#1057;&#1077;&#1088;&#1074;&#1077;&#1088;&#1099;
Name[zh_CN]=&#26381;&#21153;&#22120;
Name[zh_TW]=&#20282;&#26381;&#22120;
Exec=steam steam://open/servers

[Desktop Action Screenshots]
Name=Screenshots
Name[es]=Capturas
Name[fr]=Captures d'écran
Name[it]=Screenshot
Name[ru]=&#1057;&#1082;&#1088;&#1080;&#1085;&#1096;&#1086;&#1090;&#1099;
Name[zh_CN]=&#25130;&#22270;
Name[zh_TW]=&#34722;&#24149;&#25847;&#22294;
Exec=steam steam://open/screenshots

[Desktop Action News]
Name=News
Name[de]=Neuigkeiten
Name[es]=Noticias
Name[fr]=Actualités
Name[it]=Notizie
Name[pt]=Notícias
Name[ru]=&#1053;&#1086;&#1074;&#1086;&#1089;&#1090;&#1080;
Name[zh_CN]=&#26032;&#38395;
Name[zh_TW]=&#26032;&#32862;
Exec=steam steam://open/news

[Desktop Action Settings]
Name=Settings
Name[de]=Einstellungen
Name[es]=Parámetros
Name[fr]=Paramètres
Name[it]=Impostazioni
Name[pt]=Configurações
Name[ru]=&#1053;&#1072;&#1089;&#1090;&#1088;&#1086;&#1081;&#1082;&#1080;
Name[zh_CN]=&#35774;&#32622;
Name[zh_TW]=&#35373;&#23450;
Exec=steam steam://open/settings

[Desktop Action BigPicture]
Name=Big Picture
Exec=steam steam://open/bigpicture

[Desktop Action Friends]
Name=Friends
Name[de]=Freunde
Name[es]=Amigos
Name[fr]=Amis
Name[it]=Amici
Name[pt]=Amigos
Name[ru]=&#1044;&#1088;&#1091;&#1079;&#1100;&#1103;
Name[zh_CN]=&#22909;&#21451;
Name[zh_TW]=&#22909;&#21451;
Exec=steam steam://open/friends

```

[COLOR=#111111][FONT=Ubuntu]And here is the file for [FONT=courier new]/home/max/.config/autostart/qBittorrent.desktop[/FONT]:[/FONT][/COLOR]
```

[Desktop Entry]
Categories=Network;FileTransfer;P2P;Qt;
Exec=bash -c "qbittorrent %U > /home/max/qbitlog.txt 2>&1"
GenericName=BitTorrent client
Comment=Download and share files over BitTorrent
Icon=qbittorrent
MimeType=application/x-bittorrent;x-scheme-handler/magnet;
Name=qBittorrent
Terminal=false
Type=Application
StartupNotify=false
StartupWMClass=qbittorrent

# Translations
Comment[ar]=&#1606;&#1586;&#1617;&#1604; &#1608;&#1588;&#1575;&#1585;&#1603; &#1575;&#1604;&#1605;&#1604;&#1601;&#1575;&#1578; &#1593;&#1576;&#1585; &#1603;&#1610;&#1608;&#1576;&#1578;&#8206;&#1578;&#1608;&#1585;&#1606;&#1578;
GenericName[ar]=&#1593;&#1605;&#1610;&#1604; &#1576;&#1578; &#1578;&#1608;&#1585;&#1606;&#1578;
Name[ar]=&#1603;&#1610;&#1608;&#1576;&#1578;&#8206;&#1578;&#1608;&#1585;&#1606;&#1578;
Comment[be]=&#1057;&#1094;&#1103;&#1075;&#1074;&#1072;&#1085;&#1085;&#1077; &#1110; &#1088;&#1072;&#1079;&#1076;&#1072;&#1095;&#1072; &#1092;&#1072;&#1081;&#1083;&#1072;&#1118; &#1087;&#1088;&#1072;&#1079; &#1087;&#1088;&#1072;&#1090;&#1072;&#1082;&#1086;&#1083; BitTorrent
GenericName[be]=BitTorrent-&#1082;&#1083;&#1110;&#1077;&#1085;&#1090;
Name[be]=qBittorrent
GenericName[bg]=&#1058;&#1086;&#1088;&#1077;&#1085;&#1090; &#1082;&#1083;&#1080;&#1077;&#1085;&#1090;
Comment[bn]=&#2465;&#2494;&#2441;&#2472;&#2482;&#2507;&#2465; &#2453;&#2480;&#2497;&#2472; &#2447;&#2476;&#2434; &#2475;&#2494;&#2439;&#2482; &#2486;&#2503;&#2479;&#2492;&#2494;&#2480; &#2453;&#2480;&#2497;&#2472;
GenericName[bn]=&#2453;&#2495;&#2441;&#2476;&#2495;&#2463;&#2480;&#2503;&#2472;&#2509;&#2463; &#2453;&#2509;&#2482;&#2494;&#2527;&#2503;&#2472;&#2509;&#2463;
Name[bn]=&#2453;&#2495;&#2441;&#2476;&#2495;&#2463;&#2480;&#2503;&#2472;&#2509;&#2463;
Comment[cs]=Stahování a sdílení soubor&#367; p&#345;es sí&#357; BitTorrent
GenericName[cs]=BitTorrent klient
Name[cs]=qBittorrent
Comment[da]=Download og del filer over BitTorrent
GenericName[da]=BitTorrent klient
Name[da]=qBittorrent
Comment[de]=Über BitTorrent Dateien herunterladen und teilen
GenericName[de]=BitTorrent Client
Name[de]=qBittorrent
Comment[el]=&#923;&#942;&#968;&#951; &#954;&#945;&#953; &#948;&#953;&#945;&#956;&#959;&#953;&#961;&#945;&#963;&#956;&#972;&#962; &#945;&#961;&#967;&#949;&#943;&#969;&#957; &#956;&#941;&#963;&#969; BitTorrent
GenericName[el]=BitTorrent &#960;&#949;&#955;&#940;&#964;&#951;&#962;
Name[el]=qBittorrent
Comment[en_GB]=Download and share files over BitTorrent
GenericName[en_GB]=BitTorrent client
Name[en_GB]=qBittorrent
Comment[es]=Descargue y comparta archivos por BitTorrent
GenericName[es]=Cliente BitTorrent
Name[es]=qBittorrent
Comment[eu]=Jeitsi eta elkarbanatu agiriak BitTorrent-en
GenericName[eu]=BitTorrent bezeroa
Name[eu]=qBittorrent
Comment[fi]=Lataa ja jaa tiedostoja BitTorrentia käyttäen
GenericName[fi]=BitTorrent-ohjelma
Name[fi]=qBittorrent
Comment[fr]=Télécharger et partager des fichiers avec BitTorrent
GenericName[fr]=Client BitTorrent
Name[fr]=qBittorrent
Comment[gl]=Descargue e comparta ficheiros co protocolo BitTorrent
GenericName[gl]=Cliente BitTorrent
Name[gl]=qBittorrent
GenericName[hr]=BitTorrent klijent
Comment[hu]=Fájlok letöltése és megosztása a BitTorrent hálózaton keresztül
GenericName[hu]=BitTorrent kliens
Name[hu]=qBittorrent
Comment[it]=Client BitTorrent per il download di file via internet
GenericName[it]=Client BitTorrent
Name[it]=qBittorrent
Comment[ja]=BitTorrent &#12391;&#12501;&#12449;&#12452;&#12523;&#12434;&#12480;&#12454;&#12531;&#12525;&#12540;&#12489;&#12362;&#12424;&#12403;&#20849;&#26377;&#12375;&#12414;&#12377;
GenericName[ja]=BitTorrent &#12463;&#12521;&#12452;&#12450;&#12531;&#12488;
Name[ja]=qBittorrent
Comment[ka]=&#4329;&#4304;&#4315;&#4317;&#4322;&#4309;&#4312;&#4320;&#4311;&#4308; &#4307;&#4304; &#4306;&#4304;&#4304;&#4310;&#4312;&#4304;&#4320;&#4308; &#4324;&#4304;&#4312;&#4314;&#4308;&#4305;&#4312; Bittorrent-&#4312;&#4321; &#4321;&#4304;&#4328;&#4323;&#4304;&#4314;&#4308;&#4305;&#4312;&#4311;
GenericName[ka]=BitTorrent &#4313;&#4314;&#4312;&#4308;&#4316;&#4322;&#4312;
Name[ka]=qBittorrent
Comment[ko]=&#48708;&#53944; &#53664;&#47116;&#53944;&#47484; &#53685;&#54644; &#54028;&#51068;&#51012; &#45796;&#50868;&#47196;&#46300;&#54616;&#44256; &#44277;&#50976;&#54633;&#45768;&#45796;
GenericName[ko]=&#48708;&#53944; &#53664;&#47116;&#53944; &#53364;&#46972;&#51060;&#50616;&#53944;
Name[ko]=&#53328;&#48727; &#53664;&#47116;&#53944;
Comment[zh]=&#36890;&#36807; BitTorrent &#19979;&#36733;&#21644;&#20998;&#20139;&#25991;&#20214;
GenericName[zh]=BitTorrent &#23458;&#25143;&#31471;
Name[zh]=qBittorrent
Comment[lt]=Atsisi&#371;skite bei dalinkit&#279;s failais BitTorrent tinkle
GenericName[lt]=BitTorrent klientas
Name[lt]=qBittorrent
Comment[nb]=Last ned og del filer over BitTorrent
GenericName[nb]=BitTorrent-klient
Name[nb]=qBittorrent
Comment[nqo]=&#2014;&#2000;&#2005;&#2000;&#2031;&#2008;&#2000; &#2015;&#1998;&#2028; &#2015;&#1994;&#2006;&#1996;&#2032; &#2014;&#1994;&#2028; &#2003;&#1994;&#2027;&#2034; &#2014;&#2037;&#1994;&#2028;&#2015;&#1998;&#2028; &#2008;&#2000;&#2005;&#2015;&#1994;&#2027; &#2003;&#1996;&#2009;&#1999;&#2009;&#1997;&#2034;&#2005; &#2014;&#1994;&#2034;&#2028;
GenericName[nqo]=&#2003;&#1996;&#2009;&#1999;&#2009;&#1997;&#2034;&#2005; &#2005;&#2019;&#2000;&#2028;&#2003;&#2000;&#2028;&#2015;&#1994;
Name[nqo]=&#2014;&#1998;&#2035;&#2003;&#1996;&#2005;&#1999;&#2009;&#1997;&#2034;&#2005;
Comment[nl]=Bestanden downloaden en delen via BitTorrent
GenericName[nl]=BitTorrent-cliënt
Name[nl]=qBittorrent
Comment[pl]=Pobieraj i dziel si&#281; plikami przez BitTorrent
GenericName[pl]=Klient BitTorrent
Name[pl]=qBittorrent
Comment[pt]=Transferir e partilhar ficheiros por BitTorrent
GenericName[pt]=Aplicação BitTorrent
Name[pt]=qBittorrent
Comment[pt_BR]=Baixe e compartilhe arquivos através do qBittorrent
GenericName[pt_BR]=Cliente BitTorrent
Name[pt_BR]=qBittorrent
Comment[ro]=Desc&#259;rca&#539;i &#537;i partaja&#539;i fi&#537;iere prin BitTorrent
GenericName[ro]=Client BitTorrent
Name[ro]=qBittorrent
Comment[ru]=&#1057;&#1082;&#1072;&#1095;&#1080;&#1074;&#1072;&#1081;&#1090;&#1077; &#1080; &#1076;&#1077;&#1083;&#1080;&#1090;&#1077;&#1089;&#1100; &#1092;&#1072;&#1081;&#1083;&#1072;&#1084;&#1080; &#1089; &#1087;&#1086;&#1084;&#1086;&#1097;&#1100;&#1102; BitTorrent
GenericName[ru]=&#1082;&#1083;&#1080;&#1077;&#1085;&#1090; BitTorrent
Name[ru]=qBittorrent
Comment[sk]=S&#357;ahovanie a zdie&#318;anie súborov prostredníctvom siete BitTorrent
GenericName[sk]=Klient siete BitTorrent
Name[sk]=qBittorrent
Comment[sl]=Prenesite in delite datoteke preko BitTorrenta
GenericName[sl]=BitTorrent odjemalec
Name[sl]=qBittorrent
GenericName[sr]=BitTorrent-&#1082;&#1083;&#1080;&#1112;&#1077;&#1085;&#1090;
Comment[sv]=Hämta och dela filer över BitTorrent
GenericName[sv]=BitTorrent-klient
Name[sv]=qBittorrent
Comment[hi_IN]=&#2309;&#2346;&#2344;&#2368; &#2347;&#2366;&#2311;&#2354;&#2375;&#2306; BitTorrent &#2325;&#2375; &#2350;&#2366;&#2343;&#2381;&#2351;&#2350; &#2360;&#2375; &#2337;&#2366;&#2313;&#2344;&#2354;&#2379;&#2337; &#2310;&#2376;&#2352; &#2360;&#2366;&#2373;&#2333;&#2366; &#2325;&#2352;&#2375;&#2306;
GenericName[hi_IN]=BitTorrent &#2313;&#2346;&#2349;&#2379;&#2325;&#2381;&#2340;&#2366;
Name[hi_IN]=qBittorrent
Comment[tr]=Dosyalar&#305; BitTorrent üzerinden indir ve payla&#351;
GenericName[tr]=BitTorrent istemcisi
Name[tr]=qBittorrent
Comment[uk]=&#1047;&#1072;&#1074;&#1072;&#1085;&#1090;&#1072;&#1078;&#1091;&#1074;&#1072;&#1090;&#1080; &#1110; &#1086;&#1073;&#1084;&#1110;&#1085;&#1102;&#1074;&#1072;&#1090;&#1080;&#1089;&#1103; &#1092;&#1072;&#1081;&#1083;&#1072;&#1084;&#1080; &#1095;&#1077;&#1088;&#1077;&#1079; BitTorrent
GenericName[uk]=BitTorrent-&#1082;&#1083;&#1110;&#1108;&#1085;&#1090;
Name[uk]=qBittorrent
Comment[vi]=T&#7843;i v&#7873; và chia s&#7867; các t&#7853;p tin thông qua BitTorrent
GenericName[vi]=Máy tr&#7841;m d&#7841;ng BitTorrent
Name[vi]=qBittorrent
Comment[zh_TW]=&#32147;&#30001; BitTorrent &#19979;&#36617;&#20006;&#20998;&#20139;&#27284;&#26696;
GenericName[zh_TW]=BitTorrent &#23458;&#25142;&#31471;
Name[zh_TW]=qBittorrent
Comment[en_AU]=Download and share files over BitTorrent
GenericName[en_AU]=BitTorrent client
Name[en_AU]=qBittorrent

X-GNOME-Autostart-enabled=true
X-GNOME-Autostart-Delay=60

```
[COLOR=#111111][FONT=Ubuntu]This time with a delay of 60 seconds.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Under normal circumstances (without logging) the commands for execution are [FONT=courier new]/usr/games/steam %U[/FONT] and [FONT=courier new]qbittorrent %U[/FONT] for Steam and qBittorrent respectively.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I can provide additional information upon request. After waiting and searching for several months I haven't found anyone else with this issue. Thank you in advance.[/FONT][/COLOR]

---

### Post by Maxattax97 on 2017-01-07
Bump.

---

