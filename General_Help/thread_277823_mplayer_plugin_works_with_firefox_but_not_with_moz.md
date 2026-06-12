---
title: "mplayer plugin works with firefox but not with mozilla suite"
date: 2006-10-15
forum: General Help
---

### Post by eniel on 2006-10-15
I have installed mplayer and the mplayer plugin (sudo aptitude install mozilla-mplayer) along with several codecs.
It works all-right in firefox but not in the mozilla browser (part of the mozilla suite).

When I go to the testsite: 
	[http://fredrik.hubbe.net/plugger/test.html](http://fredrik.hubbe.net/plugger/test.html) 
and try audio > mp3 or video > mpeg firefox works fine but the mozilla browser just shows the missing plugins icon.

When I click on the icon I get the message:
   this page contains information of a type (audio/mpeg3) that 
   can only be viewed with the appropriate Plug-in.

When I look with about:plugins at the installed plugins, I get the following results:

For FireFox:
Windows Media Player Plugin:    File name: mplayerplug-in-wmp.so
Shockwave Flash:    File name: libflashplayer.so
Google VLC multimedia plugin 1.0:     File name: mplayerplug-in-gmp.so
QuickTime Plug-in 6.0:     File name: mplayerplug-in-qt.so
RealPlayer 9:    File name: mplayerplug-in-rm.so
mplayerplug-in 3.17:    File name: mplayerplug-in.so
	MIME Type 	Description 	Suffixes 	Enabled
	video/mpeg 	MPEG 		mpg,mpeg 	Yes
	audio/mpeg3 	MPEG audio 	mp3 		Yes

For the Mozilla browser:
Shockwave Flash:    File name: libflashplayer.so
Default Plugin     File name: libnullplugin.so
Google VLC multimedia plugin 1.0:    File name: mplayerplug-in-gmp.so
QuickTime Plug-in 6.0:    File name: mplayerplug-in-qt.so
RealPlayer 9:    File name: mplayerplug-in-rm.so
Windows Media Player Plugin:    File name: mplayerplug-in-wmp.so
mplayerplug-in 3.17:    File name: mplayerplug-in.so
	MIME Type 	Description 	Suffixes 	Enabled
	video/mpeg 	MPEG 		mpg,mpeg 	Yes
	audio/mpeg3 	MPEG audio 	mp3 		Yes
Adobe Reader 7.0:     File name: nppdf.so

The only differences being that Adobe reader and the default plugin are installed with the mozilla browser. The plugins appear to be installed correctly, but the mozilla browser seems unable to use them.

I have compared the plugin directories and they both contain the plugin files.
I have tried adding mplayerplug-in.so as a new helper application (edit > preferences > helper applications > new type) which did not work. However I got the warning that this file type was already handled internally.
I have run the mozilla browser as root (in case there is a rights problem) but this did not work either. 
I have reinstalled mozilla as well as  mozilla-mplayer.

By the way the flash player works on both Firefox and Mozilla browser.

I have run out of ideas, has anyone an idea how to get mplayer working with the mozilla browser?

Thanks

---

### Post by katalyst23 on 2006-10-15
I followed this:  [http://www.ubuntuforums.org/showthread.php?t=202537&highlight=firefox+amd64](http://www.ubuntuforums.org/showthread.php?t=202537&highlight=firefox+amd64)

But please note it is for AMD64.. but further down the thread he does have something about mplayer, and a script that will install it..

hope this helps

---

### Post by eniel on 2006-10-15
sorry,

my problem is not installing mplayer with firefox; this works
but why doesn't it work with the mozilla browser although according to about:plugins it has been installed successfully. Looks like I miss some setting in the mozilla browser, or does mplayer not work with this browser?

---

### Post by lchata on 2006-10-21
I, too, have this problem with mozilla-mplayer-3.17 and also with mplayerpluig-in-3.31 cvs compiled. I also posted a bug report on this issue which was reported solved in a later version of mozilla-mplayer3.25, I think. 
I don't think it's a problem with the mplayerplug-ins as firefox uses the same ones. It must be something that the Debian maintainer, Ari Pollack, or the Ubuntu folks changed as this issue has been with me since Debian Sid with no solution. Come on. Debian/Ubuntu fix up what you changed so mozilla browser will play embedds and not just the adds and stop. Haven't gotten any useful help/solution for this issue from (K)ubuntu user lists. Must I try mozilla seamonkey, which plays, in order to get mozilla browser to function as it should.
Someone said the (K)ubuntu was the user friendly distro? If it sounds like I'm a little put out on this issue, your right; I've been trying to solve it since Debian Sid over a year ago. It's about time Debian/Ubuntu resolved this issue.]([http://ubuntuforums.org/images/smilies/eusa_wall.gif*](http://ubuntuforums.org/images/smilies/eusa_wall.gif*),)

---

