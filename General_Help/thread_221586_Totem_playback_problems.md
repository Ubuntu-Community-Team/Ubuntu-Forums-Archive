---
title: "Totem playback problems"
date: 2006-07-23
forum: General Help
---

### Post by morningblur on 2006-07-23
Hi everyone, I don't ever know how to start these topics, so I'll just get into it:

I've been having a problem with Totem's playback of videos lately. It is odd, when i first log into my computer the video plays back fine. All the colors are correct, etc. As soon as i try and play a second video, the colors go instantly weird (completely over-saturated, an odd blue tint, and other general unwatchable weirdness). If i log out again and then return, the first video i play plays fine, but the second video onward still doesn't. Messing with the options in totem doesn't work either.

I have Totem-xine installed as gstreamer seems to hate me (does not support practically any video formats i want to play) and I like using totem as both mplayer and vlc don't allow me to skip ahead within the video the way I like.

I've atached a screenshot with a visual aproximation of the problem (please note this isn't an actual screenshot of the problem, as videos don't screen-cap well.)

Any help anyone can give me is greatly appreciated.

---

### Post by mllr on 2006-07-23
did you try to reinstall it?

---

### Post by morningblur on 2006-07-23
Yeah, I did. Only thing that will temporarily fix it is logging out. I installed gstreamer, and oddly, the formats it refused to play (or even render a thumbnail for) now work. Which is odd. Using gxine media player also now works, which is even odder.

---

### Post by JcZndeR on 2006-08-03
I have a similar problem except it seems that it happenes on all my apps and only the local files not the stuff i play off the internet via mplayer..
My videos look like they are old and blury.

edit: It seems that my problems are not too similar after all.  Mine just has a light blue tint that shows over every video and makes ppl look like aliens (Its not really a blue tint but it makes skin look blue).  And restarting x or anything else doesnt seems to work.  However like i stated if its a online file it seems to..   O yeah and this happened recently

---

### Post by Toufik on 2006-08-03
I've got exactly the same : [http://www.ubuntuforums.org/showthread.php?t=212611](http://www.ubuntuforums.org/showthread.php?t=212611)

But no solution for the moment (didn't yet try the new version of totem).

Tip: the problem only occurs when you re-open totem.  Keep it open while changing video!

---

### Post by beercz on 2006-08-06
I have exactly the same problem.  I have just changed laptops (now got an HP/Compaq nx7400) and since then I have had this Totem problem (same occurs with other media players too).

Everything worked fine on my previous laptop (Acer 2300cxi).

Don't know why though.

Anyone any ideas?

---

### Post by beercz on 2006-08-06
> **beercz said:**
> I have exactly the same problem.  I have just changed laptops (now got an HP/Compaq nx7400) and since then I have had this Totem problem (same occurs with other media players too).

Everything worked fine on my previous laptop (Acer 2300cxi).

Don't know why though.

Anyone any ideas?
Think I have solved this.  As a root, using the universe repositories, I did this:

apt-get install xserver-xorg*
apt-get install ubuntu-desktop

However SuperMike deserves the credit, not me.  His post (#2) in this [thread]("http://ubuntuforums.org/showthread.php?t=209265") sovled the problem for me. :-)

---

### Post by JcZndeR on 2006-08-08
Will try.
Altho my internet isn't fast enough to download ubuntu-desktop quickly.  Probably will have to try a few times.
This sucks..
lol
Thanks

---

### Post by JcZndeR on 2006-08-17
I couldn't get it installed cuz of sucky internet but I seemed to have found the reason for it doing this.  Although I don't know about you guys but apparently my video only looks funny after I run the totem movie player so if I never run it and just use Mplayer everything is fine.  And when I do run it I just reboot and open it with Mplayer.  I think totem screws up the session.  I am going to make Mplayer default now.  I like it better anyways :D .

---

### Post by rudlavibizon on 2006-09-05
](*,)

---

### Post by kenny1948 on 2008-06-16
I am having this same problem with ALL PLAYERS! It is driving me nuts:mad:

However it does this even when I first open it. Is there anyway to adjust saturation, color, brightness etc 

I am using Kubunt. Thought this was a problem with Kaffeine, but it is the same in all players I have installed.

---

