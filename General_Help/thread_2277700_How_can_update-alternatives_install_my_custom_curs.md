---
title: "How can update-alternatives install my custom cursor theme?"
date: 2015-05-11
forum: General Help
---

### Post by PenguinLust on 2015-05-11
I made a custom mouse cursor theme, but I can't seem to get it to install properly. I tried using update-alternatives, and the entry appears in list, but selecting one doesn't do anything.
I'm running LUbuntu 14.04

---

### Post by Bucky Ball on 2015-05-11
*Thread moved to **General Help**.*

---

### Post by CantankRus on 2015-05-11
If your using **galternatives** it has a bug in 14.04.
Run this terminal command to create a link.
```
sudo ln -s /usr/bin/update-alternatives /usr/sbin/
```
Everything else being OK, you should now be able to select your theme using galternatives.

---

### Post by PenguinLust on 2015-05-11
Actually, I didn't have galternatives. Now that I've installed it and took your advice, it hasn't made a difference.
I'm assuming that one of these "alternatives" is the right tool. I've also tried unity-tweak-tool, gnome-tweak-tool and the "Look and Feel" thing in the menu, but that one only affects which cursors Firefox is going to display.

---

### Post by CantankRus on 2015-05-11
I have Lubuntu installed in another partition just for testing.
All I need do is place the cursor theme folder in /usr/share/icons 
then select using lxappearance.
Didn't even use update-alternatives.
The cursor is consistent.

---

### Post by PenguinLust on 2015-05-11
Ah yes, lxappearance. That's the "Customize Look and Feel" I've been using. It's enormously convenient, but it only changes the cursors for Firefox. Googling this problem, it doesn't seem unusual, and those posts tend to recommend all those other tools for switching cursor themes.
I skipped a step, actually. Right now I'm just trying to change the cursors from DMZ-Black theme to DMZ-White theme. Once I successfully switch from one off-the-shelf theme to another, then I'll worry about whether or not I've created my own theme correctly.

---

### Post by CantankRus on 2015-05-11
Are you logging out then back in after the change in lxappearance?

---

### Post by PenguinLust on 2015-05-11
And rebooting

---

### Post by CantankRus on 2015-05-11
I have used lxappearance to change to a custom theme **DMZ-Black-Medium**
From what I can see lxappearance writes to 2 files.

[INDENT]1) **~/.icons/default/index.theme**[/INDENT]
```
# This file is written by LXAppearance. Do not edit.
[Icon Theme]
Name=Default
Comment=Default Cursor Theme
Inherits=DMZ-Black-Medium
```

[INDENT]2) **~/.config/lxsession/Lubuntu/desktop.conf**[/INDENT]
```
[GTK]
sNet/ThemeName=Lubuntu-default
sNet/IconThemeName=lubuntu
sGtk/FontName=Ubuntu 11
iGtk/ToolbarStyle=3
iGtk/ButtonImages=1
iGtk/MenuImages=1
iGtk/CursorThemeSize=18
iXft/Antialias=1
iXft/Hinting=1
sXft/HintStyle=hintslight
sXft/RGBA=rgb
sGtk/CursorThemeName=[COLOR="#FF0000"]DMZ-Black-Medium[/COLOR]
sGtk/ColorScheme=
iGtk/ToolbarIconSize=3
iNet/EnableEventSounds=1
iNet/EnableInputFeedbackSounds=1
iGtk/ColorScheme=
```

Can you attach your cursor theme or is it too big?

---

### Post by PenguinLust on 2015-05-11
Ah, now we're getting somewhere. I already has ~/.icons/default as a file (hold over from my KDE days). Deleting allowed me to switch themes for all apps and the desktops.
Thanks.

---

### Post by PenguinLust on 2015-05-14
But it is *so* not working w/my desktop. Now when I go into lxappearances and select another cursor theme, I click apply and nothing happens. When I restart and return to lxappearances (or don't restart and go to lxappearances) it still has the old DMZ-(White) selected. So now Firefox shows the black theme and everything else shows the white theme, and that doesn't change no matter what theme I try.
My desktop is a 64-bit Ubuntu 14.04.2.

---

### Post by CantankRus on 2015-05-14
In Lubuntu I didn't change alternatives, and is still set to **DMZ-White**. Revert to default.
```
sudo update-alternatives --config x-cursor-theme
```
[ATTACH=CONFIG]261966[/ATTACH]
Only change I made was in lxappearance.

Create a new user and test changing cursors in this account just using lxappearance and log out and back in.
If it works in the newly created account, then a user config in your regular account is causing the problem.

---

### Post by PenguinLust on 2015-05-14
Remember, I'm using my desktop now. I got it working in Lubuntu, but they don't seem to work the same.
Actually, I tried the new user. It mostly worked for him, but the only weird thing is that when I start lxappearances, the selection appears to be DMZ-White again.
So it's probably something about the new user's hidden directories. I don't suppose you could guess which one. Here's the recursive listing:
> ../delete_me/:
total 128
drwxr-xr-x 19 delete_me delete_me 4096 May 14 17:39 .
drwxr-xr-x  9 root      root      4096 May 14 00:24 ..
-rw-------  1 delete_me delete_me  131 May 14 00:32 .bash_history
-rw-r--r--  1 delete_me delete_me  220 May 14 00:24 .bash_logout
-rw-r--r--  1 delete_me delete_me 3637 May 14 00:24 .bashrc
drwx------ 10 delete_me delete_me 4096 May 14 00:27 .cache
drwx------  3 delete_me delete_me 4096 May 14 00:29 .compiz
drwx------ 14 delete_me delete_me 4096 May 14 00:28 .config
drwx------  3 delete_me delete_me 4096 May 14 17:37 .dbus
drwxr-xr-x  2 delete_me delete_me 4096 May 14 00:26 Desktop
-rw-r--r--  1 delete_me delete_me   25 May 14 00:26 .dmrc
drwxr-xr-x  2 delete_me delete_me 4096 May 14 00:26 Documents
drwxr-xr-x  2 delete_me delete_me 4096 May 14 00:26 Downloads
-rw-r--r--  1 delete_me delete_me 8980 May 14 00:24 examples.desktop
drwx------  3 delete_me delete_me 4096 May 14 17:39 .gconf
-rw-rw-r--  1 delete_me delete_me  597 May 14 17:38 .gtkrc-2.0
-rw-------  1 delete_me delete_me 1288 May 14 17:39 .ICEauthority
drwx------  3 delete_me delete_me 4096 May 14 17:38 .icons
drwx------  3 delete_me delete_me 4096 May 14 00:26 .local
drwxr-xr-x  2 delete_me delete_me 4096 May 14 00:26 Music
drwx------  3 delete_me delete_me 4096 May 14 00:26 .nv
drwxr-xr-x  2 delete_me delete_me 4096 May 14 00:26 Pictures
-rw-r--r--  1 delete_me delete_me  675 May 14 00:24 .profile
drwxr-xr-x  2 delete_me delete_me 4096 May 14 00:26 Public
drwx------  2 delete_me delete_me 4096 May 14 00:31 .ssh
drwxr-xr-x  2 delete_me delete_me 4096 May 14 00:26 Templates
drwxr-xr-x  2 delete_me delete_me 4096 May 14 00:26 Videos
-rw-------  1 delete_me delete_me   52 May 14 17:39 .Xauthority
-rw-------  1 delete_me delete_me 1277 May 14 17:40 .xsession-errors
-rw-------  1 delete_me delete_me 1552 May 14 17:38 .xsession-errors.old

../delete_me/.cache:
total 40
drwx------ 10 delete_me delete_me 4096 May 14 00:27 .
drwxr-xr-x 19 delete_me delete_me 4096 May 14 17:39 ..
drwx------  2 delete_me delete_me 4096 May 14 17:39 compizconfig-1
drwx------  8 delete_me delete_me 4096 May 14 00:27 evolution
drwxrwxr-x  2 delete_me delete_me 4096 May 14 00:27 gstreamer-1.0
drwxrwxr-x  3 delete_me delete_me 4096 May 14 00:26 ibus
drwxrwxr-x  2 delete_me delete_me 4096 May 14 00:31 logrotate
drwx------  4 delete_me delete_me 4096 May 14 00:27 thumbnails
drwx------  2 delete_me delete_me 4096 May 14 00:32 upstart
drwx------  2 delete_me delete_me 4096 May 14 00:27 wallpaper

../delete_me/.cache/compizconfig-1:
total 120
drwx------  2 delete_me delete_me 4096 May 14 17:39 .
drwx------ 10 delete_me delete_me 4096 May 14 00:27 ..
-rw-rw-r--  1 delete_me delete_me 4830 May 14 00:27 animation.pb
-rw-rw-r--  1 delete_me delete_me 3635 May 14 00:27 commands.pb
-rw-rw-r--  1 delete_me delete_me   92 May 14 00:27 compiztoolbox.pb
-rw-rw-r--  1 delete_me delete_me  507 May 14 00:27 composite.pb
-rw-rw-r--  1 delete_me delete_me   63 May 14 00:27 copytex.pb
-rw-rw-r--  1 delete_me delete_me 2411 May 14 00:27 core.pb
-rw-rw-r--  1 delete_me delete_me  108 May 14 17:39 decor.pb
-rw-rw-r--  1 delete_me delete_me 1527 May 14 00:27 expo.pb
-rw-rw-r--  1 delete_me delete_me 2087 May 14 00:27 ezoom.pb
-rw-rw-r--  1 delete_me delete_me  551 May 14 00:27 fade.pb
-rw-rw-r--  1 delete_me delete_me  646 May 14 00:27 gnomecompat.pb
-rw-rw-r--  1 delete_me delete_me 2010 May 14 00:27 grid.pb
-rw-rw-r--  1 delete_me delete_me  113 May 14 00:27 imgpng.pb
-rw-rw-r--  1 delete_me delete_me  146 May 14 00:27 mousepoll.pb
-rw-rw-r--  1 delete_me delete_me  552 May 14 00:27 move.pb
-rw-rw-r--  1 delete_me delete_me  525 May 14 00:27 opengl.pb
-rw-rw-r--  1 delete_me delete_me  662 May 14 00:27 place.pb
-rw-rw-r--  1 delete_me delete_me   75 May 14 00:27 regex.pb
-rw-rw-r--  1 delete_me delete_me  854 May 14 00:27 resize.pb
-rw-rw-r--  1 delete_me delete_me 1462 May 14 00:27 scale.pb
-rw-rw-r--  1 delete_me delete_me  160 May 14 00:27 session.pb
-rw-rw-r--  1 delete_me delete_me  335 May 14 00:27 snap.pb
-rw-rw-r--  1 delete_me delete_me  348 May 14 00:27 unitymtgrabhandles.pb
-rw-rw-r--  1 delete_me delete_me 3571 May 14 00:27 unityshell.pb
-rw-rw-r--  1 delete_me delete_me  956 May 14 00:27 vpswitch.pb
-rw-rw-r--  1 delete_me delete_me 2646 May 14 00:27 wall.pb
-rw-rw-r--  1 delete_me delete_me  916 May 14 00:27 workarounds.pb

../delete_me/.cache/evolution:
total 32
drwx------  8 delete_me delete_me 4096 May 14 00:27 .
drwx------ 10 delete_me delete_me 4096 May 14 00:27 ..
drwxrwxr-x  3 delete_me delete_me 4096 May 14 00:27 addressbook
drwxrwxr-x  3 delete_me delete_me 4096 May 14 00:27 calendar
drwxrwxr-x  3 delete_me delete_me 4096 May 14 00:27 mail
drwxrwxr-x  3 delete_me delete_me 4096 May 14 00:27 memos
drwxrwxr-x  3 delete_me delete_me 4096 May 14 00:27 sources
drwxrwxr-x  3 delete_me delete_me 4096 May 14 00:27 tasks

../delete_me/.cache/evolution/addressbook:
total 12
drwxrwxr-x 3 delete_me delete_me 4096 May 14 00:27 .
drwx------ 8 delete_me delete_me 4096 May 14 00:27 ..
drwxrwxr-x 2 delete_me delete_me 4096 May 14 00:27 trash

../delete_me/.cache/evolution/addressbook/trash:
total 8
drwxrwxr-x 2 delete_me delete_me 4096 May 14 00:27 .
drwxrwxr-x 3 delete_me delete_me 4096 May 14 00:27 ..

../delete_me/.cache/evolution/calendar:
total 12
drwxrwxr-x 3 delete_me delete_me 4096 May 14 00:27 .
drwx------ 8 delete_me delete_me 4096 May 14 00:27 ..
drwxrwxr-x 2 delete_me delete_me 4096 May 14 00:27 trash

../delete_me/.cache/evolution/calendar/trash:
total 8
drwxrwxr-x 2 delete_me delete_me 4096 May 14 00:27 .
drwxrwxr-x 3 delete_me delete_me 4096 May 14 00:27 ..

../delete_me/.cache/evolution/mail:
total 12
drwxrwxr-x 3 delete_me delete_me 4096 May 14 00:27 .
drwx------ 8 delete_me delete_me 4096 May 14 00:27 ..
drwxrwxr-x 2 delete_me delete_me 4096 May 14 00:27 trash

../delete_me/.cache/evolution/mail/trash:
total 8
drwxrwxr-x 2 delete_me delete_me 4096 May 14 00:27 .
drwxrwxr-x 3 delete_me delete_me 4096 May 14 00:27 ..

../delete_me/.cache/evolution/memos:
total 12
drwxrwxr-x 3 delete_me delete_me 4096 May 14 00:27 .
drwx------ 8 delete_me delete_me 4096 May 14 00:27 ..
drwxrwxr-x 2 delete_me delete_me 4096 May 14 00:27 trash

../delete_me/.cache/evolution/memos/trash:
total 8
drwxrwxr-x 2 delete_me delete_me 4096 May 14 00:27 .
drwxrwxr-x 3 delete_me delete_me 4096 May 14 00:27 ..

../delete_me/.cache/evolution/sources:
total 12
drwxrwxr-x 3 delete_me delete_me 4096 May 14 00:27 .
drwx------ 8 delete_me delete_me 4096 May 14 00:27 ..
drwxrwxr-x 2 delete_me delete_me 4096 May 14 00:27 trash

../delete_me/.cache/evolution/sources/trash:
total 8
drwxrwxr-x 2 delete_me delete_me 4096 May 14 00:27 .
drwxrwxr-x 3 delete_me delete_me 4096 May 14 00:27 ..

../delete_me/.cache/evolution/tasks:
total 12
drwxrwxr-x 3 delete_me delete_me 4096 May 14 00:27 .
drwx------ 8 delete_me delete_me 4096 May 14 00:27 ..
drwxrwxr-x 2 delete_me delete_me 4096 May 14 00:27 trash

../delete_me/.cache/evolution/tasks/trash:
total 8
drwxrwxr-x 2 delete_me delete_me 4096 May 14 00:27 .
drwxrwxr-x 3 delete_me delete_me 4096 May 14 00:27 ..

../delete_me/.cache/gstreamer-1.0:
total 856
drwxrwxr-x  2 delete_me delete_me   4096 May 14 00:27 .
drwx------ 10 delete_me delete_me   4096 May 14 00:27 ..
-rw-------  1 delete_me delete_me 865229 May 14 00:27 registry.x86_64.bin

../delete_me/.cache/ibus:
total 12
drwxrwxr-x  3 delete_me delete_me 4096 May 14 00:26 .
drwx------ 10 delete_me delete_me 4096 May 14 00:27 ..
drwxrwxr-x  2 delete_me delete_me 4096 May 14 00:26 bus

../delete_me/.cache/ibus/bus:
total 24
drwxrwxr-x 2 delete_me delete_me  4096 May 14 00:26 .
drwxrwxr-x 3 delete_me delete_me  4096 May 14 00:26 ..
-rw-r--r-- 1 delete_me delete_me 13059 May 14 00:26 registry

../delete_me/.cache/logrotate:
total 12
drwxrwxr-x  2 delete_me delete_me 4096 May 14 00:31 .
drwx------ 10 delete_me delete_me 4096 May 14 00:27 ..
-rw-rw-r--  1 delete_me delete_me 1308 May 14 00:31 status

../delete_me/.cache/thumbnails:
total 16
drwx------  4 delete_me delete_me 4096 May 14 00:27 .
drwx------ 10 delete_me delete_me 4096 May 14 00:27 ..
drwx------  3 delete_me delete_me 4096 May 14 00:27 fail
drwx------  2 delete_me delete_me 4096 May 14 00:27 normal

../delete_me/.cache/thumbnails/fail:
total 12
drwx------ 3 delete_me delete_me 4096 May 14 00:27 .
drwx------ 4 delete_me delete_me 4096 May 14 00:27 ..
drwx------ 2 delete_me delete_me 4096 May 14 00:27 gnome-thumbnail-factory

../delete_me/.cache/thumbnails/fail/gnome-thumbnail-factory:
total 12
drwx------ 2 delete_me delete_me 4096 May 14 00:27 .
drwx------ 3 delete_me delete_me 4096 May 14 00:27 ..
-rw------- 1 delete_me delete_me  236 May 14 00:27 8fe67980dd2e2442eab538f70e4ca58a.png

../delete_me/.cache/thumbnails/normal:
total 652
drwx------ 2 delete_me delete_me  4096 May 14 00:27 .
drwx------ 4 delete_me delete_me  4096 May 14 00:27 ..
-rw------- 1 delete_me delete_me 60753 May 14 00:27 051ba6888f20adf6bfd0f0709ca51882.png
-rw------- 1 delete_me delete_me 54939 May 14 00:27 0ae37d7036817693adec104f064af783.png
-rw------- 1 delete_me delete_me 24107 May 14 00:27 23d554b84cbc451cbdd1660a6c33c3bb.png
-rw------- 1 delete_me delete_me 48473 May 14 00:27 799360dcd2b2bf6f9d0ee1003d0878c5.png
-rw------- 1 delete_me delete_me 23593 May 14 00:27 80669861f9aa5aea3fe60cb442f453cc.png
-rw------- 1 delete_me delete_me 67824 May 14 00:27 81bdc9fa57cd692cd040eda14c67ce19.png
-rw------- 1 delete_me delete_me 25789 May 14 00:27 9da0fe358482e154667f4fd3f3b898ee.png
-rw------- 1 delete_me delete_me 32434 May 14 00:27 b2bdf6f2a85194544d0558983df41eb0.png
-rw------- 1 delete_me delete_me 48084 May 14 00:27 d16b0938cbe0709422a08ab6592e38a8.png
-rw------- 1 delete_me delete_me 64033 May 14 00:27 ed1486feff8053b64e9d027e91f77b2d.png
-rw------- 1 delete_me delete_me 82785 May 14 00:27 ee15d0573bf335eb8c301035b605d351.png
-rw------- 1 delete_me delete_me 45268 May 14 00:27 ee9cf2ab26402213d518127e9b5b1149.png
-rw------- 1 delete_me delete_me 57461 May 14 00:27 f458b2702111282ba10cca5ddd511daf.png

../delete_me/.cache/upstart:
total 148
drwx------  2 delete_me delete_me  4096 May 14 00:32 .
drwx------ 10 delete_me delete_me  4096 May 14 00:27 ..
-rw-r-----  1 delete_me delete_me   779 May 14 00:32 at-spi2-registryd.log
-rw-r-----  1 delete_me delete_me 31452 May 14 17:39 dbus.log
-rw-rw-r--  1 delete_me delete_me    60 May 14 17:39 dbus-session
-rw-r-----  1 delete_me delete_me   376 May 14 17:39 gnome-keyring-gpg.log
-rw-r-----  1 delete_me delete_me   376 May 14 17:39 gnome-keyring-ssh.log
-rw-r-----  1 delete_me delete_me 27772 May 14 17:40 gnome-session-Unity.log
-rw-r-----  1 delete_me delete_me   160 May 14 17:39 gpg-agent.log
-rw-r-----  1 delete_me delete_me   166 May 14 17:38 hud.log
-rw-r-----  1 delete_me delete_me   444 May 14 17:39 im-config.log
-rw-r-----  1 delete_me delete_me   446 May 14 17:38 indicator-application.log
-rw-r-----  1 delete_me delete_me   440 May 14 17:39 indicator-bluetooth.log
-rw-r-----  1 delete_me delete_me   320 May 14 17:39 indicator-power.log
-rw-r-----  1 delete_me delete_me   422 May 14 17:38 indicator-printers.log
-rw-r-----  1 delete_me delete_me  1904 May 14 17:40 indicator-sound.log
-rw-r-----  1 delete_me delete_me   160 May 14 17:39 ssh-agent.log
-rw-r-----  1 delete_me delete_me   284 May 14 17:39 unity7.log
-rw-r-----  1 delete_me delete_me  1124 May 14 17:40 unity-panel-service.log
-rw-r-----  1 delete_me delete_me  2337 May 14 17:40 unity-settings-daemon.log
-rw-r-----  1 delete_me delete_me   328 May 14 17:39 update-notifier-crash-_var_crash_nvidia-331.0.crash.log
-rw-r-----  1 delete_me delete_me   208 May 14 17:39 update-notifier-release.log
-rw-r-----  1 delete_me delete_me   336 May 14 17:39 window-stack-bridge.log

../delete_me/.cache/wallpaper:
total 1304
drwx------  2 delete_me delete_me    4096 May 14 00:27 .
drwx------ 10 delete_me delete_me    4096 May 14 00:27 ..
-rw-rw-r--  1 delete_me delete_me 1326614 May 14 00:27 0_5_1680_1050_792beab7550410d531e55f95b449f135

../delete_me/.compiz:
total 12
drwx------  3 delete_me delete_me 4096 May 14 00:29 .
drwxr-xr-x 19 delete_me delete_me 4096 May 14 17:39 ..
drwx------  2 delete_me delete_me 4096 May 14 17:40 session

../delete_me/.compiz/session:
total 24
drwx------ 2 delete_me delete_me 4096 May 14 17:40 .
drwx------ 3 delete_me delete_me 4096 May 14 00:29 ..
-rw-rw-r-- 1 delete_me delete_me  351 May 14 00:29 105fd52078c0adca5b143157762111555800000073150001
-rw-rw-r-- 1 delete_me delete_me  342 May 14 00:32 1064b4e62b497ab87e143157784433066900000023070001
-rw-rw-r-- 1 delete_me delete_me   94 May 14 17:38 10a666a5a8495a89f3143163947816126800000039470001
-rw-rw-r-- 1 delete_me delete_me   94 May 14 17:40 10c99ba3fa15ef9130143163957136170700000022880001

../delete_me/.config:
total 64
drwx------ 14 delete_me delete_me 4096 May 14 00:28 .
drwxr-xr-x 19 delete_me delete_me 4096 May 14 17:39 ..
drwx------  3 delete_me delete_me 4096 May 14 00:27 compiz-1
drwxrwxr-x  2 delete_me delete_me 4096 May 14 17:40 dconf
drwx------  3 delete_me delete_me 4096 May 14 00:27 evolution
drwxr-xr-x  3 delete_me delete_me 4096 May 14 00:27 gnome-session
drwx------  2 delete_me delete_me 4096 May 14 17:39 gtk-3.0
drwx------  3 delete_me delete_me 4096 May 14 00:26 ibus
drwxr-xr-x  2 delete_me delete_me 4096 May 14 00:27 libaccounts-glib
drwxr-xr-x  2 delete_me delete_me 4096 May 14 17:39 nautilus
drwx------  2 delete_me delete_me 4096 May 14 00:27 pulse
drwx------  2 delete_me delete_me 4096 May 14 00:27 unity
drwx------  2 delete_me delete_me 4096 May 14 00:32 update-notifier
drwx------  2 delete_me delete_me 4096 May 14 00:26 upstart
-rw-------  1 delete_me delete_me  632 May 14 00:26 user-dirs.dirs
-rw-rw-r--  1 delete_me delete_me    5 May 14 00:26 user-dirs.locale

../delete_me/.config/compiz-1:
total 12
drwx------  3 delete_me delete_me 4096 May 14 00:27 .
drwx------ 14 delete_me delete_me 4096 May 14 00:28 ..
drwx------  2 delete_me delete_me 4096 May 14 00:27 compizconfig

../delete_me/.config/compiz-1/compizconfig:
total 12
drwx------ 2 delete_me delete_me 4096 May 14 00:27 .
drwx------ 3 delete_me delete_me 4096 May 14 00:27 ..
-rw-rw-r-- 1 delete_me delete_me    0 May 14 00:27 config
-rw-rw-r-- 1 delete_me delete_me  259 May 14 00:27 done_upgrades

../delete_me/.config/dconf:
total 16
drwxrwxr-x  2 delete_me delete_me 4096 May 14 17:40 .
drwx------ 14 delete_me delete_me 4096 May 14 00:28 ..
-rw-rw-r--  1 delete_me delete_me 5164 May 14 17:40 user

../delete_me/.config/evolution:
total 12
drwx------  3 delete_me delete_me 4096 May 14 00:27 .
drwx------ 14 delete_me delete_me 4096 May 14 00:28 ..
drwx------  2 delete_me delete_me 4096 May 14 00:27 sources

../delete_me/.config/evolution/sources:
total 8
drwx------ 2 delete_me delete_me 4096 May 14 00:27 .
drwx------ 3 delete_me delete_me 4096 May 14 00:27 ..

../delete_me/.config/gnome-session:
total 12
drwxr-xr-x  3 delete_me delete_me 4096 May 14 00:27 .
drwx------ 14 delete_me delete_me 4096 May 14 00:28 ..
drwxr-xr-x  2 delete_me delete_me 4096 May 14 00:27 saved-session

../delete_me/.config/gnome-session/saved-session:
total 8
drwxr-xr-x 2 delete_me delete_me 4096 May 14 00:27 .
drwxr-xr-x 3 delete_me delete_me 4096 May 14 00:27 ..

../delete_me/.config/gtk-3.0:
total 16
drwx------  2 delete_me delete_me 4096 May 14 17:39 .
drwx------ 14 delete_me delete_me 4096 May 14 00:28 ..
-rw-rw-r--  1 delete_me delete_me  157 May 14 17:39 bookmarks
-rw-rw-r--  1 delete_me delete_me  427 May 14 17:38 settings.ini

../delete_me/.config/ibus:
total 12
drwx------  3 delete_me delete_me 4096 May 14 00:26 .
drwx------ 14 delete_me delete_me 4096 May 14 00:28 ..
drwx------  2 delete_me delete_me 4096 May 14 17:39 bus

../delete_me/.config/ibus/bus:
total 12
drwx------ 2 delete_me delete_me 4096 May 14 17:39 .
drwx------ 3 delete_me delete_me 4096 May 14 00:26 ..
-rw-rw-r-- 1 delete_me delete_me  168 May 14 17:39 18e944f74c14721c34aa6eec53c46e17-unix-0

../delete_me/.config/libaccounts-glib:
total 20
drwxr-xr-x  2 delete_me delete_me  4096 May 14 00:27 .
drwx------ 14 delete_me delete_me  4096 May 14 00:28 ..
-rw-r--r--  1 delete_me delete_me 12288 May 14 00:27 accounts.db

../delete_me/.config/nautilus:
total 24
drwxr-xr-x  2 delete_me delete_me 4096 May 14 17:39 .
drwx------ 14 delete_me delete_me 4096 May 14 00:28 ..
-rw-r--r--  1 delete_me delete_me 9460 May 14 17:40 accels
-rw-rw-r--  1 delete_me delete_me   96 May 14 17:39 desktop-metadata

../delete_me/.config/pulse:
total 68
drwx------  2 delete_me delete_me  4096 May 14 00:27 .
drwx------ 14 delete_me delete_me  4096 May 14 00:28 ..
-rw-r--r--  1 delete_me delete_me 32768 May 14 00:27 18e944f74c14721c34aa6eec53c46e17-card-database.tdb
-rw-r--r--  1 delete_me delete_me    43 May 14 17:39 18e944f74c14721c34aa6eec53c46e17-default-sink
-rw-r--r--  1 delete_me delete_me    42 May 14 17:39 18e944f74c14721c34aa6eec53c46e17-default-source
-rw-r--r--  1 delete_me delete_me 12288 May 14 00:27 18e944f74c14721c34aa6eec53c46e17-device-volumes.tdb
-rw-r--r--  1 delete_me delete_me   696 May 14 00:27 18e944f74c14721c34aa6eec53c46e17-stream-volumes.tdb
-rw-------  1 delete_me delete_me   256 May 14 00:27 cookie

../delete_me/.config/unity:
total 8
drwx------  2 delete_me delete_me 4096 May 14 00:27 .
drwx------ 14 delete_me delete_me 4096 May 14 00:28 ..
-rw-rw-r--  1 delete_me delete_me    0 May 14 00:27 first_run.stamp

../delete_me/.config/update-notifier:
total 12
drwx------  2 delete_me delete_me 4096 May 14 00:32 .
drwx------ 14 delete_me delete_me 4096 May 14 00:28 ..
-rw-rw-r--  1 delete_me delete_me   34 May 14 00:32 hooks_seen

../delete_me/.config/upstart:
total 8
drwx------  2 delete_me delete_me 4096 May 14 00:26 .
drwx------ 14 delete_me delete_me 4096 May 14 00:28 ..

../delete_me/.dbus:
total 12
drwx------  3 delete_me delete_me 4096 May 14 17:37 .
drwxr-xr-x 19 delete_me delete_me 4096 May 14 17:39 ..
drwx------  2 delete_me delete_me 4096 May 14 17:37 session-bus

../delete_me/.dbus/session-bus:
total 12
drwx------ 2 delete_me delete_me 4096 May 14 17:37 .
drwx------ 3 delete_me delete_me 4096 May 14 17:37 ..
-rw-rw-r-- 1 delete_me delete_me  463 May 14 17:37 18e944f74c14721c34aa6eec53c46e17-0

../delete_me/Desktop:
total 8
drwxr-xr-x  2 delete_me delete_me 4096 May 14 00:26 .
drwxr-xr-x 19 delete_me delete_me 4096 May 14 17:39 ..

../delete_me/Documents:
total 8
drwxr-xr-x  2 delete_me delete_me 4096 May 14 00:26 .
drwxr-xr-x 19 delete_me delete_me 4096 May 14 17:39 ..

../delete_me/Downloads:
total 8
drwxr-xr-x  2 delete_me delete_me 4096 May 14 00:26 .
drwxr-xr-x 19 delete_me delete_me 4096 May 14 17:39 ..

../delete_me/.gconf:
total 12
drwx------  3 delete_me delete_me 4096 May 14 17:39 .
drwxr-xr-x 19 delete_me delete_me 4096 May 14 17:39 ..
drwx------  3 delete_me delete_me 4096 May 14 00:28 apps

../delete_me/.gconf/apps:
total 12
drwx------ 3 delete_me delete_me 4096 May 14 00:28 .
drwx------ 3 delete_me delete_me 4096 May 14 17:39 ..
-rw------- 1 delete_me delete_me    0 May 14 00:28 %gconf.xml
drwx------ 2 delete_me delete_me 4096 May 14 00:28 nm-applet

../delete_me/.gconf/apps/nm-applet:
total 12
drwx------ 2 delete_me delete_me 4096 May 14 00:28 .
drwx------ 3 delete_me delete_me 4096 May 14 00:28 ..
-rw------- 1 delete_me delete_me  102 May 14 00:28 %gconf.xml

../delete_me/.icons:
total 12
drwx------  3 delete_me delete_me 4096 May 14 17:38 .
drwxr-xr-x 19 delete_me delete_me 4096 May 14 17:39 ..
drwx------  2 delete_me delete_me 4096 May 14 17:38 default

../delete_me/.icons/default:
total 12
drwx------ 2 delete_me delete_me 4096 May 14 17:38 .
drwx------ 3 delete_me delete_me 4096 May 14 17:38 ..
-rw-rw-r-- 1 delete_me delete_me  126 May 14 17:38 index.theme

../delete_me/.local:
total 12
drwx------  3 delete_me delete_me 4096 May 14 00:26 .
drwxr-xr-x 19 delete_me delete_me 4096 May 14 17:39 ..
drwx------ 12 delete_me delete_me 4096 May 14 00:27 share

../delete_me/.local/share:
total 56
drwx------ 12 delete_me delete_me 4096 May 14 00:27 .
drwx------  3 delete_me delete_me 4096 May 14 00:26 ..
drwx------  2 delete_me delete_me 4096 May 14 00:27 applications
-rw-rw-r--  1 delete_me delete_me    0 May 14 00:27 .converted-launchers
drwx------  7 delete_me delete_me 4096 May 14 00:27 evolution
-rw-rw-r--  1 delete_me delete_me  956 May 14 00:27 gsettings-data-convert
drwx------  2 delete_me delete_me 4096 May 14 00:28 gvfs-metadata
drwxrwxr-x  2 delete_me delete_me 4096 May 14 00:27 icc
drwx------  2 delete_me delete_me 4096 May 14 00:31 keyrings
drwx------  3 delete_me delete_me 4096 May 14 00:27 nautilus
-rw-rw-r--  1 delete_me delete_me  423 May 14 00:27 session_migration-ubuntu
drwx------  2 delete_me delete_me 4096 May 14 00:27 sounds
drwx------  3 delete_me delete_me 4096 May 14 00:27 telepathy
drwxr-xr-x  2 delete_me delete_me 4096 May 14 00:27 unity-settings-daemon
drwx------  3 delete_me delete_me 4096 May 14 00:27 zeitgeist

../delete_me/.local/share/applications:
total 8
drwx------  2 delete_me delete_me 4096 May 14 00:27 .
drwx------ 12 delete_me delete_me 4096 May 14 00:27 ..

../delete_me/.local/share/evolution:
total 28
drwx------  7 delete_me delete_me 4096 May 14 00:27 .
drwx------ 12 delete_me delete_me 4096 May 14 00:27 ..
drwxrwxr-x  3 delete_me delete_me 4096 May 14 00:27 addressbook
drwxrwxr-x  4 delete_me delete_me 4096 May 14 00:27 calendar
drwxrwxr-x  3 delete_me delete_me 4096 May 14 00:27 mail
drwxrwxr-x  3 delete_me delete_me 4096 May 14 00:27 memos
drwxrwxr-x  4 delete_me delete_me 4096 May 14 00:27 tasks

../delete_me/.local/share/evolution/addressbook:
total 12
drwxrwxr-x 3 delete_me delete_me 4096 May 14 00:27 .
drwx------ 7 delete_me delete_me 4096 May 14 00:27 ..
drwxrwxr-x 2 delete_me delete_me 4096 May 14 00:27 trash

../delete_me/.local/share/evolution/addressbook/trash:
total 8
drwxrwxr-x 2 delete_me delete_me 4096 May 14 00:27 .
drwxrwxr-x 3 delete_me delete_me 4096 May 14 00:27 ..

../delete_me/.local/share/evolution/calendar:
total 16
drwxrwxr-x 4 delete_me delete_me 4096 May 14 00:27 .
drwx------ 7 delete_me delete_me 4096 May 14 00:27 ..
drwx------ 2 delete_me delete_me 4096 May 14 00:27 system
drwxrwxr-x 2 delete_me delete_me 4096 May 14 00:27 trash

../delete_me/.local/share/evolution/calendar/system:
total 12
drwx------ 2 delete_me delete_me 4096 May 14 00:27 .
drwxrwxr-x 4 delete_me delete_me 4096 May 14 00:27 ..
-rw-rw-r-- 1 delete_me delete_me  173 May 14 00:27 calendar.ics

../delete_me/.local/share/evolution/calendar/trash:
total 8
drwxrwxr-x 2 delete_me delete_me 4096 May 14 00:27 .
drwxrwxr-x 4 delete_me delete_me 4096 May 14 00:27 ..

../delete_me/.local/share/evolution/mail:
total 12
drwxrwxr-x 3 delete_me delete_me 4096 May 14 00:27 .
drwx------ 7 delete_me delete_me 4096 May 14 00:27 ..
drwxrwxr-x 2 delete_me delete_me 4096 May 14 00:27 trash

../delete_me/.local/share/evolution/mail/trash:
total 8
drwxrwxr-x 2 delete_me delete_me 4096 May 14 00:27 .
drwxrwxr-x 3 delete_me delete_me 4096 May 14 00:27 ..

../delete_me/.local/share/evolution/memos:
total 12
drwxrwxr-x 3 delete_me delete_me 4096 May 14 00:27 .
drwx------ 7 delete_me delete_me 4096 May 14 00:27 ..
drwxrwxr-x 2 delete_me delete_me 4096 May 14 00:27 trash

../delete_me/.local/share/evolution/memos/trash:
total 8
drwxrwxr-x 2 delete_me delete_me 4096 May 14 00:27 .
drwxrwxr-x 3 delete_me delete_me 4096 May 14 00:27 ..

../delete_me/.local/share/evolution/tasks:
total 16
drwxrwxr-x 4 delete_me delete_me 4096 May 14 00:27 .
drwx------ 7 delete_me delete_me 4096 May 14 00:27 ..
drwx------ 2 delete_me delete_me 4096 May 14 00:27 system
drwxrwxr-x 2 delete_me delete_me 4096 May 14 00:27 trash

../delete_me/.local/share/evolution/tasks/system:
total 12
drwx------ 2 delete_me delete_me 4096 May 14 00:27 .
drwxrwxr-x 4 delete_me delete_me 4096 May 14 00:27 ..
-rw-rw-r-- 1 delete_me delete_me  173 May 14 00:27 tasks.ics

../delete_me/.local/share/evolution/tasks/trash:
total 8
drwxrwxr-x 2 delete_me delete_me 4096 May 14 00:27 .
drwxrwxr-x 4 delete_me delete_me 4096 May 14 00:27 ..

../delete_me/.local/share/gvfs-metadata:
total 44
drwx------  2 delete_me delete_me  4096 May 14 00:28 .
drwx------ 12 delete_me delete_me  4096 May 14 00:27 ..
-rw-------  1 delete_me delete_me    56 May 14 00:28 home
-rw-rw-r--  1 delete_me delete_me 32768 May 14 00:28 home-7f72acdf.log

../delete_me/.local/share/icc:
total 12
drwxrwxr-x  2 delete_me delete_me 4096 May 14 00:27 .
drwx------ 12 delete_me delete_me 4096 May 14 00:27 ..
-rw-rw-r--  1 delete_me delete_me 1928 May 14 00:27 edid-3b5bc8e495238fdefc63502f3742b1c4.icc

../delete_me/.local/share/keyrings:
total 8
drwx------  2 delete_me delete_me 4096 May 14 00:31 .
drwx------ 12 delete_me delete_me 4096 May 14 00:27 ..
-rw-------  1 delete_me delete_me    0 May 14 00:31 user.keystore

../delete_me/.local/share/nautilus:
total 12
drwx------  3 delete_me delete_me 4096 May 14 00:27 .
drwx------ 12 delete_me delete_me 4096 May 14 00:27 ..
drwx------  2 delete_me delete_me 4096 May 14 00:27 scripts

../delete_me/.local/share/nautilus/scripts:
total 8
drwx------ 2 delete_me delete_me 4096 May 14 00:27 .
drwx------ 3 delete_me delete_me 4096 May 14 00:27 ..

../delete_me/.local/share/sounds:
total 8
drwx------  2 delete_me delete_me 4096 May 14 00:27 .
drwx------ 12 delete_me delete_me 4096 May 14 00:27 ..

../delete_me/.local/share/telepathy:
total 12
drwx------  3 delete_me delete_me 4096 May 14 00:27 .
drwx------ 12 delete_me delete_me 4096 May 14 00:27 ..
drwx------  2 delete_me delete_me 4096 May 14 00:27 mission-control

../delete_me/.local/share/telepathy/mission-control:
total 12
drwx------ 2 delete_me delete_me 4096 May 14 00:27 .
drwx------ 3 delete_me delete_me 4096 May 14 00:27 ..
-rw------- 1 delete_me delete_me   21 May 14 00:27 accounts.cfg

../delete_me/.local/share/unity-settings-daemon:
total 8
drwxr-xr-x  2 delete_me delete_me 4096 May 14 00:27 .
drwx------ 12 delete_me delete_me 4096 May 14 00:27 ..
-rw-rw-r--  1 delete_me delete_me    0 May 14 00:27 input-sources-converted

../delete_me/.local/share/zeitgeist:
total 272
drwx------  3 delete_me delete_me   4096 May 14 00:27 .
drwx------ 12 delete_me delete_me   4096 May 14 00:27 ..
-rw-------  1 delete_me delete_me  50176 May 14 00:29 activity.sqlite
-rw-------  1 delete_me delete_me  32768 May 14 17:40 activity.sqlite-shm
-rw-------  1 delete_me delete_me 171904 May 14 17:40 activity.sqlite-wal
drwxr-xr-x  2 delete_me delete_me   4096 May 14 17:39 fts.index

../delete_me/.local/share/zeitgeist/fts.index:
total 156
drwxr-xr-x 2 delete_me delete_me  4096 May 14 17:39 .
drwx------ 3 delete_me delete_me  4096 May 14 00:27 ..
-rw-rw-r-- 1 delete_me delete_me     0 May 14 17:39 flintlock
-rw-rw-r-- 1 delete_me delete_me    28 May 14 00:27 iamchert
-rw-rw-r-- 1 delete_me delete_me    15 May 14 17:39 position.baseA
-rw-rw-r-- 1 delete_me delete_me    15 May 14 17:39 position.baseB
-rw-rw-r-- 1 delete_me delete_me 40960 May 14 17:39 position.DB
-rw-rw-r-- 1 delete_me delete_me    15 May 14 17:39 postlist.baseA
-rw-rw-r-- 1 delete_me delete_me    15 May 14 17:39 postlist.baseB
-rw-rw-r-- 1 delete_me delete_me 16384 May 14 17:39 postlist.DB
-rw-rw-r-- 1 delete_me delete_me    14 May 14 17:39 record.baseA
-rw-rw-r-- 1 delete_me delete_me    14 May 14 17:39 record.baseB
-rw-rw-r-- 1 delete_me delete_me 16384 May 14 17:39 record.DB
-rw-rw-r-- 1 delete_me delete_me    14 May 14 17:39 termlist.baseA
-rw-rw-r-- 1 delete_me delete_me    14 May 14 17:39 termlist.baseB
-rw-rw-r-- 1 delete_me delete_me 40960 May 14 17:39 termlist.DB

../delete_me/Music:
total 8
drwxr-xr-x  2 delete_me delete_me 4096 May 14 00:26 .
drwxr-xr-x 19 delete_me delete_me 4096 May 14 17:39 ..

../delete_me/.nv:
total 12
drwx------  3 delete_me delete_me 4096 May 14 00:26 .
drwxr-xr-x 19 delete_me delete_me 4096 May 14 17:39 ..
drwx------  3 delete_me delete_me 4096 May 14 00:26 GLCache

../delete_me/.nv/GLCache:
total 12
drwx------ 3 delete_me delete_me 4096 May 14 00:26 .
drwx------ 3 delete_me delete_me 4096 May 14 00:26 ..
drwx------ 3 delete_me delete_me 4096 May 14 00:26 d40c20046a05c497c189e8dea7e6998c

../delete_me/.nv/GLCache/d40c20046a05c497c189e8dea7e6998c:
total 12
drwx------ 3 delete_me delete_me 4096 May 14 00:26 .
drwx------ 3 delete_me delete_me 4096 May 14 00:26 ..
drwx------ 2 delete_me delete_me 4096 May 14 00:27 aca0d4a635bd310c

../delete_me/.nv/GLCache/d40c20046a05c497c189e8dea7e6998c/aca0d4a635bd310c:
total 100
drwx------ 2 delete_me delete_me  4096 May 14 00:27 .
drwx------ 3 delete_me delete_me  4096 May 14 00:26 ..
-rw-rw-r-- 1 delete_me delete_me   543 May 14 00:27 4e194113a4c36c32.bin
-rw-rw-r-- 1 delete_me delete_me    84 May 14 00:27 4e194113a4c36c32.toc
-rw-rw-r-- 1 delete_me delete_me 55288 May 14 00:29 736353d788902c9e.bin
-rw-rw-r-- 1 delete_me delete_me  2740 May 14 00:29 736353d788902c9e.toc
-rw-rw-r-- 1 delete_me delete_me   543 May 14 00:26 789e35a56559c8a9.bin
-rw-rw-r-- 1 delete_me delete_me    84 May 14 00:26 789e35a56559c8a9.toc
-rw-rw-r-- 1 delete_me delete_me   543 May 14 00:27 affc8b9de34bd059.bin
-rw-rw-r-- 1 delete_me delete_me    84 May 14 00:27 affc8b9de34bd059.toc
-rw-rw-r-- 1 delete_me delete_me   543 May 14 00:27 b2c44637e87988fb.bin
-rw-rw-r-- 1 delete_me delete_me    84 May 14 00:27 b2c44637e87988fb.toc

../delete_me/Pictures:
total 8
drwxr-xr-x  2 delete_me delete_me 4096 May 14 00:26 .
drwxr-xr-x 19 delete_me delete_me 4096 May 14 17:39 ..

../delete_me/Public:
total 8
drwxr-xr-x  2 delete_me delete_me 4096 May 14 00:26 .
drwxr-xr-x 19 delete_me delete_me 4096 May 14 17:39 ..

../delete_me/.ssh:
total 12
drwx------  2 delete_me delete_me 4096 May 14 00:31 .
drwxr-xr-x 19 delete_me delete_me 4096 May 14 17:39 ..
-rw-r--r--  1 delete_me delete_me  222 May 14 00:31 known_hosts

../delete_me/Templates:
total 8
drwxr-xr-x  2 delete_me delete_me 4096 May 14 00:26 .
drwxr-xr-x 19 delete_me delete_me 4096 May 14 17:39 ..

../delete_me/Videos:
total 8
drwxr-xr-x  2 delete_me delete_me 4096 May 14 00:26 .
drwxr-xr-x 19 delete_me delete_me 4096 May 14 17:39 ..

---

### Post by CantankRus on 2015-05-14
Try creating a **~/.Xresources** file specifying your cursor theme.
eg
```
Xcursor.theme:[COLOR="#0000CD"]**DMZ-Black**[/COLOR]
Xcursor.size:32
```
Use [COLOR="#0000CD"]**your theme name**[/COLOR].
You can also set the size if your theme supports different sizes.
Log out/in

PS When pasting in long text use the code "#" button.

---

### Post by CantankRus on 2015-05-14
> **PenguinLust said:**
> Remember, I'm using my desktop now. I got it working in Lubuntu, but they don't seem to work the same.

Not sure what this means.
Does that mean you got it working in the newly created account but not your normal account?

---

### Post by PenguinLust on 2015-05-15
> **CantankRus said:**
> Try creating a **~/.Xresources** file specifying your cursor theme.
eg
```
Xcursor.theme:[COLOR=#0000CD]**DMZ-Black**[/COLOR]
Xcursor.size:32
```
Use [COLOR=#0000CD]**your theme name**[/COLOR].
You can also set the size if your theme supports different sizes.
Log out/in


Ok, I created the file but didn't give a size, because I'm just looking for the default. It didn't change anything.

> Not sure what this means.
Does that mean you got it working in the newly created account but not your normal account?
It means I've been trying to get this to work on 2 systems: 1 w/Lubuntu and a desktop w/Ubuntu. I've had better (but [not perfect]("http://ubuntuforums.org/showthread.php?t=2278328")) success in Lubuntu. On Ubuntu, I've got it to mostly work on that fresh account, but can't figure out why.

---

### Post by CantankRus on 2015-05-15
> **PenguinLust said:**
> Ok, I created the file but didn't give a size, because I'm just looking for the default. It didn't change anything.


It means I've been trying to get this to work on 2 systems: 1 w/Lubuntu and a desktop w/Ubuntu. I've had better (but [not perfect]("http://ubuntuforums.org/showthread.php?t=2278328")) success in Lubuntu. On Ubuntu, I've got it to mostly work on that fresh account, but can't figure out why.

Use the **~/.Xresources** file or lxappearance in Lubuntu. 

In Ubuntu/Unity you need to... 
[LIST]
[*]install new theme to alternatives
[*]select in alternatives
[*]select in dconf (this is what the tweak tools do)
[/LIST]
Selecting in both **alternatives** and **dconf** gives you cursor consistency in Ubuntu/Unity.
See [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2221942&p=13028225#post13028225")

---

### Post by PenguinLust on 2015-05-15
Ok, I followed the instructions in your link and bullet points and we seem to be almost there.

[LIST]
[*]I used galternatives and the selection I want is already made, which is good, because the radio buttons are read-only--I can't change them.
[*]I ran unity-tweak-tool. Again, it was already selected
[*]Some apps seem to use the right cursors, but others, and the desktop environment, don't
[*]The Ubuntu Software Centre uses some of the right cursors (like the link pointer) but not others. I even got the see the elusive busy cursor, but it probably hasn't shown up everywhere it is supposed to
[/LIST]

---

### Post by CantankRus on 2015-05-15
galternatives has a bug in 14.04
Run this command to fix...
```
sudo ln -s /usr/bin/update-alternatives /usr/sbin/
```

In Ubuntu make sure you don't have an "**Xcursor.theme:**" setting in your ~/.Xresources file
as it will override your alternatives setting.

Try this script I use to change cursor themes in Ubuntu (unity) 14.04
It should work with any theme placed in /usr/share/icons 
The theme must have a cursor.theme file.
Save as **change-cursor-trusty.sh** to your home folder and make executable.
```
#!/bin/bash

#set -x

####################################################################
##                                                                ##
##     Script to change cursors. Only lists themes installed to   ##
##     /usr/share/icons.                                          ##
##     Theme must have a cursor.theme file                        ##
##                                                                ##
####################################################################

####################################################################
##                                                                ##
## To change the cursor theme, the script will                    ##
##  1) Change dconf setting                                       ##
##  2) Register the theme with update-alternatives                ##
##  3} Select the theme in update-alternatives                    ##
##                                                                ##
## To change the cursor size the script will                      ##
##  1) Change dconf setting                                       ##
##  2) Edit the ~/.Xresources file or create if                   ##
##         it doesn't exist                                       ##
##                                                                ##
##      ....................................                      ##
##      :   Tested in Ubuntu Trusty 14.04  :                      ##
##      :..................................:                      ##
####################################################################

## Adapted for Trusty as it uses a new setting for cursor size
## gsettings set com.canonical.Unity.Interface cursor-scale-factor

#color codes
startcolor=\\033[36m
endcolor=\\033[0m

CURRENTSIZE=$(gsettings get org.gnome.desktop.interface cursor-size)
THEME=$(gsettings get org.gnome.desktop.interface cursor-theme)
touch ~/.Xresources

echo -e "\n*** This script tested in Ubuntu Trusty 14.04 ***\n"
echo -e "\n$startcolor Your current cursor theme is $endcolor$THEME$startcolor of size $endcolor$CURRENTSIZE$startcolor pixels$endcolor\n"
#ask to restore to default
echo -e "$startcolor To choose a new theme just press the$endcolor \"Enter\"$startcolor key or\n type$endcolor \"d\"$startcolor and press$endcolor \"Enter\"$startcolor to reset theme to default$endcolor:"
read Ans
if [[ $Ans == "y" || $Ans == "Y" || $Ans == "yes" || $Ans == "Yes" || $Ans == "" ]]
	then
		echo
	else
		echo -e "\n$startcolor You have chosen to reset the cursor theme to default ...Continue?$endcolor(Y/n):"
			read Ans
				if [[ $Ans == "y" || $Ans == "Y" || $Ans == "yes" || $Ans == "Yes" || $Ans == "" ]]
					then
						echo -e "\n$startcolor Using update-alternatives requires Authentication of Admin privileges...$endcolor"
							gsettings reset org.gnome.desktop.interface cursor-theme && sudo update-alternatives --set x-cursor-theme /usr/share/icons/DMZ-White/cursor.theme
							sed -i "/Xcursor.size/c\\" ~/.Xresources
							gsettings reset com.canonical.Unity.Interface cursor-scale-factor	#new setting in Trusty overrides Saucy setting below
							gsettings reset org.gnome.desktop.interface cursor-size		#for Saucy
							#sed -i '/CursorThemeName/c\sGtk\/CursorThemeName=DMZ-White' ~/.config/lxsession/Lubuntu/desktop.conf  #Lubuntu
							sleep 1
							DSIZE=$(gsettings get org.gnome.desktop.interface cursor-size)
							THEME=$(gsettings get org.gnome.desktop.interface cursor-theme)
						echo -e "$startcolor--------------------------------------------------------$endcolor"
						echo -e "\n$startcolor Your cursor theme has been reset to $endcolor$THEME$startcolor of size $endcolor$DSIZE$startcolor pixels$endcolor";	
							read -n 1 -p "Press any key to exit this script..." 
						exit
					else
							read -n 1 -p "Press any key to exit this script..."
						exit
			 	fi
fi

## create installed cursor list text file
find /usr/share/icons -name "cursor.theme" | cut -f 5 -d '/' | sort > ~/.cursorlist.txt
#ack-grep "Inherits=" /usr/share/icons | grep "cursor.theme" | cut -f 2 -d '=' | sort > ~/.cursorlist.txt
#ls -R /usr/share/icons | grep "\/cursors:" | sed -e 's/\/cursors://g' -e 's/\/usr\/share\/icons\///g' > ~/.cursorlist.txt


 
## show a numbered list of cursors to choose from
echo -e "\n---$startcolor Cursor themes in /usr/share/icons$endcolor ---"
cat -b ~/.cursorlist.txt 
 
echo -e "$startcolor Enter your new theme selection number:$endcolor"
read CHOICE


## match the theme selection number to the cursor name
#CURSOR=$(cat ~/.cursorlist.txt | sed -n $CHOICE'p')
CURSOR=$(sed -n "$CHOICE"'p' < ~/.cursorlist.txt)
	echo -e "\n$startcolor You have selected $endcolor$CURSOR\n$startcolor Continue?$endcolor(Y/n):"
	read Ans
if [[ $Ans == "y" || $Ans == "Y" || $Ans == "yes" || $Ans == "Yes" || $Ans == "" ]]
	then
		echo -e "\n$startcolor Using update-alternatives requires Authentication of Admin privileges...$endcolor"
	else
		echo -e "\nYou chose not to continue...\n"
		echo -e "\n$startcolor Your current cursor theme is $endcolor$THEME"
		read -n 1 -p "Press any key to exit this script..."
	exit
fi


## Change to selected  cursor
gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR"
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/"$CURSOR"/cursor.theme 20
sleep 1
sudo update-alternatives --set x-cursor-theme /usr/share/icons/"$CURSOR"/cursor.theme


## Set size of cursor in unity. Trusty uses a dconf cursor-scale-factor setting which sets the cursor-size
CURRENTSIZE=$(gsettings get org.gnome.desktop.interface cursor-size)
#CURRENTSCALE=$(gsettings get com.canonical.Unity.Interface cursor-scale-factor)
echo -e "\n$startcolor Your current cursor size is $endcolor$CURRENTSIZE \n$startcolor Would you like to change the size?$endcolor(Y/n):"
	read Ans
if [[ $Ans == "y" || $Ans == "Y" || $Ans == "yes" || $Ans == "Yes" || $Ans == "" ]]
	then
		echo  
	else
		echo -e "$startcolor--------------------------------------------------------$endcolor"
		echo -e "\nYou chose not to continue..." 

		## writes to or creates a ~/.Xresources file to reflect curent cursor size. Need to do this when choosing not to change size and ~/.Xresources doesn't exist
		echo -e "\n$startcolor You have enabled the $endcolor$CURSOR$startcolor cursor theme with size unchanged of $endcolor$CURRENTSIZE$startcolor \nYou need to log out to complete the change$endcolor";
			if grep "Xcursor.size:" ~/.Xresources > /dev/null; then
				#echo "Xcursor.size line exists"
				sed -i "/Xcursor.size/c\Xcursor.size:${CURRENTSIZE}" ~/.Xresources
			else
				#echo "Xcursor.size line does not exist"
				echo "Xcursor.size:${CURRENTSIZE}" >> ~/.Xresources
			fi
		read -n 1 -p "Press any key to exit this script..."
 	exit
fi

## Choose size
echo -e "$startcolor Choose your new cursor-size from 24, 32, 48, or 64  Default=24$endcolor"
	read SIZE

## Confirm choice
echo -e "\n$startcolor You have selected a cursor size of$endcolor $SIZE\n$startcolor Continue?$endcolor(Y/n):"
	read Ans
if [[ $Ans == "y" || $Ans == "Y" || $Ans == "yes" || $Ans == "Yes" || $Ans == "" ]]
	then
    	echo 
	else
		echo -e "\nYou chose not to continue..."
	  	echo -e "\n$startcolor You have enabled the $endcolor$CURSOR$startcolor cursor theme with size unchanged of $endcolor$CURRENTSIZE$startcolor \nYou need to log out to complete the change$endcolor";
		echo
	 read -n 1 -p "Press any key to exit this script..."
exit
fi

## Edits dconf to reflect chosen size for Saucy 
gsettings set org.gnome.desktop.interface cursor-size $SIZE

## match size to cursor-scale-factor for Trusty
case "$SIZE" in

# 24=cursor-scale-factor 1
24)
gsettings set com.canonical.Unity.Interface cursor-scale-factor 1
;;

# 32=cursor-scale-factor 1.35
32)
gsettings set com.canonical.Unity.Interface cursor-scale-factor 1.35
;;

# 48=cursor-scale-factor 2
48)
gsettings set com.canonical.Unity.Interface cursor-scale-factor 2
;;

# 64=cursor-scale-factor 2.65
64)
gsettings set com.canonical.Unity.Interface cursor-scale-factor 2.65
;;

# input error
*)
echo -e  "\n$startcolor*** OOps wrong size ....Try again ***$endcolor"
;;
esac


## Creates a ~/.Xresources file or edits existing to reflect chosen size
if grep "Xcursor.size:" ~/.Xresources > /dev/null 
	then
		#echo "Xcursor.size line exists"
		sed -i "/Xcursor.size/c\Xcursor.size:${SIZE}" ~/.Xresources
	else
		#echo "Xcursor.size line does not exist"
		echo "Xcursor.size:${SIZE}" >> ~/.Xresources
fi
echo -e "$startcolor--------------------------------------------------------$endcolor"
echo -e "\n$startcolor You have enabled the $endcolor$CURSOR$startcolor cursor theme of size $endcolor$SIZE$startcolor pixels $endcolor";

echo -e "$startcolor You need to log out to complete cursor change\n$endcolor";
read -n 1 -p "Press any key to exit this script..." 
```
Run in terminal with...
```
./change-cursor-trusty.sh
```
Log out after running.

---

### Post by PenguinLust on 2015-05-18
> **CantankRus said:**
> 
Run in terminal with...
```
./change-cursor-trusty.sh
```
Log out after running.

What exactly was I supposed to do w/this script? It told me that the current theme is the one I wanted, so I asked to change to it to the current theme. It asked for my password, then after saying I didn't want to change the size, it exited, then I logged out. The theme is still the right one for almost all the apps, but not for the desktop.

---

### Post by CantankRus on 2015-05-18
The script does what it says at the top of the script.
If you opt not to change size, it's finished and exits.
Seems to me your theme is selected in dconf but not alternatives.
Attach your cursor theme or upload somewhere for me to download and let me see if it works here.

---

### Post by PenguinLust on 2015-05-18
Here ya go

---

### Post by CantankRus on 2015-05-18
Ok the cursor.theme file is pointing to DMZ-White so it won't install correctly to alternatives.
[ATTACH=CONFIG]262052[/ATTACH]


The following commands will...
[LIST]
[*]edit your **/usr/share/icons/Ultima/cursor.theme** file
[*]add to alternatives
[*]select in alternatives
[*]select in dconf 
[/LIST]

Run one at a time in same terminal
```
CURSOR=Ultima

echo -e "[Icon Theme]\nInherits=$CURSOR" | sudo tee /usr/share/icons/$CURSOR/cursor.theme

sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme 20

sudo update-alternatives --set x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme

gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR"
```
Log out.

Vid of cursor in action attached.

---

### Post by PenguinLust on 2015-05-18
Oh..! My OOP experience told me that "Inherits" would be like a backup theme, in case some cursors were missing.
It all works now, even on the desktop and the Ubuntu S/w Center. Thanks.
Last question: does it matter that I don't ever remember seeing the left_ptr_watch animation, which, I believe, is the sort of thing you'd see when a program is starting?

---

### Post by Dennis N on 2015-05-18
> Oh..! My OOP experience told me that "Inherits" would be like a backup theme, in case some cursors were missing.
This is what the **index.theme** file does. In that file, Inherits= names a lower priority alternate theme or themes.

---

### Post by CantankRus on 2015-05-18
No, cursors are all over the place and have been for while now.
In some cursors "watch" is just a link to "left_ptr_watch" anyway.
I vaguely remember something years ago about getting rid of watch because it was annoying.

---

### Post by PenguinLust on 2015-05-19
> **Dennis N said:**
> This is what the **index.theme** file does. In that file, Inherits= names a lower priority alternate theme or themes.
Looks like that's right.
> **CantankRus said:**
> No, cursors are all over the place and have been for while now.
In some cursors "watch" is just a link to "left_ptr_watch" anyway.
I vaguely remember something years ago about getting rid of watch because it was annoying.
I guess it is a pretty pointless cursor.

---

