---
title: "Quod Libet and Album Covers"
date: 2006-11-05
forum: General Help
---

### Post by urukrama on 2006-11-05
I've playing around with Quod Libet the last few days, and like it. 

From screenshots by other QL users (and from the QL website) it seems it is possible to add the album covers to the player, just like in many other media players. 

I've been trying to do this, but haven't been very succesful. I just can't find an option to add album covers (like in Amarok or Exaile), and they don't appear by default.

I have the QL plugins installed, but couldn't find an option there.

Can anyone help?

---

### Post by bonzodog on 2006-11-05
It is controlled from a specific plug-in that downloads album art from Amazon.com. It seems that you need this plug-in, and by browsing the directories, you can maybe see where it stores the album art, but I believe it's inside ~/.quodlibet/. Not sure how it does it, though.

---

### Post by hugmenot on 2006-11-05
If you have the quodlibet-plugins package installed you just need to enable the plugin. It is already in place.
To download covers select an album an then right-click it to use the plugin from the menu.
If you have covers for albums already just drop them next to the mp3s. The name of the images must contain "cover", "front", or "folder". The most common name for covers is folder.jpg

---

### Post by urukrama on 2006-11-05
Hmm. What is that plugin called? I can't find it in the plugin menu. I use QuodLibet 0.18.

From what you said it seems that I wouldn't be able to add custom album covers (like Amarok and Exaile), which I would want to do fairly often. Is that correct?

---

### Post by hugmenot on 2006-11-05
> **urukrama said:**
> Hmm. What is that plugin called? I can't find it in the plugin menu. I use QuodLibet 0.18.

From what you said it seems that I wouldn't be able to add custom album covers (like Amarok and Exaile), which I would want to do fairly often. Is that correct?

QL 0.18 is really old. Which Ubuntu version do you have?
There are newer packages for [Dapper]("http://www.ubuntuforums.org/showpost.php?p=1240418&postcount=69") and [Edgy]("http://www.ubuntuforums.org/showpost.php?p=1572548&postcount=126").

Once you got that it should appear in the list. See the screenshot.

Oh and you /can/ add custom album art. Just drop the image file into the appropriate folder

1.mp3
2.mp3
3.mp3
4.mp3
5.mp3
folder.jpg 

or "greatest hits front.jpg" or whatever

---

### Post by urukrama on 2006-11-05
> **hugmenot said:**
> QL 0.18 is really old. Which Ubuntu version do you have?


I use Dapper. The version I have installed is the one from the repos. Some time ago I installed 0.23 (the latest version, afaik), but then couldn't find the appropriate plugins for them. The once in the repos only went with 0.18, and I couldn't find them anywhere else.

I'm also not too fond of having a long source list with extra repos just for one application each, so I downloaded QL 0.23 from the Ql site.

But 0.23 looked very much like 0.18, and I couldn't see any added features. Are the changes only in terms of stability and bug removal?

> 
Oh and you /can/ add custom album art. Just drop the image file into the appropriate folder


Thank you, that worked fine. I had them in the right folder, but didn't rename them to 'cover' or 'folder'. It works now.

I just came accross Quod Libet recently, and am now deciding whether I'll stick with it or use Exaile (instead of Amarok, which I've used so far).

---

### Post by hugmenot on 2006-11-05
> **urukrama said:**
> I'm also not too fond of having a long source list with extra repos just for one application each, so I downloaded QL 0.23 from the Ql site.


The repo is there because people seem to prefer it that way. There&#8217;s no hassle with dependencies etc pp. There&#8217;s acutally no problem with removing the source after installing. I comment unnecessay lines out in the sources.list. For sure entering a line in that list is faster than installing from source.
Oh and there have been plenty of new features and bugfixes since. They might not be apparent from a superficial glance but they are very useful.

---

### Post by urukrama on 2006-11-06
Thanks for all the help. 

It seems like I will go for Exaile in the end, though. I quite like Quod Libet (which makes it hard to decide), but it just is a bit too complicated to switch between viewing your playlists, your albums, artists, or just files. In Exaile you can access those by clicking on a tab, in QL I have to go through the menu and select what view I want, and then select whatever playlist/album/file I want to play.

Quod Libet is a great player and has a good look, but it doesn't quite do what I want it to do. A pity... :(

---

### Post by hugmenot on 2006-11-06
Dilemmatic. It looks good because it doesn&#8217;t put crap all over the place. But then you want the crap occasionally, or even often. Personally I use album list all the time, unless I need to queue stuff, then I push my global shortcut to open an extra find browser, type, type, Q, Q, Q, done, close.

Another case, no slider for song position permanently on the screen. Hm, that&#8217;s bad, but do I need it often? ... No.

---

### Post by urukrama on 2006-11-06
> **hugmenot said:**
> Another case, no slider for song position permanently on the screen. Hm, that&#8217;s bad, but do I need it often? ... No.

I actually like that! I think it is neat.

But I do often move between playlists, artists and files, and that is a bit difficult. 

I might stick with it in the end. I still like its basic layout better than Exaile.

---

