---
title: "SiS 7012 Audio Driver Install"
date: 2006-09-01
forum: General Help
---

### Post by JonasE on 2006-09-01
I am brand spankin' new to Ubuntu and am tired of fooling around on Linux without my music blasting.

I have installed mp3 codecs and what-not and have a player that I know it working but I am not getting anything out of my speakers.

I just formatted and put xp pro onto one partition and then Ubuntu onto the other and I have the drivers installed for xp, so now I just need to get them for Ubuntu but the regular install file doesnt work so I heard something about having to recompile the kernel, but that stuff is way over my head right now cause im so new. Does anyone know what I need to do in order to get some sound and make it easy to understand for a first time Linux user.

Thanks in advance.

Jonas.

---

### Post by senuxis on 2006-09-01
[LIST=1]
[*]on the top right corner of your desktop should be a speaker icon. right-click on it. [IMG]http://static.flickr.com/72/230947715_7934b72477.jpg?v=0[/IMG]
[*] 
[*]click on "Open Volume Control" and a window should appear. [IMG]http://static.flickr.com/81/230947717_896778c198.jpg?v=0[/IMG]
[*]
[*]enable "Master Surround" by clicking on the speaker icon that is underneath it's scroll bar. Also, move the scroll bar to about half-way up the bar. Then, choose "Edit" --> "Preferences". [IMG]http://static.flickr.com/95/230947718_69b0d037d2.jpg?v=0[/IMG]
[*]
another window should popup. in this window, scroll down to the bottom. [IMG]http://static.flickr.com/67/230947719_050b2d1506.jpg?v=0[/IMG]
[*]
choose "Spread Front to Surround and Center/LFE" by selecting the box that's next to it. [IMG]http://static.flickr.com/96/230947722_d27a342b4e.jpg?v=0[/IMG]
[*]
close all the windows. you should now have sound.
[*]
open your music file with VLC and you music should come forth (it may not be blasting out though) 
[/LIST]

---

### Post by JonasE on 2006-09-01
Thanks for the reply, but im sorry to say that my music was not blasting, nor was it even twitching. I followed your very nicely layed out explanation to the dot and wasnt able to get anything coming out of my speakers. I am pretty sure that they are plugged in because I can get sound in Win XP.

Any more suggestions?

---

### Post by senuxis on 2006-09-01
Go to the window where you had enabled "Spread Front to Surround and Center/LFE" and then enable "PCM" and "Channel Mode" as well, you should then see a PCM scroll bar appear next to the "Master Surround" scroll bar. **[COLOR="Red"]Then, repeat [COLOR="Black"]_[B]step 3**_[/COLOR] for the "PCM" scroll bar[/COLOR][/B]. [COLOR="Blue"]**Then click on the "Options" tab and then change the channel mode to "4ch"**[/COLOR].

---

### Post by JonasE on 2006-09-03
Thank you very much for the help - I messed around a little more with those settings you just mentioned and figured it out.

---

