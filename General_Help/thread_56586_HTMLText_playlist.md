---
title: "HTML/Text playlist"
date: 2005-08-13
forum: General Help
---

### Post by Caboose on 2005-08-13
I'm looking for somthing that can generate a playlist a la WinAmp.

I need to create a list of my songs, just the names of the songs, no more information than that, in a numbered list.

Is there anything out there?

---

### Post by egon spengler on 2005-08-13
Tagtool is a program I find useful. It can tag and rename mp3s and create playlists.

If all that you need is a playlist and nothing more though then try this

```
find / -iname '*.mp3' > playlist.m3u
```

That will make a playlist with every mp3 on your system. Of course you can alter the search path and the search string to suit your needs

---

### Post by H.E. Pennypacker on 2007-01-06
I was trying to do the same thing, and luckily, I had everything I already needed.  If you're trying to create a playlist in .m3u format, do the following.

1.  Open up an application such as Audacious (or probably any XMMS derivative).

2.  Go to "Add" and open all files you'd like in that playlist.

3.  If you're using Audacious, you can do Shif-S to save the playlist.  Then browse to your desired location, give the list a name, and end the name with .m3u.  If you're using another audio player, it should work like this, especially if its based on XMMS.

There you go.  The m3u list is now where you saved it.  Good luck!

---

### Post by finer recliner on 2007-01-06
do you want to save a playlist of all your songs or just a normal list of all your songs (in a txt document)??

if you want the latter, you can write a short shell script to do it :)

---

