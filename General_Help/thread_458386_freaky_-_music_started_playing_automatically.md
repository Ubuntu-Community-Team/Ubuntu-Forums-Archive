---
title: "freaky - music started playing automatically"
date: 2007-05-29
forum: General Help
---

### Post by vav on 2007-05-29
I was just working on my computer. Firefox etc. The phone rang and I left my desk for 10 seconds, and suddenly music started playing! one of the songs in my collection!

I use amarok. in combination with media keys (inspiron 9300), so I thought that had malfunctioned. But amarok wasnt running! 

I finally found a rogue "mpg123 -y -q" process running. I NEVER use mpg123. killed it and the music stopped.

Why could this have happened? Is my system compromised or buggy?

---

### Post by earobinson on 2007-05-29
have you ever messed with using cron jobs to set up an alarm clock or something?

---

### Post by reclusivemonkey on 2007-05-30
Did you have one of your music folders open? When you hold your mouse over an mp3 file, it will automatically preview using mpg123.

---

### Post by earobinson on 2007-05-30
> **reclusivemonkey said:**
> Did you have one of your music folders open? When you hold your mouse over an mp3 file, it will automatically preview using mpg123.
Cant seem to get that to work for me :(

---

### Post by reclusivemonkey on 2007-05-30
It might be mpg321 ;-)

You're not accessing these mp3s over a network connection are you?

I've had some problem with this in the past, but I think it was down to Ubuntu not having the mp3 codecs by default. Remember to restart nautilus if you have to install one of the command line mp3 players with

```

killall -9 nautilus

```

---

### Post by earobinson on 2007-05-30
nope I got the codecs, had them for ages and they are on my local HD, hover the mouse over the icon all I will and the icon gets the little music icon but no sound plays

---

### Post by reclusivemonkey on 2007-05-30
> **earobinson said:**
> nope I got the codecs, had them for ages and they are on my local HD, hover the mouse over the icon all I will and the icon gets the little music icon but no sound plays

Hmm, don't know what to suggest? Its definitely mpg123 as I am at home now and just checked it.

---

### Post by earobinson on 2007-05-30
weird, all the options are on in nautilus.

---

### Post by reclusivemonkey on 2007-05-30
> **earobinson said:**
> weird, all the options are on in nautilus.

Have you checked mpg123 will work from the CLI?

---

### Post by vav on 2007-05-30
The auto-play on mouse-over stopped working at some point while installing/uninstalling/upgrading. Maybe it's dormant... well at least now I know its not Tom Petty using his guitar to get into the network :P it was one of his songs.

---

### Post by babs51 on 2007-06-05
Hello, 
I had this happen as well.  I recognized the background music from some kids games that had been played earlier.  The game was not open when the music started playing.  
Strange.

---

### Post by Fireblend on 2007-06-05
Woah, I just tried out that hover-mouse-over-file and it worked! How did I not know this? XD

---

### Post by earobinson on 2007-06-07
I want mouse hover over :(

---

### Post by Subban on 2007-06-07
> **earobinson said:**
> I want mouse hover over :(

If I recall correctly try this:

```
sudo apt-get install mpg123-esd
```

---

### Post by FuturePilot on 2007-06-07
Hmmm. I had the mouse over preview working and now it won't work anymore. I have everything install too. mpg123, correct codecs, etc. It used to work.:(

---

### Post by FuturePilot on 2007-06-07
> **Subban said:**
> If I recall correctly try this:

```
sudo apt-get install mpg123-esd
```

Wait never mind. That fixed it. Thanks!:D

---

### Post by screaminj3sus on 2007-06-07
> **Subban said:**
> If I recall correctly try this:

```
sudo apt-get install mpg123-esd
```

Thanks I remember this feature form PClinuxOS, great now that I have it working in ubuntu.

---

### Post by chickendude on 2008-04-17
The auto-play on my computer used to work, and i really enjoyed it. Somehow over the course of time it just disappeared... What settings do i need to ensure that it functions? I've tried turning ESD on/off, have mpg123-alsa and mpg123-esd installed, and have the preview feature on also (and i've tried a few different files, ogg, wav, and mp3).
Thanks!

---

### Post by marufaberlin on 2008-04-17
I think there's a setting somewhere... Just don't know where, just got a blackout... gconf, nautilus or something else. You can set up which file types to preview, including sound files.

---

### Post by chickendude on 2008-04-18
Are you talking about the System -> Preferences -> File Management -> Preview tab? I've turned that on and i believe installed all the right files, i'm not quite sure what it is that i'm missing, heh.

---

### Post by marufaberlin on 2008-04-19
k dunno then :-s

---

### Post by chickendude on 2008-04-23
Heh, well thanks anyway :)

---

