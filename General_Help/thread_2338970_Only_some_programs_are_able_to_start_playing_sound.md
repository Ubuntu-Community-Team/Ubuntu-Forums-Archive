---
title: "Only some programs are able to start playing sound"
date: 2016-10-03
forum: General Help
---

### Post by snufk1n on 2016-10-03
Hi! 

I recently ugraded from 15.10 (I think) to 16.04, and now I have stumbled upon a mysterious audio problem.

I can't start a song neither using mpd nor Spotify when no sound is playing on my computer. Nothing happens, even though the progress bars show that the songs are playing. If I however open a movie using VLC, the sound plays flawlessly. I can't get VLC to play the songs either though. 

**Now, here's the strange part:**

If I open a movie using VLC (which plays the audio just fine), and then start a song using either mdp or Spotify before I stop/pause VLC, the song is heard as well. If I stop/pause VLC, the songs continue to play. 

What is happening? 

I've used Linux on a daily basis for 7 years or so now, but I don't even know where to start troubleshooting this problem. 

Here's some other random information that might shine some light on the problem:

 
[LIST]
[*]When the songs are playing, I can't stop and play it again. Then I 
[*]have to go through the whole process again. 
[*]Firefox can play sounds seemlingy random. The same webm/Youtube video works some times, but not others. 
[*]In the "Test Sound" application found in the sound settings, I ALWAYS have to press two times to hear the first "Front center"/"Front left"/etc after having tried playing a song. When the first test sound is succesfully played, the others work on their first tries. 
[/LIST]
 
Ask me for logs, and I'll give you them. I don't know which ones are relevant.

---

### Post by ajgreeny on 2016-10-03
Do spotify and mpd both use pulseaudio or some other sound service by default, such as jack?
Is there a configuration setting available to make them use pulse?

With pulseaudio you should be able to have as many applications as you wish all playing simultaneously, as far as I'm aware, but other sound systems are not so forgiving and tend to keep everything to one application.  I've never used jack as far as I'm aware, so I may be totally wrong about this, but I do remember reading about the problem in the past.

---

### Post by snufk1n on 2016-10-04
As far as I know (and I've just been googling it to verify), both Spotify and mpd uses pulseaudio by default. 

The problem isn't that the applications can't play simultaneously, it's that only some applications "enables" audio output through my speakers. When I've got the audio working (using the hack in OP), I can play how many sounds at the same time.

---

### Post by snufk1n on 2016-10-04
I thougth it might be an upgrade problem, so I did a fresh install (16.04.01 server, and then installed ubuntu-desktop), but all to no avail. The problem still exists. I still can't start playing audio from most applications unless there's already another application playing audio.

---

