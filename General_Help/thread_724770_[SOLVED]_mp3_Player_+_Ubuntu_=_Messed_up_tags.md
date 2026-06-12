---
title: "[SOLVED] mp3 Player + Ubuntu = Messed up tags"
date: 2008-03-14
forum: General Help
---

### Post by jessika-kaos on 2008-03-14
I bought a cheapie mp3 player and have noticed that none of the artist or track titles display correctly on mp3s that I have transferred. The player just shows chinese characters/boxes (which, I imagine, is not how it is supposed to appear). I am assuming that there is some sort of character encoding conflict? Any suggestions?

---

### Post by gobbles414 on 2008-03-15
> **jessika-kaos said:**
> I bought a cheapie mp3 player and have noticed that none of the artist or track titles display correctly on mp3s that I have transferred. The player just shows chinese characters/boxes (which, I imagine, is not how it is supposed to appear). I am assuming that there is some sort of character encoding conflict? Any suggestions?

It's difficult to help you without more details. Please tell us: What brand and model number of MP3 player are you using? What music manager are you using in Ubuntu -- Rhythmbox, Banshee, other? What procedure are you using to transfer your music to your MP3 player?

---

### Post by jessika-kaos on 2008-03-15
Sorry, it's a Centon 1GB player. I use Amarok, but did not use that for writing the ID3 tags or for transferring he files (I just copied the files onto the device via Nautilus).

---

### Post by gobbles414 on 2008-03-15
> **jessika-kaos said:**
> Sorry, it's a Centon 1GB player. I use Amarok, but did not use that for writing the ID3 tags or for transferring he files (I just copied the files onto the device via Nautilus).

Since you're just copying your existing music, it sounds to me like the problem is with the music files themselves. I've never used Amarok. But it looks like a nice program. Can you use Amarok to transfer your music to your MP3 player? I know that both Rhythmbox and Banshee can "transcode" music into formats that are more friendly for your MP3 player -- at least with iPods. So I would imagine that Amarok can do something similar.

Does this help?

---

### Post by jessika-kaos on 2008-03-15
Figured it out. After some searching I came upon a similar problem and someone had suggested using Easytag to rewrite the ID3 tags, It gives a choice of saving in UTF-8 or other formats. I resaved them as Western (ISO-8859-1) and now they show up.

---

### Post by gobbles414 on 2008-03-15
> **jessika-kaos said:**
> Figured it out. After some searching I came upon a similar problem and someone had suggested using Easytag to rewrite the ID3 tags, It gives a choice of saving in UTF-8 or other formats. I resaved them as Western (ISO-8859-1) and now they show up.

Glad that you're problem has been solved!

---

