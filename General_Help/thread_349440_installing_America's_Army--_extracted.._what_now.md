---
title: "installing America's Army-- extracted.. what now??"
date: 2007-01-30
forum: General Help
---

### Post by presbp on 2007-01-30
I have download america's army 2.8 and extracted it but when I cd into the new directory and do ./configure I get no such file or directory.  What do I do??

---

### Post by renzokuken on 2007-01-30
Correct me if i'm wrong but is Americas Army a windows game?

If thats the case then you will need "wine" to run it. what are the contents of the directory you are trying to run ./configure from?

---

### Post by presbp on 2007-01-30
no there is a Linux version I downloaded the tar.bz2 file and extracted it and then cd'ed into the new directory and typed ./configure and it said no such file or directory.

---

### Post by taurus on 2007-01-30
I bet you probably just run it.  Change to the new directory that created after you unpacked it and list the output of this command here.

```
ls -la
```

---

### Post by presbp on 2007-01-30
total 40
drwxr-xr-x 10 presbp presbp 4096 2006-12-29 03:36 .
drwxr-xr-x  3 presbp presbp 4096 2007-01-30 11:32 ..
drwxr-xr-x  2 presbp presbp 4096 2006-12-21 12:28 Animations
drwxr-xr-x  2 presbp presbp 4096 2006-12-21 12:28 KarmaData
drwx------  2 presbp presbp 4096 2006-12-29 03:36 Logs
drwxr-xr-x  2 presbp presbp 4096 2006-12-21 12:29 Maps
drwxr-xr-x  2 presbp presbp 4096 2006-12-21 12:29 Sounds
drwxr-xr-x  2 presbp presbp 4096 2006-12-21 12:30 StaticMeshes
drwxr-xr-x  8 presbp presbp 4096 2006-12-29 04:23 System
drwxr-xr-x  2 presbp presbp 4096 2006-12-21 12:31 Textures

there are the contents.

---

### Post by taurus on 2007-01-30
Change to the System directory and list the content of it.

```
cd System
ls -la
```

---

### Post by presbp on 2007-01-30
drwxr-xr-x  8 presbp presbp     4096 2006-12-29 04:23 .
drwxr-xr-x 10 presbp presbp     4096 2006-12-29 03:36 ..
-r--r--r--  1 presbp presbp       56 2006-12-21 12:31 aa.sdk.key.data
-r--r--r--  1 presbp presbp   470662 2006-12-21 12:31 aa.sdk.rsa.data
-r--r--r--  1 presbp presbp     3437 2006-12-21 12:31 AdditionalCredits.txt
-rwx------  1 presbp presbp    42107 2006-12-21 16:10 AGP_AI.u
-rwx------  1 presbp presbp   105232 2006-12-21 16:10 AGP_Armory.u
-rwx------  1 presbp presbp   185442 2006-12-21 16:10 AGP_Characters.u
-rwx------  1 presbp presbp   206647 2006-12-21 16:10 AGP_Effects.u
-rwx------  1 presbp presbp   524876 2006-12-21 16:10 AGP_Gameplay.u
-rwx------  1 presbp presbp    83244 2006-12-21 16:10 AGP_Game.u
-r--r--r--  1 presbp presbp       99 2006-12-21 12:31 AGP.int
-r--r--r--  1 presbp presbp    59915 2006-12-21 12:31 AGP_Interface.int
-rwx------  1 presbp presbp  1443460 2006-12-21 16:11 AGP_Interface.u
-rwx------  1 presbp presbp   998859 2006-12-21 16:11 AGP_Inventory.u
-rwx------  1 presbp presbp      884 2006-12-21 16:11 AGP_Objects.u
-rwx------  1 presbp presbp   901952 2006-12-21 16:11 AGP_Script.u
-rwx------  1 presbp presbp     4720 2006-12-21 16:11 AGP_Security.u
-rwx------  1 presbp presbp  2325353 2006-12-21 16:10 AGP.u
-rwx------  1 presbp presbp   311829 2006-12-21 16:11 AGP_UI.u
-rwx------  1 presbp presbp    32248 2006-12-21 16:11 AGP_Utils.u
-r--r--r--  1 presbp presbp     5233 2006-12-21 12:31 AGP_Vehicles.int
-rwx------  1 presbp presbp   528238 2006-12-21 16:12 AGP_Vehicles.u
-r--r--r--  1 presbp presbp      254 2006-12-21 12:31 ALAudio.int
-r--r--r--  1 presbp presbp     9565 2006-12-21 12:31 ArmyGameEULA.rtf
-r--r--r--  1 presbp presbp     7253 2006-12-21 12:31 ArmyOpsGlossary.txt
-r--r--r--  1 presbp presbp    11797 2006-12-21 12:31 ArmyOpsReadMe.txt
-r--r--r--  1 presbp presbp      151 2006-12-21 12:31 BUGSUBMIT.url
-r--r--r--  1 presbp presbp       73 2006-12-21 12:31 Build.ini
drwxr-xr-x  2 presbp presbp     4096 2006-12-21 12:29 conf
drwxr-xr-x  2 presbp presbp     4096 2006-12-21 12:31 Config
-r--r--r--  1 presbp presbp     3628 2006-12-21 12:31 Core.int
-rwx------  1 presbp presbp    63207 2006-12-21 16:12 Core.u
-r--r--r--  1 presbp presbp    17216 2006-12-21 12:31 CountryFlags.ini
-r--r--r--  1 presbp presbp     3015 2006-12-21 12:31 creditsarmy.txt
-r--r--r--  1 presbp presbp     4918 2006-12-21 12:31 credits.txt
-r--r--r--  1 presbp presbp      359 2006-12-21 12:31 D3DDrv.int
-rwx------  1 presbp presbp    81228 2006-12-21 16:12 DBAuth.u
-rwxr-xr-x  1 presbp presbp     9316 2006-12-21 12:31 DBMBS.so
-r--r--r--  1 presbp presbp    37253 2006-12-21 12:31 Default.ini
-r--r--r--  1 presbp presbp     3359 2006-12-21 12:31 DefUnrealEd.ini
-r--r--r--  1 presbp presbp    12239 2006-12-21 12:31 DefUser.ini
drwxr-xr-x  2 presbp presbp     4096 2006-12-21 12:31 Descriptions
-r--r--r--  1 presbp presbp       32 2006-12-21 12:31 Distribution.ini
-r--r--r--  1 presbp presbp     9225 2006-12-21 12:31 Editor.int
-rwx------  1 presbp presbp   433987 2006-12-21 16:12 Editor.u
-r--r--r--  1 presbp presbp    19174 2006-12-21 12:31 Engine.int
-rwx------  1 presbp presbp  2429145 2006-12-21 16:12 Engine.u
-r--r--r--  1 presbp presbp      899 2006-12-21 12:31 FanSites.ini
-rwx------  1 presbp presbp     9934 2006-12-21 16:13 Fire.u
-rwx------  1 presbp presbp   484037 2006-12-21 16:13 FSTS.u
-r--r--r--  1 presbp presbp     7513 2006-12-21 12:31 GamePlay.int
-rwx------  1 presbp presbp   155791 2006-12-21 16:13 GamePlay.u
-r--r--r--  1 presbp presbp     1825 2006-12-21 12:31 Help.ini
-r--r--r--  1 presbp presbp     1527 2006-12-21 12:31 IpDrv.int
-rwx------  1 presbp presbp   124867 2006-12-21 16:13 IpDrv.u
-r--r--r--  1 presbp presbp     6556 2006-12-21 12:31 KeyBindings.ini
-r-xr-xr-x  1 presbp presbp  3831849 2006-12-21 12:31 libdbauth.so
-r-xr-xr-x  1 presbp presbp   255861 2006-12-21 12:31 libgmp.so
-r--r--r--  1 presbp presbp    14245 2006-12-21 12:31 Links.ini
drwxr-xr-x  4 presbp presbp     4096 2006-12-21 12:31 LipSincData
-r--r--r--  1 presbp presbp      312 2006-12-21 12:31 mbs.demo.server.public.rsa.key
-r--r--r--  1 presbp presbp      930 2006-12-21 12:31 mbs.demo.server.rsa.key
-r--r--r--  1 presbp presbp     7173 2006-12-21 12:31 MBSFilters.ini
-r--r--r--  1 presbp presbp   743667 2006-12-21 12:31 npcaicc.decision.xml
-r--r--r--  1 presbp presbp   195519 2006-12-21 12:31 NPCAICC.speech.xml
-r--r--r--  1 presbp presbp     6298 2006-12-21 12:31 overview.txt
-r--r--r--  1 presbp presbp       68 2006-12-21 12:31 Packages.md5
-r--r--r--  1 presbp presbp     9321 2006-12-21 12:31 partners.ini
drwxr-xr-x  3 presbp presbp     4096 2006-12-21 12:31 pb
-r--r--r--  1 presbp presbp     5677 2006-12-21 12:31 PunkBusterEULA.rtf
drwxr-xr-x  2 presbp presbp     4096 2006-12-21 12:31 Save
-rwxr-xr-x  1 presbp presbp 12401868 2006-12-29 04:20 server-bin
-r--r--r--  1 presbp presbp    25359 2006-12-21 12:31 server.ini
-r--r--r--  1 presbp presbp     2274 2006-12-21 12:31 services.ini
-r--r--r--  1 presbp presbp     8871 2006-12-21 12:31 Setup.int
-r--r--r--  1 presbp presbp    11346 2006-12-21 12:31 Skins.int
-r--r--r--  1 presbp presbp      323 2006-12-21 12:31 SoftDrv.int
-r--r--r--  1 presbp presbp    66356 2006-12-21 12:31 splash.bmp
-r--r--r--  1 presbp presbp      313 2006-12-21 12:31 sso.public.rsa.key
-r--r--r--  1 presbp presbp     3936 2006-12-21 12:31 Startup.int
-r--r--r--  1 presbp presbp    25268 2006-12-21 12:31 tournament.ini
-r--r--r--  1 presbp presbp    22735 2006-12-21 12:31 tours.ini
-r--r--r--  1 presbp presbp      266 2006-12-21 12:31 UnrealEd.int
-rwx------  1 presbp presbp    11714 2006-12-21 16:13 UnrealEd.u
-r--r--r--  1 presbp presbp       61 2006-12-21 12:31 UPlaylists.ini
-rw-r--r--  1 presbp presbp    19518 2006-12-21 12:31 User.ini
-rwx------  1 presbp presbp    11325 2006-12-21 16:13 UTelnet.u
-r--r--r--  1 presbp presbp      121 2006-12-21 12:31 UWeb.int
-r--r--r--  1 presbp presbp      198 2006-12-21 12:31 Vehicles.int
-r--r--r--  1 presbp presbp     1624 2006-12-21 12:31 WeaponMods.ini
-r--r--r--  1 presbp presbp     2331 2006-12-21 12:31 Window.int
-r--r--r--  1 presbp presbp      680 2006-12-21 12:31 WinDrv.int
-r--r--r--  1 presbp presbp    50707 2006-12-21 12:31 XInterface.int
-rwx------  1 presbp presbp   934649 2006-12-21 16:13 XInterface.u

contents of system folder

---

### Post by taurus on 2007-01-30
Read the overview.txt to see what does it say.

```
more overview.txt
```
(Hit the space bar for the next 24 lines.)

---

### Post by presbp on 2007-01-30
all that says is an overview of what america's army actually is and how to play not how to install or anything like that.

---

### Post by Cirrocco on 2007-01-30
I vaguely recall there being a .sh or a .run file in there.

---

### Post by presbp on 2007-01-30
I don't see a sh or run file in there.  only a bin that is to launch the server for the game not the actual game itself

---

### Post by josesanders on 2007-01-30
Can you post the site you downloaded it from?  I can't seem to find the linux version.

---

### Post by presbp on 2007-01-30
[http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/FPS/America-s-Army-Link-Up-with-Dedicated-Server-for-Linux-10048.shtml](http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/FPS/America-s-Army-Link-Up-with-Dedicated-Server-for-Linux-10048.shtml)

yep there it is.

---

### Post by josesanders on 2007-01-30
Did you see this:
[http://forum.americasarmy.com/viewtopic.php?t=237481](http://forum.americasarmy.com/viewtopic.php?t=237481)

I'm still downloading, since the file is more than 2GB, but I'll try it later tonight when it finishes.

---

### Post by Hanzerik on 2007-01-30
AA 2.8 linux is for servers only, no client. Meaning that you will be able to host a AA 2.8 game server, but not actually play 2.8 on a linux machine.

Wonder if my name is still in the credits?

---

