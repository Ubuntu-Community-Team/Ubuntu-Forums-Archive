---
title: "realplayer segmentation fault"
date: 2005-05-08
forum: General Help
---

### Post by sharmaravi on 2005-05-08
I use firefox and have installed realplayer 10. I am trying to listen to streaming music ([www.musicindiaonline.com](www.musicindiaonline.com)) but realplayer segfaults. The website claims that their music player runs on linux. Here is the error message I get on console


/home/ravi/.themes/MilkMint/gtk-2.0/../icons/iconrc:12: Unable to locate image file in pixmap_path: "stock_volume.svg"
/home/ravi/.themes/MilkMint/gtk-2.0/../icons/iconrc:68: Unable to locate image file in pixmap_path: "stock_brokenimage.svg"
/home/ravi/.themes/MilkMint/gtk-2.0/../icons/iconrc:83: Unable to locate image file in pixmap_path: "stock_quit.svg"
/home/ravi/.themes/MilkMint/gtk-2.0/../icons/iconrc:145: Unable to locate image file in pixmap_path: "media-previous.svg"
/home/ravi/.themes/MilkMint/gtk-2.0/../icons/iconrc:165: Unable to locate image file in pixmap_path: "stock_quit.svg"
/home/ravi/.themes/MilkMint/gtk-2.0/../icons/iconrc:178: Unable to locate image file in pixmap_path: "media-previous.svg"
Calling realplay
playeripc: Got command Version 1
playeripc: Got command Embed type='audio/x-pn-realaudio-plugin' name='RAPlayer' src='http://www.musicindiaonline.com/z/default/m/blank.smil' console='_unique' controls='PositionField' nolabels='TRUE' autostart='FALSE' height='2' width='2' 
playeripc: Got command Browser 0 'Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.6) Gecko/20050405 Firefox/1.0 (Ubuntu package 1.0.2)' 1 1
playeripc: Got command SetWindow 0 46145754 0 0 2 2 0 0 2 2 1
/home/ravi/.themes/MilkMint/gtk-2.0/../icons/iconrc:12: Unable to locate image file in pixmap_path: "stock_volume.svg"
/home/ravi/.themes/MilkMint/gtk-2.0/../icons/iconrc:68: Unable to locate image file in pixmap_path: "stock_brokenimage.svg"
/home/ravi/.themes/MilkMint/gtk-2.0/../icons/iconrc:83: Unable to locate image file in pixmap_path: "stock_quit.svg"
/home/ravi/.themes/MilkMint/gtk-2.0/../icons/iconrc:145: Unable to locate image file in pixmap_path: "media-previous.svg"
/home/ravi/.themes/MilkMint/gtk-2.0/../icons/iconrc:165: Unable to locate image file in pixmap_path: "stock_quit.svg"
/home/ravi/.themes/MilkMint/gtk-2.0/../icons/iconrc:178: Unable to locate image file in pixmap_path: "media-previous.svg"
playeripc: Got command SetWindow 0 46145754 0 0 2 2 0 0 2 2 1
playeripc: Got command SetWindow 0 46145754 0 23 2 2 0 0 2 2 1
playeripc: Got command NewStream 0 0 [http://www.musicindiaonline.com/z/default/m/blank.smil](http://www.musicindiaonline.com/z/default/m/blank.smil) application/smil 15
playeripc: Got command SetPlayerStringProp 0 'src' 'http://www.musicindiaonline.com/g/r/F6pmIWo6NSNvwrOupt7D/play.smil'
playeripc: Got command SetPlayerUINT32Prop 0 'contextmenu' 0
playeripc: Got command SetPlayerUINT32Prop 0 'autostart' 1
playeripc: Got command Play 0
playeripc: Got command SetPlayerUINT32Prop 0 'volume' 40
playeripc: Got command SetPlayerUINT32Prop 0 'mute' 0
playeripc: Got command SetPlayerUINT32Prop 0 'loop' 0

(realplay.bin:8275): GLib-GObject-WARNING **: gvalue.c:89: cannot initialize GValue with type `gboolean', the value has already been initialized as `(null)'
/usr/bin/realplay: line 75:  8275 Segmentation fault      $REALPLAYBIN "$@"

I have searched google, forums...but could not find a fix. Can somebody please help me. Some clue ???


Thanks.

---

### Post by ming0 on 2005-05-08
I have found that realplayer doesn't work so well in hoary... it worked pretty well for me in warty, but unless i shut down esd (the sound daemon), I can't get RP to start. 
 
Try using the following command: **killall esd**, and see if RP will start. to get sound back (after closing RP) just issue the command: **esd**

---

### Post by sharmaravi on 2005-05-08
Thanks for the reply, I tried your suggestion and I still get the same error on trying to play streaming audio. Also, RealPlayer starts fine with/without esd and plays mp3 files without any problem.

---

### Post by ming0 on 2005-05-09
That sounds sort of mysterious... My only suggestion is to try re-installing realplayer.

Like I say, I got the real streams working under warty, but haven't had any luck w/ hoary. 

In addition, I think that Real is the devil (along w/ most other multimedia protocols **which are proprietary**). I'm very sorry that there isn't a robust OS alternative that places like PBS and the BBC couldn't start using for multi-media streaming!!! Video/Audio streaming is a HUGE nightmare :)

---

### Post by sharmaravi on 2005-05-10
Do I need to uninstall and then install. If yes, how do I uninstall. Since this is not from repository, I am not quite sure how to uninstall it.  Thanks

---

