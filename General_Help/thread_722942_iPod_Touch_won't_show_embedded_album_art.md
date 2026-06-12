---
title: "iPod Touch won't show embedded album art"
date: 2008-03-13
forum: General Help
---

### Post by xjgnsdof on 2008-03-13
I recently figured out how to sync my iPod Touch in Ubuntu using gtkpod. After I synched a song, I saw that several of my album covers were missing. I decided to boot into Windows to fix this problem, but I couldn't even get the album covers to show. That is, the album covers show up in iTunes, but not on my iPod Touch. Why is my iPod Touch suddenly unable to show album art?

---

### Post by Suparious on 2008-03-13
so the art shows-up fine in iTunes in windows?
does it display when you sync with iTunes in windows? if yes, then you may want to file a bug with the 'gtkpod' developers [here]("http://www.gtkpod.org/contact.html"). Otherwise this would be something to ask Apple (why you cant sync album art in windows).

---

### Post by xjgnsdof on 2008-03-13
I actually fixed it. I just deleted the Artwork folder in the iPod_Control folder. When I plugged into iTunes, it created a new Artwork folder. From there, it was just a matter of resynching my iPod to my mp3 backups.

On a side note, why does Ubuntu screw up the artwork? How can one prevent the need for a full backup restoration?

---

### Post by xjgnsdof on 2008-03-17
up

---

### Post by xjgnsdof on 2008-03-18
up

---

### Post by scramasax on 2008-03-18
> **elgilicious said:**
> On a side note, why does Ubuntu screw up the artwork? How can one prevent the need for a full backup restoration?

If you're using GTKPod -- it's not clear from your posts -- then I'd guess that only someone really familiar with that program and how it's written could answer that.  Perhaps no one fitting that description has passed this way.

What I do know is that iTunes primarily looks to be downloading artwork from the iTunes store and storing it in a database.  However, if you've imbedded artwork directly in these MP3s, using ID3 tags, it will use the imbedded artwork instead.  Either way, when synching with an iPod, smaller versions of the images seem to be created, placed on the iPod, and, one assumes, managed via a database.

Maybe the GTKPod people just haven't reverse-engineered how the artwork is done yet.  They may have other interests and other calls on their time.  Why not manage the player under Windows at least for now?  If you'd find it preferable to do it under Linux for whatever reason, you could always check new versions of the program as they are released to see if they've added the capability you want.

---

### Post by xjgnsdof on 2008-03-18
I get this artwork glitch even when I'm just using Ubuntu (Rhythmbox, gtkpod) to play songs from my iPod Touch. I'll fiddle with the artwork folder later. Until then, I'm open to any insights.

---

