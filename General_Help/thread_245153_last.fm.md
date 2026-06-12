---
title: "last.fm"
date: 2006-08-27
forum: General Help
---

### Post by Tarvok on 2006-08-27
I am interested in the last.fm service, and would like to know the best way to go about using that service in Ubuntu 6.06. I prefer using Rhythembox, but because I figured the simplest thing is to just go with whatever last.fm gave me, I downloaded their client.

The problem with that is that running qmake -v shows me using version 3.3.6, when the last.fm client requres version 4.

At any rate, if I can use Rhythembox instead, I would prefer that. I have noticed that there is an xmms plugin, so if there's no other way, I'll use that, but I would rather use Rhythembox, if possible.

---

### Post by kotnik on 2006-08-27
I use last.fm services fully with Amarok. You should try it.

---

### Post by hw-tph on 2006-08-27
I use [Quod Libet](http://sacredchao.net/quodlibet), a player similar to Rhythmbox written in Python. The last.fm plugin, [QLScrobbler](http://sacredchao.net/quodlibet/wiki/Plugins/QLScrobbler), works very well for me, using Quod Libet 0.23.

Håkan

---

### Post by mlind on 2006-08-27
I'm using Audioscrobbler with both Quodlibet and Rhythmbox (0.9.5). Both work without problems.

---

### Post by SishGupta on 2006-08-27
I use audacious which is a xmms/beep fork.

Download the unsupported xmms plugin from last.fm downloads
download the audacious source

compile the last.fm plugin
then compile audacious

---

### Post by Anonii on 2006-08-27
> **Tarvok said:**
> I am interested in the last.fm service, and would like to know the best way to go about using that service in Ubuntu 6.06. I prefer using Rhythembox, but because I figured the simplest thing is to just go with whatever last.fm gave me, I downloaded their client.

The problem with that is that running qmake -v shows me using version 3.3.6, when the last.fm client requres version 4.

At any rate, if I can use Rhythembox instead, I would prefer that. I have noticed that there is an xmms plugin, so if there's no other way, I'll use that, but I would rather use Rhythembox, if possible.

I was using Quod Libet, but recently changed to "Banshee" there is a plugin there  by default if you follow the guide on how to install it, that uses last.fm. Check the guide:
[http://ubuntuforums.org/showthread.php?t=202464&highlight=banshee+guide](http://ubuntuforums.org/showthread.php?t=202464&highlight=banshee+guide)
You probably dont care about the CVS version, if you just want last.fm.

---

### Post by Tarvok on 2006-08-27
I decided to give Quod Libet a try. It seems decent enough, and on the "Plugins" menu, I've checkmarked "QLScrobbler" and entered my username and password. Now what? Does it just automatically start sending data, or is there something else I need to do?

---

### Post by Shikai on 2006-08-27
I'm not sure what kind of functionality the other players actually give you, but Amarok rawks with last.fm. Amarok will play last.fm streams right from it's menu.

(I should probably mention that I'm using Amarok 1.4 from SVN. The version in Ubuntu's repos is 1.3.9, and I'm not sure if it supports last.fm streams from within the player)

---

### Post by mindtrick on 2006-08-28
> **Shikai said:**
> (I should probably mention that I'm using Amarok 1.4 from SVN. The version in Ubuntu's repos is 1.3.9, and I'm not sure if it supports last.fm streams from within the player)

Does anyone know the answer?

---

### Post by Perfect Storm on 2006-08-28
> **SishGupta said:**
> I use audacious which is a xmms/beep fork.

Download the unsupported xmms plugin from last.fm downloads
download the audacious source

compile the last.fm plugin
then compile audacious

That shouldn't be a problem anymore.
I compiled the Audacious (v.1.1.1) some weeks ago, it had last FM support build-in from scratch.

---

### Post by hw-tph on 2006-08-28
> **Tarvok said:**
> I decided to give Quod Libet a try. It seems decent enough, and on the "Plugins" menu, I've checkmarked "QLScrobbler" and entered my username and password. Now what? Does it just automatically start sending data, or is there something else I need to do?

If your have entered your last.fm username and password correctly and checked the Enable button it should work. Note that there are often delays in displaying on last.fm what you're playing. And in order not to display what you just skip past, the QLScrobbler plugin will send the song information when two minutes of playing the song have passed, or after half of the song - whichever comes first.


Håkan

---

### Post by SishGupta on 2006-08-28
> **Artificial Intelligence said:**
> That shouldn't be a problem anymore.
I compiled the Audacious (v.1.1.1) some weeks ago, it had last FM support build-in from scratch.

The only version of audacious that i have ever compiled was 1.1.1 and on a brand new ubuntu install there was no last.fm support w/o downloading the last.fm xmms plugin and "make installing" it.

i am a newb though so maybe i am mistaken.

---

### Post by Perfect Storm on 2006-08-28
> **SishGupta said:**
> The only version of audacious that i have ever compiled was 1.1.1 and on a brand new ubuntu install there was no last.fm support w/o downloading the last.fm xmms plugin and "make installing" it.

i am a newb though so maybe i am mistaken.

Just make sure that your have all the lib that are required.

You can try this: [http://www.filelodge.com/files/room38/1059449/Audacious.tar.gz](http://www.filelodge.com/files/room38/1059449/Audacious.tar.gz) it contains a fake .deb, so it can't help you with dependency.

---

