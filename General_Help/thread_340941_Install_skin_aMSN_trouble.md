---
title: "Install skin aMSN trouble"
date: 2007-01-17
forum: General Help
---

### Post by DougieFresh4U on 2007-01-17
I need help installing skin from zip file for aMSN, any takers please:)

---

### Post by taurus on 2007-01-17
Where did you download Candy-1.0.zip then?

---

### Post by DougieFresh4U on 2007-01-17
I thought desktop but as you saw from code you provided it said temp

---

### Post by taurus on 2007-01-17
See if it's in /temp or /tmp because it was in /tmp the last time!

```
ls -la /temp
ls -la /tmp
```

---

### Post by DougieFresh4U on 2007-01-17
dougie@DougiesToyBox:~$ ls -la /temp
ls: /temp: No such file or directory
dougie@DougiesToyBox:~$ ls -la /tmp
total 848
drwxrwxrwt 11 root   root     4096 2007-01-17 23:25 .
drwxr-xr-x 21 root   root     4096 2007-01-11 00:37 ..
-rw-------  1 dougie dougie 809873 2007-01-17 22:41 Candy-1.0.zip
drwx------  3 dougie dougie   4096 2007-01-16 13:09 gconfd-dougie
srw-rw-rw-  1 root   root        0 2007-01-16 13:08 .gdm_socket
drwxr-xr-x  2 dougie dougie   4096 2007-01-17 23:25 hsperfdata_dougie
drwxrwxrwt  2 root   root     4096 2007-01-17 22:42 .ICE-unix
srwx------  1 dougie dougie      0 2007-01-17 23:25 jpsock.150_10.7655
drwx------  2 dougie dougie   4096 2007-01-17 23:24 kde-dougie
drwx------  2 dougie dougie   4096 2007-01-16 13:09 keyring-IixtLW
drwx------  2 dougie dougie   4096 2007-01-17 22:43 ksocket-dougie
drwx------  2 dougie dougie   4096 2007-01-17 22:24 orbit-dougie
drwx------  2 dougie dougie   4096 2007-01-16 13:09 ssh-Wfmdns4600
-r--r--r--  1 root   root       11 2007-01-16 13:08 .X0-lock
drwxrwxrwt  2 root   root     4096 2007-01-16 13:08 .X11-unix
-rw-------  1 dougie dougie    217 2007-01-16 13:09 .xfsm-ICE-LE66LT
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-01-17
```
cp /tmp/Candy-1.0.zip  ~/.amsn/skins
cd  ~/.amsn/skins
unzip -x Candy-1.0.zip
```

---

### Post by DougieFresh4U on 2007-01-17
ougie@DougiesToyBox:~$ cd  ~/.amsn/skins
[email]dougie@DougiesToyBox:~/.amsn[/email]/skins$ unzip -x Candy-1.0.zip
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
[email]dougie@DougiesToyBox:~/.amsn[/email]/skins$ 
Next move?

---

### Post by taurus on 2007-01-17
There should be a directory called Candy in ~/.amsn/skins (~/.amsn/skins/Candy).  Fire up amsn and see if you can apply that new skin with it...

---

### Post by DougieFresh4U on 2007-01-17
you are like that aflak commercial-"your my hero", thanks

---

### Post by taurus on 2007-01-17
Is that the new Candy theme?  

I am out of heeeeeeeeeeeeeeeeeeeeere.

---

