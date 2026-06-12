---
title: "how to play online music in mozilla"
date: 2007-03-11
forum: General Help
---

### Post by jaind on 2007-03-11
hello,

i cannot figure out how to play online music in ubuntu using mozilla. most of the sites play in realplayer, which ive used for eons in windows. 
I've installed realplayer in ubuntu but all i get is the following popup(when i try to play the online song):

-------------------------------------------------------------------------------------------------------------------------
Totem could not play 'file:///home/adam/.mozilla/firefox/q0p950j1.default/Cache/59D91DD6d01'.
 
Could not determine type of stream.
-------------------------------------------------------------------------------------------------------------------------

Any suggestions??

---

### Post by Redeyes_Gambit on 2007-03-11
Could you post the output of your about:plugins? If you have never done that before, just type "about:plugins" in your address bar :) .

---

### Post by jaind on 2007-03-11
hello. the output for about:plugins is attached. 
--cant see realplayer in there. do i have to install the plugin?

Thanks!

PS: i personally couldn't get the totem player to even play songs on my hard drive!

---

### Post by Redeyes_Gambit on 2007-03-11
Lol, yea generally Totem stinks UNTIL you install the proper plugins. So, without further ado, the proper plugins:

Edit: Stupid me! I forgot you could lump all the things to install together!

```

sudo apt-get install gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-fluendo-mpegdemux gstreamer0.10-gl gstreamer0.10-gnomevfs gstreamer0.10-gnonlin gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-sdl gstreamer0.10-tools libgstreamer0.10-0  libgstreamer-plugins-base0.10-0 gstreamer0.10-x

``` 


Lol, yes that is a lot of code. Just copy-paste it all into a Terminal. Chances are you probably already have a bunch of those, and will probably never need or use a bunch of those, but better to get it all over with in one big gulp right? :)

If you get any errors, or have any other questions, just post them here.

---

### Post by jaind on 2007-03-12
I ran the command you gave me and got the following:

E: Couldn't find package gstreamer0.10-bad-multiverse

-- i removed "gstreamer0.10-bad-multiverse" and the command ran. I rebooted the machine but still got the original error message when i try to play online music :(

Any solutions??

---

### Post by Redeyes_Gambit on 2007-03-13
Oops! My bad. With all those plugins I was bound to have put a typo in somewhere :) . That should read "gstreamer0.10-plugins-bad-multiverse"

```

sudo apt-get install gstreamer0.10-plugins-bad-multiverse

```

If I'm not mistaken that is one of the plugins you need most. If problems still persist just post here :) .

---

### Post by jaind on 2007-03-13
Still getting the same error!
-------------------------------------------------------------------------------------------------------------------------
Totem could not play 'file:///home/adam/.mozilla/firefox/q0p950j1.default/Cache/59D91DD6d01'.

Could not determine type of stream.
-------------------------------------------------------------------------------------------------------------------------

-- I looked up the file "59D91DD6d01" and its blank.

~~~???~~~

---

### Post by Redeyes_Gambit on 2007-03-13
Hm... What website specifically are you trying to access? I also notice that you have an old version of flash player (version 7.)

---

### Post by CocoAUS on 2007-03-13
Have you installed the mplayer plugin?  It'll do much better, depending on what you're trying to run.  And, for the record, Linux and Mozilla simply don't handle online media very well.

```
sudo aptitude install mozilla-mplayer
```

---

### Post by jaind on 2007-03-14
tried mplayer and it didnt work either!

One of the websites i listen online music on is(the songs are not in english):
[http://www.raaga.com/channels/hindi/movie/H001102.html](http://www.raaga.com/channels/hindi/movie/H001102.html)

--i guess the problem is in the totem player. Is there any way we can change the default player from totem to realplayer in mozilla?

--i dont need flashplayer for playing this. 

~~**~~

---

### Post by Safder on 2007-04-02
Hi ,

I am a new ubuntu user, just switched this weekend :) 
I was wondering whether you could tell me how you fixed the problem if you did fix the problem, 'cuz I listen to music from the same website too. However, I managed to install a real player plugin, so I dont get the error.All I get is the player with a message saying "Loading...", so I'd really appreciate it, if you could suggest me a solution:confused: :confused:

---

