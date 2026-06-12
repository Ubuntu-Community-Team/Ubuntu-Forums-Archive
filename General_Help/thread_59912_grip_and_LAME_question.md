---
title: "grip and LAME question"
date: 2005-08-25
forum: General Help
---

### Post by escobar on 2005-08-25
Looking for something to replace EAC in Ubuntu.

I recently installed Grip and LAME, both through Synaptic. Problem is trying to rip mp3's. What I did is set the encoder executable path as /usr/bin//LAME, and set the encoder command line as --alt-preset extreme. After the CD rips, it creates mp3's about 128k or so large. These of course do not work, trying to play them, there is no sound, and the track last all of a second, so I am assuming that some of my options are wrong.

Anyone able to provide any insight?

---

### Post by glug101 on 2005-08-26
> After the CD rips, it creates mp3's about 128k or so large. These of course do not work

Of course, but I'm sure they encode in lightning time :)

Ok, I told myself that I was too busy to meddle for the next week or so, but this one has me interested.  Have you tried using lame on the command line?  What kind of output do you get?

If you can, try ripping to a WAV file or something from grip and then encode it manually with lame. (pick a short track so you'll get instant satisfaction ;) )  

Hope this helps:)

---

### Post by escobar on 2005-08-26
Bump.

Hate to sound ungrateful but I'm not to good with the command line. Would anyone be able to post the settings they use in grip (LAME)? Specifically the settings under the "rip" and "encode" tabs. Would be highly appreciated. Thanks.

---

### Post by glug101 on 2005-08-26
[QUOTE=escobar]Bump.

Hate to sound ungrateful but I'm not to good with the command line. Would anyone be able to post the settings they use in grip (LAME)? Specifically the settings under the "rip" and "encode" tabs. Would be highly appreciated. Thanks.[/QUOTE]
 I hate to sound like a snooty techie, but better lame documentation than I can give you is found by typing: > man lame

The command line switchs listed here are the settings you type into grip for lame.  

I wanted you to run lame on the command line because there is possibly something broken with your lame installation.  Good luck diagnosing it without the command line.

---

