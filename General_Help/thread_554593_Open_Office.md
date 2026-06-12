---
title: "Open Office"
date: 2007-09-19
forum: General Help
---

### Post by xtang on 2007-09-19
When I launch it through the (debian?) menu in xubuntu, it launches fine but the app itself does not load any of the specific modules like writer or spreadsheet which I had selected in the menu. Instead its just a window with a toolbar where I have to click new->text document/spreadsheet or whatever. Thing is it it kind of makes those 5 menu entries wasteful.

---

### Post by eggdeng on 2007-09-19
Use the menu editor to check the menuitems are not just pointing to ooffice. They should be pointing to ooffice -calc, ooffice -writer, ooffice -base, ooffice -impress or oowriter, oocalc, ooimpress, oobase.

---

### Post by McNils on 2007-09-19
Thats not how its suppose to work. You should det an empty document of the application you started. Im using fwvm-crystal on a feisty server installation (on a very old laptop) and I dont experience your problem.

---

### Post by xtang on 2007-09-20
This is what my .desktop file looks like.

```

[Desktop Entry]
Version=0.92
Encoding=UTF-8
Terminal=0
Exec=ooffice -writer %U
Icon=ooo-writer
Type=Application
Categories=Application;Office;WordProcessor
StartupNotify=false
MimeType=application/vnd.oasis.opendocument.text;application/vnd.oasis.opendocument.text-template;application/vnd.oasis.opendocument.text-master;application/vnd.sun.xml.writer;application/vnd.sun.xml.writer.template;application/vnd.sun.xml.writer.global;application/vnd.stardivision.writer;application/msword;application/vnd.ms-word;application/x-doc;text/rtf;application/rtf;application/rtf;application/vnd.wordperfect
InitialPreference=5
Name=OpenOffice.org Word Processor
Name[am]=&#4774;&#4949;&#4757;&#4774;&#4938;&#4661;.&#4774;&#4653;&#4877; &#4640;&#4757;&#4896;&#4648;&#4837; &#4768;&#4661;&#4618;
Name[bn]=&#2451;&#2474;&#2503;&#2472;&#2437;&#2475;&#2495;&#2488;.&#2437;&#2480;&#2509;&#2455; &#2451;&#2527;&#2494;&#2480;&#2509;&#2465; &#2474;&#2509;&#2480;&#2488;&#2503;&#2488;&#2480;
Name[cs]=OpenOffice.org Textový procesor
Name[de]=OpenOffice.org Textverarbeitung
Name[en_GB]=OpenOffice.org Word Processor
Name[es]=OpenOffice.org Procesador de textos
Name[et]=OpenOffice.org Kirjutaja
Name[fi]=OpenOffice.org-tekstinkäsittely
Name[fil]=Tagaproseso ng Salita sa OpenOffice.org
Name[fr]=Traitement de texte OpenOffice.org
Name[he]=OpenOffice.org &#1502;&#1506;&#1489;&#1491; &#1514;&#1502;&#1500;&#1497;&#1500;&#1497;&#1501;
Name[hr]=OpenOffice.org obrada teksta
Name[hu]=OpenOffice.org szövegszerkeszt&#337;
Name[it]=OpenOffice.org - Word processor
Name[ka]=OpenOffice.org &#4322;&#4308;&#4325;&#4321;&#4322;&#4312;&#4321; &#4320;&#4308;&#4307;&#4304;&#4325;&#4322;&#4317;&#4320;&#4312;
Name[ko]=&#50724;&#54536;&#50724;&#54588;&#49828; &#50892;&#46300; &#54532;&#47196;&#49464;&#49436;
Name[ku]=Bernameya nivîsandina OpenOffice.org
Name[nl]=OpenOffice.org Tekstverwerker
Name[oc]=Tractament de tèxt OpenOffice.org
Name[pl]=Edytor tekstu OpenOffice.org
Name[pt]=Processador de Texto OpenOffice.org
Name[pt_BR]=OpenOffice.org Editor de Texto
Name[ru]=OpenOffice.org: &#1056;&#1077;&#1076;&#1072;&#1082;&#1090;&#1086;&#1088; &#1090;&#1077;&#1082;&#1089;&#1090;&#1086;&#1074;
Name[sk]=Textový editor OpenOffice.org
Name[sv]=OpenOffice.org Ordbehandlare
Name[tl]=Tagaproseso ng Salita sa OpenOffice.org
Name[tr]=OpenOffice.org Kelime &#304;&#351;lemci
Name[zh_CN]=OpenOffice.org&#25991;&#23383;&#22788;&#29702;
GenericName=Word Processor
GenericName[am]=&#4925;&#4609;&#4941; &#4768;&#4672;&#4755;&#4869;
GenericName[ar]=&#1605;&#1593;&#1575;&#1604;&#1580; &#1606;&#1589;&#1608;&#1589;
GenericName[az]=K&#601;lm&#601; &#304;&#351;l&#601;dici
GenericName[bg]=&#1058;&#1077;&#1082;&#1089;&#1090;&#1086;&#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1072;
GenericName[bn]=&#2451;&#2527;&#2494;&#2480;&#2509;&#2465; &#2474;&#2509;&#2480;&#2488;&#2503;&#2488;&#2480;
GenericName[bs]=Word Processor
GenericName[ca]=Processador de textos
GenericName[cs]=Textový procesor
GenericName[da]=Tekstbehandler
GenericName[de]=Textverarbeitung
GenericName[dz]=&#3937;&#3954;&#3906;&#3851;&#3942;&#4006;&#4017;&#3964;&#3938;&#3851;&#3924;&#3853;
GenericName[el]=&#917;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#964;&#942;&#962; &#954;&#949;&#953;&#956;&#941;&#957;&#959;&#965;
GenericName[en_CA]=Word Processor
{


Some more language stuff


}
X-KDE-Protocols=file,http,smb,ftp,webdav

```



EDIT: hmm,, i seemed to fix the impress shortcut by changing the "EXEC=" to "ooimpress" and rebooting instead of "Exec=ooffice -impress %U". Will play around a bit more.

EDIT2: Actually I get the feeling that "%U"  option is the culprit, what does it do?

---

