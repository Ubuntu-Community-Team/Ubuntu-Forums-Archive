---
title: "Problems with GCC"
date: 2007-01-15
forum: General Help
---

### Post by Stomstedt on 2007-01-15
I am currently having an issue.  A program that has always worked in the past was working fine until I installed the update.  Now when I click the icon for the program, nothing happens.  I decided to open it in terminal.  Here is my result:

owner@owner-desktop:~$ graal
graal: /lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by graal)
owner@owner-desktop:~$ graalexe
/usr/bin/graal: /lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/bin/graal)
owner@owner-desktop:~$
owner@owner-desktop:

Please help with my issue.. I currently have GCC, but not 4.2.0.  I do not understand because I don't think 4.2.0 has been released yet.  

Thanks

---

### Post by taurus on 2007-01-15
```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by Stomstedt on 2007-01-15
owner@owner-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [50.9kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release [50.9kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release [50.9kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages [21.3kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [128kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [17.4kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages [964B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources [47.7kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [968B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [6178B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [49.2kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [88.7kB]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [6460B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages [2782B]
Fetched 523kB in 16s (32.2kB/s)
Reading package lists... Done
owner@owner-desktop:~$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  language-pack-en language-pack-gnome-en libgtop2-7 libkrb53
  openoffice.org openoffice.org-base openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk
  openoffice.org-impress openoffice.org-java-common
  openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer
  python-uno ttf-opensymbol xserver-xorg-core
0 packages upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
owner@owner-desktop:~$


Im still getting the same error :(

---

### Post by taurus on 2007-01-15
The program that plan to run requires you to have gcc 4.2 and I believe you only have version 4.1.2 on your machine right now.  So, either upgrade your gcc or maybe you need to download the source and build it again...

---

### Post by Stomstedt on 2007-01-15
Could you please tell me where i can find the source and build it?  I can only find GCC 4.1 on the website.

---

### Post by taurus on 2007-01-15
Is that a game?  How did you install it before anyway?

[http://www.graalonline.com/downloads/index.php](http://www.graalonline.com/downloads/index.php)
[http://www.graalonline.com/downloads/graal4setup](http://www.graalonline.com/downloads/graal4setup)

---

### Post by Stomstedt on 2007-01-15
Before it was open source, now it currently has an auto package installer.  They just recently changed the setup file.

---

### Post by Stomstedt on 2007-01-15
And also, yes, it is a game

---

### Post by taurus on 2007-01-15
Just click the second from my post to download the setup file.  Then, change permission with chmod and install it.

```
cd ~/Desktop
chmod 755 graal4setup
./graal4setup
-or-
sudo ./graal4setup
```

---

### Post by Stomstedt on 2007-01-15
I am still having the same error.  During the install, i got an error that said "Error: Cannot find graalicon.png" or something like that.  However, still the same error for starting the program.

---

### Post by taurus on 2007-01-15
Maybe you still use the one previously installed on your machine, not the new one!  See if you can remove it 

```
sudo aptitude purge grall
-or-
sudo dpkg -r graal
```
And if either one of those two commands works, then reinstall graal again.

Otherwise, what's the output of this command?

```
locate graal
```

---

### Post by Stomstedt on 2007-01-15
Neither of those commands work.. It says this:
wner@owner-desktop:~$ sudo aptitude purge graal
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
owner@owner-desktop:~$ graal: /lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by graal)
> owner@owner-desktop:~$ graalexe
> /usr/bin/graal: /lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/bin/graal)
> owner@owner-desktop:~$
>


So I tried to use the 
owner@owner-desktop:~$ sudo dpkg -r graal
dpkg: status database area is locked by another process
owner@owner-desktop:~$

---
I attempted to use the locate graal command and it brought up hundreds of lines.  But here is what i can fit:

/home/owner/.graal/graal4/sounds/flute6.wav
/home/owner/.graal/graal4/sounds/flute4.wav
/home/owner/.graal/graal4/sounds/flute3.wav
/home/owner/.graal/graal4/sounds/flute1.wav
/home/owner/.graal/graal4/sounds/flute2.wav
/home/owner/.graal/graal4/sounds/era_mk23-fire-sil_old.wav
/home/owner/.graal/graal4/sounds/shotgun.wav
/home/owner/.graal/graal4/sounds/weapon_bamboo.wav
/home/owner/.graal/graal4/sounds/eragulp.wav
/home/owner/.graal/graal4/sounds/mal_rain2.wav
/home/owner/.graal/graal4/sounds/era_fire.wav
/home/owner/.graal/graal4/sounds/de_magout.wav
/home/owner/.graal/graal4/sounds/revolver.wav
/home/owner/.graal/graal4/sounds/44magnum.wav
/home/owner/.graal/graal4/sounds/m4a1-1.wav
/home/owner/.graal/graal4/sounds/era_gatling-fuzz.wav
/home/owner/.graal/graal4/sounds/pl9_fire.wav
/home/owner/.graal/graal4/sounds/de_magin.wav
/home/owner/.graal/graal4/sounds/era_ehos-forcefield.wav
/home/owner/.graal/graal4/sounds/de_fire1.wav
/home/owner/.graal/graal4/sounds/pl9_reload.wav
/home/owner/.graal/graal4/sounds/pl9_reload2.wav
/home/owner/.graal/graal4/sounds/era_car-horn.wav
/home/owner/.graal/graal4/sounds/era_ravson5.wav
/home/owner/.graal/graal4/sounds/era_crash.wav
/home/owner/.graal/graal4/sounds/fart2.wav
/home/owner/.graal/graal4/sounds/portal.wav
/home/owner/.graal/graal4/sounds/era_m16a1.wav
/home/owner/.graal/graal4/sounds/whistle.wav
/home/owner/.graal/graal4/sounds/door_open.wav
/home/owner/.graal/graal4/sounds/door_close.wav
/home/owner/.graal/graal4/sounds/spell_fireprojectile.wav
/home/owner/.graal/graal4/sounds/spell_fire.wav
/home/owner/.graal/graal4/sounds/jobs_pickaxe.wav
/home/owner/.graal/graal4/sounds/cannon_shot5.wav
/home/owner/.graal/graal4/sounds/g2k2monkey1.wav
/home/owner/.graal/graal4/sounds/monster_spikes.wav
/home/owner/.graal/graal4/sounds/monster_explo.wav
/home/owner/.graal/graal4/sounds/monster_howl.wav
/home/owner/.graal/graal4/sounds/monster_jump.wav
/home/owner/.graal/graal4/sounds/monster_howl2.wav
/home/owner/.graal/graal4/sounds/g2k2pet_step0.wav
/home/owner/.graal/graal4/sounds/g2k2pet_step1.wav
/home/owner/.graal/graal4/sounds/g2k2pet_eat.wav
/home/owner/.graal/graal4/sounds/g2k2horse_fall.wav
/home/owner/.graal/graal4/sounds/axe_hit2.wav
/home/owner/.graal/graal4/sounds/spell_burnhands.wav
/home/owner/.graal/graal4/sounds/monster_dead.wav
/home/owner/.graal/graal4/sounds/arrow_load.wav
/home/owner/.graal/graal4/sounds/zone_saber2.wav
/home/owner/.graal/graal4/sounds/zone_saber3.wav
/home/owner/.graal/graal4/sounds/g2k2voice_yawn.wav
/home/owner/.graal/graal4/sounds/spell_beam.wav
/home/owner/.graal/graal4/sounds/rebirth.wav
/home/owner/.graal/graal4/sounds/sword_swing.wav
/home/owner/.graal/graal4/sounds/weapon_axe.wav
/home/owner/.graal/graal4/sounds/walk_snow.wav
/home/owner/.graal/graal4/sounds/monster_attack2.wav
/home/owner/.graal/graal4/sounds/spell_storm.wav
/home/owner/.graal/graal4/sounds/g2k2spar_end.wav
/home/owner/.graal/graal4/sounds/g2k2horse_run.wav
/home/owner/.graal/graal4/sounds/era_gas-bang.wav
/home/owner/.graal/graal4/sounds/era_wav-drill.wav
/home/owner/.graal/graal4/sounds/era_reallyannoyingsound.wav
/home/owner/.graal/graal4/sounds/era_wav-drill2.wav
/home/owner/.graal/graal4/sounds/shock.wav
/home/owner/.graal/graal4/sounds/bell.wav
/home/owner/.graal/graal4/sounds/era_gunglock.wav
/home/owner/.graal/graal4/sounds/dc9-fire.wav
/home/owner/.graal/graal4/sounds/dc9-bolt.wav
/home/owner/.graal/graal4/sounds/dc9-clipout.wav
/home/owner/.graal/graal4/sounds/dc9-clipin.wav
/home/owner/.graal/graal4/sounds/monster_attack1.wav
/home/owner/.graal/graal4/sounds/era-slotmove.wav
/home/owner/.graal/graal4/sounds/era-slotdone.wav
/home/owner/.graal/graal4/sounds/era-slotslose.wav
/home/owner/.graal/graal4/sounds/era-slotswin.wav
/home/owner/.graal/graal4/sounds/era_morano-thomsound.wav
/home/owner/.graal/graal4/sounds/monster_punch.wav
/home/owner/.graal/graal4/sounds/weapon_naginata.wav
/home/owner/.graal/graal4/sounds/spell_acidlaunch.wav
/home/owner/.graal/graal4/sounds/g2k2trumpet0.wav
/home/owner/.graal/graal4/sounds/g2k2trumpet3.wav
/home/owner/.graal/graal4/sounds/g2k2trumpet5.wav
/home/owner/.graal/graal4/sounds/g2k2trumpet4.wav
/home/owner/.graal/graal4/sounds/g2k2trumpet2.wav
/home/owner/.graal/graal4/sounds/g2k2monkey4.wav
/home/owner/.graal/graal4/sounds/g2k2pet_born.wav
/home/owner/.graal/graal4/sounds/pl9_logistic-fire.wav
/home/owner/.graal/graal4/sounds/shipka-fire.wav
/home/owner/.graal/graal4/sounds/shipka-bolt.wav
/home/owner/.graal/graal4/sounds/shipka-magout.wav
/home/owner/.graal/graal4/sounds/shipka-magin.wav
/home/owner/.graal/graal4/sounds/shipka-sound.wav
/home/owner/.graal/graal4/sounds/beep3.wav
/home/owner/.graal/graal4/sounds/era_ppa-denied.wav
/home/owner/.graal/graal4/sounds/era_ehosdoor.wav
/home/owner/.graal/graal4/sounds/g2k2bat_attack.wav
/home/owner/.graal/graal4/sounds/waterlaunch.wav
/home/owner/.graal/graal4/sounds/wolf.wav
/home/owner/.graal/graal4/sounds/horror_chair.wav
/home/owner/.graal/graal4/sounds/horror_thunder.wav
/home/owner/.graal/graal4/sounds/horror_wind.wav
/home/owner/.graal/graal4/sounds/horror_door.wav
/home/owner/.graal/graal4/sounds/horror_scream.wav
/home/owner/.graal/graal4/sounds/horror_ghost.wav
/home/owner/.graal/graal4/sounds/horror_slime1.wav
/home/owner/.graal/graal4/sounds/bird01.wav
/home/owner/.graal/graal4/sounds/bird02.wav
/home/owner/.graal/graal4/sounds/eyeswatter.wav
/home/owner/.graal/graal4/sounds/babylon_tempfart.wav
/home/owner/.graal/graal4/sounds/rage_guitar3.wav
/home/owner/.graal/graal4/sounds/rage_guitar2.wav
/home/owner/.graal/graal4/sounds/rage_guitar4.wav
/home/owner/.graal/graal4/sounds/rage_guitar6.wav
/home/owner/.graal/graal4/sounds/rage_guitar8.wav
/home/owner/.graal/graal4/sounds/rage_guitar1.wav
/home/owner/.graal/graal4/sounds/bab_instrument-grandpiano4.wav
/home/owner/.graal/graal4/sounds/bab_instrument-grandpiano6.wav
/home/owner/.graal/graal4/sounds/rage_elec4.wav
/home/owner/.graal/graal4/sounds/rage_elec2.wav
/home/owner/.graal/graal4/sounds/rage_elec1.wav
/home/owner/.graal/graal4/movemap.txt
/home/owner/.graal/graal4/movemap2d.txt
/home/owner/.graal/graal4/graal4config.txt
/home/owner/.graal/graal4/graal_1161125657.jpeg
/home/owner/.graal/graal4/mutedaccounts.txt
/home/owner/.graal/graal4/graal_1161668189.jpeg
/home/owner/.graal/graal4/graal_1161668192.jpeg
/home/owner/.graal/graal4/webfiles
/home/owner/.graal/graal4/webfiles/http%058%047%047wiki%046graal%046net%047images%0477%04777%047Zone_screenshot_candyreapers%046png
/home/owner/.graal/graal4/webfiles/http%058%047%047wiki%046graal%046net%047images%0473%04734%047Kingdoms_screenshot_snow%046png
/home/owner/.graal/graal4/graal4setup
/home/owner/.graal/.registry
/home/owner/.graal/rc
/home/owner/.graal/rc/control2config.txt
/home/owner/rc/rcfiles_graal.png
/home/owner/rc/rc_graalonline2.jpg
/home/owner/rc/rc_graalonline.jpg
/home/owner/rc/language-specs/graal.lang
/usr/bin/graal
/usr/bin/graalexe
/usr/share/applications/apkg-graal.desktop
/usr/share/icons/graalicon.png
/usr/share/pixmaps/graalicon.png
/usr/share/graal
/usr/share/graal/license
/usr/share/graal/license/sig.graal
/usr/share/graal/license/sig.license
/usr/share/graal/license/license.graal
/usr/share/graal/languages3D
/usr/share/graal/languages3D/languageDeutsch.cs
/usr/share/graal/languages3D/languageEnglish.cs
/usr/share/graal/languages3D/languageEspanol.cs
/usr/share/graal/languages3D/languageFrancais.cs
/usr/share/graal/languages3D/languageItaliano.cs
/usr/share/graal/languages3D/languageNederlands.cs
/usr/share/graal/languages3D/languageNorsk.cs
/usr/share/graal/languages3D/languagePortuguese.cs
/usr/share/graal/languages3D/languageSvenska.cs
/usr/share/graal/sounds
/usr/share/graal/sounds/cauldron_bubbles.wav
/usr/share/graal/sounds/fire_torch0.wav
/usr/share/graal/sounds/fire_torch1.wav
/usr/share/graal/sounds/fire_torch2.wav
/usr/share/graal/sounds/nextpage.wav
/usr/share/graal/sounds/spell_firelaunch.wav
/usr/share/graal/sounds/walk_grass2.wav
/usr/share/graal/sounds/walk_grass4.wav
/usr/share/graal/sounds/water.wav
/usr/share/graal/levels
/usr/share/graal/levels/bodies
/usr/share/graal/levels/bodies/kfbody111.png
/usr/share/graal/levels/bodies/kmbody100.png
/usr/share/graal/levels/fonts
/usr/share/graal/levels/fonts/arial.ttf
/usr/share/graal/levels/ganis
/usr/share/graal/levels/ganis/g2k2dievil_attack.gani
/usr/share/graal/levels/ganis/g2k2dievil_idle.gani
/usr/share/graal/levels/ganis/g2k2cauldron_open.gani
/usr/share/graal/levels/ganis/g2k2master.gani
/usr/share/graal/levels/ganis/g2k2squirrel_sleep.gani
/usr/share/graal/levels/ganis/human2_grab.gani
/usr/share/graal/levels/ganis/human2_idle.gani
/usr/share/graal/levels/ganis/human2_pull.gani
/usr/share/graal/levels/ganis/human2_push.gani
/usr/share/graal/levels/ganis/human2_sit.gani
/usr/share/graal/levels/ganis/human2_swim.gani
/usr/share/graal/levels/ganis/human2_walk.gani
/usr/share/graal/levels/ganis/lamps_wood.gani
/usr/share/graal/levels/ganis/palmtree1.gani
/usr/share/graal/levels/ganis/palmtree2.gani
/usr/share/graal/levels/ganis/startmenu_lamps_wood.gani
/usr/share/graal/levels/ganis/tutorial_touch.gani
/usr/share/graal/levels/heads
/usr/share/graal/levels/heads/head26.png
/usr/share/graal/levels/heads/khead0.png
/usr/share/graal/levels/images
/usr/share/graal/levels/images/2002_32x32sprites-flame.png
/usr/share/graal/levels/images/g2k2_dievil.png
/usr/share/graal/levels/images/g2k2cauldron_acid0.png
/usr/share/graal/levels/images/g2k2cauldron_acid1.png
/usr/share/graal/levels/images/g2k2cauldron_pot.png
/usr/share/graal/levels/images/g2k2cauldron_top.png
/usr/share/graal/levels/images/g2k2mastermustach.png
/usr/share/graal/levels/images/g2k2master.png
/usr/share/graal/levels/images/g2k2monster_fire.png
/usr/share/graal/levels/images/g2k2pet_squirrelm0.png
/usr/share/graal/levels/images/khairs0.png
/usr/share/graal/levels/images/khairs5.png
/usr/share/graal/levels/images/klegs0.png
/usr/share/graal/levels/images/klegs13.png
/usr/share/graal/levels/images/kfarms120.png
/usr/share/graal/levels/images/kmarms100.png
/usr/share/graal/levels/images/lamps_wood.png
/usr/share/graal/levels/images/light2.png
/usr/share/graal/levels/images/petzzz.mng
/usr/share/graal/levels/images/realtreeshadow2.png
/usr/share/graal/levels/images/trees_palm2.png
/usr/share/graal/levels/images/trees_palm.png
/usr/share/graal/levels/images/tutorial_arrowdown.png
/usr/share/graal/levels/particles
/usr/share/graal/levels/particles/g4_particle_smoke.png
/usr/share/graal/levels/tiles
/usr/share/graal/levels/tiles/pics1.png
/usr/share/graal/levels/tiles/picso.png
/usr/share/graal/levels/tutorial
/usr/share/graal/levels/tutorial/offlinetutorial_a-1.graal
/usr/share/graal/levels/tutorial/offlinetutorial_a-2.graal
/usr/share/graal/levels/tutorial/offlinetutorial_a-3.graal
/usr/share/graal/levels/tutorial/offlinetutorial_b-1.graal
/usr/share/graal/levels/tutorial/offlinetutorial_b-2.graal
/usr/share/graal/levels/tutorial/offlinetutorial_b-3.graal
/usr/share/graal/levels/tutorial/offlinetutorial_c-1.graal
/usr/share/graal/levels/tutorial/offlinetutorial_c-2.graal
/usr/share/graal/levels/tutorial/offlinetutorial_c-3.graal
/usr/share/graal/levels/tutorial/offlinetutorial.gmap
/usr/share/graal/levels/letters
/usr/share/graal/levels/letters/graal2002letters.png
/usr/share/graal/levels3d
/usr/share/graal/levels3d/gui
/usr/share/graal/levels3d/gui/graalv4screen.jpg
/usr/share/graal/levels3d/gui/graalv4title.png
/usr/share/graal/levels3d/gui/default3darrow.png
/usr/share/graal/levels3d/gui/defaultborder.png
/usr/share/graal/levels3d/gui/defaultbutton.png
/usr/share/graal/levels3d/gui/defaultcheck.png
/usr/share/graal/levels3d/gui/defaultcursor.png
/usr/share/graal/levels3d/gui/defaultguiborder.png
/usr/share/graal/levels3d/gui/defaulthandle.png
/usr/share/graal/levels3d/gui/defaultmenu.png
/usr/share/graal/levels3d/gui/defaultnamehud.png
/usr/share/graal/levels3d/gui/defaultradio.png
/usr/share/graal/levels3d/gui/defaultscroll.png
/usr/share/graal/levels3d/gui/defaultslider.png
/usr/share/graal/levels3d/gui/defaulttab.png
/usr/share/graal/levels3d/gui/defaulttextedit.png
/usr/share/graal/levels3d/gui/defaultwindow_noback.png
/usr/share/graal/levels3d/gui/defaultwindow.png
/usr/share/graal/levels3d/gui/graaldarkbutton3d.png
/usr/share/graal/levels3d/gui/graalicon.png
/usr/share/graal/levels3d/gui/guiblue_button.png
/usr/share/graal/levels3d/gui/guiblue_check.png
/usr/share/graal/levels3d/gui/guiblue_radio.png
/usr/share/graal/levels3d/gui/guiblue_scroll.png
/usr/share/graal/levels3d/gui/guiblue_slider.png
/usr/share/graal/levels3d/gui/guiblue_tab.png
/usr/share/graal/levels3d/gui/guiblue_textedit.png
/usr/share/graal/levels3d/gui/guiblue_window_noback.png
/usr/share/graal/levels3d/gui/guiblue_window.png
/usr/share/graal/levels3d/gui/playerlist_closed.png
/usr/share/graal/levels3d/gui/playerlist_icons.png
/usr/share/graal/levels3d/gui/playerlist_open.png
/usr/share/graal/levels3d/gui/plistcat_chatters.png
/usr/share/graal/levels3d/gui/plistcat_events.png
/usr/share/graal/levels3d/gui/plistcat_guilds.png
/usr/share/graal/levels3d/gui/plistcat_online.png
/usr/share/graal/levels3d/gui/plistcat_servers.png
/usr/share/graal/levels3d/gui/pmbubble_admin.png
/usr/share/graal/levels3d/gui/pmbubble_guild.png
/usr/share/graal/levels3d/gui/pmbubble_mass.png
/usr/share/graal/levels3d/gui/pmbubble_normal.png
/usr/share/graal/levels3d/gui/pmbubble_toall.png
/usr/share/graal/levels3d/gui/rcicon_gold.png
/usr/share/graal/levels3d/gui/treeview_serverlisticons.png
/usr/share/graal/levels3d/help
/usr/share/graal/levels3d/help/0._About.hfl
/usr/share/graal/levels3d/help/1._Links.hfl
/usr/share/graal/levels3d/help/2._Key_shortcuts.hfl
/usr/share/graal/levels3d/help/graal_horses2.jpg
/usr/share/graal/levels3d/help/graal_houseshop.jpg
/usr/share/graal/levels3d/help/graal_warships.jpg

---

### Post by taurus on 2007-01-15
How about

```
ls -la /usr/bin/graal  /usr/bin/graalexe
```
And if you ever want to remove graal from your system, you need to remove those two binaries and everything in /usr/share/graal & /home/owner/.graal.

---

### Post by Stomstedt on 2007-01-15
-rwxr-xr-x 1 root root 7864128 2007-01-15 19:57 /usr/bin/graal
owner@owner-desktop:~$ ls -la /usr/bin/graalexe
-rwxr-xr-x 1 root root 293 2007-01-15 19:57 /usr/bin/graalexe
owner@owner-desktop:~$

---

### Post by taurus on 2007-01-15
You just installed those two!  I guess you can file a bug report with the maker of that game then!  Or check their forums.

[http://forums.graal2001.com/forums/](http://forums.graal2001.com/forums/)

---

### Post by Stomstedt on 2007-01-15
When I try to remove the game, it says i don't have permission -- How do I do this via console?

---

### Post by taurus on 2007-01-15
Use the sudo command.

```
sudo rm /usr/bin/graal  /usr/bin/graalexe  /usr/share/applications/apkg-graal.desktop  /usr/share/icons/graalicon.png  /usr/share/pixmaps/graalicon.png
sudo rm -rf /usr/share/graal
rm -rf ~/.graal
rm ~/rc/*
```
That should do it.

---

### Post by Stomstedt on 2007-01-15
I deleted all the folders and I am having the same issue.  Can you provide me a way to get GCC 4.2.0?

---

### Post by Stomstedt on 2007-01-15
By the way, I am having troubles after I reinstalled it.

---

### Post by taurus on 2007-01-15
You probably need to build GCC 4.2 yourself since it's not released, yet.

[ftp://ftp.nluug.nl/mirror/languages/gcc/snapshots/LATEST-4.2/gcc-4.2-20070110.tar.bz2](ftp://ftp.nluug.nl/mirror/languages/gcc/snapshots/LATEST-4.2/gcc-4.2-20070110.tar.bz2)

[http://gcc.gnu.org/](http://gcc.gnu.org/)

---

