---
title: "mp3 player for last.fm"
date: 2006-12-19
forum: General Help
---

### Post by Subw00fer on 2006-12-19
HI everyone.  I'm new to Ubuntu for about a week now and I am truely enjoying it.  All I really need to get fixed and working is Wine and Beryl but those are just extras.  My real enjoyment is to surf the web and listen to my MP3s that get submitted to [www.last.fm](www.last.fm)  which is an amazing site for keeping track of your music.  Here is my issue:

About half of my mp3s are tagged with id3v1 and the other half with id3v2.  I have searched high and low and tried just about everyone gnu mp3 player available that supports a last.fm plugin.  The main ones I've used are Beep Media Player, XMMS, Audacious and Amarok.  Each player will each not submit or crash when it uses a file that only has id3v2.  How do I get a plugin or a player that will recognize this type of tag?

Any ideas?

---

### Post by 23meg on 2006-12-19
In my experience Rhythmbox, Songbird and Exaile all work with last.fm with all kinds of tags; Songbird sometimes triggers last.fm's spam protection though, which is to be expected, since it's not mature enough for casual use yet.

---

### Post by ciscosurfer on 2006-12-19
> **Subw00fer said:**
> HI everyone.  I'm new to Ubuntu for about a week now and I am truely enjoying it.  All I really need to get fixed and working is Wine and Beryl but those are just extras.  My real enjoyment is to surf the web and listen to my MP3s that get submitted to [www.last.fm]("http://www.last.fm")  which is an amazing site for keeping track of your music.  Here is my issue:

About half of my mp3s are tagged with id3v1 and the other half with id3v2.  I have searched high and low and tried just about everyone gnu mp3 player available that supports a last.fm plugin.  The main ones I've used are Beep Media Player, XMMS, Audacious and Amarok.  Each player will each not submit or crash when it uses a file that only has id3v2.  How do I get a plugin or a player that will recognize this type of tag?

Any ideas?You can install **last-exit** or **lastfm** (and perhaps **lastfmsubmitd**) from the repositories and they will submit your songs for you.

---

### Post by Subw00fer on 2006-12-19
> **ciscosurfer said:**
> You can install **last-exit** or **lastfm** (and perhaps **lastfmsubmitd**) from the repositories and they will submit your songs for you.

I thought both of those programs are only for listening to LastFM stations and not playing your own MP3s?

I'm also looking for a player that is tiny and slick looking

---

### Post by Subw00fer on 2006-12-20
> **23meg said:**
> In my experience Rhythmbox, Songbird and Exaile all work with last.fm with all kinds of tags; Songbird sometimes triggers last.fm's spam protection though, which is to be expected, since it's not mature enough for casual use yet.

each of those seem great but can you customize them to be compact like Winamp?

---

### Post by 23meg on 2006-12-20
> **Subw00fer said:**
> each of those seem great but can you customize them to be compact like Winamp?Rhythmbox and Songbird have compact modes, though not exactly like Winamp.

---

### Post by Subw00fer on 2006-12-20
> **23meg said:**
> Rhythmbox and Songbird have compact modes, though not exactly like Winamp.

How so?  I just want something that is tiny and can be modified with some wild skins

---

### Post by TeeAhr1 on 2006-12-20
Try [gmusicbrowser]("squentin.free.fr/gmusicbrowser/gmusicbrowser.html"), it comes with a plugin that submits your songs to your last.fm account.  It's not in the repositories but there's a .deb on the webpage.

---

### Post by 23meg on 2006-12-20
> **Subw00fer said:**
> How so? 
Songbird above, Rhythmbox below, both in compact mode. Rhythmbox can be shrunk further.[IMG]http://i16.tinypic.com/2mxl89y.png[/IMG]
>  I just want something that is tiny and can be modified with some wild skins
Rhythmbox doesn't have skin support. Songbird does; they're called "feathers".

---

### Post by Subw00fer on 2006-12-20
> **23meg said:**
> Songbird above, Rhythmbox below, both in compact mode. Rhythmbox can be shrunk further.[IMG]http://i16.tinypic.com/2mxl89y.png[/IMG]

Rhythmbox doesn't have skin support. Songbird does; they're called "feathers".

Songbird looks great.  I'll have to give that a try tonight and see how it handles my ID3v2 tags.

thanks!

More suggestions are welcome

---

### Post by ciscosurfer on 2006-12-20
> **Subw00fer said:**
> I thought both of those programs are only for listening to LastFM stations and not playing your own MP3s?

I'm also looking for a player that is tiny and slick lookingSorry 'bout that...I must have read your post wrong.

---

### Post by paulyche on 2006-12-20
That's interesting.

I've got a very large music collection that I've used with loads of players and last.fm (mostly amarok though). I've never encountered this even with files with only ID3v2 tags. 

Would it be possible to attach one of the mp3s that doesn't submit (maybe a free legal download if you're uncomfortable with the legality of that). Then we could see if it's something unique to your system. I suppose it could be different character encoding between ID3 versions or something..

Last.fm is indeed great..

---

### Post by Dubbayoo on 2006-12-20
What is the point of last.fm? Is it just myspace revolving around music?

---

### Post by paulyche on 2006-12-20
> **Dubbayoo said:**
> What is the point of last.fm? Is it just myspace revolving around music?

For some people - yes. I don't use all the social networking stuff though. I like it cause it gives good recommendations for music I might like and for the superb personalised radio.

edit// plus it lists local gigs you might (and probably will) like.

---

### Post by Old Pink on 2006-12-20
amaroK has a compact "player" supports last.fm and is possibly the best MP3 player out there for Linux, in my opinion. 

[http://amarok.kde.org](http://amarok.kde.org) or ```
sudo aptitude install amarok
```in terminal :)

---

### Post by orb9220 on 2006-12-20
Well the only problems with tags has always been a badly or corrupt mp3 tag in Amarok for me.

Best solution I see is to retag the complete collection to stave off future problems along these lines.

Yes it is a pain and I had to do it to my 500cd collection at the time. Now I am up to 1000+ with all tags the same with zilch problems.

Good luck!

---

### Post by AndyCooll on 2006-12-20
> **Old Pink said:**
> amaroK has a compact "player" supports last.fm and is possibly the best MP3 player out there for Linux, in my opinion. 

[http://amarok.kde.org](http://amarok.kde.org) or ```
sudo aptitude install amarok
```in terminal :)

I was surprised I got this far in to the thread before someone mentioned this! I use Amarok and it's set so that it contribute my songs. And under "playlists" I can play back various last.fm streams.

:cool:

---

### Post by Subw00fer on 2006-12-20
I installed Songbird but when I play any song, it says "error" in the part of the program that shows how long the song is.  Any ideas?

---

### Post by 23meg on 2006-12-21
Only "error" and no detail? Try running it from a terminal and see if it throws out a more detailed error message when you play a song.

---

### Post by paulyche on 2006-12-21
If you want to retag. The musicbrainz tagger has a ubuntu deb for easy install on their website. It automatically identifies the correct tagging by a kind audio fingerprinting

[Picard Tagger](http://musicbrainz.org/doc/PicardLinuxInstall#head-5f60c040c32c67c304b335181b88678ad34149c2)

---

### Post by xopher on 2006-12-21
Another player that supports Last.fm is BMPx (Beep Media Player), it's still in development, but is starting to look great ;)

Check it out: [http://beep-media-player.org](http://beep-media-player.org) - Ubuntu debs available from an unofficial repository.

---

### Post by Subw00fer on 2006-12-21
Alright now I am COMPLETELY confused.  I just tried a file that has an ID3v1 tag and it crashed XMMS half way through the song.  I then tried another song that has an ID3v2 tag (meaning that it appears to look blank) and that one ran to the end.  Neither song recorded on the last.fm website.  Now for the weird part.....when I played the first song back again, it ran through until the end but didn't crash.  Then for a third time, it died half way again.

What should I do?!?!

It seems that Musicbrainz is a good way to edit all of your tags very quickly and for free.  Should I go with this?  I downloaded the install from the site that paulyche gave me.

---

### Post by paulyche on 2006-12-22
Make sure you configure musicbrainz to clear all the tags before it rewrites them. Also be aware that musicbrainz database doesn't include genre info (this is intentional and a good thing in my opinion).

You may want to backup your collection beforehand, in case you want to go back to your old tags.

---

### Post by Naegling23 on 2006-12-22
I noticed that the original poster was saying they wanted a slick winamp style mode with customizable skins.   That is one of the issues with a lot of linux media players, they dont have great skin support, but there is a work around.  I really like amarok, but there is no skin support, so what I do is to use a custom amarok skin for superkaramba.  I put amarok on another desktop, then control everything through superkaramba.  This allows the skins to be more varied as well.  Works great, and there are some slick amarok, xxms and other player controls for superkaramba.

I will vote for amarok as well, its one of the programs that really made me switch to linux.

---

### Post by Subw00fer on 2007-01-16
Hey everyone, its me again!  I've been away from my Ubuntu for a while and I need to get back into it cause I want to play around with Wine and some other features some more.  (just got Warcraft 3 and want to try it in this OS)

Here is my current issue with my MP3s and retagging them.....I tried using musicbrainz and it is a decent program and will absolutely tag them perfectly but I am picky about my tags and would prefer to have the albums remain as "unknown".  The reason I do this is that when I load my mp3s onto my Creative Vision player, I like to have my MP3s in one catagory called unknown (or mp3) and my CDs that I have loaded in their own folders.  So is there a way to use this software to change every file to have the same album name?  This is so much work for something so stupid but I really want to use Ubuntu while listening to music.

I still don't know if this will solve the issue with a few of my MP3s crashing various Linux mp3 programs but I need to worry about retagging them first.

---

