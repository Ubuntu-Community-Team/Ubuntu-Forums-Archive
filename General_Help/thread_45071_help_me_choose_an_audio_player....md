---
title: "help me choose an audio player..."
date: 2005-06-28
forum: General Help
---

### Post by escobar on 2005-06-28
Not to trash *nix because I am a fan but is there an audio player that is (relatively) easy to setup and use? Now I know this will attract some trolls so let me explain my case first.

I tried using Beep Media Player, I'm sure it's very nice but I have some 17GB of music, and poor Beep just crashes whenever trying to add all my music to the library. It tried though, poor little guy...(sniff)

Tried XMMS, but I do not seem to be able to add my entire collection. Not sure why, but I just can't select my entire music folder and let XMMS take it from there.Selecting individual tracks seems to work ok, but since my music is categorized the "iTunes way" meaning it's artist/album/song in seperate folders, it would take FOREVER to add it all to XMMS.

Rhythm Box was ok, but does not automatically scan my music folder and add new tracks, plus has no built in tagging feature. I've been told to wait on the next version which should be really nice.....

I really like AmaroK from my Mepis days, but sadly cannot get the sound to work in Ubuntu,gives a bunch of errors when booting up.  :neutral: 

Quod Libet....O GOD! I had high hopes for this, but just could never get it to launch. I tried following the tutorial some kind soul put together in these forums but still never got it to actually launch.

-So at the present time I still use iTunes via VMWare to saisfy my music needs. 

What I'm looking for is just an audio player that will work with minimal amount of fuss. Preferably one that can re-scan your collection at bootup, or auto imports tracks when you double-click them. In short something that makes really easy to manage your collection. I'm still fiddling around with XMMS but I'm open to any suggestions. I cannot tell you what it's like to wanna hear you favorite jam, but have to wait until VMWare boots up first.......then the audio gets a little choppy when you're doing anything else on the machine....

Thanks for any responses....

---

### Post by intangible on 2005-06-28
I hear good things about muine: [http://www.gnomefiles.org/app.php?soft_id=244](http://www.gnomefiles.org/app.php?soft_id=244)

Also, [http://www.gnomefiles.org](http://www.gnomefiles.org) is a good place to find information about programs.

---

### Post by felipe on 2005-06-28
right now i'm sticking with rhythmbox... it's not perfect, still lacking some basic features, but it integrates perfectly into gnome

amarok is far more complete, i'd say the best player in the known universe right now :D

if you don't mind mixing kde apps with gnome desktop... i'd recommend amarok. the issue about sound could be resolved by using xine as "audio engine" for amarok, although it should work ok with gstreamer

---

### Post by afonic on 2005-06-28
[QUOTE=escobar]Not to trash *nix because I am a fan but is there an audio player that is (relatively) easy to setup and use? Now I know this will attract some trolls so let me explain my case first.

I tried using Beep Media Player, I'm sure it's very nice but I have some 17GB of music, and poor Beep just crashes whenever trying to add all my music to the library. It tried though, poor little guy...(sniff)

Tried XMMS, but I do not seem to be able to add my entire collection. Not sure why, but I just can't select my entire music folder and let XMMS take it from there.Selecting individual tracks seems to work ok, but since my music is categorized the "iTunes way" meaning it's artist/album/song in seperate folders, it would take FOREVER to add it all to XMMS.

Rhythm Box was ok, but does not automatically scan my music folder and add new tracks, plus has no built in tagging feature. I've been told to wait on the next version which should be really nice.....

I really like AmaroK from my Mepis days, but sadly cannot get the sound to work in Ubuntu,gives a bunch of errors when booting up.  :neutral: 

Quod Libet....O GOD! I had high hopes for this, but just could never get it to launch. I tried following the tutorial some kind soul put together in these forums but still never got it to actually launch.

-So at the present time I still use iTunes via VMWare to saisfy my music needs. 

What I'm looking for is just an audio player that will work with minimal amount of fuss. Preferably one that can re-scan your collection at bootup, or auto imports tracks when you double-click them. In short something that makes really easy to manage your collection. I'm still fiddling around with XMMS but I'm open to any suggestions. I cannot tell you what it's like to wanna hear you favorite jam, but have to wait until VMWare boots up first.......then the audio gets a little choppy when you're doing anything else on the machine....

Thanks for any responses....[/QUOTE]
 Install amarok-xine and it will work. The best player in the universe indeed!

However you don't like all these players and like iTunes player?? :-S
Now iTunes is some serious c**p, I was so pissed I had to used it for my iPod I almost cried when I found out about gtkpod!

---

### Post by escobar on 2005-06-28
"Install amarok-xine and it will work. The best player in the universe indeed!

However you don't like all these players and like iTunes player?? :-S
Now iTunes is some serious c**p, I was so pissed I had to used it for my iPod I almost cried when I found out about gtkpod!"

Not so much I don't like them, just encountered a few quirks when attempting to use them, or just cannot install them at all. I like iTunes because it's simplicity, it always worked fine for me, never any real problems, but then again I was with the Apple Help Desk for 18 months.

I never actually tried "amarok-xine" just Amarok on it's own, so that gives me something additional to try when I get home. I also don't own an iPod so I'm afraid I can't relate with respect to gtkpod but I hear it's really good. I'm not really a fan of KDE but it Amarok works, I'll stick with it. Thanks.

---

### Post by psychicdragon on 2005-06-28
I'm a big fan of Muine. It seems to be mostly geared towards people, like me, who like to pick an album and then listen to it. The playlist management features are not as robust as iTunes or Rhythmbox.

It will watch over your music collection. When you run it for the first time tell it to import the folder where you keep all your music, in my case that's /home/david/music. Whenever you add an album either from sound-juicer or from p2p it will magically appear in your album list.

Since it seems to be about the only music player you haven't tried yet, it's worth giving a shot I guess. It might work for your needs.

---

### Post by Tyr_7BE on 2005-06-29
[QUOTE=psychicdragon]I'm a big fan of Muine. It seems to be mostly geared towards people, like me, who like to pick an album and then listen to it. The playlist management features are not as robust as iTunes or Rhythmbox.

It will watch over your music collection. When you run it for the first time tell it to import the folder where you keep all your music, in my case that's /home/david/music. Whenever you add an album either from sound-juicer or from p2p it will magically appear in your album list.

Since it seems to be about the only music player you haven't tried yet, it's worth giving a shot I guess. It might work for your needs.[/QUOTE]

Agreed.  I love Muine.  Dead sexy application.  It has completely ruined BMP and Rhythmbox for me.  I'm addicted to the way it manages albums.

Just make sure you have universe in your repo, and type "sudo apt-get install muine".  Simple as that!

---

### Post by angkor on 2005-06-29
[QUOTE=afonic]Install amarok-xine and it will work. The best player in the universe indeed!

However you don't like all these players and like iTunes player?? :-S
Now iTunes is some serious c**p, I was so pissed I had to used it for my iPod I almost cried when I found out about gtkpod![/QUOTE]

iTunes for windows is indeed quite crappy, but iTunes for mac is actually _very_ good, especially with airtunes.

You could also try the gstreamer-engine for amarok:

```
apt-cache search amarok-engine
amarok - versatile and easy to use audio player for KDE
amarok-arts - aRts engine for the amaroK audio player
amarok-engines - output engines for the amaroK audio player
amarok-gstreamer - GStreamer engine for the amaroK audio player
amarok-xine - xine engine for the amaroK audio player
``` 

Just mess around in amarok settings and it should work...to me it's the best music player for Linux (especially when you have a large music collection).

---

