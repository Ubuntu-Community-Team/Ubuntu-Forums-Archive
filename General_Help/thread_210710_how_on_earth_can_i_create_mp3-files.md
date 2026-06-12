---
title: "how on earth can i create mp3-files?"
date: 2006-07-07
forum: General Help
---

### Post by eewald on 2006-07-07
how on earth can i create mp3-files with dapper? sound-juicer only knows about .ogg and .flac... 

and you may call me dumb, but i can not figure out how to make mp3c encode to . mp3 instead of .ogg. 

](*,)

---

### Post by matthew on 2006-07-07
It is possible. You will want to start with this wiki page.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

After reading it you will understand why you can't do it by default as well as know how to enable the ability.

---

### Post by raldz on 2006-07-07
You may use K3B to rip an Audio CD into MP3..just be sure you have the "lame" package and the "libk3b2-mp3" package installed through the repos.. Then just insert in your Audio CD and open K3B.. by selecting your CD, you will find the "Audio CD" window, in that same window, the first tiny icon on the left is for ripping CDs.. click that icon, a window will appear listing the tracks to be ripped, at the bottom of that window, choose MP3 Lame as your audio format.. ;) ;)

---

### Post by eewald on 2006-07-07
thanks for your help. 

but still: i understand completely legal reasons behind not including mp3-support in standard distribution. that was not my problem. 

the problem is that enabling ripping cd-s to only format supported by all portable players is made to a usability nightmare. 

i should write a cryptic "audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1001" to a tiny-tiny dialog box to enable it!? in 2006!? 

i admit that is a rant, but not aimed at you. thanks for help.

edit: 
i was talking about sound-juicer. using k3b in gnome environment is comparable usability nightmare.

---

### Post by FredB on 2006-07-07
You can also use grip + lame. It found it to work better than SoundJuicer !

---

