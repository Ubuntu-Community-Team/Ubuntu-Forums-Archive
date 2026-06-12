---
title: "Macromedia Flash Player"
date: 2005-03-28
forum: General Help
---

### Post by xNight Wraithx on 2005-03-28
Okay! I've went to the Mozilla Plug-in Faq, the Linux Plug-in Faq and scoured the forums. I downloaded gpl as well as Flash player from it's own "For Linux" site. I tried to go into the terminal and inputting different scores and I can't figure it out. If you can't tell, I have no programming background so this is interesting for me. Thanks in advance again.

Also...what is the difference between x86, SPARC, Alpha and PPC and will any of these work with ubuntu?

---

### Post by kassetra on 2005-03-28
[QUOTE=xNight Wraithx]Okay! I've went to the Mozilla Plug-in Faq, the Linux Plug-in Faq and scoured the forums. I downloaded gpl as well as Flash player from it's own "For Linux" site. I tried to go into the terminal and inputting different scores and I can't figure it out. If you can't tell, I have no programming background so this is interesting for me. Thanks in advance again.

Also...what is the difference between x86, SPARC, Alpha and PPC and will any of these work with ubuntu?[/QUOTE]

Hi!  Are you trying to get the flash *player* to work and show you flash movies on the web, or are you trying to write flash script / action script code?

---

### Post by xNight Wraithx on 2005-03-28
I am trying to get Flashplayer and also Shockwave somehow. Especially Shockwave because that is what America's Army uses for its website. I think that I have Flash though. This is what I did:


$ sudo apt-get install flashplayer-mozilla
 
and it ran so I think that I have it

---

### Post by DJ_Max on 2005-03-28
> Also...what is the difference between x86, SPARC, Alpha and PPC and will any of these work with ubuntu? 
You need to know a bit about computers, these are Architectures.
x86 = Intel, AMD
SPARC = Sun's processors
PPC = IBM's POWER, Apple mac's.
I forget what Alpha's.

I think flashplayer-mozilla is just the mozilla plugin, I may be wrong.

---

### Post by lukem on 2005-03-28
I also installed the Plugin through Mozilla and the apt get install mozilla flash player.  I am able to see the animation ok, but do not get the sound to go along with it.  Any suggestions?

Thanks
Luke

---

### Post by kassetra on 2005-03-28
[QUOTE=xNight Wraithx]I am trying to get Flashplayer and also Shockwave somehow. Especially Shockwave because that is what America's Army uses for its website. I think that I have Flash though. This is what I did:


$ sudo apt-get install flashplayer-mozilla
 
and it ran so I think that I have it[/QUOTE]

if you can go to [http://www.macromedia.com](http://www.macromedia.com) and see moving images, you've got flash installed just fine.

At this time, however, there is no known Linux version of the shockwave player.  :(

---

### Post by kassetra on 2005-03-28
[QUOTE=lukem]I also installed the Plugin through Mozilla and the apt get install mozilla flash player. I am able to see the animation ok, but do not get the sound to go along with it. Any suggestions?

Thanks
Luke[/QUOTE]

Can you hear anything else?  The Ubuntu startup sound, for instance, after you log in.

---

### Post by lukem on 2005-03-29
Yes, all other sound functions appear normal.  Gnome startup,  dvd playback and Audacity (if I kill esd first) all have good sound.  I haven't actually tried to play a cd or mp3 since I upgraded to hoary however.
Thanks

---

### Post by kassetra on 2005-03-29
[QUOTE=lukem]Yes, all other sound functions appear normal. Gnome startup, dvd playback and Audacity (if I kill esd first) all have good sound. I haven't actually tried to play a cd or mp3 since I upgraded to hoary however.
Thanks[/QUOTE]

Eh... have you tried asking about this in the Hoary sections?  Because normally I would say that killing esd is a bad thing for your flash sound output...

---

### Post by Xeon3D on 2005-04-06
I got no sound as well :(

Everything else plays fine.. but there is no sound on Flash files...

Please help :D

Edit:

As I found on other topic, it seems that this fixes the flash sound problems. I'm gonna test it now. :D \\:D/

---

