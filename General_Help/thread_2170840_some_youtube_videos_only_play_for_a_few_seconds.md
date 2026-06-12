---
title: "some youtube videos only play for a few seconds"
date: 2013-08-27
forum: General Help
---

### Post by Kojak Peg on 2013-08-27
Hi Everyone 
I wasn't sure were to put this one, I'm having some trouble with youtube videos, and it's only just started happening. Youtube is playing some videos without any problems, but with others it's only playing a few seconds worth (typically 30 seconds). And when I used windows xp it worked no problem, so it's not youtube playing silly bugger 

I've got Ubuntu restricted extras installed, and when I checked for adobe flash updates it said, "chrome users don't have to download new versions". So the only other thing I can think of is that clamtx found a virus the other day, I deleted it, but I'm now wondering if it could have something to do with that, but I honestly have no idea  
 
Thanks for the help

p.s.

I'm a novice linux user so please explain everything to me as if you were talking to a small child :)

p.p.s.
even though flash said there was no need to download new versions for chrome, I thought I'd give it a go. So I tried installing libflashplayer.so on the command line and got this message

sudo apt-get install libflashplayer.so
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libflashplayer.so
E: Couldn't find any package by regex 'libflashplayer.so'

I've also installed, sudo apt-get gnash, disabling hardware acceleration and tried the flash-aid, which is no longer available. 

{SOLVED}
I've solved the problem and it was so simple... all I had to do was clear my browser history (didn't realise it had been so long)

---

