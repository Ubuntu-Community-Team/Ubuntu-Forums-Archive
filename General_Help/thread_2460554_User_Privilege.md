---
title: "User Privilege?"
date: 2021-04-13
forum: General Help
---

### Post by Quarkrad on 2021-04-13
My wife's machine is running mate 18.04 - this machine cannot update via the Software Updater GUI.  The attached *update.png* shows all the updates that need installing - after clicking on _Install Now _the loader.png windows pops up and then crashes after a few seconds of visibility.  I'm guessing there is an update that needs sudo privilege and it is the inability to launch the sudo window that is causing the crash. (This machine also has problems launching any gui that is followed by the sudo window - e.g. Synaptic.  (The following sudo window that normally pops up where you enter your password fails to launch and whatever gui is initially launched crashes).   One can update using the terminal but as this is my wife's machine the gui interface is preferred.

---

### Post by TheFu on 2021-04-13
Could be a case of sudo abuse.  Using sudo when it isn't needed, especially with GUI applications.  When this happens, some directories and files get created with root:root as the owner/group in the userid's HOME.  **sudo chown -R $USER:$USER $HOME** should fix it with very few negative side effects.

Mate-18.04 support ends (3 yrs) soon.  Time to move to 20.04 if staying on Mate is desired.

Is her account in the "sudo" group? Otherwise, she can't run the updates.

I prefer patching weekly, on the weekends, so any problems don't impact the work-week and have a few days to be corrected on Sat/Sun.

---

### Post by Quarkrad on 2021-04-13
Afraid that hasn't worked - wife is member of sudoers group.

---

### Post by TheFu on 2021-04-13
> **Quarkrad said:**
> Afraid that hasn't worked - wife is member of sudoers group.

What hasn't worked?  Also, text rather than images, please.

---

### Post by ActionParsnip on 2021-04-13
If she uses sudo in the terminal is it ok? If you run a test command like
```

sudo ls

```
is it OK and no issues?

---

### Post by Quarkrad on 2021-04-13
If I type /usr/bin/update-manager in the terminal the graphical software updater is launched - from there, I get the same response as #1. I.e. the sudo window asking me to enter the sudo password does not launch and the gui crashes.   If I enter sudo gparted in the terminal I get asked for my password and the gui opens - the gui will not open if I try and launch it from the main menu.

Any gui application that needs to fully launch by also asking for the sudo password (e.g. gparted, synaptic) crashes because the gui window asking for the sudo password never opens - the whole thing crashes.  If I open the same gui applications from the terminal preceded by sudo ....  the gui opens.

```
liz@lizubuntu:~$ sudo gparted
[sudo] password for liz: 
```

Also:

```
liz@lizubuntu:~$ sudo ls
cmcanu	 Documents  Music     Public  Templates
Desktop  Downloads  Pictures  snap    Videos

```

---

### Post by TheFu on 2021-04-13
Did you have her userid run: 
```
 sudo chown -R $USER:$USER $HOME
```

BTW, whenever using sudo with any GUI program, please, please, please, use **sudo -H** so the HOME directory environment will be changed to /root/.

Is the problem only with her account or does it happen to all sudo-capable accounts?

---

### Post by Quarkrad on 2021-04-13
I have used your command (sudo chown) and it has made no difference.  Wife is the only user on this machine - I will create another test user and report back.

---

### Post by deadflowr on 2021-04-13
What happens when you try running the terminal apt update/upgrade commands?

---

### Post by Quarkrad on 2021-04-13
If I run the normal update commands everything is fine.  Most things I've tried using the terminal works OK - but I do not use this machine much as it is the wife's and almost everything see does is via the gui.

---

### Post by Quarkrad on 2021-04-13
I have created a new user called test with the password test - using the terminal.  I try and launch gparted and the authentication window comes up asking me for the password for liz (althoughI'm logged into the new user test account.  I can only launch gparted using the liz password, not test.  If I try and add test to the sudoers group I get:

```
test@lizubuntu:~$ sudo usermod -aG sudo test
[sudo] password for test: 
test is not in the sudoers file.  This incident will be reported.
test@lizubuntu:~$ sudo usermod -aG sudo test
[sudo] password for test: 
Sorry, try again.
[sudo] password for test: 

```

The first attempt above I use test as the password - the second attempt I used my wife's password.

---

### Post by CelticWarrior on 2021-04-13
Only the user already in sudoers can add another with the same level of permissions.

---

### Post by TheFu on 2021-04-13
We're trying to figure out if this is really a **sudo** issue or a **pkexec** issue or an environment issue.
I never use the GUI for software updates and rarely use any menu, so I don't have any clue which programs in the menus use sudo/pkexec in their .desktop files. I suppose a quick grep would find those.

```
tf@hadar:/var/lib/menu-xdg/applications/menu-xdg$ egrep pkexec *
X-Debian-Applications-System-Package-Management-synaptic_package_manager.desktop:Exec=x-terminal-emulator -e synaptic-pkexec

tf@hadar:/var/lib/menu-xdg/applications/menu-xdg$ which synaptic-pkexec
/usr/bin/synaptic-pkexec

tf@hadar:/var/lib/menu-xdg/applications/menu-xdg$ file /usr/bin/synaptic-pkexec
/usr/bin/synaptic-pkexec: POSIX shell script, ASCII text executable

tf@hadar:/var/lib/menu-xdg/applications/menu-xdg$ more /usr/bin/synaptic-pkexec 
#!/bin/sh
pkexec "/usr/sbin/synaptic" "$@"
```

I looked at the script: /usr/sbin/gparted ... and it has 
```
**pkexec** --disable-internal-agent '/usr/sbin/gparted' "$@"
```
inside it.  Eventually, it calls **gpartedbin** as the real program.  

What does all this mean?  It means that gparted uses pkexec unless it is called by itself using pkexec. Also, in the script it does to X/11 xhost + magic to ensure it always works, then it cleans up itself after.  Nice of them to do that to avoid hassles that some other programs (cough ... every GUI file manager) will likely see.

---

### Post by Quarkrad on 2021-04-13
```
liz@lizubuntu:~$ /var/lib/menu-xdg/applications/menu-xdg$ egrep pkexec *
bash: /var/lib/menu-xdg/applications/menu-xdg$: No such file or directory
liz@lizubuntu:~$ X-Debian-Applications-System-Package-Management-synaptic_package_manager.desktop:Exec=x-terminal-emulator -e synaptic-pkexec
X-Debian-Applications-System-Package-Management-synaptic_package_manager.desktop:Exec=x-terminal-emulator: command not found
liz@lizubuntu:~$ /var/lib/menu-xdg/applications/menu-xdg$ which synaptic-pkexec
bash: /var/lib/menu-xdg/applications/menu-xdg$: No such file or directory
liz@lizubuntu:~$ /usr/bin/synaptic-pkexec
==== AUTHENTICATING FOR com.ubuntu.pkexec.synaptic ===
Authentication is required to run the Synaptic Package Manager
Authenticating as: liz,,, (liz)
Password: 
polkit-agent-helper-1: error response to PolicyKit daemon: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: No session for cookie
==== AUTHENTICATION FAILED ===
Error executing command as another user: Not authorized

This incident has been reported.
liz@lizubuntu:~$ 
```

Also - in /usr/sbin/gparted I have the command

```
pkexec --disable-internal-agent '/usr/sbin/gparted' "$@"
	status=$?
```

---

### Post by Quarkrad on 2021-04-13
Sorry didn't really understand what to do.  I have the same output as your good self:

```
liz@lizubuntu:~$ cd /var/lib/menu-xdg/applications/menu-xdg
liz@lizubuntu:/var/lib/menu-xdg/applications/menu-xdg$ egrep pkexec *
X-Debian-Applications-System-Package-Management-synaptic_package_manager.desktop:Exec=x-terminal-emulator -e synaptic-pkexec
liz@lizubuntu:/var/lib/menu-xdg/applications/menu-xdg$ which synaptic-pkexec
/usr/bin/synaptic-pkexec
liz@lizubuntu:/var/lib/menu-xdg/applications/menu-xdg$ file /usr/bin/synaptic-pkexec
/usr/bin/synaptic-pkexec: POSIX shell script, ASCII text executable
liz@lizubuntu:/var/lib/menu-xdg/applications/menu-xdg$ more /usr/bin/synaptic-pkexec
#!/bin/sh
pkexec "/usr/sbin/synaptic" "$@"

```

And as in #14 I also appear to have the same coding in the /usr/sbin/gparted scipt.

---

### Post by deadflowr on 2021-04-13
> polkit-agent-helper-1: error response to PolicyKit daemon: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: No session for cookie
This might mean the polkit agent isn't running, or something's not running properly.
Check if it's enabled in autostart
```
cat /etc/xdg/autostart/polkit-mate-authentication-agent-1.desktop 
```
What does polkit's systemd status show:
```
systemctl status polkit
```

---

### Post by Quarkrad on 2021-04-13
```
liz@lizubuntu:~$ cat /etc/xdg/autostart/polkit-mate-authentication-agent-1.desktop
[Desktop Entry]
Name=PolicyKit Authentication Agent
Name[am]=&#4840; &#4768;&#4656;&#4651;&#4653; &#4901;&#4677;&#4621; &#4635;&#4648;&#4875;&#4872;&#4907; &#4808;&#4778;&#4621;
Name[ar]=&#1605;&#1583;&#1610;&#1585; &#1575;&#1604;&#1575;&#1587;&#1578;&#1610;&#1579;&#1575;&#1602; PolicyKit
Name[be]=PolicyKit, &#1072;&#1075;&#1077;&#1085;&#1090; &#1072;&#1118;&#1090;&#1101;&#1085;&#1090;&#1099;&#1092;&#1110;&#1082;&#1072;&#1094;&#1099;&#1110;
Name[bg]=&#1055;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1072; &#1079;&#1072; &#1080;&#1076;&#1077;&#1085;&#1090;&#1080;&#1092;&#1080;&#1082;&#1072;&#1094;&#1080;&#1103; PolicyKit
Name[bn_IN]=PolicyKit &#2437;&#2472;&#2497;&#2478;&#2507;&#2470;&#2472;&#2503;&#2480; &#2447;&#2460;&#2503;&#2472;&#2509;&#2463;
Name[ca]=Agent d'autenticació PolicyKit
Name[ca@valencia]=Agent d'autenticació PolicyKit
Name[cmn]=PolicyKit &#39511;&#35657;&#20195;&#29702;&#31243;&#24335;
Name[cs]=Ov&#283;&#345;ovací agent PolicyKit
Name[da]=Godkendelsesprogrammet PolicyKit
Name[de]=PolicyKit-Legitimationsagent
Name[el]=&#928;&#961;&#940;&#954;&#964;&#959;&#961;&#945;&#962; &#960;&#953;&#963;&#964;&#959;&#960;&#959;&#943;&#951;&#963;&#951;&#962; PolicyKit
Name[en_AU]=PolicyKit Authentication Agent
Name[en_GB]=PolicyKit Authentication Agent
Name[es]=Agente de autenticación de PolicyKit
Name[es_CO]=Agente de autenticación PolicyKit
Name[et]=Autentimisagent PolicyKit
Name[eu]=PolicyKit autentifikatzeko agentea
Name[fi]=PolicytKit-tunnistautumisohjelma
Name[fr]=Agent d'authentification de PolicyKit
Name[gl]=Axente de autenticación PolicyKit
Name[gu]=PolicyKit &#2744;&#2724;&#2765;&#2724;&#2750;&#2727;&#2751;&#2709;&#2736;&#2723; &#2703;&#2716;&#2728;&#2765;&#2719;
Name[he]=&#1505;&#1493;&#1499;&#1503; &#1492;&#1488;&#1497;&#1502;&#1493;&#1503; PolicyKit
Name[hi]=PolicyKit &#2346;&#2381;&#2352;&#2350;&#2366;&#2339;&#2368;&#2325;&#2352;&#2339; &#2346;&#2381;&#2352;&#2340;&#2367;&#2344;&#2367;&#2343;&#2367;
Name[hr]=Programski izvršitelj pravila ovjere
Name[hu]=PolicyKit hitelesítési ügynök
Name[hy]=PolicyKit &#1350;&#1400;&#1410;&#1397;&#1398;&#1377;&#1391;&#1377;&#1398;&#1377;&#1409;&#1396;&#1377;&#1398; &#1379;&#1400;&#1408;&#1390;&#1377;&#1391;&#1377;&#1388;&#1384;
Name[id]=PolicyKit Authentication Agent
Name[is]=PolicyKit auðkenningarþjónn
Name[it]=Agente di autenticazione per PolicyKit
Name[ja]=PolicyKit &#35469;&#35388;&#12456;&#12540;&#12472;&#12455;&#12531;&#12488;
Name[kk]=PolicyKit &#1072;&#1091;&#1090;&#1077;&#1085;&#1090;&#1080;&#1092;&#1080;&#1082;&#1072;&#1094;&#1080;&#1103; &#1072;&#1075;&#1077;&#1085;&#1090;&#1110;
Name[kn]=PolicyKit &#3238;&#3267;&#3234;&#3264;&#3221;&#3248;&#3235; &#3246;&#3239;&#3277;&#3247;&#3253;&#3248;&#3277;&#3236;&#3263;
Name[ko]=PolicyKit &#51064;&#51613; &#50640;&#51060;&#51204;&#53944;
Name[lt]=PolicyKit tapatyb&#279;s nustatymo agentas
Name[lv]=PolicyKot Apliecin&#257;juma A&#291;ents
Name[ml]=&#3370;&#3403;&#3379;&#3391;&#3384;&#3391;&#3349;&#3405;&#3349;&#3391;&#3377;&#3405;&#3377;&#3405; &#3347;&#3365;&#3368;&#3405;&#3377;&#3391;&#3349;&#3405;&#3349;&#3399;&#3383;&#3368;&#3405;* &#3343;&#3356;&#3368;&#3405;&#3377;&#3405;
Name[mr]=PolicyKit &#2321;&#2341;&#2375;&#2306;&#2335;&#2368;&#2325;&#2375;&#2358;&#2344; &#2319;&#2332;&#2375;&#2306;&#2335;
Name[ms]=Ejen Pengesahihan PolicyKit
Name[nb]=Agent for fodkjennelsesprogrammet PolicyKit
Name[nl]=PolicyKit Authenticatie-agent
Name[oc]=Agent d'autentificacion de PolicyKit
Name[or]=PolicyKit &#2860;&#2888;&#2855;&#2879;&#2837;&#2864;&#2851; &#2872;&#2854;&#2872;&#2893;&#2911;
Name[pa]=&#2602;&#2622;&#2610;&#2616;&#2624;&#2581;&#2623;&#2673;&#2591; &#2602;&#2608;&#2606;&#2622;&#2595;&#2581;&#2623;&#2596;&#2622; &#2575;&#2588;&#2672;&#2591;
Name[pl]=Agent uwierzytelniania PolicyKit
Name[pt]=Agente de Autenticação PolicyKit
Name[pt_BR]=Agente de autenticação PolicyKit
Name[ro]=Agent de autentificare PolicyKit
Name[ru]=&#1040;&#1075;&#1077;&#1085;&#1090; &#1072;&#1091;&#1090;&#1077;&#1085;&#1090;&#1080;&#1092;&#1080;&#1082;&#1072;&#1094;&#1080;&#1080; PolicyKit
Name[sk]=Agent PolicyKit na overovanie totožnosti
Name[sl]=Posrednik overjanja PolicyKit
Name[sr]=&#1040;&#1075;&#1077;&#1085;&#1090; &#1087;&#1086;&#1090;&#1074;&#1088;&#1106;&#1080;&#1074;&#1072;&#1114;&#1072; &#1080;&#1076;&#1077;&#1085;&#1090;&#1080;&#1090;&#1077;&#1090;&#1072; &#1055;&#1088;&#1080;&#1073;&#1086;&#1088; &#1087;&#1086;&#1083;&#1080;&#1090;&#1080;&#1082;&#1077;
Name[sv]=Autentiseringsagent för PolicyKit
Name[ta]=PolicyKit &#2949;&#2969;&#3021;&#2965;&#3008;&#2965;&#3006;&#2992; &#2990;&#3009;&#2965;&#2997;&#2992;&#3021;
Name[te]=&#3114;&#3134;&#3122;&#3128;&#3136;&#3093;&#3135;&#3103;&#3149; &#3111;&#3139;&#3125;&#3136;&#3093;&#3120;&#3107; &#3114;&#3149;&#3120;&#3108;&#3135;&#3112;&#3135;&#3111;&#3135;
Name[th]=&#3605;&#3633;&#3623;&#3585;&#3621;&#3634;&#3591;&#3626;&#3635;&#3627;&#3619;&#3633;&#3610;&#3618;&#3639;&#3609;&#3618;&#3633;&#3609;&#3605;&#3633;&#3623;&#3610;&#3640;&#3588;&#3588;&#3621; PolicyKit
Name[tr]=PolicyKit Kimlik Do&#287;rulama Arac&#305;
Name[uk]=&#1040;&#1075;&#1077;&#1085;&#1090; &#1088;&#1086;&#1079;&#1087;&#1110;&#1079;&#1085;&#1072;&#1085;&#1085;&#1103; PolicyKit
Name[ur]=&#1662;&#1575;&#1604;&#1740;&#1587;&#1740; &#1705;&#1616;&#1657; PolicyKit &#1578;&#1608;&#1579;&#1740;&#1602;&#1740; &#1575;&#1740;&#1580;&#1606;&#1657;
Name[vi]=PolicyKit Authentication Agent
Name[zh_CN]=PolicyKit &#35748;&#35777;&#20195;&#29702;
Name[zh_HK]=PolicyKit &#39511;&#35657;&#20195;&#29702;&#31243;&#24335;
Name[zh_TW]=PolicyKit &#39511;&#35657;&#20195;&#29702;&#31243;&#24335;
Comment=PolicyKit Authentication Agent for the MATE Desktop
Comment[am]=&#4840; &#4768;&#4656;&#4651;&#4653; &#4901;&#4677;&#4621; &#4635;&#4648;&#4875;&#4872;&#4907; &#4808;&#4778;&#4621; &#4616; &#4636;&#4725; &#4852;&#4661;&#4781;&#4726;&#4949;
Comment[ar]=&#1593;&#1605;&#1610;&#1604; &#1575;&#1604;&#1575;&#1587;&#1578;&#1610;&#1579;&#1575;&#1602; PolicyKit &#1604;&#1587;&#1591;&#1581; &#1605;&#1603;&#1578;&#1576; &#1605;&#1578;&#1617;&#1577;
Comment[be]=PolicyKit, &#1072;&#1075;&#1077;&#1085;&#1090; &#1072;&#1118;&#1090;&#1101;&#1085;&#1090;&#1099;&#1092;&#1110;&#1082;&#1072;&#1094;&#1099;&#1110; &#1076;&#1083;&#1103; &#1072;&#1089;&#1103;&#1088;&#1086;&#1076;&#1076;&#1079;&#1103; MATE
Comment[bg]=&#1055;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1072; &#1079;&#1072; &#1080;&#1076;&#1077;&#1085;&#1090;&#1080;&#1092;&#1080;&#1082;&#1072;&#1094;&#1080;&#1103; PolicyKit &#1079;&#1072; MATE
Comment[ca]=Agent d'autenticació PolicyKit per a l'escriptori MATE
Comment[ca@valencia]=Agent d'autenticació PolicyKit per a l'escriptori MATE
Comment[cs]=Ov&#283;&#345;ovací agent PolicyKit pro MATE Desktop 
Comment[da]=Godkendelsesprogrammet PolicyKit for MATE-skrivebordet
Comment[de]=PolicyKit-Legitimationsagent für die MATE-Arbeitsumgebung
Comment[el]=&#928;&#961;&#940;&#954;&#964;&#959;&#961;&#945;&#962; &#960;&#953;&#963;&#964;&#959;&#960;&#959;&#943;&#951;&#963;&#951;&#962; PolicyKit &#947;&#953;&#945; &#964;&#959; MATE Desktop
Comment[en_AU]=PolicyKit Authentication Agent for the MATE Desktop
Comment[en_GB]=PolicyKit Authentication Agent for the MATE Desktop
Comment[es]=Agente de autenticación de PolicyKit para escritorio MATE
Comment[es_CO]=Agente de autenticación PolicyKit para el entorno MATE
Comment[et]=MATE töölaua autentimisagent PolicyKit
Comment[fi]=PolicyKit-tunnistautumisagentti MATE-työpöydälle
Comment[fr]=Agent d'authentification PolicyKit pour MATE Desktop
Comment[gl]=Axente de autenticación PolicyKit para o escritorio MATE
Comment[he]=&#1505;&#1493;&#1499;&#1503; &#1492;&#1488;&#1497;&#1502;&#1493;&#1503; PolicyKit &#1506;&#1489;&#1493;&#1512; &#1513;&#1493;&#1500;&#1495;&#1503; &#1492;&#1506;&#1489;&#1493;&#1491;&#1492; MATE
Comment[hi]=&#2350;&#2366;&#2335;&#2375; &#2337;&#2375;&#2360;&#2381;&#2325;&#2335;&#2377;&#2346; &#2325;&#2375; &#2354;&#2367;&#2319; &#2346;&#2379;&#2354;&#2367;&#2360;&#2368;&#2325;&#2367;&#2335; &#2346;&#2381;&#2352;&#2350;&#2366;&#2339;&#2368;&#2325;&#2352;&#2339; &#2328;&#2335;&#2325;
Comment[hr]=Programski izvršitelj pravila ovjere za radno okruženje MATE
Comment[hu]=PolicyKit hitelesítési ügynök a MATE Desktophoz
Comment[hy]=PolicyKit &#1350;&#1400;&#1410;&#1397;&#1398;&#1377;&#1391;&#1377;&#1398;&#1377;&#1409;&#1396;&#1377;&#1398; &#1379;&#1400;&#1408;&#1390;&#1377;&#1391;&#1377;&#1388;&#1384; MATE &#1377;&#1399;&#1389;&#1377;&#1407;&#1377;&#1398;&#1412;&#1377;&#1397;&#1387;&#1398; &#1405;&#1381;&#1394;&#1377;&#1398;&#1387; &#1392;&#1377;&#1396;&#1377;&#1408;
Comment[id]=Agen Autentikasi PolicyKit untuk MATE Desktop
Comment[is]=PolicyKit auðkenningarþjónn fyrir MATE-skjáborðið
Comment[it]=Agente di autenticazione per PolicyKit di MATE Desktop
Comment[ja]=PolicyKit &#35469;&#35388;&#12456;&#12540;&#12472;&#12455;&#12531;&#12488;
Comment[kk]=MATE &#1078;&#1201;&#1084;&#1099;&#1089; &#1199;&#1089;&#1090;&#1077;&#1083;&#1110; &#1199;&#1096;&#1110;&#1085; PolicyKit &#1072;&#1091;&#1090;&#1077;&#1085;&#1090;&#1080;&#1092;&#1080;&#1082;&#1072;&#1094;&#1080;&#1103; &#1072;&#1075;&#1077;&#1085;&#1090;&#1110;
Comment[ko]=&#47560;&#53580; &#45936;&#49828;&#53356;&#53681;&#50857; &#51221;&#52293;&#53412;&#53944; &#51064;&#51613; &#50640;&#51060;&#51204;&#53944;
Comment[lt]=PolicyKit tapatyb&#279;s nustatymo agentas MATE darbalaukiui
Comment[mr]=MATE &#2337;&#2375;&#2360;&#2381;&#2325;&#2335;&#2366;&#2373;&#2346;&#2360;&#2366;&#2336;&#2368; PolicyKit &#2321;&#2341;&#2375;&#2306;&#2335;&#2368;&#2325;&#2375;&#2358;&#2344; &#2319;&#2332;&#2375;&#2306;&#2335;
Comment[ms]=Ejen pengesahihan PolicyKit untuk Desktop MATE
Comment[nb]=Godkjennelsesprogrammet PolicyKit for MATE-skrivebordet
Comment[nl]=PolicyKit Authenticatie-agent voor de MATE-werkomgeving
Comment[oc]=Agent d'autentificacion PolicyKit per MATE Desktop
Comment[pl]=Agent uwierzytelniania PolicyKit dla MATE
Comment[pt]=Agente de Autenticação PolicyKit do Ambiente MATE
Comment[pt_BR]=Agente de autenticação PolicyKit para o ambiente de trabalho MATE
Comment[ro]=Agent de autentificare PolicyKit
Comment[ru]=&#1040;&#1075;&#1077;&#1085;&#1090; &#1072;&#1091;&#1090;&#1077;&#1085;&#1090;&#1080;&#1092;&#1080;&#1082;&#1072;&#1094;&#1080;&#1080; PolicyKit &#1076;&#1083;&#1103; &#1088;&#1072;&#1073;&#1086;&#1095;&#1077;&#1081; &#1089;&#1088;&#1077;&#1076;&#1099; MATE
Comment[sk]=PolicyKit Authentication Agent pre MATE Desktop
Comment[sl]=Posrednik overitve PolicyKit za namizje MATE
Comment[sr]=&#1055;&#1088;&#1080;&#1073;&#1086;&#1088; &#1087;&#1086;&#1083;&#1080;&#1090;&#1080;&#1082;&#1077; &#1112;&#1077; &#1072;&#1075;&#1077;&#1085;&#1090; &#1079;&#1072; &#1087;&#1086;&#1090;&#1074;&#1088;&#1106;&#1080;&#1074;&#1072;&#1114;&#1077; &#1080;&#1076;&#1077;&#1085;&#1090;&#1080;&#1090;&#1077;&#1090;&#1072; &#1079;&#1072; &#1052;&#1077;&#1112;&#1090;&#1086;&#1074;&#1091; &#1088;&#1072;&#1076;&#1085;&#1091; &#1087;&#1086;&#1074;&#1088;&#1096;
Comment[sv]=PolicyKit autentiseringsagent för MATE skrivbordsmiljön
Comment[th]=&#3605;&#3633;&#3623;&#3585;&#3621;&#3634;&#3591;&#3626;&#3635;&#3627;&#3619;&#3633;&#3610;&#3618;&#3639;&#3609;&#3618;&#3633;&#3609;&#3605;&#3633;&#3623;&#3610;&#3640;&#3588;&#3588;&#3621; PolicyKit &#3626;&#3635;&#3627;&#3619;&#3633;&#3610;&#3614;&#3639;&#3657;&#3609;&#3650;&#3605;&#3658;&#3632;&#3586;&#3629;&#3591; MATE
Comment[tr]=MATE Masaüstü için PolicyKit Kimlik Do&#287;rulama Arac&#305;
Comment[uk]=&#1040;&#1075;&#1077;&#1085;&#1090; &#1088;&#1086;&#1079;&#1087;&#1110;&#1079;&#1085;&#1072;&#1085;&#1085;&#1103; PolicyKit &#1076;&#1083;&#1103; &#1089;&#1090;&#1110;&#1083;&#1100;&#1085;&#1080;&#1094;&#1110; MATE
Comment[vi]=PolicyKit Authentication Agent cho môi tr&#432;&#7901;ng MATE
Comment[zh_CN]=MATE &#26700;&#38754;&#30340; PolicyKit &#35748;&#35777;&#20195;&#29702;
Comment[zh_TW]=MATE &#26700;&#38754;&#29872;&#22659;&#30340; PolicyKit &#39511;&#35657;&#20195;&#29702;&#31243;&#24335;
Exec=/usr/lib/x86_64-linux-gnu/polkit-mate/polkit-mate-authentication-agent-1
Terminal=false
Type=Application
Categories=
NoDisplay=true
OnlyShowIn=MATE;
X-MATE-AutoRestart=true
```

and 

```
liz@lizubuntu:~$ systemctl status polkit
&#9679; polkit.service - Authorization Manager
   Loaded: loaded (/lib/systemd/system/polkit.service; static; vendor preset: en
   Active: active (running) since Tue 2021-04-13 20:54:59 BST; 4min 1s ago
     Docs: man:polkit(8)
 Main PID: 856 (polkitd)
    Tasks: 3 (limit: 3982)
   CGroup: /system.slice/polkit.service
           &#9492;&#9472;856 /usr/lib/policykit-1/polkitd --no-debug

Apr 13 20:54:59 lizubuntu systemd[1]: Starting Authorization Manager...
Apr 13 20:54:59 lizubuntu polkitd[856]: started daemon version 0.105 using autho
Apr 13 20:54:59 lizubuntu systemd[1]: Started Authorization Manager.

```

---

### Post by Quarkrad on 2021-04-13
Slight difference to my machine but I'm on 20.04

---

### Post by deadflowr on 2021-04-13
Was that the full output for the status command?
Seems to be missing the crucial last line,
which should show what registered authentication agent is in use.
If you run the Exec command from the autostart desktop file what happens:
```
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
```

---

### Post by Quarkrad on 2021-04-14
Sorry I am not sure what you want me to do - I do not understand the last sentence, what is the autostart desktop file? 

When I run systemctl status polkit (from a terminal on my Desktop) **ON MY MACHINE** the last line is:
 

```
Apr 14 06:58:28 dadubuntu polkitd(authority=local)[658]: Registered Authentication Agent for unix-session:c1 (system bus name :1.57 [/usr/lib/x86_64-linux-gnu/polkit-mate/polkit-mate-authentication-agent-1], object path /org/mate/PolicyKit1/AuthenticationAgent, locale en_GB.UTF-8)
```

When I run the status command on my wife's machine there is no such line - so the output in #17 was correct.  I have run the command on her machine a number of times - she does not have a last line like mine above.

---

### Post by deadflowr on 2021-04-14
> Sorry I am not sure what you want me to do - I do not understand the last sentence, what is the autostart desktop file?
That was the file you posted for the first output in post #17.
The line I posted was the Exec entry, which is what the file actually runs.
I was thinking maybe the autostart file wasn't running properly.
I believe if the file is running properly then the output should show something about it unable to do it because an agent already exists.

That said, I also think maybe you can try a reinstall of the mate-polkit package.
```
sudo apt install --reinstall mate-polkit
```

---

### Post by Quarkrad on 2021-04-14
Appreciate your help - nervous on this machine as it is the wife's!  Unfortunately reinstalling the polkit has made no difference.

deadflowr:  not sure how to change thread title. Should be Use**r** Privilege - mis spelling on my part!

---

### Post by ajgreeny on 2021-04-14
I have edited the thread title for you but all subsequent posts will retain the original typo I'm afraid and I think the thread title on the first post is the important one when searching the forum.

Just to check on your wife's problem, have any edits been made to the /etc/sudoers file; if that is done without using ***sudo visudo*** as the means of an edit, minor incorrect syntax edits can cause problems of this sort.
To check that let's see the output of command ```
sudo cat /etc/sudoers
``` which may throw up some answers, though, of course, it may not.

---

### Post by Quarkrad on 2021-04-14
```
liz@lizubuntu:~$ sudo cat /etc/sudoers
[sudo] password for liz: 
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults	env_reset
Defaults	mail_badpass
Defaults	secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d
liz@lizubuntu:~$ sudo cat /etc/sudoers

```

---

### Post by ActionParsnip on 2021-04-14
If you add the users to the admin group, does it help?

---

### Post by Quarkrad on 2021-04-14
Do you mean the sudoers groups?  Wife is already a member #3

---

### Post by ajgreeny on 2021-04-14
Just for clarity there is no such group as **sudoers**, only a **sudo** group, and as you show in post #3 your wife is a member of **sudo** and **adm** (admin) groups.

Your /etc/sudoers file is absolutely fine with no problems that I can see, so I am totally baffled by this problem your wife is seeing.

---

### Post by Quarkrad on 2021-04-19
bump

---

### Post by Quarkrad on 2021-04-19
I've just reinstalled ubuntu mate 18.04 - only / as I have a separate /home partition and that stayed the same.   To my surprise I still have the same problem.  I though reinstalling would have sorted everything out so I assuming there must be some sort of config setting in /home that is causing my problems.

---

