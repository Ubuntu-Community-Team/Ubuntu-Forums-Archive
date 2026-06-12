---
title: "Install skin aMSN trouble"
date: 2007-01-14
forum: General Help
---

### Post by DougieFresh4U on 2007-01-14
I ALWAYS have trouble installing .zip files. I download them and extract then when in terminal it always tells me no directory or whatever ](*,) ](*,)  Can some one please help me instal the candy skin for aMSN? Please

---

### Post by DougieFresh4U on 2007-01-15
This Bump is for U** taurus** :) :) I see your up, please tell me you can solve this one!!

---

### Post by taurus on 2007-01-15
> **DougieFresh4U said:**
> This Bump is for U** taurus** :) :) I see your up, please tell me you can solve this one!!

#-o 

Where did you save that Candy-1.0.zip and where do you plan to install/unzip it?

---

### Post by DougieFresh4U on 2007-01-15
I thought that ALL my downloads are saved to desktop, but it looks as though temp ended up with it., let me check, hang on-can;t find it now. So let me start over and download it again-still with me? And I will save it to Desktop. Of course tar and zip files are like some way out there geometry class in school-yuk. :) :)

---

### Post by taurus on 2007-01-15
```
cd ~/Desktop
unzip -x Candy-1.0.zip
```

---

### Post by DougieFresh4U on 2007-01-15
dougie@DougiesToyBox:~$ cd ~/Desktop
dougie@DougiesToyBox:~/Desktop$ unzip -x Candy-1.0.zip
unzip:  cannot find or open Candy-1.0.zip, Candy-1.0.zip.zip or Candy-1.0.zip.ZIP.
dougie@DougiesToyBox:~/Desktop$ 
why me!!!@

---

### Post by DougieFresh4U on 2007-01-15
Could some one (guru) please put together a nice little wget or what ever it would be, for me to copy/paste in the terminal deal. That would be so great :p :p

---

### Post by taurus on 2007-01-15
```
ls -la ~/Desktop
```

---

### Post by DougieFresh4U on 2007-01-15
You've seen my last screen shot? download box says Desktop, correct?    dougie@DougiesToyBox:~$ ls -la ~/Desktop
total 76
drwx------  2 dougie dougie 4096 2007-01-14 16:16 .
drwxr-xr-x 39 dougie dougie 4096 2007-01-15 10:26 ..
-rw-r--r--  1 dougie dougie  222 2007-01-10 02:19 Amarok.desktop
-rw-r--r--  1 dougie dougie  182 2007-01-12 12:05 aMSN.desktop
-rw-r--r--  1 dougie dougie  214 2007-01-10 02:19 Exaile!.desktop
-rw-r--r--  1 dougie dougie  248 2007-01-10 02:18 FreeCell Solitaire.desktop
-rw-r--r--  1 dougie dougie  233 2007-01-10 00:22 FrostWire.desktop
-rw-r--r--  1 dougie dougie  222 2007-01-10 02:21 Gaim Internet Messenger.desktop
-rw-r--r--  1 dougie dougie  258 2007-01-10 02:20 GNOME ALSA Mixer.desktop
-rw-r--r--  1 dougie dougie  204 2007-01-10 02:18 KMahjongg.desktop
-rw-r--r--  1 dougie dougie  215 2007-01-10 02:20 Listen Music Player.desktop
-rw-r--r--  1 dougie dougie  241 2007-01-10 02:18 Mahjongg.desktop
-rw-r--r--  1 dougie dougie  225 2007-01-10 02:24 Rhythmbox Music Player.desktop
-rw-r--r--  1 dougie dougie  201 2007-01-10 02:22 Shisen-Sho.desktop
-rw-r--r--  1 dougie dougie  213 2007-01-10 02:19 streamtuner.desktop
-rw-r--r--  1 dougie dougie  215 2007-01-14 16:16 Swiftfox Browser.desktop
-rw-r--r--  1 dougie dougie  193 2007-01-10 02:21 Terminal.desktop
-rw-r--r--  1 dougie dougie  231 2007-01-10 02:21 Thunderbird Mail.desktop
-rw-r--r--  1 dougie dougie  175 2007-01-10 02:19 XMMS Music Player.desktop
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-01-15
Well, it's not in ~/Desktop so you probably saved it somewhere else!

```
ls -l ~/
sudo find / -name Candy-1.0.zip -print
```

---

### Post by DougieFresh4U on 2007-01-15
Ok, so why in screen shot I posted does it show in download window "Desktop"? I see it's in temp, but I wanna know why(see screen shot) why that says** Desktop** So let's proceed from here please, thanks.Hope you have an answer for why downloads **are not** where they are supposed to bedougie@DougiesToyBox:~$ sudo find / -name Candy-1.0.zip -print
Password:
/tmp/Candy-1.0.zip
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-01-15
It's also in /tmp!  Did you download it from swiftfox (and did you restart swiftfox) or did you download it from a terminal?

---

### Post by DougieFresh4U on 2007-01-15
swiftfox>sourceforge, yes, restarted

---

### Post by DougieFresh4U on 2007-01-15
I'm ready to fix this, please help

---

### Post by DougieFresh4U on 2007-01-15
dougie@DougiesToyBox:~$ cd ~/temp
bash: cd: /home/dougie/temp: No such file or directory
dougie@DougiesToyBox:~$ cd ~/Desktop
dougie@DougiesToyBox:~/Desktop$ unzip -x Candy-1.0.zip
unzip:  cannot find or open Candy-1.0.zip, Candy-1.0.zip.zip or Candy-1.0.zip.ZIP.
dougie@DougiesToyBox:~/Desktop$

---

### Post by taurus on 2007-01-15
> **DougieFresh4U said:**
> dougie@DougiesToyBox:~$ cd ~/temp
bash: cd: /home/dougie/temp: No such file or directory
dougie@DougiesToyBox:~$ cd ~/Desktop
dougie@DougiesToyBox:~/Desktop$ unzip -x Candy-1.0.zip
unzip:  cannot find or open Candy-1.0.zip, Candy-1.0.zip.zip or Candy-1.0.zip.ZIP.
dougie@DougiesToyBox:~/Desktop$

It's in /tmp.

---

### Post by DougieFresh4U on 2007-01-15
boy, that was simple. now whats next please. talk about needing my hand held:) dougie@DougiesToyBox:~$ cd /tmp
dougie@DougiesToyBox:/tmp$ unzip -x Candy-1.0.zip
Archive:  Candy-1.0.zip
   creating: Candy/
  inflating: Candy/license           
   creating: Candy/smileys/
  inflating: Candy/smileys/Red_lips.gif  
  inflating: Candy/smileys/null      
  inflating: Candy/smileys/Vampire_bat.gif  
 extracting: Candy/smileys/devil.gif  
 extracting: Candy/smileys/Cat_face.gif  
 extracting: Candy/smileys/girl.gif  
 extracting: Candy/smileys/Smiley.gif  
  inflating: Candy/smileys/lightning.gif  
  inflating: Candy/smileys/Hi_five.gif  
 extracting: Candy/smileys/Sick_smiley.gif  
 extracting: Candy/smileys/note.gif  
  inflating: Candy/smileys/pizza.gif  
  inflating: Candy/smileys/Sarcastic_smiley.gif  
  inflating: Candy/smileys/rainbow.gif  
  inflating: Candy/smileys/Island_with_a_palm_tree.gif  
  inflating: Candy/smileys/Dog_face.gif  
  inflating: Candy/smileys/Sleepy_smiley.gif  
  inflating: Candy/smileys/plate.gif  
 extracting: Candy/smileys/Boy.gif   
  inflating: Candy/smileys/Mobile_phone.gif  
  inflating: Candy/smileys/xbox.gif  
 extracting: Candy/smileys/Telephone_receiver.gif  
  inflating: Candy/smileys/email.gif  
 extracting: Candy/smileys/beer.gif  
  inflating: Candy/smileys/Eye_rolling_smiley.gif  
 extracting: Candy/smileys/handcuffs.gif  
 extracting: Candy/smileys/Red_heart.gif  
  inflating: Candy/smileys/Birthday_cake.gif  
 extracting: Candy/smileys/Open_mouthed_smiley.gif  
  inflating: Candy/smileys/Nerd_smiley.gif  
 extracting: Candy/smileys/rain.gif  
 extracting: Candy/smileys/Surprised_smiley.gif  
 extracting: Candy/smileys/Coffee_cup.gif  
 extracting: Candy/smileys/umbrella.gif  
 extracting: Candy/smileys/sun.gif   
 extracting: Candy/smileys/Hot_smiley.gif  
  inflating: Candy/smileys/Winking_smiley.gif  
 extracting: Candy/smileys/angel.gif  
  inflating: Candy/smileys/Dont_tell_anyone.gif  
  inflating: Candy/smileys/Be_Right_Back.gif  
  inflating: Candy/smileys/Cigarette.gif  
  inflating: Candy/smileys/Money.gif  
 extracting: Candy/smileys/Sleeping_half-moon.gif  
  inflating: Candy/smileys/clock.gif  
 extracting: Candy/smileys/Left_hug.gif  
 extracting: Candy/smileys/smile.png  
 extracting: Candy/smileys/Embarrassed_smiley.gif  
 extracting: Candy/smileys/Red_rose.gif  
 extracting: Candy/smileys/Right_hug.gif  
  inflating: Candy/smileys/i_dont_know.gif  
 extracting: Candy/smileys/Confused_smiley.gif  
  inflating: Candy/smileys/What_The_****.gif  
 extracting: Candy/smileys/Messenger.gif  
 extracting: Candy/smileys/Sad_smiley.gif  
  inflating: Candy/smileys/Bowl.gif  
 extracting: Candy/smileys/star.gif  
 extracting: Candy/smileys/Smiley_with_tonque_out.gif  
 extracting: Candy/smileys/Broken_heart.gif  
  inflating: Candy/smileys/Crying_face.gif  
 extracting: Candy/smileys/computer.gif  
 extracting: Candy/smileys/Airplane.gif  
 extracting: Candy/smileys/asl.gif   
  inflating: Candy/smileys/turtle.gif  
 extracting: Candy/smileys/Thumbs_down.gif  
 extracting: Candy/smileys/camera.gif  
 extracting: Candy/smileys/Gift_with_a_bow.gif  
  inflating: Candy/smileys/party_smiley.gif  
  inflating: Candy/smileys/Fingerscrossed.gif  
 extracting: Candy/smileys/Dry_martini.gif  
 extracting: Candy/smileys/filmstrip.gif  
 extracting: Candy/smileys/Light_bulb.gif  
 extracting: Candy/smileys/Angry_smiley.gif  
  inflating: Candy/smileys/Black_sheep.gif  
 extracting: Candy/smileys/Thumbs_up.gif  
  inflating: Candy/smileys/Soccer_ball.gif  
 extracting: Candy/smileys/Auto.gif  
 extracting: Candy/smileys/Wilted_rose.gif  
 extracting: Candy/smileys/Disappointed_smiley.gif  
 extracting: Candy/smileys/snail.gif  
  inflating: Candy/smileys/Secret_telling_smiley.gif  
  inflating: Candy/smileys/Thinking_smiley.gif  
  inflating: Candy/smileys/Baring_teeth_smiley.gif  
   creating: Candy/winicons/
  inflating: Candy/winicons/online.ico  
  inflating: Candy/winicons/inactive.ico  
  inflating: Candy/winicons/away.ico  
  inflating: Candy/winicons/bossmode.ico  
  inflating: Candy/winicons/offline.ico  
  inflating: Candy/winicons/msn.ico  
  inflating: Candy/winicons/unread.ico  
  inflating: Candy/winicons/phone.ico  
  inflating: Candy/winicons/busy.ico  
  inflating: Candy/winicons/brb.ico  
  inflating: Candy/winicons/hidden.ico  
  inflating: Candy/winicons/lunch.ico  
  inflating: Candy/settings.xml      
   creating: Candy/sounds/
  inflating: Candy/sounds/null       
  inflating: Candy/sounds/online.wav  
  inflating: Candy/sounds/type.wav   
  inflating: Candy/sounds/newemail.wav  
  inflating: Candy/sounds/offline.wav  
  inflating: Candy/sounds/alarm.wav  
 extracting: Candy/desc.txt          
   creating: Candy/displaypic/
  inflating: Candy/displaypic/null   
 extracting: Candy/displaypic/amsn.dat  
  inflating: Candy/displaypic/amsn.png  
  inflating: Candy/displaypic/blood.dat  
  inflating: Candy/displaypic/blood.gif  
  inflating: Candy/displaypic/blood.png  
  inflating: Candy/displaypic/skins_readme.txt  
  inflating: Candy/displaypic/rubberduck.dat  
  inflating: Candy/displaypic/rubberduck.gif  
 extracting: Candy/displaypic/rubberduck.png  
  inflating: Candy/displaypic/castle.dat  
  inflating: Candy/displaypic/castle.gif  
 extracting: Candy/displaypic/castle.png  
  inflating: Candy/displaypic/doggie.dat  
  inflating: Candy/displaypic/doggie.gif  
 extracting: Candy/displaypic/doggie.png  
  inflating: Candy/displaypic/lightbulb.dat  
  inflating: Candy/displaypic/lightbulb.gif  
 extracting: Candy/displaypic/lightbulb.png  
 extracting: Candy/displaypic/lock.dat  
  inflating: Candy/displaypic/lock.gif  
 extracting: Candy/displaypic/lock.png  
  inflating: Candy/displaypic/phone.dat  
  inflating: Candy/displaypic/phone.gif  
 extracting: Candy/displaypic/phone.png  
  inflating: Candy/displaypic/loading.gif  
  inflating: Candy/displaypic/nopic.gif  
 extracting: Candy/displaypic/ball.dat  
  inflating: Candy/displaypic/ball.gif  
 extracting: Candy/displaypic/ball.png  
 extracting: Candy/displaypic/car.dat  
  inflating: Candy/displaypic/car.gif  
 extracting: Candy/displaypic/car.png  
  inflating: Candy/displaypic/shell.dat  
  inflating: Candy/displaypic/shell.gif  
 extracting: Candy/displaypic/shell.png  
   creating: Candy/pixmapscroll/
  inflating: Candy/pixmapscroll/pkgIndex.tcl  
  inflating: Candy/pixmapscroll/pixmapscroll.tcl  
  inflating: Candy/pixmapscroll/test.tcl  
   creating: Candy/pixmapscroll/vertical/
  inflating: Candy/pixmapscroll/vertical/sliderbottom_disabled.png  
  inflating: Candy/pixmapscroll/vertical/slidertop.png  
 extracting: Candy/pixmapscroll/vertical/sliderbody_hover.png  
  inflating: Candy/pixmapscroll/vertical/sliderbottom_hover.png  
  inflating: Candy/pixmapscroll/vertical/slidertop_hover.png  
  inflating: Candy/pixmapscroll/vertical/slidergrip_pressed.gif  
 extracting: Candy/pixmapscroll/vertical/arrow1_pressed.png  
 extracting: Candy/pixmapscroll/vertical/trough.png  
  inflating: Candy/pixmapscroll/vertical/sliderbottom.png  
  inflating: Candy/pixmapscroll/vertical/slidergrip_hover.gif  
  inflating: Candy/pixmapscroll/vertical/sliderbody_disabled.png  
 extracting: Candy/pixmapscroll/vertical/arrow2_hover.png  
  inflating: Candy/pixmapscroll/vertical/sliderbody.png  
  inflating: Candy/pixmapscroll/vertical/slidertop_pressed.png  
 extracting: Candy/pixmapscroll/vertical/arrow2_pressed.png  
 extracting: Candy/pixmapscroll/vertical/arrow1.png  
 extracting: Candy/pixmapscroll/vertical/arrow2.png  
 extracting: Candy/pixmapscroll/vertical/arrow2_disabled.png  
 extracting: Candy/pixmapscroll/vertical/arrow1_hover.png  
 extracting: Candy/pixmapscroll/vertical/slidergrip_disabled.gif  
  inflating: Candy/pixmapscroll/vertical/sliderbottom_pressed.png  
 extracting: Candy/pixmapscroll/vertical/sliderbody_pressed.png  
  inflating: Candy/pixmapscroll/vertical/slidertop_disabled.png  
 extracting: Candy/pixmapscroll/vertical/arrow1_disabled.png  
  inflating: Candy/pixmapscroll/vertical/slidergrip.gif  
   creating: Candy/pixmapscroll/horizontal/
  inflating: Candy/pixmapscroll/horizontal/sliderbottom_disabled.png  
  inflating: Candy/pixmapscroll/horizontal/slidertop.png  
 extracting: Candy/pixmapscroll/horizontal/sliderbody_hover.png  
  inflating: Candy/pixmapscroll/horizontal/sliderbottom_hover.png  
  inflating: Candy/pixmapscroll/horizontal/slidertop_hover.png  
  inflating: Candy/pixmapscroll/horizontal/slidergrip_pressed.gif  
 extracting: Candy/pixmapscroll/horizontal/arrow1_pressed.png  
 extracting: Candy/pixmapscroll/horizontal/trough.png  
  inflating: Candy/pixmapscroll/horizontal/sliderbottom.png  
  inflating: Candy/pixmapscroll/horizontal/slidergrip_hover.gif  
 extracting: Candy/pixmapscroll/horizontal/sliderbody_disabled.png  
 extracting: Candy/pixmapscroll/horizontal/arrow2_hover.png  
 extracting: Candy/pixmapscroll/horizontal/sliderbody.png  
  inflating: Candy/pixmapscroll/horizontal/slidertop_pressed.png  
 extracting: Candy/pixmapscroll/horizontal/arrow2_pressed.png  
 extracting: Candy/pixmapscroll/horizontal/arrow1.png  
 extracting: Candy/pixmapscroll/horizontal/arrow2.png  
 extracting: Candy/pixmapscroll/horizontal/arrow2_disabled.png  
 extracting: Candy/pixmapscroll/horizontal/arrow1_hover.png  
 extracting: Candy/pixmapscroll/horizontal/slidergrip_disabled.gif  
  inflating: Candy/pixmapscroll/horizontal/sliderbottom_pressed.png  
 extracting: Candy/pixmapscroll/horizontal/sliderbody_pressed.png  
  inflating: Candy/pixmapscroll/horizontal/slidertop_disabled.png  
 extracting: Candy/pixmapscroll/horizontal/arrow1_disabled.png  
  inflating: Candy/pixmapscroll/horizontal/slidergrip.gif  
   creating: Candy/pixmaps/
 extracting: Candy/pixmaps/prefpers.png  
 extracting: Candy/pixmaps/tab_close.png  
 extracting: Candy/pixmaps/prefhist2.png  
 extracting: Candy/pixmaps/prefmobile.png  
 extracting: Candy/pixmaps/butdraw.png  
 extracting: Candy/pixmaps/donline.png  
  inflating: Candy/pixmaps/amsn.xbm  
 extracting: Candy/pixmaps/button_focus.png  
  inflating: Candy/pixmaps/loganim.gif  
 extracting: Candy/pixmaps/butsmile.png  
 extracting: Candy/pixmaps/cam_in_chatwin.png  
  inflating: Candy/pixmaps/notifico.gif  
 extracting: Candy/pixmaps/webcam.png  
 extracting: Candy/pixmaps/tab_flicker.png  
 extracting: Candy/pixmaps/buttext.png  
 extracting: Candy/pixmaps/bbusy.png  
 extracting: Candy/pixmaps/imghide_hover.gif  
 extracting: Candy/pixmaps/dphone.png  
 extracting: Candy/pixmaps/tab_close_hover.png  
 extracting: Candy/pixmaps/online.png  
 extracting: Candy/pixmaps/notesdispic.png  
 extracting: Candy/pixmaps/newline.png  
 extracting: Candy/pixmaps/butdraw_hover.png  
 extracting: Candy/pixmaps/amsnplusbutton.png  
 extracting: Candy/pixmaps/boffline.png  
 extracting: Candy/pixmaps/blocked.png  
 extracting: Candy/pixmaps/imgshow_hover.gif  
 extracting: Candy/pixmaps/mobile.png  
 extracting: Candy/pixmaps/dbrb.png  
  inflating: Candy/pixmaps/grid.png  
 extracting: Candy/pixmaps/dbusy.png  
 extracting: Candy/pixmaps/prefemotic.png  
 extracting: Candy/pixmaps/actions_addcontact.png  
 extracting: Candy/pixmaps/nudgebutton.png  
 extracting: Candy/pixmaps/butfont_hover.png  
 extracting: Candy/pixmaps/miniwarn.png  
 extracting: Candy/pixmaps/away.png  
 extracting: Candy/pixmaps/typing.png  
 extracting: Candy/pixmaps/butwebcam_hover.png  
 extracting: Candy/pixmaps/bstatus.png  
 extracting: Candy/pixmaps/lesstabs.png  
  inflating: Candy/pixmaps/notifyoffline.png  
  inflating: Candy/pixmaps/notifyonline.png  
 extracting: Candy/pixmaps/tab.png   
 extracting: Candy/pixmaps/cwtopback.png  
 extracting: Candy/pixmaps/dlunch.png  
 extracting: Candy/pixmaps/notinlist.png  
 extracting: Candy/pixmaps/preffont.png  
 extracting: Candy/pixmaps/nudgebutton_hover.png  
 extracting: Candy/pixmaps/butwipe.png  
 extracting: Candy/pixmaps/butsend.png  
 extracting: Candy/pixmaps/prefaway.png  
 extracting: Candy/pixmaps/butblock_hover.png  
 extracting: Candy/pixmaps/mystatus_bg.png  
 extracting: Candy/pixmaps/offline.png  
  inflating: Candy/pixmaps/box_up.png  
 extracting: Candy/pixmaps/messenger.png  
  inflating: Candy/pixmaps/arrowmac.gif  
 extracting: Candy/pixmaps/butgridoff.png  
 extracting: Candy/pixmaps/bell.gif  
 extracting: Candy/pixmaps/doffline.png  
  inflating: Candy/pixmaps/notifyoffline1.png  
  inflating: Candy/pixmaps/colorbar.png  
 extracting: Candy/pixmaps/minileaves.png  
 extracting: Candy/pixmaps/expand_hover.png  
 extracting: Candy/pixmaps/imgshow.gif  
 extracting: Candy/pixmaps/actions_startchat.png  
 extracting: Candy/pixmaps/actions_bg.png  
  inflating: Candy/pixmaps/box_body.png  
  inflating: Candy/pixmaps/greyline.png  
 extracting: Candy/pixmaps/butgridon_hover.png  
  inflating: Candy/pixmaps/box_downright.png  
 extracting: Candy/pixmaps/prefnat.png  
  inflating: Candy/pixmaps/box_upright.png  
 extracting: Candy/pixmaps/prefphone.png  
 extracting: Candy/pixmaps/nudgeoff.png  
 extracting: Candy/pixmaps/butblock.png  
 extracting: Candy/pixmaps/button.png  
 extracting: Candy/pixmaps/moretabs.png  
 extracting: Candy/pixmaps/tab_hover.png  
 extracting: Candy/pixmaps/buttext_hover.png  
 extracting: Candy/pixmaps/amsnplusbutton_hover.png  
 extracting: Candy/pixmaps/miniinfo.png  
 extracting: Candy/pixmaps/dinactive.png  
 extracting: Candy/pixmaps/butinvite.png  
 extracting: Candy/pixmaps/prefmsg.png  
 extracting: Candy/pixmaps/butsend_hover.png  
 extracting: Candy/pixmaps/smile.png  
 extracting: Candy/pixmaps/baway.png  
  inflating: Candy/pixmaps/alarm.png  
 extracting: Candy/pixmaps/minijoins.png  
 extracting: Candy/pixmaps/bonline.png  
 extracting: Candy/pixmaps/prefalerts.png  
 extracting: Candy/pixmaps/camicon.png  
 extracting: Candy/pixmaps/butinvite_hover.png  
 extracting: Candy/pixmaps/unread.png  
  inflating: Candy/pixmaps/logolinmsn1.png  
 extracting: Candy/pixmaps/butsmile_hover.png  
 extracting: Candy/pixmaps/Warning.png  
 extracting: Candy/pixmaps/daway.png  
 extracting: Candy/pixmaps/arrow.png  
 extracting: Candy/pixmaps/prefstatus.png  
  inflating: Candy/pixmaps/logolinmsn.png  
  inflating: Candy/pixmaps/back.gif  
 extracting: Candy/pixmaps/nudge.png  
 extracting: Candy/pixmaps/prefproxy.png  
 extracting: Candy/pixmaps/belloff.gif  
 extracting: Candy/pixmaps/tab_current.png  
 extracting: Candy/pixmaps/contract.png  
 extracting: Candy/pixmaps/prefhist.png  
 extracting: Candy/pixmaps/imghide.gif  
 extracting: Candy/pixmaps/expand.png  
 extracting: Candy/pixmaps/button_hover.png  
 extracting: Candy/pixmaps/butgridon.png  
 extracting: Candy/pixmaps/fticon.png  
 extracting: Candy/pixmaps/pop3_mailpic.png  
 extracting: Candy/pixmaps/notespic.png  
 extracting: Candy/pixmaps/ftreject.png  
  inflating: Candy/pixmaps/box_downleft.png  
 extracting: Candy/pixmaps/globe.png  
 extracting: Candy/pixmaps/msnbot.png  
  inflating: Candy/pixmaps/notifystate.png  
 extracting: Candy/pixmaps/sendbut.png  
 extracting: Candy/pixmaps/amsnicon.png  
 extracting: Candy/pixmaps/sendbut_hover.png  
  inflating: Candy/pixmaps/logomacmsn.png  
 extracting: Candy/pixmaps/butwebcam.png  
 extracting: Candy/pixmaps/button_pressed.png  
 extracting: Candy/pixmaps/busy.png  
 extracting: Candy/pixmaps/dhidden.png  
  inflating: Candy/pixmaps/notifclose.gif  
  inflating: Candy/pixmaps/box_upleft.png  
 extracting: Candy/pixmaps/camempty.png  
  inflating: Candy/pixmaps/box_right.png  
 extracting: Candy/pixmaps/actions_expcol.png  
  inflating: Candy/pixmaps/box_down.png  
 extracting: Candy/pixmaps/butwipe_hover.png  
 extracting: Candy/pixmaps/preflook.png  
 extracting: Candy/pixmaps/contract_hover.png  
 extracting: Candy/pixmaps/button_disabled.png  
  inflating: Candy/pixmaps/amsnmask.xbm  
 extracting: Candy/pixmaps/download.png  
 extracting: Candy/pixmaps/butfont.png  
 extracting: Candy/pixmaps/butgridoff_hover.png  
  inflating: Candy/pixmaps/box_left.png  
dougie@DougiesToyBox:/tmp$

---

### Post by taurus on 2007-01-15
Now, you need to move Candy's directory to wherever aMsn is looking for.  It could be ~/.amsn!!!

---

### Post by DougieFresh4U on 2007-01-15
and (could you provide some sort of code) you easily forget I'm a dummy:rolleyes:

---

### Post by DougieFresh4U on 2007-01-15
I need just a little more hand holding, please:-?

---

### Post by taurus on 2007-01-15
Do you have a directory called ~/.amsn?  I assume under that there is a subdirectory called Skins then.  That's where you want to move/copy Candy to.

```
mkdir ~/.amsn/Skins/Candy
cp -R /tmp/Candy/* ~/.amsn/Skins/Candy
```

---

### Post by DougieFresh4U on 2007-01-15
dougie@DougiesToyBox:~$ mkdir ~/.amsn/Skins/Candy
mkdir: cannot create directory `/home/dougie/.amsn/Skins/Candy': No such file or directory
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-01-15
```
ls -la ~
```

---

### Post by DougieFresh4U on 2007-01-15
dougie@DougiesToyBox:~$ ls -la ~
total 2808
drwxr-xr-x 39 dougie dougie   4096 2007-01-15 11:24 .
drwxr-xr-x  3 root   root     4096 2007-01-09 21:56 ..
drwx------  8 dougie dougie   4096 2007-01-12 01:37 .amsn
drwx------  2 dougie dougie   4096 2007-01-12 01:33 amsn_received
drwxr-xr-x  2 dougie root     4096 2007-01-09 23:30 .automatix
-rw-r--r--  1 dougie dougie 454656 2007-01-11 03:34 avatar13.gif
-rw-r--r--  1 dougie dougie   4388 2007-01-11 03:40 avatar_46.jpg
-rw-------  1 dougie dougie   2225 2007-01-15 16:44 .bash_history
-rw-r--r--  1 dougie dougie    220 2007-01-09 21:56 .bash_logout
-rw-r--r--  1 dougie dougie    414 2007-01-09 21:56 .bash_profile
-rw-r--r--  1 dougie dougie   2227 2007-01-09 21:56 .bashrc
drwxr-xr-x  4 dougie dougie   4096 2007-01-10 02:24 .bmp
drwx------  5 dougie dougie   4096 2007-01-10 04:22 .cache
drwx------  6 dougie dougie   4096 2007-01-12 15:57 .config
-rw-r--r--  1 dougie dougie     60 2007-01-15 10:09 .DCOPserver_DougiesToyBox__0
lrwxrwxrwx  1 dougie dougie     41 2007-01-15 10:09 .DCOPserver_DougiesToyBox_:0 -> /home/dougie/.DCOPserver_DougiesToyBox__0
drwx------  2 dougie dougie   4096 2007-01-14 16:16 Desktop
-rw-------  1 dougie dougie     24 2007-01-09 22:12 .dmrc
drwxr-xr-x  5 dougie dougie   4096 2007-01-12 02:36 .exaile
lrwxrwxrwx  1 dougie dougie     26 2007-01-09 21:56 Examples -> /usr/share/example-content
drwxr-xr-x  2 dougie dougie   4096 2007-01-13 09:26 .fontconfig
-rw-r--r--  1 dougie dougie 483359 2007-01-09 23:12 .fonts.cache-1
drwxr-xr-x  4 dougie dougie   4096 2007-01-15 09:04 .frostwire
drwx------  6 dougie dougie   4096 2007-01-15 15:44 .gaim
drwx------  4 dougie dougie   4096 2007-01-15 10:21 .gconf
drwx------  2 dougie dougie   4096 2007-01-15 15:50 .gconfd
drwxr-xr-x 21 dougie dougie   4096 2007-01-13 09:29 .gimp-2.2
-rw-r-----  1 dougie dougie      0 2007-01-14 21:07 .gksu.lock
drwx------  5 dougie dougie   4096 2007-01-14 19:47 .gnome2
drwx------  2 dougie dougie   4096 2007-01-09 23:37 .gnome2_private
drwx------  2 dougie dougie   4096 2007-01-09 22:48 .gnupg
drwxr-xr-x  2 dougie dougie   4096 2007-01-14 20:30 .gstreamer-0.10
-rw-------  1 dougie dougie   1098 2007-01-15 10:09 .ICEauthority
drwxr-xr-x  2 dougie dougie   4096 2007-01-09 23:51 .icons
drwxr-xr-x  2 dougie dougie   4096 2007-01-15 09:04 Incomplete
drwxr-xr-x  3 dougie dougie   4096 2007-01-14 19:22 .java
drwx------  3 dougie dougie   4096 2007-01-10 02:22 .kde
-rw-r--r--  1 dougie dougie   1730 2007-01-07 16:34 key.gpg.asc
drwxr-xr-x  3 dougie dougie   4096 2007-01-09 22:12 .local
drwxr-xr-x  4 dougie dougie   4096 2007-01-10 22:26 .lyrics
drwx------  3 dougie dougie   4096 2007-01-09 23:56 .macromedia
drwxr-xr-x  3 dougie dougie   4096 2007-01-10 15:56 .mcop
-rw-------  1 dougie dougie     31 2007-01-12 15:57 .mcoprc
drwx------  3 dougie dougie   4096 2007-01-10 01:58 .mozilla
drwx------  3 dougie dougie   4096 2007-01-10 01:58 .mozilla-thunderbird
drwxr-xr-x  2 dougie dougie   4096 2007-01-14 19:30 .mplayer
drwxr-xr-x  2 dougie dougie   4096 2007-01-11 01:04 .qt
drwxr-xr-x  2 dougie dougie   4096 2007-01-15 09:03 Shared
-rw-r--r--  1 dougie dougie 442392 2007-01-15 11:24 snapshot10.png
-rw-r--r--  1 dougie dougie 274019 2007-01-15 10:09 snapshot8.png
-rw-r--r--  1 dougie dougie 437878 2007-01-15 10:26 snapshot9.png
drwxr-xr-x  3 dougie dougie   4096 2007-01-13 09:00 .streamtuner
-rw-r--r--  1 dougie dougie      0 2007-01-09 22:13 .sudo_as_admin_successful
-rw-r--r--  1 dougie dougie 492997 2007-01-13 08:47 Swiftfox_wallpaper.png
drwxr-xr-x  3 dougie dougie   4096 2007-01-10 00:22 .thumbnails
drwxr-xr-x  2 dougie dougie   4096 2007-01-09 22:18 .update-manager
drwxr-xr-x  4 dougie dougie   4096 2007-01-10 05:30 .wine
-rw-------  1 dougie dougie    124 2007-01-15 09:47 .Xauthority
drwxr-xr-x  2 dougie dougie   4096 2007-01-10 04:28 .xine
drwxr-xr-x  4 dougie dougie   4096 2007-01-11 03:52 .xmms
-rw-r--r--  1 dougie dougie  11416 2007-01-09 23:47 .xscreensaver
-rw-r--r--  1 dougie dougie  32327 2007-01-15 16:54 .xsession-errors
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-01-15
```
ls -la ~/.amsn
```

---

### Post by DougieFresh4U on 2007-01-16
> **taurus said:**
> ```
ls -la ~/.amsn
```

dougie@DougiesToyBox:~$ ls -la ~/.amsn
total 64
drwx------  8 dougie dougie  4096 2007-01-12 01:37 .
drwxr-xr-x 48 dougie dougie  4096 2007-01-16 13:32 ..
-rw-------  1 dougie dougie 12539 2007-01-12 01:37 config.xml
drwx------  6 dougie dougie  4096 2007-01-14 20:00 DougiesTA_hotmail_com
-rw-------  1 dougie dougie   504 2007-01-16 02:29 gconfig.xml
-rw-r--r--  1 dougie dougie     0 2007-01-16 02:28 langlistnew.xml
-rw-r--r--  1 dougie dougie  4854 2007-01-12 01:33 langlist.xml
drwx------  2 dougie dougie  4096 2007-01-12 01:33 logs
drwx------  2 dougie dougie  4096 2007-01-12 01:33 plugins
-rw-------  1 dougie dougie    48 2007-01-16 02:29 profiles
drwx------  2 dougie dougie  4096 2007-01-12 01:33 skins
drwx------  2 dougie dougie  4096 2007-01-12 01:33 smileys
drwx------  2 dougie dougie  4096 2007-01-12 01:33 webcam
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-01-16
```
cp -R /tmp/Candy  ~/.amsn/skins
```

---

### Post by DougieFresh4U on 2007-01-16
> **taurus said:**
> ```
cp -R /tmp/Candy  ~/.amsn/skins
```

dougie@DougiesToyBox:~$ cp -R /tmp/Candy  ~/.amsn/skins
cp: cannot stat `/tmp/Candy': No such file or directory
dougie@DougiesToyBox:~$ 
I am gonna give this about 5 minutes of my times and then I am gonna scream and go to sleep, I can never install any thing

---

### Post by taurus on 2007-01-16
```
cp /tmp/Candy-1.0.zip ~/.amsn/skins
cd ~/.amsn/skins
unzip -x Candy-1.0.zip
```

:-$

---

### Post by DougieFresh4U on 2007-01-16
> **taurus said:**
> ```
cp /tmp/Candy-1.0.zip ~/.amsn/skins
cd ~/.amsn/skins
unzip -x Candy-1.0.zip
```

:-$

dougie@DougiesToyBox:~$ cp /tmp/Candy-1.0.zip ~/.amsn/skins
cp: cannot stat `/tmp/Candy-1.0.zip': No such file or directory
dougie@DougiesToyBox:~$ 
wtf-excuse me-yesterday it was in temp, right? now what, start over/

---

### Post by taurus on 2007-01-16
I thought it was in /tmp!

```
sudo find / -name Candy-1.0.zip -print
```

---

### Post by IusedTObeSOMEONEelse on 2007-01-16
AIM dummy:D

---

### Post by taurus on 2007-01-16
> **MustangSallydd said:**
> AIM dummy:D

Hey, you can't talk to your older brother like that!!!  ](*,)

---

### Post by DougieFresh4U on 2007-01-16
> **taurus said:**
> I thought it was in /tmp!

```
sudo find / -name Candy-1.0.zip -print
```

dougie@DougiesToyBox:~$ sudo find / -name Candy-1.0.zip -print
Password:
dougie@DougiesToyBox:~$ 
Im not a dummy, I'm ignoring your AIM , now what taurus?

---

### Post by taurus on 2007-01-16
Is there a /tmp/Candy?

```
ls -la /tmp/Candy
```
Otherwise, download Candy-1.0.zip over again (to some place you remember).

---

### Post by DougieFresh4U on 2007-01-16
dougie@DougiesToyBox:~$ ls -la /tmp/Candy
ls: /tmp/Candy: No such file or directory
dougie@DougiesToyBox:~$  This is like a serious mission. I quit for tonite as I am tired and wanna sleep, thanks for helping and you CAN BET WERE GONNA PICK AT THIS AGAIN AFTER I HAVE HAD SOME REST. I AM JUST GLAD TO BE BACK WHERE IT'S WARM AGAIN:p Good nite and close this thread please:evil:

---

### Post by taurus on 2007-01-16
Since you saved your stuff to /tmp, it's got erased when system boots so next time save it to your own home directory.

---

