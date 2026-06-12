---
title: "why does audacious not read mp3 info correctly?"
date: 2017-07-15
forum: General Help
---

### Post by ardouronerous on 2017-07-15
I'm looking for a lightweight media player to manage my mp3 collection, and a lot of users recommend Audacious, but I'm not getting a very good experience with it, a lot of my mp3 files aren't being read correctly, like song title, artist and album are blank, and when I tried to add the info manually nothing happens.

Can anyone tell me how to fix this issue or suggest another lightweight media player?

I've tried CMUS, I didn't like it.

---

### Post by TheFu on 2017-07-15
I use easytag to manage audio file tags.
Players are a different thing entirely - at least for me.  I tend to use mpv or mplayer with a playlist as input. THAT is minimal. ;)

---

### Post by Dennis N on 2017-07-15
I also use easytag. Easytag will even offer to repair any miscoded tags you might have when it loads a folder of music files. Otherwise, I haven't seen any errors in displaying song information in audacious and I have been using it for years.

---

### Post by ardouronerous on 2017-07-15
Can easytag help me with Audacious?

I have GNOME MPlayer installed, I use it as my default video player, but it doesn't do well with large collections though, it doesn't exit after I used it on my 6GB mp3 collection, so I had to use Task Manager to force it to exit.

> **Dennis N said:**
> I also use easytag. Easytag will even offer to repair any miscoded tags you might have when it loads a folder of music files. Otherwise, I haven't seen any errors in displaying song information in audacious and I have been using it for years.

Well, I don't know why Audacious doesn't work for me, when I try to edit the song information, I get a save error message.

---

### Post by Dennis N on 2017-07-15
I just tested editing in the Audacious "Song Info" window, and that worked ok for me. Is it possibly a write permissions problem on the music file? Otherwise load the music file in easytag and see if editing works there, and also see if it offers to correct a miscoded tag.

My audacious version is 3.8.2

---

### Post by mc4man on 2017-07-15
If the id3 tags on your mp3's are poorly done then audacious won't be able to read or edit. 
You could try opening a folder of them in easytag & see if it reports 'Error reading id3 tag'
If so then fix the tagging.
(- I've one such mp3 here. Simply by doing a stream copy with ffmpeg it then could be edited.

---

### Post by ardouronerous on 2017-07-15
> **Dennis N said:**
> I just tested editing in the Audacious "Song  Info" window, and that worked ok for me. Is it possibly a write  permissions problem on the music file? Otherwise load the music file in  easytag and see if editing works there, and also see if it offers to  correct a miscoded tag.

My audacious version is 3.8.2

> **mc4man said:**
> If the id3 tags on your mp3's are poorly done then audacious won't be able to read or edit. 
You could try opening a folder of them in easytag & see if it reports 'Error reading id3 tag'
If so then fix the tagging.
(- I've one such mp3 here. Simply by doing a stream copy with ffmpeg it then could be edited.

Okay EasyTAG helped a lot, almost all of my mp3s are labeled correctly on Audacious, and those with errors I was able to save successfully within Audacious.

Thanks for the help guys :)

What made tags on my mp3 files poorly done? Most of my mp3 files are really old, like from 2002 and upwards, can old age be a factor?

And also, why does this happen on Audacious and not on other media players like GNOME MPlayer? GNOME MPlayer read my tags just fine before I applied EasyTAG.

> **Dennis N said:**
> My audacious version is 3.8.2

How did you get version 3.8.2?

I'm running Xubuntu 16.04 LTS and the version available in the repos is 3.6.2.

---

### Post by Dennis N on 2017-07-15
> **ardouronerous said:**
> How did you get version 3.8.2?

I'm running Xubuntu 16.04 LTS and the version available in the repos is 3.6.2.

My apologies - I switch quite a bit between OSes and forgot I was using Manjaro, which supplies 3.8.2. I have Ubuntu Gnome 17.04 and it has 3.7.2 so that would be the highest version in an Ubuntu release.

---

### Post by ardouronerous on 2017-07-15
Okay, thanks for the info.
I guess the version available for LTS release is 3.6.2.

What's the difference with 3.8.2? Any improvements?

---

### Post by Dennis N on 2017-07-15
> **ardouronerous said:**
> Okay, thanks for the info.
I guess the version available for LTS release is 3.6.2.

What's the difference with 3.8.2? Any improvements?

You can see what bug fixes and any other changes are made here:
[http://audacious-media-player.org/news/](http://audacious-media-player.org/news/)

---

