---
title: "DVD playback, starter guide not sufficient"
date: 2005-05-15
forum: General Help
---

### Post by Strife on 2005-05-15
I've been around Linux for about 5 years now, and I recently purchased a laptop. In order to get a system setup without having to do manual configuration, I decided to go with Ubuntu. Overall, I am very pleased with it thus far. However, I do have a number of outstanding issues, DVD playback being one of them.

I followed the (very short) DVD playback howto on the Unofficial Ubuntu Starter Guide, but no luck. Trying to paly DVDs with Totem, I get the following output on the console:

** Message: don't know how to handle video/mpeg, mpegversion=(int)2, systemstream=(boolean)false
** Message: don't know how to handle audio/x-ac3
** Message: don't know how to handle audio/x-ac3
** Message: don't know how to handle audio/x-ac3
** Message: don't know how to handle video/x-dvd-subpicture
** Message: don't know how to handle video/x-dvd-subpicture
** Message: don't know how to handle video/x-dvd-subpicture

Depending on the DVD, these messages may be a little different. Also, on some DVDs, Totem doesn't get any further than this, and just hangs, while on some it actually displays a GTK error message telling me that it cannot play the DVD for an "unknown reason."

Any help would be greatly appreciated. If there's some other information that would be helpful in answering this question, please let me know and I'll post that as soon as possible.

---

### Post by zaxer on 2005-05-15
[QUOTE=Strife]I've been around Linux for about 5 years now, and I recently purchased a laptop. In order to get a system setup without having to do manual configuration, I decided to go with Ubuntu. Overall, I am very pleased with it thus far. However, I do have a number of outstanding issues, DVD playback being one of them.

I followed the (very short) DVD playback howto on the Unofficial Ubuntu Starter Guide, but no luck. Trying to paly DVDs with Totem, I get the following output on the console:

** Message: don't know how to handle video/mpeg, mpegversion=(int)2, systemstream=(boolean)false
** Message: don't know how to handle audio/x-ac3
** Message: don't know how to handle audio/x-ac3
** Message: don't know how to handle audio/x-ac3
** Message: don't know how to handle video/x-dvd-subpicture
** Message: don't know how to handle video/x-dvd-subpicture
** Message: don't know how to handle video/x-dvd-subpicture

Depending on the DVD, these messages may be a little different. Also, on some DVDs, Totem doesn't get any further than this, and just hangs, while on some it actually displays a GTK error message telling me that it cannot play the DVD for an "unknown reason."

Any help would be greatly appreciated. If there's some other information that would be helpful in answering this question, please let me know and I'll post that as soon as possible.[/QUOTE]
 I cant play DVD´s either :(

---

### Post by Strife on 2005-05-15
Update:

I also tried the instructions on the "RestrictedFormats" document on the Wiki available here: [http://www.ubuntulinux.org/wiki/RestrictedFormats/view?searchterm=dvd%20playback](http://www.ubuntulinux.org/wiki/RestrictedFormats/view?searchterm=dvd%20playback).

However, this also proved not to work.

Any ideas? This is the one thing that I would really like to get working that isn't working yet.

---

### Post by gratefulfrog on 2005-05-16
I'm running a 64bit platformm and have also found that totem is not great, (read "worthless"), I suggest trying some of the other viewers:

mplayer (gmplayer is the GUI interface)
vlc mdeia player (wxvlc is the command line to start it)

maybe even, realplayer  for linux, but you'll need a 32bit chroot if you're on 64bit...

Both mplayer and vlc work perfectly on my machine, you'll need to reset the 'open with' from nautilus to get the double-click to play to work, use right click on the appropriate file....

good luck!

---

### Post by logan2004 on 2005-05-16
i personally can't stand totem, but i found VLC for gnome to be great, i couldn't get dvds to work with totem either, but i haven't yet found a file or disc that VLC can't handle.

---

### Post by Strife on 2005-05-16
I actually looked into VLC yesterday, but to my surprise, I couldn't seem to find the package. I know that in Debian, it's just the package vlc (or gnome-vlc or whatever if you want that extra stuff), but I coudln't seem to find it with apt-cache search nor Synaptic on Ubuntu.

Of course, maybe it was just a typo on my part... I'll give it a try when I get home later today.

Thanks for the suggestions.

---

### Post by Strife on 2005-05-16
Nevermind, just a dumb typo on my part apparnetly. I'll download VLC and see what happens.

---

### Post by bored2k on 2005-05-16
[QUOTE=Strife]Nevermind, just a dumb typo on my part apparnetly. I'll download VLC and see what happens.[/QUOTE]
 Make sure you get vlc-esd or vlc-whateversoundsystem you're on.

---

### Post by Strife on 2005-05-16
Oh one more question. In the past, I have used and liked xine quite a bit. Do people have less problems with it, too?

From what I understand, Totem uses xine-lib, so I would imagine that problems with Totem may manifest themselves with xine as well.

---

### Post by clb137 on 2005-05-16
[QUOTE=Strife]I've been around Linux for about 5 years now, and I recently purchased a laptop. In order to get a system setup without having to do manual configuration, I decided to go with Ubuntu. Overall, I am very pleased with it thus far. However, I do have a number of outstanding issues, DVD playback being one of them.

I followed the (very short) DVD playback howto on the Unofficial Ubuntu Starter Guide, but no luck. Trying to paly DVDs with Totem, I get the following output on the console:

** Message: don't know how to handle video/mpeg, mpegversion=(int)2, systemstream=(boolean)false
** Message: don't know how to handle audio/x-ac3
** Message: don't know how to handle audio/x-ac3
** Message: don't know how to handle audio/x-ac3
** Message: don't know how to handle video/x-dvd-subpicture
** Message: don't know how to handle video/x-dvd-subpicture
** Message: don't know how to handle video/x-dvd-subpicture

Depending on the DVD, these messages may be a little different. Also, on some DVDs, Totem doesn't get any further than this, and just hangs, while on some it actually displays a GTK error message telling me that it cannot play the DVD for an "unknown reason."

Any help would be greatly appreciated. If there's some other information that would be helpful in answering this question, please let me know and I'll post that as soon as possible.[/QUOTE]


Hi there,

Have u tried to play dvd with 'xine' ???? with all the correct codecs loaded and the following guide followed the only minor problem i had was  with 'dma' on the dvd this was very eaisly solved by a quick edit in the 'hdparm.conf'

any probs give me a shout


clinton

---

### Post by bored2k on 2005-05-16
[QUOTE=Strife]Oh one more question. In the past, I have used and liked xine quite a bit. Do people have less problems with it, too?

From what I understand, Totem uses xine-lib, so I would imagine that problems with Totem may manifest themselves with xine as well.[/QUOTE]
 I trust xine-ui 200 times more than I trust totem-xine, even if they use the same engine.

---

### Post by chombee on 2005-05-16
I find that Xine works very well for DVDs. Totem-xine and gxone etc do not work anywhere near as well as just plain xine does. In Warty for me totem-xine would not play DVS etc that Xine would play fine. In hoary I found the sounds gets out of synch in totem xine but not in xine.

So use Xine for playing DVDs, I say.

Ogle is also a very good DVD player that is packaged for Ubuntu.

I use the following programs whenever I need to play a DVD or video file of some kind, usually one of these will work:

xine (best for DVDs)
ogle (second best for DVDs)
mplayer (best for downloaded video files)
totem-gstreamer (a last resort, really)

Well those are the ones I can remember straight off. And off the top of my head I have the following packages for codecs etc related to video:

w32codecs
ffmpeg
libdvdcss2
gstreamer0.8-plugins

---

### Post by Strife on 2005-05-16
Well this is good news. I've always liked xine-ui, so hopefully it'll work. Thanks for all the input thus far.

I'll let you know how it goes tonight.

---

### Post by jodef on 2005-05-16
[QUOTE=Strife]Well this is good news. I've always liked xine-ui, so hopefully it'll work. Thanks for all the input thus far.

I'll let you know how it goes tonight.[/QUOTE]I have never tried vlc although from what I have read here might be worth a look but xine has never let me down. Never really liked Totem works horribly on my system and mplayer just doesn't like me.

---

### Post by Strife on 2005-05-17
Yep, xine-ui works. Thanks a lot guys!  :grin:

---

### Post by ganatronic on 2005-05-19
Yeah, early thanks from me, too (can't check just yet).

I wasn't having luck with totem-xine yesterday. I was able to play the interpol warning and the "commentary on this dvd..." screen, but then it wouldn't go past that. Attempting to load individual files from the DVDs folders also did not work - unknown error. It's especially annoying because some DVDs will work fine. By that I mean Futurama Season 4, disc 1 will work fine, while Futurama Season 3, disc 3 will not. Doesn't make much sense.

I tried to use VLC (which I had installed previously and used with similar success as totem-xine). In VLC I was able to load the DVD menu screen, but clicking "Play movie" would cause the entire program to close. I almost got it to work by bypassing the menu (choosing "DVD" rather than "DVD menu..." under File > Open). This looked hopeful at first, as the movie began player, and the timer on the bottom said "0:31 of 126:42". But then it never made it past three minutes - which I'm assuming was the first chapter. It just repeated the chapter over and over. If I attempted to load files individually in VLC it would play them in a garbled and slow manner.

I know these players work, since they've worked for me before. They just don't seem to do it consistently. It was a real bummer last night when I had a pretty girl snuggling with me, the laptop resting on a chair next to the bed, and then me struggling for twenty minutes (with all these false starts) to get it to work. And it never did. I tried a second DVD, and that didn't work either.

So I think I'll give xine-ui a try. And also Ogle, since I've never even noticed that one before. I'd love to have a player where I could just go to File > Play DVD, and then a DVD would play. But it never seems that simple.

And I have all the correct libs and all the correct VLC things.

---

