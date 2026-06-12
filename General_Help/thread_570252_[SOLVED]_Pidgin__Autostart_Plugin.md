---
title: "[SOLVED] Pidgin:  Autostart Plugin?"
date: 2007-10-08
forum: General Help
---

### Post by Ek0nomik on 2007-10-08
Is there a way to have a plugin with Pidgin start automatically?  I want the Message Notification plugin to start everytime Pidgin is loaded rather than having to check it every time.

Thanks!

---

### Post by kbracer on 2007-10-08
You can start almost anything upon login by adding it to sessions. Go to System>Preferences>Sessions and add an entry to Startup Programs. Be sure to click it "enabled".

---

### Post by strabes on 2007-10-08
> **kbracer said:**
> You can start almost anything upon login by adding it to sessions. Go to System>Preferences>Sessions and add an entry to Startup Programs. Be sure to click it "enabled".

I think he wants the plugin to start up with pidgin, not to have pidgin start up with gnome.

The default behavior of pidgin should remember the plugins that you have selected. There might be a problem with the permissions of some files in the ~/.purple directory. Make sure they're owned by your user name/group name and you have read/write access to them.

---

### Post by Ek0nomik on 2007-10-08
> **strabes said:**
> I think he wants the plugin to start up with pidgin, not to have pidgin start up with gnome.

Yep, you're exactly correct.

[QUOTE=strabes]The default behavior of pidgin should remember the plugins that you have selected. There might be a problem with the permissions of some files in the ~/.pidgin directory. Make sure they're owned by your user name/group name and you have read/write access to them.[/QUOTE]

I actually don't have a ~/.pidgin directory.  Root also doesn't have a .pidgin directory in the home folder.

Any other ideas where it should be?

---

### Post by Ek0nomik on 2007-10-08
Here is the result of running locate:

```
x-leaf@edelweiss:~$ locate pidgin
/var/lib/dpkg/info/pidgin-data.conffiles
/var/lib/dpkg/info/pidgin.postinst
/var/lib/dpkg/info/pidgin.list
/var/lib/dpkg/info/pidgin-data.md5sums
/var/lib/dpkg/info/pidgin.prerm
/var/lib/dpkg/info/pidgin-data.postrm
/var/lib/dpkg/info/pidgin-data.list
/var/lib/dpkg/info/pidgin.postrm
/var/lib/dpkg/info/pidgin.md5sums
/var/lib/dpkg/info/pidgin-data.postinst
/var/lib/dpkg/info/pidgin.preinst
/var/cache/apt/archives/pidgin_1%3a2.2.1-1ubuntu3_i386.deb
/var/cache/apt/archives/pidgin-data_1%3a2.2.1-1ubuntu3_all.deb
/usr/lib/nautilus-sendto/plugins/libnstpidgin.so
/usr/lib/pidgin
/usr/lib/pidgin/extplacement.so
/usr/lib/pidgin/convcolors.so
/usr/lib/pidgin/gestures.so
/usr/lib/pidgin/ticker.so
/usr/lib/pidgin/cap.so
/usr/lib/pidgin/xmppconsole.so
/usr/lib/pidgin/timestamp.so
/usr/lib/pidgin/gtkbuddynote.so
/usr/lib/pidgin/notify.so
/usr/lib/pidgin/timestamp_format.so
/usr/lib/pidgin/iconaway.so
/usr/lib/pidgin/nautilus.so
/usr/lib/pidgin/history.so
/usr/lib/pidgin/gevolution.so
/usr/lib/pidgin/spellchk.so
/usr/lib/pidgin/markerline.so
/usr/lib/pidgin/pidginrc.so
/usr/lib/pidgin/musicmessaging.so
/usr/share/lintian/overrides/pidgin
/usr/share/man/man1/pidgin.1.gz
/usr/share/app-install/desktop/pidgin.desktop
/usr/share/applications/pidgin.desktop
/usr/share/doc/pidgin
/usr/share/doc/pidgin/NEWS.gz
/usr/share/doc/pidgin/copyright
/usr/share/doc/pidgin/changelog.Debian.gz
/usr/share/doc/pidgin/TODO.Debian
/usr/share/doc/pidgin/README
/usr/share/doc/pidgin/changelog.gz
/usr/share/doc/pidgin/AUTHORS
/usr/share/doc/pidgin-data
/usr/share/doc/pidgin-data/NEWS.gz
/usr/share/doc/pidgin-data/copyright
/usr/share/doc/pidgin-data/changelog.Debian.gz
/usr/share/doc/pidgin-data/ChangeLog.API.gz
/usr/share/doc/pidgin-data/README
/usr/share/doc/pidgin-data/changelog.gz
/usr/share/doc/pidgin-data/AUTHORS
/usr/share/menu/pidgin
/usr/share/pixmaps/pidgin
/usr/share/pixmaps/pidgin/buttons
/usr/share/pixmaps/pidgin/buttons/edit.png
/usr/share/pixmaps/pidgin/buttons/music.png
/usr/share/pixmaps/pidgin/buttons/info.png
/usr/share/pixmaps/pidgin/buttons/pause.png
/usr/share/pixmaps/pidgin/logo.png
/usr/share/pixmaps/pidgin/arrow-up.xpm
/usr/share/pixmaps/pidgin/emblems
/usr/share/pixmaps/pidgin/emblems/16
/usr/share/pixmaps/pidgin/emblems/16/not-authorized.png
/usr/share/pixmaps/pidgin/emblems/16/video.png
/usr/share/pixmaps/pidgin/emblems/16/hiptop.png
/usr/share/pixmaps/pidgin/emblems/16/half-operator.png
/usr/share/pixmaps/pidgin/emblems/16/bot.png
/usr/share/pixmaps/pidgin/emblems/16/voice.png
/usr/share/pixmaps/pidgin/emblems/16/external.png
/usr/share/pixmaps/pidgin/emblems/16/secure.png
/usr/share/pixmaps/pidgin/emblems/16/operator.png
/usr/share/pixmaps/pidgin/emblems/16/aol-client.png
/usr/share/pixmaps/pidgin/emblems/16/blocked.png
/usr/share/pixmaps/pidgin/emblems/16/game.png
/usr/share/pixmaps/pidgin/emblems/16/male.png
/usr/share/pixmaps/pidgin/emblems/16/free-for-chat.png
/usr/share/pixmaps/pidgin/emblems/16/mobile.png
/usr/share/pixmaps/pidgin/emblems/16/qq-member.png
/usr/share/pixmaps/pidgin/emblems/16/unavailable.png
/usr/share/pixmaps/pidgin/emblems/16/founder.png
/usr/share/pixmaps/pidgin/emblems/16/female.png
/usr/share/pixmaps/pidgin/animations
/usr/share/pixmaps/pidgin/animations/16
/usr/share/pixmaps/pidgin/animations/16/connect0.png
/usr/share/pixmaps/pidgin/animations/16/connect2.png
/usr/share/pixmaps/pidgin/animations/16/connect5.png
/usr/share/pixmaps/pidgin/animations/16/connect4.png
/usr/share/pixmaps/pidgin/animations/16/typing1.png
/usr/share/pixmaps/pidgin/animations/16/connect7.png
/usr/share/pixmaps/pidgin/animations/16/typing2.png
/usr/share/pixmaps/pidgin/animations/16/connect6.png
/usr/share/pixmaps/pidgin/animations/16/connect3.png
/usr/share/pixmaps/pidgin/animations/16/typing0.png
/usr/share/pixmaps/pidgin/animations/16/connect1.png
/usr/share/pixmaps/pidgin/animations/16/typing3.png
/usr/share/pixmaps/pidgin/animations/16/typing4.png
/usr/share/pixmaps/pidgin/animations/16/typing5.png
/usr/share/pixmaps/pidgin/animations/16/connect8.png
/usr/share/pixmaps/pidgin/dialogs
/usr/share/pixmaps/pidgin/dialogs/64
/usr/share/pixmaps/pidgin/dialogs/64/cool.png
/usr/share/pixmaps/pidgin/dialogs/64/auth.png
/usr/share/pixmaps/pidgin/dialogs/64/question.png
/usr/share/pixmaps/pidgin/dialogs/64/info.png
/usr/share/pixmaps/pidgin/dialogs/64/dialog.png
/usr/share/pixmaps/pidgin/dialogs/64/warning.png
/usr/share/pixmaps/pidgin/dialogs/64/error.png
/usr/share/pixmaps/pidgin/dialogs/64/mail.png
/usr/share/pixmaps/pidgin/dialogs/16
/usr/share/pixmaps/pidgin/dialogs/16/auth.png
/usr/share/pixmaps/pidgin/dialogs/16/question.png
/usr/share/pixmaps/pidgin/dialogs/16/info.png
/usr/share/pixmaps/pidgin/dialogs/16/error.png
/usr/share/pixmaps/pidgin/dialogs/16/mail.png
/usr/share/pixmaps/pidgin/protocols
/usr/share/pixmaps/pidgin/protocols/48
/usr/share/pixmaps/pidgin/protocols/48/meanwhile.png
/usr/share/pixmaps/pidgin/protocols/48/myspace.png
/usr/share/pixmaps/pidgin/protocols/48/silc.png
/usr/share/pixmaps/pidgin/protocols/48/simple.png
/usr/share/pixmaps/pidgin/protocols/48/irc.png
/usr/share/pixmaps/pidgin/protocols/48/yahoo.png
/usr/share/pixmaps/pidgin/protocols/48/gadu-gadu.png
/usr/share/pixmaps/pidgin/protocols/48/novell.png
/usr/share/pixmaps/pidgin/protocols/48/qq.png
/usr/share/pixmaps/pidgin/protocols/48/zephyr.png
/usr/share/pixmaps/pidgin/protocols/48/msn.png
/usr/share/pixmaps/pidgin/protocols/48/icq.png
/usr/share/pixmaps/pidgin/protocols/48/jabber.png
/usr/share/pixmaps/pidgin/protocols/48/bonjour.png
/usr/share/pixmaps/pidgin/protocols/48/aim.png
/usr/share/pixmaps/pidgin/protocols/22
/usr/share/pixmaps/pidgin/protocols/22/meanwhile.png
/usr/share/pixmaps/pidgin/protocols/22/myspace.png
/usr/share/pixmaps/pidgin/protocols/22/silc.png
/usr/share/pixmaps/pidgin/protocols/22/simple.png
/usr/share/pixmaps/pidgin/protocols/22/irc.png
/usr/share/pixmaps/pidgin/protocols/22/yahoo.png
/usr/share/pixmaps/pidgin/protocols/22/gadu-gadu.png
/usr/share/pixmaps/pidgin/protocols/22/novell.png
/usr/share/pixmaps/pidgin/protocols/22/qq.png
/usr/share/pixmaps/pidgin/protocols/22/zephyr.png
/usr/share/pixmaps/pidgin/protocols/22/msn.png
/usr/share/pixmaps/pidgin/protocols/22/icq.png
/usr/share/pixmaps/pidgin/protocols/22/jabber.png
/usr/share/pixmaps/pidgin/protocols/22/bonjour.png
/usr/share/pixmaps/pidgin/protocols/22/google-talk.png
/usr/share/pixmaps/pidgin/protocols/22/aim.png
/usr/share/pixmaps/pidgin/protocols/16
/usr/share/pixmaps/pidgin/protocols/16/meanwhile.png
/usr/share/pixmaps/pidgin/protocols/16/myspace.png
/usr/share/pixmaps/pidgin/protocols/16/silc.png
/usr/share/pixmaps/pidgin/protocols/16/simple.png
/usr/share/pixmaps/pidgin/protocols/16/irc.png
/usr/share/pixmaps/pidgin/protocols/16/yahoo.png
/usr/share/pixmaps/pidgin/protocols/16/gadu-gadu.png
/usr/share/pixmaps/pidgin/protocols/16/novell.png
/usr/share/pixmaps/pidgin/protocols/16/qq.png
/usr/share/pixmaps/pidgin/protocols/16/zephyr.png
/usr/share/pixmaps/pidgin/protocols/16/msn.png
/usr/share/pixmaps/pidgin/protocols/16/icq.png
/usr/share/pixmaps/pidgin/protocols/16/jabber.png
/usr/share/pixmaps/pidgin/protocols/16/bonjour.png
/usr/share/pixmaps/pidgin/protocols/16/google-talk.png
/usr/share/pixmaps/pidgin/protocols/16/aim.png
/usr/share/pixmaps/pidgin/arrow-left.xpm
/usr/share/pixmaps/pidgin/status
/usr/share/pixmaps/pidgin/status/48
/usr/share/pixmaps/pidgin/status/48/log-out.png
/usr/share/pixmaps/pidgin/status/48/busy.png
/usr/share/pixmaps/pidgin/status/48/chat.png
/usr/share/pixmaps/pidgin/status/48/available.png
/usr/share/pixmaps/pidgin/status/48/person.png
/usr/share/pixmaps/pidgin/status/48/log-in.png
/usr/share/pixmaps/pidgin/status/48/rtl
/usr/share/pixmaps/pidgin/status/48/rtl/extended-away.png
/usr/share/pixmaps/pidgin/status/48/away.png
/usr/share/pixmaps/pidgin/status/48/offline.png
/usr/share/pixmaps/pidgin/status/48/extended-away.png
/usr/share/pixmaps/pidgin/status/22
/usr/share/pixmaps/pidgin/status/22/log-out.png
/usr/share/pixmaps/pidgin/status/22/busy.png
/usr/share/pixmaps/pidgin/status/22/chat.png
/usr/share/pixmaps/pidgin/status/22/available.png
/usr/share/pixmaps/pidgin/status/22/invisible.png
/usr/share/pixmaps/pidgin/status/22/person.png
/usr/share/pixmaps/pidgin/status/22/log-in.png
/usr/share/pixmaps/pidgin/status/22/rtl
/usr/share/pixmaps/pidgin/status/22/rtl/log-out.png
/usr/share/pixmaps/pidgin/status/22/rtl/log-in.png
/usr/share/pixmaps/pidgin/status/22/rtl/extended-away.png
/usr/share/pixmaps/pidgin/status/22/away.png
/usr/share/pixmaps/pidgin/status/22/offline.png
/usr/share/pixmaps/pidgin/status/22/extended-away.png
/usr/share/pixmaps/pidgin/status/11
/usr/share/pixmaps/pidgin/status/11/busy.png
/usr/share/pixmaps/pidgin/status/11/chat.png
/usr/share/pixmaps/pidgin/status/11/available.png
/usr/share/pixmaps/pidgin/status/11/invisible.png
/usr/share/pixmaps/pidgin/status/11/person.png
/usr/share/pixmaps/pidgin/status/11/rtl
/usr/share/pixmaps/pidgin/status/11/rtl/extended-away.png
/usr/share/pixmaps/pidgin/status/11/away.png
/usr/share/pixmaps/pidgin/status/11/offline.png
/usr/share/pixmaps/pidgin/status/11/extended-away.png
/usr/share/pixmaps/pidgin/status/16
/usr/share/pixmaps/pidgin/status/16/log-out.png
/usr/share/pixmaps/pidgin/status/16/busy.png
/usr/share/pixmaps/pidgin/status/16/chat.png
/usr/share/pixmaps/pidgin/status/16/available.png
/usr/share/pixmaps/pidgin/status/16/invisible.png
/usr/share/pixmaps/pidgin/status/16/person.png
/usr/share/pixmaps/pidgin/status/16/log-in.png
/usr/share/pixmaps/pidgin/status/16/rtl
/usr/share/pixmaps/pidgin/status/16/rtl/log-out.png
/usr/share/pixmaps/pidgin/status/16/rtl/log-in.png
/usr/share/pixmaps/pidgin/status/16/rtl/extended-away.png
/usr/share/pixmaps/pidgin/status/16/away.png
/usr/share/pixmaps/pidgin/status/16/offline.png
/usr/share/pixmaps/pidgin/status/16/extended-away.png
/usr/share/pixmaps/pidgin/status/32
/usr/share/pixmaps/pidgin/status/32/log-out.png
/usr/share/pixmaps/pidgin/status/32/busy.png
/usr/share/pixmaps/pidgin/status/32/chat.png
/usr/share/pixmaps/pidgin/status/32/available.png
/usr/share/pixmaps/pidgin/status/32/invisible.png
/usr/share/pixmaps/pidgin/status/32/person.png
/usr/share/pixmaps/pidgin/status/32/log-in.png
/usr/share/pixmaps/pidgin/status/32/rtl
/usr/share/pixmaps/pidgin/status/32/rtl/log-out.png
/usr/share/pixmaps/pidgin/status/32/rtl/log-in.png
/usr/share/pixmaps/pidgin/status/32/rtl/extended-away.png
/usr/share/pixmaps/pidgin/status/32/away.png
/usr/share/pixmaps/pidgin/status/32/offline.png
/usr/share/pixmaps/pidgin/status/32/extended-away.png
/usr/share/pixmaps/pidgin/arrow-down.xpm
/usr/share/pixmaps/pidgin/toolbar
/usr/share/pixmaps/pidgin/toolbar/22
/usr/share/pixmaps/pidgin/toolbar/22/select-avatar.png
/usr/share/pixmaps/pidgin/toolbar/16
/usr/share/pixmaps/pidgin/toolbar/16/insert-link.png
/usr/share/pixmaps/pidgin/toolbar/16/font-size-down.png
/usr/share/pixmaps/pidgin/toolbar/16/plugins.png
/usr/share/pixmaps/pidgin/toolbar/16/insert-image.png
/usr/share/pixmaps/pidgin/toolbar/16/emote-select.png
/usr/share/pixmaps/pidgin/toolbar/16/change-fgcolor.png
/usr/share/pixmaps/pidgin/toolbar/16/send-file.png
/usr/share/pixmaps/pidgin/toolbar/16/font-face.png
/usr/share/pixmaps/pidgin/toolbar/16/message-new.png
/usr/share/pixmaps/pidgin/toolbar/16/insert.png
/usr/share/pixmaps/pidgin/toolbar/16/font-size-up.png
/usr/share/pixmaps/pidgin/toolbar/16/unblock.png
/usr/share/pixmaps/pidgin/toolbar/16/change-bgcolor.png
/usr/share/pixmaps/pidgin/emotes
/usr/share/pixmaps/pidgin/emotes/default
/usr/share/pixmaps/pidgin/emotes/default/curse.png
/usr/share/pixmaps/pidgin/emotes/default/bowl.png
/usr/share/pixmaps/pidgin/emotes/default/male-fighter1.png
/usr/share/pixmaps/pidgin/emotes/default/snowman.png
/usr/share/pixmaps/pidgin/emotes/default/snail.png
/usr/share/pixmaps/pidgin/emotes/default/poop.png
/usr/share/pixmaps/pidgin/emotes/default/search.png
/usr/share/pixmaps/pidgin/emotes/default/yawn.png
/usr/share/pixmaps/pidgin/emotes/default/act-up.png
/usr/share/pixmaps/pidgin/emotes/default/soccerball.png
/usr/share/pixmaps/pidgin/emotes/default/worship.png
/usr/share/pixmaps/pidgin/emotes/default/hammer.png
/usr/share/pixmaps/pidgin/emotes/default/at-wits-end.png
/usr/share/pixmaps/pidgin/emotes/default/rose-dead.png
/usr/share/pixmaps/pidgin/emotes/default/mean.png
/usr/share/pixmaps/pidgin/emotes/default/monkey.png
/usr/share/pixmaps/pidgin/emotes/default/smirk.png
/usr/share/pixmaps/pidgin/emotes/default/pizza.png
/usr/share/pixmaps/pidgin/emotes/default/waiting.png
/usr/share/pixmaps/pidgin/emotes/default/dazed.png
/usr/share/pixmaps/pidgin/emotes/default/turtle.png
/usr/share/pixmaps/pidgin/emotes/default/soldier.png
/usr/share/pixmaps/pidgin/emotes/default/coins.png
/usr/share/pixmaps/pidgin/emotes/default/cow.png
/usr/share/pixmaps/pidgin/emotes/default/flag.png
/usr/share/pixmaps/pidgin/emotes/default/drool.png
/usr/share/pixmaps/pidgin/emotes/default/glasses-nerdy.png
/usr/share/pixmaps/pidgin/emotes/default/cloudy.png
/usr/share/pixmaps/pidgin/emotes/default/clover.png
/usr/share/pixmaps/pidgin/emotes/default/crying.png
/usr/share/pixmaps/pidgin/emotes/default/beer.png
/usr/share/pixmaps/pidgin/emotes/default/computer.png
/usr/share/pixmaps/pidgin/emotes/default/disapointed.png
/usr/share/pixmaps/pidgin/emotes/default/brb.png
/usr/share/pixmaps/pidgin/emotes/default/present.png
/usr/share/pixmaps/pidgin/emotes/default/go-away.png
/usr/share/pixmaps/pidgin/emotes/default/curl-lip.png
/usr/share/pixmaps/pidgin/emotes/default/shout.png
/usr/share/pixmaps/pidgin/emotes/default/alien.png
/usr/share/pixmaps/pidgin/emotes/default/meeting.png
/usr/share/pixmaps/pidgin/emotes/default/handcuffs.png
/usr/share/pixmaps/pidgin/emotes/default/kissed.png
/usr/share/pixmaps/pidgin/emotes/default/talktohand.png
/usr/share/pixmaps/pidgin/emotes/default/bad.png
/usr/share/pixmaps/pidgin/emotes/default/camera.png
/usr/share/pixmaps/pidgin/emotes/default/bomb.png
/usr/share/pixmaps/pidgin/emotes/default/cowboy.png
/usr/share/pixmaps/pidgin/emotes/default/liquor.png
/usr/share/pixmaps/pidgin/emotes/default/hug-left.png
/usr/share/pixmaps/pidgin/emotes/default/love.png
/usr/share/pixmaps/pidgin/emotes/default/vampire.png
/usr/share/pixmaps/pidgin/emotes/default/sad.png
/usr/share/pixmaps/pidgin/emotes/default/pumpkin.png
/usr/share/pixmaps/pidgin/emotes/default/skeleton.png
/usr/share/pixmaps/pidgin/emotes/default/highfive.png
/usr/share/pixmaps/pidgin/emotes/default/excruciating.png
/usr/share/pixmaps/pidgin/emotes/default/bashful.png
/usr/share/pixmaps/pidgin/emotes/default/teeth.png
/usr/share/pixmaps/pidgin/emotes/default/question.png
/usr/share/pixmaps/pidgin/emotes/default/in-love.png
/usr/share/pixmaps/pidgin/emotes/default/devil.png
/usr/share/pixmaps/pidgin/emotes/default/mad-tongue.png
/usr/share/pixmaps/pidgin/emotes/default/victory.png
/usr/share/pixmaps/pidgin/emotes/default/theme
/usr/share/pixmaps/pidgin/emotes/default/cake.png
/usr/share/pixmaps/pidgin/emotes/default/music.png
/usr/share/pixmaps/pidgin/emotes/default/eyeroll.png
/usr/share/pixmaps/pidgin/emotes/default/tremble.png
/usr/share/pixmaps/pidgin/emotes/default/goat.png
/usr/share/pixmaps/pidgin/emotes/default/starving.png
/usr/share/pixmaps/pidgin/emotes/default/glasses-cool.png
/usr/share/pixmaps/pidgin/emotes/default/angel.png
/usr/share/pixmaps/pidgin/emotes/default/bulgy-eyes.png
/usr/share/pixmaps/pidgin/emotes/default/island.png
/usr/share/pixmaps/pidgin/emotes/default/wilt.png
/usr/share/pixmaps/pidgin/emotes/default/shame.png
/usr/share/pixmaps/pidgin/emotes/default/freaked-out.png
/usr/share/pixmaps/pidgin/emotes/default/dont-know.png
/usr/share/pixmaps/pidgin/emotes/default/pirate.png
/usr/share/pixmaps/pidgin/emotes/default/bye.png
/usr/share/pixmaps/pidgin/emotes/default/moon.png
/usr/share/pixmaps/pidgin/emotes/default/tongue.png
/usr/share/pixmaps/pidgin/emotes/default/lashes.png
/usr/share/pixmaps/pidgin/emotes/default/snicker.png
/usr/share/pixmaps/pidgin/emotes/default/beat-up.png
/usr/share/pixmaps/pidgin/emotes/default/call-me.png
/usr/share/pixmaps/pidgin/emotes/default/love-over.png
/usr/share/pixmaps/pidgin/emotes/default/cute.png
/usr/share/pixmaps/pidgin/emotes/default/blowkiss.png
/usr/share/pixmaps/pidgin/emotes/default/qq.png
/usr/share/pixmaps/pidgin/emotes/default/pissed-off.png
/usr/share/pixmaps/pidgin/emotes/default/thinking.png
/usr/share/pixmaps/pidgin/emotes/default/fingers-crossed.png
/usr/share/pixmaps/pidgin/emotes/default/sweat.png
/usr/share/pixmaps/pidgin/emotes/default/watermelon.png
/usr/share/pixmaps/pidgin/emotes/default/star.png
/usr/share/pixmaps/pidgin/emotes/default/pill.png
/usr/share/pixmaps/pidgin/emotes/default/sarcastic.png
/usr/share/pixmaps/pidgin/emotes/default/rainbow.png
/usr/share/pixmaps/pidgin/emotes/default/silly.png
/usr/share/pixmaps/pidgin/emotes/default/msn.png
/usr/share/pixmaps/pidgin/emotes/default/umbrella.png
/usr/share/pixmaps/pidgin/emotes/default/hug-right.png
/usr/share/pixmaps/pidgin/emotes/default/time-out.png
/usr/share/pixmaps/pidgin/emotes/default/rotfl.png
/usr/share/pixmaps/pidgin/emotes/default/loser.png
/usr/share/pixmaps/pidgin/emotes/default/laugh.png
/usr/share/pixmaps/pidgin/emotes/default/stop.png
/usr/share/pixmaps/pidgin/emotes/default/clown.png
/usr/share/pixmaps/pidgin/emotes/default/good.png
/usr/share/pixmaps/pidgin/emotes/default/film.png
/usr/share/pixmaps/pidgin/emotes/default/kissing.png
/usr/share/pixmaps/pidgin/emotes/default/ghost.png
/usr/share/pixmaps/pidgin/emotes/default/doh.png
/usr/share/pixmaps/pidgin/emotes/default/quiet.png
/usr/share/pixmaps/pidgin/emotes/default/coffee.png
/usr/share/pixmaps/pidgin/emotes/default/sick.png
/usr/share/pixmaps/pidgin/emotes/default/boy.png
/usr/share/pixmaps/pidgin/emotes/default/rain.png
/usr/share/pixmaps/pidgin/emotes/default/smile.png
/usr/share/pixmaps/pidgin/emotes/default/lamp.png
/usr/share/pixmaps/pidgin/emotes/default/sigarette.png
/usr/share/pixmaps/pidgin/emotes/default/girl.png
/usr/share/pixmaps/pidgin/emotes/default/angry.png
/usr/share/pixmaps/pidgin/emotes/default/disdain.png
/usr/share/pixmaps/pidgin/emotes/default/msn_online.png
/usr/share/pixmaps/pidgin/emotes/default/clock.png
/usr/share/pixmaps/pidgin/emotes/default/waving.png
/usr/share/pixmaps/pidgin/emotes/default/mobile.png
/usr/share/pixmaps/pidgin/emotes/default/phone.png
/usr/share/pixmaps/pidgin/emotes/default/pray.png
/usr/share/pixmaps/pidgin/emotes/default/shock.png
/usr/share/pixmaps/pidgin/emotes/default/weep.png
/usr/share/pixmaps/pidgin/emotes/default/sun.png
/usr/share/pixmaps/pidgin/emotes/default/lying.png
/usr/share/pixmaps/pidgin/emotes/default/knife.png
/usr/share/pixmaps/pidgin/emotes/default/skywalker.png
/usr/share/pixmaps/pidgin/emotes/default/sheep.png
/usr/share/pixmaps/pidgin/emotes/default/confused.png
/usr/share/pixmaps/pidgin/emotes/default/terror.png
/usr/share/pixmaps/pidgin/emotes/default/beauty.png
/usr/share/pixmaps/pidgin/emotes/default/tv.png
/usr/share/pixmaps/pidgin/emotes/default/arrogant.png
/usr/share/pixmaps/pidgin/emotes/default/console.png
/usr/share/pixmaps/pidgin/emotes/default/mohawk.png
/usr/share/pixmaps/pidgin/emotes/default/female-fighter.png
/usr/share/pixmaps/pidgin/emotes/default/foot-in-mouth.png
/usr/share/pixmaps/pidgin/emotes/default/kiss.png
/usr/share/pixmaps/pidgin/emotes/default/party.png
/usr/share/pixmaps/pidgin/emotes/default/pig.png
/usr/share/pixmaps/pidgin/emotes/default/male-fighter2.png
/usr/share/pixmaps/pidgin/emotes/default/yin-yang.png
/usr/share/pixmaps/pidgin/emotes/default/smile-big.png
/usr/share/pixmaps/pidgin/emotes/default/messed.png
/usr/share/pixmaps/pidgin/emotes/default/thunder.png
/usr/share/pixmaps/pidgin/emotes/default/hypnotized.png
/usr/share/pixmaps/pidgin/emotes/default/peace.png
/usr/share/pixmaps/pidgin/emotes/default/sidefrown.png
/usr/share/pixmaps/pidgin/emotes/default/car.png
/usr/share/pixmaps/pidgin/emotes/default/airplane.png
/usr/share/pixmaps/pidgin/emotes/default/dog.png
/usr/share/pixmaps/pidgin/emotes/default/dance.png
/usr/share/pixmaps/pidgin/emotes/default/struggle.png
/usr/share/pixmaps/pidgin/emotes/default/chicken.png
/usr/share/pixmaps/pidgin/emotes/default/sinister.png
/usr/share/pixmaps/pidgin/emotes/default/cyclops.png
/usr/share/pixmaps/pidgin/emotes/default/drink.png
/usr/share/pixmaps/pidgin/emotes/default/moneymouth.png
/usr/share/pixmaps/pidgin/emotes/default/musical-note.png
/usr/share/pixmaps/pidgin/emotes/default/embarrassed.png
/usr/share/pixmaps/pidgin/emotes/default/handshake.png
/usr/share/pixmaps/pidgin/emotes/default/desire.png
/usr/share/pixmaps/pidgin/emotes/default/secret.png
/usr/share/pixmaps/pidgin/emotes/default/wink.png
/usr/share/pixmaps/pidgin/emotes/default/mail.png
/usr/share/pixmaps/pidgin/emotes/default/eat.png
/usr/share/pixmaps/pidgin/emotes/default/plate.png
/usr/share/pixmaps/pidgin/emotes/default/nailbiting.png
/usr/share/pixmaps/pidgin/emotes/default/on-the-phone.png
/usr/share/pixmaps/pidgin/emotes/default/doctor.png
/usr/share/pixmaps/pidgin/emotes/default/sleepy.png
/usr/share/pixmaps/pidgin/emotes/default/shut-mouth.png
/usr/share/pixmaps/pidgin/emotes/default/clap.png
/usr/share/pixmaps/pidgin/emotes/default/msn-busy.png
/usr/share/pixmaps/pidgin/emotes/default/neutral.png
/usr/share/pixmaps/pidgin/emotes/default/cat.png
/usr/share/pixmaps/pidgin/emotes/default/jump.png
/usr/share/pixmaps/pidgin/emotes/default/giggle.png
/usr/share/pixmaps/pidgin/emotes/default/can.png
/usr/share/pixmaps/pidgin/emotes/default/msn-away.png
/usr/share/pixmaps/pidgin/emotes/default/rose.png
/usr/share/pixmaps/pidgin/emotes/none
/usr/share/pixmaps/pidgin/emotes/none/theme
/usr/share/pixmaps/pidgin/arrow-right.xpm
/usr/share/pixmaps/pidgin/tray
/usr/share/pixmaps/pidgin/tray/48
/usr/share/pixmaps/pidgin/tray/48/tray-online.png
/usr/share/pixmaps/pidgin/tray/48/tray-extended-away.png
/usr/share/pixmaps/pidgin/tray/48/tray-connecting.png
/usr/share/pixmaps/pidgin/tray/48/tray-busy.png
/usr/share/pixmaps/pidgin/tray/48/tray-away.png
/usr/share/pixmaps/pidgin/tray/48/tray-offline.png
/usr/share/pixmaps/pidgin/tray/48/tray-invisible.png
/usr/share/pixmaps/pidgin/tray/48/tray-new-im.png
/usr/share/pixmaps/pidgin/tray/22
/usr/share/pixmaps/pidgin/tray/22/tray-online.png
/usr/share/pixmaps/pidgin/tray/22/tray-extended-away.png
/usr/share/pixmaps/pidgin/tray/22/tray-message.png
/usr/share/pixmaps/pidgin/tray/22/tray-connecting.png
/usr/share/pixmaps/pidgin/tray/22/tray-busy.png
/usr/share/pixmaps/pidgin/tray/22/tray-away.png
/usr/share/pixmaps/pidgin/tray/22/tray-offline.png
/usr/share/pixmaps/pidgin/tray/22/tray-invisible.png
/usr/share/pixmaps/pidgin/tray/22/tray-new-im.png
/usr/share/pixmaps/pidgin/tray/16
/usr/share/pixmaps/pidgin/tray/16/tray-online.png
/usr/share/pixmaps/pidgin/tray/16/tray-extended-away.png
/usr/share/pixmaps/pidgin/tray/16/tray-message.png
/usr/share/pixmaps/pidgin/tray/16/tray-connecting.png
/usr/share/pixmaps/pidgin/tray/16/tray-busy.png
/usr/share/pixmaps/pidgin/tray/16/tray-away.png
/usr/share/pixmaps/pidgin/tray/16/tray-offline.png
/usr/share/pixmaps/pidgin/tray/16/tray-invisible.png
/usr/share/pixmaps/pidgin/tray/16/tray-new-im.png
/usr/share/pixmaps/pidgin/tray/32
/usr/share/pixmaps/pidgin/tray/32/tray-online.png
/usr/share/pixmaps/pidgin/tray/32/tray-extended-away.png
/usr/share/pixmaps/pidgin/tray/32/tray-connecting.png
/usr/share/pixmaps/pidgin/tray/32/tray-busy.png
/usr/share/pixmaps/pidgin/tray/32/tray-away.png
/usr/share/pixmaps/pidgin/tray/32/tray-offline.png
/usr/share/pixmaps/pidgin/tray/32/tray-invisible.png
/usr/share/pixmaps/pidgin/tray/32/tray-new-im.png
/usr/share/pixmaps/pidgin-menu.xpm
/usr/share/icons/hicolor/22x22/apps/pidgin.png
/usr/share/icons/hicolor/scalable/apps/pidgin.svg
/usr/share/icons/hicolor/32x32/apps/pidgin.png
/usr/share/icons/hicolor/16x16/apps/pidgin.png
/usr/share/icons/hicolor/24x24/apps/pidgin.png
/usr/share/icons/hicolor/48x48/apps/pidgin.png
/usr/share/locale-langpack/en_CA/LC_MESSAGES/pidgin.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/pidgin.mo
/usr/share/locale-langpack/en_AU/LC_MESSAGES/pidgin.mo
/usr/bin/pidgin

```

---

### Post by Ek0nomik on 2007-10-08
Bump.  :)

---

### Post by Ek0nomik on 2007-10-09
[https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/144122](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/144122)

This solved the problem.

---

### Post by strabes on 2007-10-09
[QUOTE=Ek0nomik]I actually don't have a ~/.pidgin directory.  Root also doesn't have a .pidgin directory in the home folder. Any other ideas where it should be?[/QUOTE]

Oops, I'm sorry. I wasn't thinking clearly I guess. The correct directory is ~/.purple. I don't know why they don't just use ~/.pidgin. Anyway, glad you fixed your problem. Please mark the thread as SOLVED.

---

### Post by strabes on 2007-10-09
Funny, I just realized I was having the same issue!

Anyway, in case anyone else is having the same problem, the fix is to close pidgin, open ~/.purple/prefs.xml, change "stringlist" to "pathlist" and then restart pidgin.

---

