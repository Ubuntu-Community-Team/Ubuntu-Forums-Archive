---
title: "Audacious Plays Too Low!!!"
date: 2008-05-17
forum: General Help
---

### Post by Trueno22 on 2008-05-17
I was listening to music on audacious just now.  Was bored so I decided to open the same mp3 in Totem.  The sound output doubled which I initialy attributed 2 players = double the sound.  I turned off audacious and the sound level didn't decrease one bit.  So I turned off Totem and then reopened the mp3 with totem and got the same nice loud bassful playback.  Is ther anythng I can do to get audacious to play mp3's as loud as totem.

---

### Post by linkdesink on 2008-05-19
I have the same problem with you.I cant found any solution about that.Exaile, rhythmbox,amarok plays my music loud but i like audacious and i want to use it.

---

### Post by bogdan_5844 on 2008-06-01
i found a solution :-D

Using pulse audio,go to prerefernces -> audio and set these:

Buffer Size:3500
Sampling Rate [Hz] 95000

Check "Bypass all signal processing if possible" and "Use software volume control".The output bit depth should be 16 bit.

Here's a screenshot:

[[IMG]http://img230.imageshack.us/img230/3876/screenshotnl8.th.png[/IMG]](http://img230.imageshack.us/my.php?image=screenshotnl8.png)


Hope it works for you ;-)

---

### Post by rasheid2kx on 2008-12-03
My songs weren't playing any at all. This is what i did.
Max out speakers
Max out volume control on Audacious
Load a song and press play.

go to prefrences > audio
select a audio plugin
(Audacious will restart the song after selecting a plugin... wait bit... if you dont hear the song select a different plugin and repeat the process until you do.... Jacks output usually works)

if the Volume is to low do this adjust Preamp and the Default Gain above the negative value to your liking.

Prefrences > Replay Gain

Preamp: 0.1
Default Gain: 5.0(or adjust accordingly)

---

### Post by toufel on 2009-01-15
For some reason the default gain setting in a fresh audacious install is set to -9! Either disable Replay Gain or change the setting to 0 (Under the Replay Gain Option in Audacious Preferences).

---

### Post by _shak_ on 2009-01-26
it worked like a charm ! Thanks a lot for your help toufel , i've been searching for a way to make the output louder with audacious but i've never expected the solution to be so simple . I've changed the Default Gain from -9.00 to 0.00 and it works fine , just like the other media players (amarok , totem )

---

### Post by Fancycakes on 2009-10-19
> **rasheid2kx said:**
> My songs weren't playing any at all. This is what i did.
Max out speakers
Max out volume control on Audacious
Load a song and press play.

go to prefrences > audio
select a audio plugin
(Audacious will restart the song after selecting a plugin... wait bit... if you dont hear the song select a different plugin and repeat the process until you do.... Jacks output usually works)

if the Volume is to low do this adjust Preamp and the Default Gain above the negative value to your liking.

Prefrences > Replay Gain

Preamp: 0.1
Default Gain: 5.0(or adjust accordingly)

This worked perfectly, grazie molto. Although I must say 5.00 seems pretty high when 0 is normal. =/

---

