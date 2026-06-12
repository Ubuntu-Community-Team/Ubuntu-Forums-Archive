---
title: "Aol Aim"
date: 2007-01-18
forum: General Help
---

### Post by DougieFresh4U on 2007-01-18
so I downloaded and supposedly installed AIM but I do not see launcher in any menu on my Xubuntu. How and where do I launch, thanks

---

### Post by bionnaki on 2007-01-18
sudo apt-get install gaim

---

### Post by DougieFresh4U on 2007-01-18
Thanks but I do use GAIM but I would like to try the original AIM as you can see from installer it put it some where

---

### Post by subdee on 2007-01-18
Try running it from console by typing aim. If it works then all you gotta do is create a shortcut. Unfortunately I haven't worked xfce so I don't know how to do that.

---

### Post by DougieFresh4U on 2007-01-18
dougie@DougiesToyBox:~$ aim
aim: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
dougie@DougiesToyBox:~$ 
 What does this mean? Thanks for trying!:)

---

### Post by Antonlacon on 2007-01-18
The official AIM client for Linux hasn't been updated in years.  Looks like a glibc incompatibility.

---

### Post by subdee on 2007-01-18
Agreed. Unfortunately, it looks as if you might have to stick with GAIM, which in my opinion is much better than AIM. Good luck.

---

### Post by DougieFresh4U on 2007-01-18
I am ready taurus. I downloaded the tgz and how much you wanna bet it's in temp, when download window says "Desktop"

---

### Post by taurus on 2007-01-18
```
ls -la ~/.aim
```

---

### Post by DougieFresh4U on 2007-01-18
dougie@DougiesToyBox:~$ ls -la ~/.aimls -la ~/.aim
ls: /home/dougie/.aimls: No such file or directory
ls: /home/dougie/.aim: No such file or directory
dougie@DougiesToyBox:~

---

### Post by taurus on 2007-01-18
Have you started aim before so it would create a config file in your $HOME directory?

---

### Post by DougieFresh4U on 2007-01-18
Not sure I understand, but you see the screen shots which say I have downloaded it

---

### Post by taurus on 2007-01-18
Start aim either from the menu or from a command line.  Then close it down.  Now, what does this command look like then?

```
ls -la ~/.aim
-or-
ls -la ~
```

---

### Post by DougieFresh4U on 2007-01-18
dougie@DougiesToyBox:~$ ls -la ~
total 11376
drwxr-xr-x 48 dougie dougie    4096 2007-01-18 11:10 .
drwxr-xr-x  3 root   root      4096 2007-01-09 21:56 ..
drwxr-xr-x  3 dougie dougie    4096 2007-01-15 23:44 .adobe
drwx------  8 dougie dougie    4096 2007-01-12 01:37 .amsn
drwx------  2 dougie dougie    4096 2007-01-12 01:33 amsn_received
-rw-r--r--  1 dougie dougie     283 2007-01-16 01:51 .audacity
drwxr-xr-x  2 dougie root      4096 2007-01-09 23:30 .automatix
-rw-r--r--  1 dougie dougie  454656 2007-01-11 03:34 avatar13.gif
-rw-r--r--  1 dougie dougie    4388 2007-01-11 03:40 avatar_46.jpg
-rw-------  1 dougie dougie    5094 2007-01-18 11:17 .bash_history
-rw-r--r--  1 dougie dougie     220 2007-01-09 21:56 .bash_logout
-rw-r--r--  1 dougie dougie     414 2007-01-09 21:56 .bash_profile
-rw-r--r--  1 dougie dougie    2227 2007-01-09 21:56 .bashrc
drwxr-xr-x  4 dougie dougie    4096 2007-01-10 02:24 .bmp
drwx------  5 dougie dougie    4096 2007-01-10 04:22 .cache
drwx------  7 dougie dougie    4096 2007-01-18 05:36 .config
-rw-r--r--  1 dougie dougie      51 2007-01-16 05:44 .current-song
-rw-r--r--  1 dougie dougie      60 2007-01-18 01:10 .DCOPserver_DougiesToyBox__0
lrwxrwxrwx  1 dougie dougie      41 2007-01-17 22:42 .DCOPserver_DougiesToyBox_:0 -> /home/dougie/.DCOPserver_DougiesToyBox__0
drwx------  2 dougie dougie    4096 2007-01-17 08:38 Desktop
-rw-------  1 dougie dougie      24 2007-01-09 22:12 .dmrc
drwxr-xr-x  5 dougie dougie    4096 2007-01-18 10:13 .exaile
lrwxrwxrwx  1 dougie dougie      26 2007-01-09 21:56 Examples -> /usr/share/example-content
drwxr-xr-x  2 dougie dougie    4096 2007-01-13 09:26 .fontconfig
-rw-r--r--  1 dougie dougie  483359 2007-01-09 23:12 .fonts.cache-1
drwxr-xr-x  4 dougie dougie    4096 2007-01-15 19:58 .frostwire
drwx------  6 dougie dougie    4096 2007-01-18 10:37 .gaim
drwx------  4 dougie dougie    4096 2007-01-18 00:45 .gconf
drwx------  2 dougie dougie    4096 2007-01-18 10:31 .gconfd
drwxr-xr-x 21 dougie dougie    4096 2007-01-13 09:29 .gimp-2.2
-rw-r-----  1 dougie dougie       0 2007-01-18 01:05 .gksu.lock
drwx------  5 dougie dougie    4096 2007-01-14 19:47 .gnome2
drwx------  2 dougie dougie    4096 2007-01-09 23:37 .gnome2_private
drwx------  2 dougie dougie    4096 2007-01-09 22:48 .gnupg
drwxr-xr-x  5 dougie dougie    4096 2007-01-15 23:47 .gqview
drwxr-xr-x  2 dougie dougie    4096 2007-01-18 00:06 .gstreamer-0.10
drwx------  2 dougie dougie    4096 2007-01-16 01:53 .gxine
-rw-------  1 dougie dougie    1677 2007-01-18 01:10 .ICEauthority
drwxr-xr-x 13 dougie dougie    4096 2006-10-22 11:26 iceweasel-1.5.0.7-g2-i386
-rw-r--r--  1 dougie dougie 7236984 2006-10-22 11:24 iceweasel-1.5.0.7-g2-i386.tar.bz2
drwxr-xr-x  2 dougie dougie    4096 2007-01-09 23:51 .icons
drwxr-xr-x  2 dougie dougie    4096 2007-01-15 19:58 Incomplete
drwxr-xr-x  3 dougie dougie    4096 2007-01-14 19:22 .java
drwx------  3 dougie dougie    4096 2007-01-10 02:22 .kde
-rw-r--r--  1 dougie dougie    1730 2007-01-07 16:34 key.gpg.asc
drwxr-xr-x  3 dougie dougie    4096 2007-01-16 05:19 .listen
drwxr-xr-x  3 dougie dougie    4096 2007-01-09 22:12 .local
drwxr-xr-x  4 dougie dougie    4096 2007-01-10 22:26 .lyrics
drwx------  3 dougie dougie    4096 2007-01-09 23:56 .macromedia
drwxr-xr-x  3 dougie dougie    4096 2007-01-10 15:56 .mcop
-rw-------  1 dougie dougie      31 2007-01-18 02:19 .mcoprc
drwx------  3 dougie dougie    4096 2007-01-10 01:58 .mozilla
drwx------  3 dougie dougie    4096 2007-01-10 01:58 .mozilla-thunderbird
drwxr-xr-x  2 dougie dougie    4096 2007-01-14 19:30 .mplayer
drwxr-xr-x  2 dougie dougie    4096 2007-01-16 01:48 NewName
drwxr-xr-x  2 dougie dougie    4096 2007-01-16 05:16 Podcasts
drwxr-xr-x  2 dougie dougie    4096 2007-01-17 22:43 .qt
drwxr-xr-x  2 dougie dougie    4096 2007-01-15 19:57 Shared
-rw-r--r--  1 dougie dougie  442392 2007-01-15 11:24 snapshot10.png
-rw-r--r--  1 dougie dougie  333006 2007-01-17 22:43 snapshot11.png
-rw-r--r--  1 dougie dougie   70646 2007-01-17 23:41 snapshot12.png
-rw-r--r--  1 dougie dougie  357661 2007-01-18 01:10 snapshot13.png
-rw-r--r--  1 dougie dougie  181942 2007-01-18 01:28 snapshot14.png
-rw-r--r--  1 dougie dougie  271200 2007-01-18 10:45 snapshot15.png
-rw-r--r--  1 dougie dougie  177783 2007-01-18 11:10 snapshot16.png
-rw-r--r--  1 dougie dougie  274019 2007-01-15 10:09 snapshot8.png
-rw-r--r--  1 dougie dougie  437878 2007-01-15 10:26 snapshot9.png
drwxr-xr-x  5 dougie dougie    4096 2007-01-16 01:00 src
drwxr-xr-x  3 dougie dougie    4096 2007-01-13 09:00 .streamtuner
-rw-r--r--  1 dougie dougie       0 2007-01-09 22:13 .sudo_as_admin_successful
-rw-r--r--  1 dougie dougie  492997 2007-01-13 08:47 Swiftfox_wallpaper.png
drwxr-xr-x  3 dougie dougie    4096 2007-01-10 00:22 .thumbnails
drwxr-xr-x  2 dougie dougie    4096 2007-01-09 22:18 .update-manager
drwxr-xr-x  3 dougie dougie    4096 2007-01-18 05:25 .vlc
drwxr-xr-x  4 dougie dougie    4096 2007-01-10 05:30 .wine
-rw-------  1 dougie dougie     124 2007-01-18 00:45 .Xauthority
drwxr-xr-x  2 dougie dougie    4096 2007-01-10 04:28 .xine
drwxr-xr-x  4 dougie dougie    4096 2007-01-11 03:52 .xmms
-rw-r--r--  1 dougie dougie   11416 2007-01-09 23:47 .xscreensaver
-rw-r--r--  1 dougie dougie   66929 2007-01-18 11:17 .xsession-errors
I don't see it any where

---

### Post by taurus on 2007-01-18
And you did run **aim** before you ran that command, ls -la ~, right?

```
locate aim
```

---

### Post by DougieFresh4U on 2007-01-18
/usr/share/pixmaps/gaim/smileys/maya/easteregg05.png
/usr/share/pixmaps/gaim/smileys/maya/easteregg06.png
/usr/share/pixmaps/gaim/smileys/maya/easteregg07.png
/usr/share/pixmaps/gaim/smileys/maya/easteregg08.png
/usr/share/pixmaps/gaim/smileys/maya/easteregg09.png
/usr/share/pixmaps/gaim/smileys/maya/easteregg10.png
/usr/share/pixmaps/gaim/smileys/maya/easteregg11.png
/usr/share/pixmaps/gaim/smileys/maya/easteregg12.png
/usr/share/pixmaps/gaim/smileys/maya/easteregg13.png
/usr/share/pixmaps/gaim/smileys/maya/easteregg14.png
/usr/share/pixmaps/gaim/smileys/maya/easteregg15.png
/usr/share/pixmaps/gaim/smileys/maya/easteregg16.png
/usr/share/pixmaps/gaim/smileys/maya/cartman_cop.gif
/usr/share/pixmaps/gaim/smileys/maya/cartman_ghost.gif
/usr/share/pixmaps/gaim/smileys/maya/cartman_hitler.gif
/usr/share/pixmaps/gaim/smileys/maya/cartman_pissed.gif
/usr/share/pixmaps/gaim/smileys/maya/maya-smile02.png
/usr/share/pixmaps/gaim/smileys/maya/maya-smile.png
/usr/share/pixmaps/gaim/smileys/maya/maya-embarrassed.png
/usr/share/pixmaps/gaim/smileys/maya/maya-smile03.png
/usr/share/pixmaps/gaim/smileys/maya/maya-fish.png
/usr/share/pixmaps/gaim/smileys/maya/maya-im.png
/usr/share/pixmaps/gaim/smileys/maya/maya-kiss.png
/usr/share/pixmaps/gaim/smileys/maya/maya-shock.png
/usr/share/pixmaps/gaim/smileys/maya/maya-snake.png
/usr/share/pixmaps/gaim/smileys/maya/maya-tongue.png
/usr/share/pixmaps/gaim/smileys/maya/maya-wink.png
/usr/share/pixmaps/gaim/smileys/maya/maya-angry.png
/usr/share/pixmaps/gaim/smileys/maya/maya-smiley.png
/usr/share/pixmaps/gaim/smileys/maya/maya-laugh.png
/usr/share/pixmaps/gaim/smileys/maya/maya-neutral.png
/usr/share/pixmaps/gaim/smileys/maya/maya-sleep.png
/usr/share/pixmaps/gaim/smileys/maya/maya-kiss2.png
/usr/share/pixmaps/gaim/smileys/maya/maya-rainbow.png
/usr/share/pixmaps/gaim/smileys/maya/maya-angel.png
/usr/share/pixmaps/gaim/smileys/maya/maya-cry.png
/usr/share/pixmaps/gaim/smileys/maya/maya-theme.png
/usr/share/pixmaps/gaim/smileys/maya/maya-01-30.png
/usr/share/pixmaps/gaim/smileys/maya/maya-smiley02.png
/usr/share/pixmaps/gaim/smileys/maya/maya-sad.png
/usr/share/pixmaps/gaim/smileys/maya/maya-02-50.png
/usr/share/pixmaps/gaim/smileys/maya/maya-16-45.png
/usr/share/pixmaps/gaim/smileys/maya/maya-secret.png
/usr/share/pixmaps/gaim/smileys/maya/maya-tongue2.png
/usr/share/pixmaps/gaim/smileys/maya/maya-tea.png
/usr/share/pixmaps/gaim/smileys/maya/maya-oops.png
/usr/share/pixmaps/gaim/smileys/maya/maya-nolisten.png
/usr/share/pixmaps/gaim/smileys/maya/maya-email.png
/usr/share/pixmaps/gaim/smileys/maya/maya-pizza.png
/usr/share/pixmaps/gaim/smileys/maya/maya-frustrated.png
/usr/share/pixmaps/gaim/smileys/maya/maya-monkey.png
/usr/share/pixmaps/gaim/smileys/maya/maya-xmouth.png
/usr/share/pixmaps/gaim/smileys/nis
/usr/share/pixmaps/gaim/smileys/nis/yahoo_cowboy.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_cry.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_devil.gif
/usr/share/pixmaps/gaim/smileys/nis/download.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_cow.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_frustrated.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_neutral.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_confused.gif
/usr/share/pixmaps/gaim/smileys/nis/msn_boy.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_tired.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_bye.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_drool.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_bigsmile.gif
/usr/share/pixmaps/gaim/smileys/nis/msn_star.png
/usr/share/pixmaps/gaim/smileys/nis/msn_cat.png
/usr/share/pixmaps/gaim/smileys/nis/nis_cool.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_whistling.gif
/usr/share/pixmaps/gaim/smileys/nis/msn_photo.png
/usr/share/pixmaps/gaim/smileys/nis/msn_handcuffs.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_love.gif
/usr/share/pixmaps/gaim/smileys/nis/nis_kiss.png
/usr/share/pixmaps/gaim/smileys/nis/msn_wink.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_clap.gif
/usr/share/pixmaps/gaim/smileys/nis/msn_hot.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_worried.gif
/usr/share/pixmaps/gaim/smileys/nis/nis_smile.png
/usr/share/pixmaps/gaim/smileys/nis/msn_phone.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_clown.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_peace.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_hypnotized.gif
/usr/share/pixmaps/gaim/smileys/nis/nis_embarrassed.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_pig.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_sunglas.gif
/usr/share/pixmaps/gaim/smileys/nis/msn_rainbow.png
/usr/share/pixmaps/gaim/smileys/nis/msn_bat.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_mean.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_smiley.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_liar.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_huggs.gif
/usr/share/pixmaps/gaim/smileys/nis/farted.png
/usr/share/pixmaps/gaim/smileys/nis/luke.png
/usr/share/pixmaps/gaim/smileys/nis/nis_angel.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_eyeroll.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_glasses.gif
/usr/share/pixmaps/gaim/smileys/nis/nis_muted.png
/usr/share/pixmaps/gaim/smileys/nis/msn_neutral.png
/usr/share/pixmaps/gaim/smileys/nis/msn_angry.png
/usr/share/pixmaps/gaim/smileys/nis/msn_coffee.png
/usr/share/pixmaps/gaim/smileys/nis/msn_kiss.png
/usr/share/pixmaps/gaim/smileys/nis/msn_occ.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_alien2.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_angry.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_ghost.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_silly.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_question.gif
/usr/share/pixmaps/gaim/smileys/nis/msn_cake.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_tongue.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_flag.gif
/usr/share/pixmaps/gaim/smileys/nis/msn_film.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_wink.gif
/usr/share/pixmaps/gaim/smileys/nis/msn_flower.png
/usr/share/pixmaps/gaim/smileys/nis/mrt.png
/usr/share/pixmaps/gaim/smileys/nis/msn_clock.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_pray.gif
/usr/share/pixmaps/gaim/smileys/nis/oneeye.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_eyebrow.gif
/usr/share/pixmaps/gaim/smileys/nis/msn_icon.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_alien.gif
/usr/share/pixmaps/gaim/smileys/nis/msn_idea.png
/usr/share/pixmaps/gaim/smileys/nis/crazy.png
/usr/share/pixmaps/gaim/smileys/nis/msn_deadflower.png
/usr/share/pixmaps/gaim/smileys/nis/msn_beer.png
/usr/share/pixmaps/gaim/smileys/nis/msn_away.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_beatup.gif
/usr/share/pixmaps/gaim/smileys/nis/msn_sun.png
/usr/share/pixmaps/gaim/smileys/nis/msn_angel.png
/usr/share/pixmaps/gaim/smileys/nis/nis_tongue.png
/usr/share/pixmaps/gaim/smileys/nis/msn_thumbdown.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_chicken.gif
/usr/share/pixmaps/gaim/smileys/nis/msn_question.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_angel.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_pumpkin.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_shame.gif
/usr/share/pixmaps/gaim/smileys/nis/msn_heart.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_batting.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_shamrock.gif
/usr/share/pixmaps/gaim/smileys/nis/nis_happy.png
/usr/share/pixmaps/gaim/smileys/nis/msn_embarrassed.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_kiss.gif
/usr/share/pixmaps/gaim/smileys/nis/nis_weird.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_silent.gif
/usr/share/pixmaps/gaim/smileys/nis/msn_thumbup.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_dance.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_shhhh.gif
/usr/share/pixmaps/gaim/smileys/nis/msn_brheart.png
/usr/share/pixmaps/gaim/smileys/nis/nis_ungry.png
/usr/share/pixmaps/gaim/smileys/nis/msn_run.png
/usr/share/pixmaps/gaim/smileys/nis/msn_email.png
/usr/share/pixmaps/gaim/smileys/nis/msn_sleep.png
/usr/share/pixmaps/gaim/smileys/nis/msn_ooooh.png
/usr/share/pixmaps/gaim/smileys/nis/nis_sad.png
/usr/share/pixmaps/gaim/smileys/nis/msn_note.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_moneyeyes.gif
/usr/share/pixmaps/gaim/smileys/nis/nis_sealed.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_sleep.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_ooooh.gif
/usr/share/pixmaps/gaim/smileys/nis/msn_smiley.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_idea.gif
/usr/share/pixmaps/gaim/smileys/nis/msn_girl.png
/usr/share/pixmaps/gaim/smileys/nis/nis_cry.png
/usr/share/pixmaps/gaim/smileys/nis/msn_online.png
/usr/share/pixmaps/gaim/smileys/nis/msn_dog.png
/usr/share/pixmaps/gaim/smileys/nis/msn_sad.png
/usr/share/pixmaps/gaim/smileys/nis/nis_surprised.png
/usr/share/pixmaps/gaim/smileys/nis/theme
/usr/share/pixmaps/gaim/smileys/nis/msn_runback.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_monkey.gif
/usr/share/pixmaps/gaim/smileys/nis/msn_weird.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_think.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_laughloud.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_coffee.gif
/usr/share/pixmaps/gaim/smileys/nis/msn_cry.png
/usr/share/pixmaps/gaim/smileys/nis/msn_tongue.png
/usr/share/pixmaps/gaim/smileys/nis/msn_gift.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_doh.gif
/usr/share/pixmaps/gaim/smileys/nis/yahoo_sad.gif
/usr/share/pixmaps/gaim/smileys/nis/msn_drink.png
/usr/share/pixmaps/gaim/smileys/nis/msn_devil.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_flower.gif
/usr/share/pixmaps/gaim/smileys/nis/nis_wink.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_sick.gif
/usr/share/pixmaps/gaim/smileys/nis/nis_demon.png
/usr/share/pixmaps/gaim/smileys/nis/msn_laugh.png
/usr/share/pixmaps/gaim/smileys/nis/yahoo_blush.gif
/usr/share/pixmaps/gaim/status
/usr/share/pixmaps/gaim/status/default
/usr/share/pixmaps/gaim/status/default/activebuddy.png
/usr/share/pixmaps/gaim/status/default/admin.png
/usr/share/pixmaps/gaim/status/default/aim.png
/usr/share/pixmaps/gaim/status/default/aol.png
/usr/share/pixmaps/gaim/status/default/away.png
/usr/share/pixmaps/gaim/status/default/blocked.png
/usr/share/pixmaps/gaim/status/default/bonjour.png
/usr/share/pixmaps/gaim/status/default/dnd.png
/usr/share/pixmaps/gaim/status/default/extended_away.png
/usr/share/pixmaps/gaim/status/default/external.png
/usr/share/pixmaps/gaim/status/default/female.png
/usr/share/pixmaps/gaim/status/default/founder.png
/usr/share/pixmaps/gaim/status/default/freeforchat.png
/usr/share/pixmaps/gaim/status/default/gadu-gadu.png
/usr/share/pixmaps/gaim/status/default/game.png
/usr/share/pixmaps/gaim/status/default/halfop.png
/usr/share/pixmaps/gaim/status/default/hiptop.png
/usr/share/pixmaps/gaim/status/default/icq.png
/usr/share/pixmaps/gaim/status/default/ignored.png
/usr/share/pixmaps/gaim/status/default/invisible.png
/usr/share/pixmaps/gaim/status/default/irc.png
/usr/share/pixmaps/gaim/status/default/jabber.png
/usr/share/pixmaps/gaim/status/default/login.png
/usr/share/pixmaps/gaim/status/default/logout.png
/usr/share/pixmaps/gaim/status/default/male.png
/usr/share/pixmaps/gaim/status/default/meanwhile.png
/usr/share/pixmaps/gaim/status/default/msn.png
/usr/share/pixmaps/gaim/status/default/notauthorized.png
/usr/share/pixmaps/gaim/status/default/novell.png
/usr/share/pixmaps/gaim/status/default/occupied.png
/usr/share/pixmaps/gaim/status/default/offline.png
/usr/share/pixmaps/gaim/status/default/op.png
/usr/share/pixmaps/gaim/status/default/pending.png
/usr/share/pixmaps/gaim/status/default/secure.png
/usr/share/pixmaps/gaim/status/default/silc.png
/usr/share/pixmaps/gaim/status/default/simple.png
/usr/share/pixmaps/gaim/status/default/unavailable.png
/usr/share/pixmaps/gaim/status/default/voice.png
/usr/share/pixmaps/gaim/status/default/wireless.png
/usr/share/pixmaps/gaim/status/default/yahoo.png
/usr/share/pixmaps/gaim/status/default/zephyr.png
/usr/share/pixmaps/gaim/status/default/qq.png
/usr/share/pixmaps/gaim/status/default/qq_1.png
/usr/share/pixmaps/gaim/status/default/qq_2.png
/usr/share/pixmaps/gaim/status/default/qq_3.png
/usr/share/pixmaps/gaim/status/default/qq_4.png
/usr/share/pixmaps/gaim/status/default/qq_5.png
/usr/share/pixmaps/gaim/status/default/qq_6.png
/usr/share/pixmaps/gaim/status/default/qq_7.png
/usr/share/pixmaps/gaim/status/default/qq_8.png
/usr/share/pixmaps/gaim/status/default/qq_9.png
/usr/share/pixmaps/gaim/status/default/qq_10.png
/usr/share/pixmaps/gaim/status/default/qq_11.png
/usr/share/pixmaps/gaim/status/default/qq_12.png
/usr/share/pixmaps/gaim/status/default/qq_13.png
/usr/share/pixmaps/gaim/status/default/qq_14.png
/usr/share/pixmaps/gaim/status/default/qq_15.png
/usr/share/pixmaps/gaim/status/default/qq_16.png
/usr/share/pixmaps/gaim/status/default/qq_17.png
/usr/share/pixmaps/gaim/status/default/qq_18.png
/usr/share/pixmaps/gaim/status/default/qq_19.png
/usr/share/pixmaps/gaim/status/default/qq_20.png
/usr/share/pixmaps/gaim/status/default/qq_21.png
/usr/share/pixmaps/gaim/status/default/qq_22.png
/usr/share/pixmaps/gaim/status/default/qq_23.png
/usr/share/pixmaps/gaim/status/default/qq_24.png
/usr/share/pixmaps/gaim/status/default/qq_25.png
/usr/share/pixmaps/gaim/status/default/qq_26.png
/usr/share/pixmaps/gaim/status/default/qq_27.png
/usr/share/pixmaps/gaim/status/default/qq_28.png
/usr/share/pixmaps/gaim/status/default/qq_29.png
/usr/share/pixmaps/gaim/status/default/qq_30.png
/usr/share/pixmaps/gaim/status/default/qq_31.png
/usr/share/pixmaps/gaim/status/default/qq_32.png
/usr/share/pixmaps/gaim/status/default/qq_33.png
/usr/share/pixmaps/gaim/status/default/qq_34.png
/usr/share/pixmaps/gaim/status/default/qq_35.png
/usr/share/pixmaps/gaim/status/default/qq_36.png
/usr/share/pixmaps/gaim/status/default/qq_37.png
/usr/share/pixmaps/gaim/status/default/qq_38.png
/usr/share/pixmaps/gaim/status/default/qq_39.png
/usr/share/pixmaps/gaim/status/default/qq_40.png
/usr/share/pixmaps/gaim/status/default/qq_41.png
/usr/share/pixmaps/gaim/status/default/qq_42.png
/usr/share/pixmaps/gaim/status/default/qq_43.png
/usr/share/pixmaps/gaim/status/default/qq_44.png
/usr/share/pixmaps/gaim/status/default/qq_45.png
/usr/share/pixmaps/gaim/status/default/qq_46.png
/usr/share/pixmaps/gaim/status/default/qq_47.png
/usr/share/pixmaps/gaim/status/default/qq_48.png
/usr/share/pixmaps/gaim/status/default/qq_49.png
/usr/share/pixmaps/gaim/status/default/qq_50.png
/usr/share/pixmaps/gaim/status/default/qq_51.png
/usr/share/pixmaps/gaim/status/default/qq_52.png
/usr/share/pixmaps/gaim/status/default/qq_53.png
/usr/share/pixmaps/gaim/status/default/qq_54.png
/usr/share/pixmaps/gaim/status/default/qq_55.png
/usr/share/pixmaps/gaim/status/default/qq_56.png
/usr/share/pixmaps/gaim/status/default/qq_57.png
/usr/share/pixmaps/gaim/status/default/qq_58.png
/usr/share/pixmaps/gaim/status/default/qq_59.png
/usr/share/pixmaps/gaim/status/default/qq_60.png
/usr/share/pixmaps/gaim/status/default/qq_61.png
/usr/share/pixmaps/gaim/status/default/qq_62.png
/usr/share/pixmaps/gaim/status/default/qq_63.png
/usr/share/pixmaps/gaim/status/default/qq_64.png
/usr/share/pixmaps/gaim/status/default/qq_65.png
/usr/share/pixmaps/gaim/status/default/qq_66.png
/usr/share/pixmaps/gaim/status/default/qq_67.png
/usr/share/pixmaps/gaim/status/default/qq_68.png
/usr/share/pixmaps/gaim/status/default/qq_69.png
/usr/share/pixmaps/gaim/status/default/qq_70.png
/usr/share/pixmaps/gaim/status/default/qq_71.png
/usr/share/pixmaps/gaim/status/default/qq_72.png
/usr/share/pixmaps/gaim/status/default/qq_73.png
/usr/share/pixmaps/gaim/status/default/qq_74.png
/usr/share/pixmaps/gaim/status/default/qq_75.png
/usr/share/pixmaps/gaim/status/default/qq_76.png
/usr/share/pixmaps/gaim/status/default/qq_77.png
/usr/share/pixmaps/gaim/status/default/qq_78.png
/usr/share/pixmaps/gaim/status/default/qq_79.png
/usr/share/pixmaps/gaim/status/default/qq_80.png
/usr/share/pixmaps/gaim/status/default/qq_81.png
/usr/share/pixmaps/gaim/status/default/qq_82.png
/usr/share/pixmaps/gaim/status/default/qq_83.png
/usr/share/pixmaps/gaim/status/default/qq_84.png
/usr/share/pixmaps/gaim/status/default/qq_85.png
/usr/share/pixmaps/gaim/status/default/qq_86.png
/usr/share/pixmaps/gaim/status/default/qq_87.png
/usr/share/pixmaps/gaim/status/default/qq_88.png
/usr/share/pixmaps/gaim/status/default/qq_89.png
/usr/share/pixmaps/gaim/status/default/qq_90.png
/usr/share/pixmaps/gaim/status/default/qq_91.png
/usr/share/pixmaps/gaim/status/default/qq_92.png
/usr/share/pixmaps/gaim/status/default/qq_93.png
/usr/share/pixmaps/gaim/status/default/qq_94.png
/usr/share/pixmaps/gaim/status/default/qq_95.png
/usr/share/pixmaps/gaim/status/default/qq_96.png
/usr/share/pixmaps/gaim/status/default/qq_97.png
/usr/share/pixmaps/gaim/status/default/qq_98.png
/usr/share/pixmaps/gaim/status/default/qq_99.png
/usr/share/pixmaps/gaim/status/default/qq_100.png
/usr/share/pixmaps/gaim/logo.png
/usr/share/pixmaps/gaim/phone.png
/usr/share/pixmaps/gaim/status-away.png
/usr/share/pixmaps/gaim/status-connect0.png
/usr/share/pixmaps/gaim/status-connect1.png
/usr/share/pixmaps/gaim/status-connect2.png
/usr/share/pixmaps/gaim/status-connect3.png
/usr/share/pixmaps/gaim/status-invisible.png
/usr/share/pixmaps/gaim/status-offline.png
/usr/share/pixmaps/gaim/status-online.png
/usr/share/pixmaps/gaim/status-typing0.png
/usr/share/pixmaps/gaim/status-typing1.png
/usr/share/pixmaps/gaim/status-typing2.png
/usr/share/pixmaps/gaim/status-typing3.png
/usr/share/pixmaps/gaim/tb_drag_arrow_down.xpm
/usr/share/pixmaps/gaim/tb_drag_arrow_left.xpm
/usr/share/pixmaps/gaim/tb_drag_arrow_right.xpm
/usr/share/pixmaps/gaim/tb_drag_arrow_up.xpm
/usr/share/pixmaps/gaim/typed.png
/usr/share/pixmaps/gaim/typing.png
/usr/share/pixmaps/gaim/insert-image.png
/usr/share/pixmaps/gaim/gaim-encryption
/usr/share/pixmaps/gaim/gaim-encryption/crypto.png
/usr/share/pixmaps/gaim/guifications
/usr/share/pixmaps/gaim/guifications/conf
/usr/share/pixmaps/gaim/guifications/conf/item_icon_size_large.png
/usr/share/pixmaps/gaim/guifications/conf/item_icon_size_big.png
/usr/share/pixmaps/gaim/guifications/conf/item_icon_size_huge.png
/usr/share/pixmaps/gaim/guifications/conf/item_position_north_east.png
/usr/share/pixmaps/gaim/guifications/conf/item_icon_size_little.png
/usr/share/pixmaps/gaim/guifications/conf/item_icon_size_normal.png
/usr/share/pixmaps/gaim/guifications/conf/item_icon_size_small.png
/usr/share/pixmaps/gaim/guifications/conf/item_icon_size_tiny.png
/usr/share/pixmaps/gaim/guifications/conf/item_position_center.png
/usr/share/pixmaps/gaim/guifications/conf/item_position_east.png
/usr/share/pixmaps/gaim/guifications/conf/item_position_north_west.png
/usr/share/pixmaps/gaim/guifications/conf/item_position_north.png
/usr/share/pixmaps/gaim/guifications/conf/item_text_clipping_ellipsis_end.png
/usr/share/pixmaps/gaim/guifications/conf/item_position_south_east.png
/usr/share/pixmaps/gaim/guifications/conf/item_position_south.png
/usr/share/pixmaps/gaim/guifications/conf/item_position_south_west.png
/usr/share/pixmaps/gaim/guifications/conf/item_position_west.png
/usr/share/pixmaps/gaim/guifications/conf/item_text_clipping_ellipsis_middle.png
/usr/share/pixmaps/gaim/guifications/conf/item_text_clipping_ellipsis_start.png
/usr/share/pixmaps/gaim/guifications/conf/item_text_clipping_truncate.png
/usr/share/pixmaps/gaim/guifications/conf/window_position_north_east.png
/usr/share/pixmaps/gaim/guifications/conf/window_position_north_west.png
/usr/share/pixmaps/gaim/guifications/conf/window_position_south_east.png
/usr/share/pixmaps/gaim/guifications/conf/window_position_south_west.png
/usr/share/pixmaps/gaim/guifications/themes
/usr/share/pixmaps/gaim/guifications/themes/Penguins
/usr/share/pixmaps/gaim/guifications/themes/Penguins/penguin.png
/usr/share/pixmaps/gaim/guifications/themes/Penguins/theme.xml
/usr/share/pixmaps/gaim/guifications/themes/default
/usr/share/pixmaps/gaim/guifications/themes/default/background.png
/usr/share/pixmaps/gaim/guifications/themes/default/theme.xml
/usr/share/pixmaps/gaim/guifications/themes/mini
/usr/share/pixmaps/gaim/guifications/themes/mini/background.png
/usr/share/pixmaps/gaim/guifications/themes/mini/theme.xml
/usr/share/pixmaps/gaim-menu.xpm
/usr/share/pixmaps/gaim.png
/usr/share/pixmaps/gaim.svg
/usr/share/sounds/gaim
/usr/share/sounds/gaim/alert.wav
/usr/share/sounds/gaim/login.wav
/usr/share/sounds/gaim/logout.wav
/usr/share/sounds/gaim/receive.wav
/usr/share/sounds/gaim/send.wav
/usr/share/ttf-arphic-ukai/ukaimbe2ukai.xdelta
/usr/share/services/aim.protocol
/usr/share/services/kopete_aim.desktop
dougie@DougiesToyBox**:~to much output from that code and will not let me load it**

---

### Post by taurus on 2007-01-18
What happens when you run aim from a terminal?

```
aim
```

---

### Post by DougieFresh4U on 2007-01-18
dougie@DougiesToyBox:~$ aim
aim: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-01-18
There's your problem.  You first need to run aim so it would create a ~/.aim; and that's where you would unpack your skin.  And I believe you installed aim from the repos!  Remove it and install the latest version from here.

[http://channels.netscape.com/wrap/linker.jsp?floc=at_oslin_1_l3&ref=http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb](http://channels.netscape.com/wrap/linker.jsp?floc=at_oslin_1_l3&ref=http://ftp.newaol.com/aimgen/380469/aim_1.5.286-2_i386.deb)

```
sudo aptitude purge aim
sudo aptitude update
sudo dpkg -i /tmp/aim_1.5.286-2.i386.deb
aim
```

---

### Post by DougieFresh4U on 2007-01-18
dougie@DougiesToyBox:~$ sudo dpkg -i /tmp/aim_1.5.286-2.i386.deb
dpkg: error processing /tmp/aim_1.5.286-2.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /tmp/aim_1.5.286-2.i386.deb
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-01-18
Okay, where did you save it this time?

```
ls -l ~
ls -l ~/Desktop
```

---

### Post by DougieFresh4U on 2007-01-18
**I don't know:confused:  machines got a mind of it's own:-k** dougie@DougiesToyBox:~$ ls -l ~
total 10604
drwx------  2 dougie dougie    4096 2007-01-12 01:33 amsn_received
-rw-r--r--  1 dougie dougie  454656 2007-01-11 03:34 avatar13.gif
-rw-r--r--  1 dougie dougie    4388 2007-01-11 03:40 avatar_46.jpg
drwx------  2 dougie dougie    4096 2007-01-17 08:38 Desktop
lrwxrwxrwx  1 dougie dougie      26 2007-01-09 21:56 Examples -> /usr/share/example-content
drwxr-xr-x 13 dougie dougie    4096 2006-10-22 11:26 iceweasel-1.5.0.7-g2-i386
-rw-r--r--  1 dougie dougie 7236984 2006-10-22 11:24 iceweasel-1.5.0.7-g2-i386.tar.bz2
drwxr-xr-x  2 dougie dougie    4096 2007-01-15 19:58 Incomplete
-rw-r--r--  1 dougie dougie    1730 2007-01-07 16:34 key.gpg.asc
drwxr-xr-x  2 dougie dougie    4096 2007-01-16 01:48 NewName
drwxr-xr-x  2 dougie dougie    4096 2007-01-16 05:16 Podcasts
drwxr-xr-x  2 dougie dougie    4096 2007-01-15 19:57 Shared
-rw-r--r--  1 dougie dougie  442392 2007-01-15 11:24 snapshot10.png
-rw-r--r--  1 dougie dougie  333006 2007-01-17 22:43 snapshot11.png
-rw-r--r--  1 dougie dougie   70646 2007-01-17 23:41 snapshot12.png
-rw-r--r--  1 dougie dougie  357661 2007-01-18 01:10 snapshot13.png
-rw-r--r--  1 dougie dougie  181942 2007-01-18 01:28 snapshot14.png
-rw-r--r--  1 dougie dougie  271200 2007-01-18 10:45 snapshot15.png
-rw-r--r--  1 dougie dougie  177783 2007-01-18 11:10 snapshot16.png
-rw-r--r--  1 dougie dougie  274019 2007-01-15 10:09 snapshot8.png
-rw-r--r--  1 dougie dougie  437878 2007-01-15 10:26 snapshot9.png
drwxr-xr-x  5 dougie dougie    4096 2007-01-16 01:00 src
-rw-r--r--  1 dougie dougie  492997 2007-01-13 08:47 Swiftfox_wallpaper.png
dougie@DougiesToyBox:~$ ls -l ~/Desktop
total 68
-rw-r--r-- 1 dougie dougie 222 2007-01-10 02:19 Amarok.desktop
-rw-r--r-- 1 dougie dougie 182 2007-01-12 12:05 aMSN.desktop
-rw-r--r-- 1 dougie dougie 214 2007-01-10 02:19 Exaile!.desktop
-rw-r--r-- 1 dougie dougie 248 2007-01-10 02:18 FreeCell Solitaire.desktop
-rw-r--r-- 1 dougie dougie 233 2007-01-10 00:22 FrostWire.desktop
-rw-r--r-- 1 dougie dougie 222 2007-01-10 02:21 Gaim Internet Messenger.desktop
-rw-r--r-- 1 dougie dougie 258 2007-01-10 02:20 GNOME ALSA Mixer.desktop
-rw-r--r-- 1 dougie dougie 205 2007-01-16 02:30 Kopete.desktop
-rw-r--r-- 1 dougie dougie 215 2007-01-10 02:20 Listen Music Player.desktop
-rw-r--r-- 1 dougie dougie 241 2007-01-10 02:18 Mahjongg.desktop
-rw-r--r-- 1 dougie dougie 225 2007-01-10 02:24 Rhythmbox Music Player.desktop
-rw-r--r-- 1 dougie dougie 201 2007-01-10 02:22 Shisen-Sho.desktop
-rw-r--r-- 1 dougie dougie 213 2007-01-10 02:19 streamtuner.desktop
-rw-r--r-- 1 dougie dougie 215 2007-01-14 16:16 Swiftfox Browser.desktop
-rw-r--r-- 1 dougie dougie 193 2007-01-10 02:21 Terminal.desktop
-rw-r--r-- 1 dougie dougie 231 2007-01-10 02:21 Thunderbird Mail.desktop
-rw-r--r-- 1 dougie dougie 175 2007-01-10 02:19 XMMS Music Player.desktop
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-01-18
Here we go again.  Now we have to find it!

```
sudo find / -name aim_1.5.286-2.i386.deb -print
```

---

### Post by DougieFresh4U on 2007-01-18
here look:

---

### Post by DougieFresh4U on 2007-01-18
dougie@DougiesToyBox:~$ sudo find / -name aim_1.5.286-2.i386.deb -print
Password:
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-01-18
Did you download the one that I provided from above because it's a .deb file.  Otherwise, you have to build it from the version on your machine right now, .tgz! 

p.s.  You did remove the previous version, aim, from your machine, right?  So when you type **aim** at the prompt, you would get an error message of command not found!

---

### Post by strabes on 2007-01-18
sorry for the non-answer but what is that font in your 1st screenshot? it's awesome.

---

### Post by arnieboy on 2007-01-19
> **DougieFresh4U said:**
> dougie@DougiesToyBox:~$ aim
aim: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
dougie@DougiesToyBox:~$ 
 What does this mean? Thanks for trying!:)

please paste the results of the following command:
```
ls -l /usr/lib/libstdc++-libc6*
```

---

### Post by DougieFresh4U on 2007-01-19
Ok, after several failures I want to start from scratch and attempt to install  AIM. So how do I get rid of all and start over:confused:

---

### Post by arnieboy on 2007-01-19
> **DougieFresh4U said:**
> Ok, after several failures I want to start from scratch and attempt to install  AIM. So how do I get rid of all and start over:confused:

starting all over wont help. read my last post.

---

### Post by DougieFresh4U on 2007-01-19
> **arnieboy said:**
> please paste the results of the following command:
```
ls -l /usr/lib/libstdc++-libc6*
```

dougie@DougiesToyBox:~$ ls -l /usr/lib/libstdc++-libc6*
ls: /usr/lib/libstdc++-libc6*: No such file or directory
dougie@DougiesToyBox:~$ 
Sorry for not replying sooner, had to step out.:lolflag:

---

### Post by DougieFresh4U on 2007-01-20
Bump
):P

---

### Post by DougieFresh4U on 2007-01-20
> **DougieFresh4U said:**
> dougie@DougiesToyBox:~$ ls -l /usr/lib/libstdc++-libc6*
ls: /usr/lib/libstdc++-libc6*: No such file or directory
dougie@DougiesToyBox:~$ 
Sorry for not replying sooner, had to step out.:lolflag:

Can some one please help me get these packages):P

---

### Post by twisted_steel on 2007-01-21
I'm not sure if you can get these packages for Ubuntu at all.  I was looking around on Google and I found some RPM packages that provided it for RedHat 6 in [1999]("http://www.dlhoffman.com/publiclibrary/RPM/contrib/libc6/i386/libstdc++-2.95.1_2.10.0-3.i386.html").  These are for gcc 2.95, and Edgy comes with gcc 4.1.2.  If you look at the [compatibility]("http://www.aim.com/get_aim/linux/latest_linux.adp") for AIM, it lists distribution versions that were last released around 2000.  You might be able to do something crazy like install RedHat 6 or Mandrake 7 in VMware, and then install AIM assuming you can still find ISOs.

I do remember using the official AIM client around 1999 or 2000, back when I had to download ISOs over dialup, and it was pretty bad. :roll:

---

