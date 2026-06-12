---
title: "Sharing Music Between Three OSes"
date: 2006-12-17
forum: General Help
---

### Post by Falcorian on 2006-12-17
I live in an apartment with a couple other guys from my University. We've set up a Ubuntu (Dapper) box in the living room that's hooked up to our stereo and TV. We currently use it as an FTP server for files, we watch (downloaded) media on it, and we play music on it.

However, our music system is not currently optimal, since the music must be moved onto the shuttle's local hard drive. We'd much rather stream the music, but this is where I've been hitting a brick wall.

I use Edgy, but with Amarok. Amarok doesn't seem to want to share my music (and from the threads I've read, won't share it on Gnome), and I don't want to have to leave Banshee/Rythmbox or whatnot on to share (They work, but they have to be running). I'd rather have something running in the background serving my music all the time. Is this possible? From the reading I've done it looks like it, but I'm not sure what I need to do it, any suggestions and helpful tips?

The second issue is that we have a bunch of Windows boxes running iTunes 7 (which won't share with anything but iTunes 7 it seems). We'd like to set up a similar thing for them, where they can be serving all the time. Any recommendations of what to look for there? We also have a OSX laptop that in theory we'd like to get to work with sharing it's music, but that's not really critical.



So to sum it up: We'd like to share music from Edgy, Windows XP, and OSX to a Dapper box. That's the main goal.

As an aside, iTunes 7 can see and play music from the Ubuntu machines if they have Banshee/Rythmbox up, so that's a minor victory for umm... The cold corporate world? ;)


Thanks for the help in advance!

---

### Post by Travisty on 2006-12-17
I found this article earlier when I was trying to do the same thing as you. I haven't tried it yet but it seams simple enough.

[http://www.oreillynet.com/xml/blog/2004/12/streaming_itunes_from_ubuntu.html](http://www.oreillynet.com/xml/blog/2004/12/streaming_itunes_from_ubuntu.html)

---

### Post by Mike'sHardLinux on 2006-12-17
Are you against the idea of using your Linux box as a fileserver via NFS and Samba? It's pretty easy to setup in Ubuntu. Then you don't need to leave any special prgrams like Amarok running - Samba and NFS run in the background. This is how I have set up several home networks. The only thing different is that the music wouldn't literally be streaming in the truest sense of the word. You'd simply be playing the files right off of the server's hard-drive.

---

### Post by Travisty on 2006-12-17
Have you ran in to any issues with sharing via Samba? I've notice that quite a few programs do not like to "stream" via this method while others will download the file before it plays.

---

### Post by Falcorian on 2006-12-17
I hadn't tried samba yet. No reason for not doing so, I just wasn't sure if it was worth a shot. I'll give it a shot and see what happens.

---

### Post by Falcorian on 2006-12-21
As an update:

Tangerine ([http://www.snorp.net/log/tangerine](http://www.snorp.net/log/tangerine)) has solved our problems. Samba seemed like overkill, so I gave this a try first. It runs in the background and publishes music using DAAP. It works on Windows and linux (haven't tried it on our OSX box yet, but should work there too), and was a snap to set up, just point it to the directories (or let it find the files, or let it read off your music player's library) and you're done.

So now everyone can see each other's music. 8)

---

### Post by christhemonkey on 2006-12-21
If you are still interested, mpd does exactly what you were wanting.
With frontends for all systems.

Im glad you found a solution that worked.

---

### Post by Falcorian on 2006-12-21
> **christhemonkey said:**
> If you are still interested, mpd does exactly what you were wanting.
With frontends for all systems.

Im glad you found a solution that worked.

Well, I'm always looking for a better solution! :) Unfortunately I just got home for the holidays, so I won't be able to give it a shot, but I'll certainly look into it when I get back to University!

---

