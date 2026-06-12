---
title: "Nemo and right-click &gt; change desktop background"
date: 2014-04-15
forum: General Help
---

### Post by BlackoutWorm on 2014-04-15
Hello. My file manager is nemo.
When I right click to change desktop background, the link doesn't work.
Not a big deal though. I can change the background from gnome settings.
But it's just one of these little things I wish would work.
Any suggestion?
Thanks

---

### Post by slickymaster on 2014-04-15
Did you replace Nautilus with Nemo? The reason I'm asking is because the right click option to change the desktop wallpaper is from nautilus. Nautilus is actually controlling the desktop. Turning off nautilus has disabled this feature.

---

### Post by BlackoutWorm on 2014-04-15
No I got rid of nautilus long ago.
Nemo is controlling the desktop.
I just need to link "change desktop background" to gnome setting's background dialog.

---

### Post by BlackoutWorm on 2014-04-17
Bump

---

### Post by grumblebum2 on 2014-04-17
If you update nemo using the ppa from webupd8.org this is fixed.
[http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html](http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html)

If you don't want to use the ppa you can try adding this file to **~/.local/share/nemo/actions/**

In the terminal run ...
```
gedit ~/.local/share/nemo/actions/change-background2.nemo_action
```
and copy and paste the following...
```
[Nemo Action]

Name=Change Desktop _Background

Comment=Change Desktop _Background

Exec=unity-control-center appearance

Selection=None

Icon-Name=desktop

Extensions=any;

Dependencies=unity-control-center;unity-settings-daemon;

Conditions=desktop;dbus com.canonical.Unity;

Name[el]=&#913;&#955;&#955;&#945;&#947;&#942; _&#949;&#953;&#954;&#972;&#957;&#945;&#962; &#949;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945;&#962; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;
Name[vi]=&#272;&#7893;i &#7842;nh _n&#7873;n Màn hình
Name[is]=Breyta _bakgrunni skjáborðs
Name[am]=&#4840;&#4852;&#4661;&#4781;&#4726;&#4949; _&#4632;&#4848;&#4709; &#4632;&#4672;&#4840;&#4650;&#4843;
Name[it]=Ca_mbia sfondo scrivania
Name[eu]=Aldatu _mahaigainaren atzeko planoa
Name[cy]=Newid Cefndir y _Bwrdd Gwaith
Name[ar]=&#1578;&#1594;&#1610;&#1610;&#1585; _&#1582;&#1604;&#1601;&#1610;&#1577; &#1587;&#1591;&#1581; &#1575;&#1604;&#1605;&#1603;&#1578;&#1576;
Name[ga]=Athraigh Cúl_ra na Deisce
Name[cs]=Zm&#283;nit _pozadí plochy
Name[et]=Vaheta töölaua _taust
Name[id]=Ubah Latar _Belakang Desktop
Name[es]=Cambiar el _fondo del escritorio
Name[ru]=_&#1048;&#1079;&#1084;&#1077;&#1085;&#1080;&#1090;&#1100; &#1092;&#1086;&#1085; &#1088;&#1072;&#1073;&#1086;&#1095;&#1077;&#1075;&#1086; &#1089;&#1090;&#1086;&#1083;&#1072;
Name[nl]=Werk_bladachtergrond wijzigen
Name[pt]=Alterar _fundo da área de trabalho
Name[tr]=Masaüstü _Arkaplan&#305;n&#305; De&#287;i&#351;tir
Name[en_AU]=Change Desktop _Background
Name[lt]=Keisti darbalaukio _fon&#261;
Name[ca]=Canvia el _fons de l'escriptori
Name[en_GB]=Change Desktop _Background
Name[fr]=Modifier l'arrière-plan du _bureau
Name[de]=_Hintergrund der Arbeitsfläche ändern
Name[uk]=&#1047;&#1084;&#1110;&#1085;&#1080;&#1090;&#1080; &#1090;_&#1083;&#1086; &#1089;&#1090;&#1110;&#1083;&#1100;&#1085;&#1080;&#1094;&#1110;
Name[pt_BR]=Alterar plano de _Fundo
Name[sl]=Spremeni _ozadje namizja
Name[hr]=Promijeni _pozadinu desktopa
Name[sr@latin]=Iz_meni pozadinu
Name[hu]=Asztal _hátterének módosítása
Name[bs]=Promijeni _pozadinu desktopa
Name[ja]=&#32972;&#26223;&#12434;&#22793;&#26356; (_B)
Name[fr_CA]=Changer l'_arrière-plan du bureau
Name[zh_CN]=&#26356;&#25913;&#26700;&#38754;&#32972;&#26223;(_B)
Name[ml]=&#3361;&#3398;&#3384;&#3405;&#3349;&#3405;&#3359;&#3403;&#3370;&#3405;&#3370;&#3391;&#3368;&#3405;&#3377;&#3398; _&#3370;&#3382;&#3405;&#3354;&#3390;&#3364;&#3405;&#3364;&#3378;&#3330; &#3374;&#3390;&#3377;&#3405;&#3377;&#3393;&#3349;
Name[sv]=Byt skrivbordsbak_grund
Name[sk]=Zmeni&#357; _pozadie plochy
Name[pl]=Zmie&#324; _t&#322;o pulpitu
Name[ms]=Tukar Latar _Belakang Desktop
Name[sr]=&#1048;&#1079;_&#1084;&#1077;&#1085;&#1080; &#1087;&#1086;&#1079;&#1072;&#1076;&#1080;&#1085;&#1091;
Name[nds]=Desktop_Hintergrund ändern
Comment[el]=&#913;&#955;&#955;&#945;&#947;&#942; _&#949;&#953;&#954;&#972;&#957;&#945;&#962; &#949;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945;&#962; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;
Comment[vi]=&#272;&#7893;i &#7842;nh _n&#7873;n Màn hình
Comment[is]=Breyta _bakgrunni skjáborðs
Comment[am]=&#4840;&#4852;&#4661;&#4781;&#4726;&#4949; _&#4632;&#4848;&#4709; &#4632;&#4672;&#4840;&#4650;&#4843;
Comment[it]=Ca_mbia sfondo scrivania
Comment[eu]=Aldatu _mahaigainaren atzeko planoa
Comment[cy]=Newid Cefndir y _Bwrdd Gwaith
Comment[ar]=&#1578;&#1594;&#1610;&#1610;&#1585; _&#1582;&#1604;&#1601;&#1610;&#1577; &#1587;&#1591;&#1581; &#1575;&#1604;&#1605;&#1603;&#1578;&#1576;
Comment[ga]=Athraigh Cúl_ra na Deisce
Comment[cs]=Zm&#283;nit _pozadí plochy
Comment[et]=Vaheta töölaua _taust
Comment[id]=Ubah Latar _Belakang Desktop
Comment[es]=Cambiar el _fondo del escritorio
Comment[ru]=_&#1048;&#1079;&#1084;&#1077;&#1085;&#1080;&#1090;&#1100; &#1092;&#1086;&#1085; &#1088;&#1072;&#1073;&#1086;&#1095;&#1077;&#1075;&#1086; &#1089;&#1090;&#1086;&#1083;&#1072;
Comment[nl]=Werk_bladachtergrond wijzigen
Comment[pt]=Alterar _fundo da área de trabalho
Comment[tr]=Masaüstü _Arkaplan&#305;n&#305; De&#287;i&#351;tir
Comment[en_AU]=Change Desktop _Background
Comment[lt]=Keisti darbalaukio _fon&#261;
Comment[ca]=Canvia el _fons de l'escriptori
Comment[en_GB]=Change Desktop _Background
Comment[fr]=Modifier l'arrière-plan du _bureau
Comment[de]=_Hintergrund der Arbeitsfläche ändern
Comment[uk]=&#1047;&#1084;&#1110;&#1085;&#1080;&#1090;&#1080; &#1090;_&#1083;&#1086; &#1089;&#1090;&#1110;&#1083;&#1100;&#1085;&#1080;&#1094;&#1110;
Comment[pt_BR]=Alterar plano de _Fundo
Comment[sl]=Spremeni _ozadje namizja
Comment[hr]=Promijeni _pozadinu desktopa
Comment[sr@latin]=Iz_meni pozadinu
Comment[hu]=Asztal _hátterének módosítása
Comment[bs]=Promijeni _pozadinu desktopa
Comment[ja]=&#32972;&#26223;&#12434;&#22793;&#26356; (_B)
Comment[fr_CA]=Changer l'_arrière-plan du bureau
Comment[zh_CN]=&#26356;&#25913;&#26700;&#38754;&#32972;&#26223;(_B)
Comment[ml]=&#3361;&#3398;&#3384;&#3405;&#3349;&#3405;&#3359;&#3403;&#3370;&#3405;&#3370;&#3391;&#3368;&#3405;&#3377;&#3398; _&#3370;&#3382;&#3405;&#3354;&#3390;&#3364;&#3405;&#3364;&#3378;&#3330; &#3374;&#3390;&#3377;&#3405;&#3377;&#3393;&#3349;
Comment[sv]=Byt skrivbordsbak_grund
Comment[sk]=Zmeni&#357; _pozadie plochy
Comment[pl]=Zmie&#324; _t&#322;o pulpitu
Comment[ms]=Tukar Latar _Belakang Desktop
Comment[sr]=&#1048;&#1079;_&#1084;&#1077;&#1085;&#1080; &#1087;&#1086;&#1079;&#1072;&#1076;&#1080;&#1085;&#1091;
Comment[nds]=Desktop_Hintergrund ändern
```

Save and close.
It works but you still have the old "change background" entry as well.

---

### Post by BlackoutWorm on 2014-04-18
Thanks but this links to unity, which I don't have installed.
So the new entry doesn't do anything.
I'm using gnome shell. Gnome shell uses gnome-control-center

---

### Post by grumblebum2 on 2014-04-18
> **BlackoutWorm said:**
> Thanks but this links to unity, which I don't have installed.
So the new entry doesn't do anything.
I'm using gnome shell. Gnome shell uses gnome-control-center
I don't have gnome-shell installed but I think the patch should work there as well.

The nemo update includes another **change-background.nemo_action** file that targets gnome-shell.
```
[Nemo Action]

Name=Change Desktop _Background

Comment=Change Desktop _Background

Exec=[COLOR="#FF0000"]gnome-control-center background[/COLOR]

Selection=None

Icon-Name=desktop

Extensions=any;

Dependencies=gnome-control-center;

Conditions=desktop;dbus [COLOR="#FF0000"]org.gnome.Shell[/COLOR].Screencast;

Name[el]=&#913;&#955;&#955;&#945;&#947;&#942; _&#949;&#953;&#954;&#972;&#957;&#945;&#962; &#949;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945;&#962; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;
Name[vi]=&#272;&#7893;i &#7842;nh _n&#7873;n Màn hình
Name[is]=Breyta _bakgrunni skjáborðs
Name[am]=&#4840;&#4852;&#4661;&#4781;&#4726;&#4949; _&#4632;&#4848;&#4709; &#4632;&#4672;&#4840;&#4650;&#4843;
Name[it]=Ca_mbia sfondo scrivania
Name[eu]=Aldatu _mahaigainaren atzeko planoa
Name[cy]=Newid Cefndir y _Bwrdd Gwaith
Name[ar]=&#1578;&#1594;&#1610;&#1610;&#1585; _&#1582;&#1604;&#1601;&#1610;&#1577; &#1587;&#1591;&#1581; &#1575;&#1604;&#1605;&#1603;&#1578;&#1576;
Name[ga]=Athraigh Cúl_ra na Deisce
Name[cs]=Zm&#283;nit _pozadí plochy
Name[et]=Vaheta töölaua _taust
Name[id]=Ubah Latar _Belakang Desktop
Name[es]=Cambiar el _fondo del escritorio
Name[ru]=_&#1048;&#1079;&#1084;&#1077;&#1085;&#1080;&#1090;&#1100; &#1092;&#1086;&#1085; &#1088;&#1072;&#1073;&#1086;&#1095;&#1077;&#1075;&#1086; &#1089;&#1090;&#1086;&#1083;&#1072;
Name[nl]=Werk_bladachtergrond wijzigen
Name[pt]=Alterar _fundo da área de trabalho
Name[tr]=Masaüstü _Arkaplan&#305;n&#305; De&#287;i&#351;tir
Name[en_AU]=Change Desktop _Background
Name[lt]=Keisti darbalaukio _fon&#261;
Name[ca]=Canvia el _fons de l'escriptori
Name[en_GB]=Change Desktop _Background
Name[fr]=Modifier l'arrière-plan du _bureau
Name[de]=_Hintergrund der Arbeitsfläche ändern
Name[uk]=&#1047;&#1084;&#1110;&#1085;&#1080;&#1090;&#1080; &#1090;_&#1083;&#1086; &#1089;&#1090;&#1110;&#1083;&#1100;&#1085;&#1080;&#1094;&#1110;
Name[pt_BR]=Alterar plano de _Fundo
Name[sl]=Spremeni _ozadje namizja
Name[hr]=Promijeni _pozadinu desktopa
Name[sr@latin]=Iz_meni pozadinu
Name[hu]=Asztal _hátterének módosítása
Name[bs]=Promijeni _pozadinu desktopa
Name[ja]=&#32972;&#26223;&#12434;&#22793;&#26356; (_B)
Name[fr_CA]=Changer l'_arrière-plan du bureau
Name[zh_CN]=&#26356;&#25913;&#26700;&#38754;&#32972;&#26223;(_B)
Name[ml]=&#3361;&#3398;&#3384;&#3405;&#3349;&#3405;&#3359;&#3403;&#3370;&#3405;&#3370;&#3391;&#3368;&#3405;&#3377;&#3398; _&#3370;&#3382;&#3405;&#3354;&#3390;&#3364;&#3405;&#3364;&#3378;&#3330; &#3374;&#3390;&#3377;&#3405;&#3377;&#3393;&#3349;
Name[sv]=Byt skrivbordsbak_grund
Name[sk]=Zmeni&#357; _pozadie plochy
Name[pl]=Zmie&#324; _t&#322;o pulpitu
Name[ms]=Tukar Latar _Belakang Desktop
Name[sr]=&#1048;&#1079;_&#1084;&#1077;&#1085;&#1080; &#1087;&#1086;&#1079;&#1072;&#1076;&#1080;&#1085;&#1091;
Name[nds]=Desktop_Hintergrund ändern
Comment[el]=&#913;&#955;&#955;&#945;&#947;&#942; _&#949;&#953;&#954;&#972;&#957;&#945;&#962; &#949;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945;&#962; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;
Comment[vi]=&#272;&#7893;i &#7842;nh _n&#7873;n Màn hình
Comment[is]=Breyta _bakgrunni skjáborðs
Comment[am]=&#4840;&#4852;&#4661;&#4781;&#4726;&#4949; _&#4632;&#4848;&#4709; &#4632;&#4672;&#4840;&#4650;&#4843;
Comment[it]=Ca_mbia sfondo scrivania
Comment[eu]=Aldatu _mahaigainaren atzeko planoa
Comment[cy]=Newid Cefndir y _Bwrdd Gwaith
Comment[ar]=&#1578;&#1594;&#1610;&#1610;&#1585; _&#1582;&#1604;&#1601;&#1610;&#1577; &#1587;&#1591;&#1581; &#1575;&#1604;&#1605;&#1603;&#1578;&#1576;
Comment[ga]=Athraigh Cúl_ra na Deisce
Comment[cs]=Zm&#283;nit _pozadí plochy
Comment[et]=Vaheta töölaua _taust
Comment[id]=Ubah Latar _Belakang Desktop
Comment[es]=Cambiar el _fondo del escritorio
Comment[ru]=_&#1048;&#1079;&#1084;&#1077;&#1085;&#1080;&#1090;&#1100; &#1092;&#1086;&#1085; &#1088;&#1072;&#1073;&#1086;&#1095;&#1077;&#1075;&#1086; &#1089;&#1090;&#1086;&#1083;&#1072;
Comment[nl]=Werk_bladachtergrond wijzigen
Comment[pt]=Alterar _fundo da área de trabalho
Comment[tr]=Masaüstü _Arkaplan&#305;n&#305; De&#287;i&#351;tir
Comment[en_AU]=Change Desktop _Background
Comment[lt]=Keisti darbalaukio _fon&#261;
Comment[ca]=Canvia el _fons de l'escriptori
Comment[en_GB]=Change Desktop _Background
Comment[fr]=Modifier l'arrière-plan du _bureau
Comment[de]=_Hintergrund der Arbeitsfläche ändern
Comment[uk]=&#1047;&#1084;&#1110;&#1085;&#1080;&#1090;&#1080; &#1090;_&#1083;&#1086; &#1089;&#1090;&#1110;&#1083;&#1100;&#1085;&#1080;&#1094;&#1110;
Comment[pt_BR]=Alterar plano de _Fundo
Comment[sl]=Spremeni _ozadje namizja
Comment[hr]=Promijeni _pozadinu desktopa
Comment[sr@latin]=Iz_meni pozadinu
Comment[hu]=Asztal _hátterének módosítása
Comment[bs]=Promijeni _pozadinu desktopa
Comment[ja]=&#32972;&#26223;&#12434;&#22793;&#26356; (_B)
Comment[fr_CA]=Changer l'_arrière-plan du bureau
Comment[zh_CN]=&#26356;&#25913;&#26700;&#38754;&#32972;&#26223;(_B)
Comment[ml]=&#3361;&#3398;&#3384;&#3405;&#3349;&#3405;&#3359;&#3403;&#3370;&#3405;&#3370;&#3391;&#3368;&#3405;&#3377;&#3398; _&#3370;&#3382;&#3405;&#3354;&#3390;&#3364;&#3405;&#3364;&#3378;&#3330; &#3374;&#3390;&#3377;&#3405;&#3377;&#3393;&#3349;
Comment[sv]=Byt skrivbordsbak_grund
Comment[sk]=Zmeni&#357; _pozadie plochy
Comment[pl]=Zmie&#324; _t&#322;o pulpitu
Comment[ms]=Tukar Latar _Belakang Desktop
Comment[sr]=&#1048;&#1079;_&#1084;&#1077;&#1085;&#1080; &#1087;&#1086;&#1079;&#1072;&#1076;&#1080;&#1085;&#1091;
Comment[nds]=Desktop_Hintergrund ändern
```

---

### Post by BlackoutWorm on 2014-04-18
Thanks but it wouldn't work.
So I changed it to "Change settings" and removed "background" from the name and path.
I can live with that.
But it's still stupid that they can't fix that dead "change desktop background".

---

### Post by grumblebum2 on 2014-04-18
I did have gnome-shell installed from when I installed gnome-panel and found you can turn off nemo drawing the desktop
whereby you will get the gnome-shell menu.
```
gsettings set org.nemo.desktop show-desktop-icons false
```
See below command to also turn off nautilus if necessary.
[ATTACH=CONFIG]252195[/ATTACH]




Also tested with the version of nemo from webupd8 and when show-desktop-icons is set to true(default) for nemo
the desktop menu item brings up the gnome-shell background window.
The reason this does not work for you is that you may have nautilus set to draw the desktop.
Turn off with....
```
gsettings set org.gnome.desktop.background show-desktop-icons false
```
Then kill nautilus...
```
nautilus -q
```
[ATTACH=CONFIG]252196[/ATTACH] [ATTACH=CONFIG]252198[/ATTACH]

---

