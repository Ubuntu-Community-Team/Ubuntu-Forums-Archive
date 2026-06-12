---
title: "Curious about JFS"
date: 2008-04-23
forum: General Help
---

### Post by krelverehan on 2008-04-23
Tomorrow, when I move to Hardy, I'll be making my /home directory a separate partition. I have _a lot_ of music and movies, and I have been reading a bit about it and the consensus seems to agree that JFS is a slightly better FS.

Would it be worth it to formate that partition as JFS? Should I format both my / and /home partition as JFS...

Or would it be too much of a headache to do that and I should just stick to ext3, because the differences would be too minor?

Any thoughts?

---

### Post by jjthomas on 2008-04-26
I've been using JFS for about a year with Slackware.  I prefer it over ext2(3) and Reiser.  Is it available with Ubuntu?

I still create a /boot partition and format it ext2. The /boot partition is old school and probably is not needed.  But I'm an old guy, so I still do it that way.

I also create a /tmp partition and format it as ext2 as well, because I read somewhere that PulseAudio does not like journel'ing file systems and wants a non-journeled FS for its temporary (/tmp) storage.  Whether that is still true or not, I do not know.

-JJ

PS I'm at work, so the spelling errors are the result of a lack of spell checker on my bosses competer.

---

### Post by sekinto on 2008-04-26
I use XFS, I encourage you to give XFS a try, it is great.

---

### Post by articpenguin on 2008-04-26
JFS is in ubuntu and i use it too. XFS corrupts way to easy.

---

### Post by krelverehan on 2008-04-26
I actually tried to install hardy with a JFS, with success. But I use [Quod Libet]("http://www.sacredchao.net/quodlibet/") (a music player which I find there is no substitute) to organize and play my MP3's, and I noticed that QL was scanning my directory *a lot* slower. This is a pretty big deal when you have to load 800+ albums. Anyway, I noticed this pretty soon after the fresh install and I was curious if it was the JFS or the new ubuntu which was causing this to go slowly. So I did a fresh install again, but using ext3 this time, and QL was up to speed again... Maybe QL just isn't meant to be running on a journaled file system, I don't know. But I am back with plain old ext3 and it is working fine. I guess that everything on ubuntu is programed to be running on ext3...

Aside from QL acting a bit buggy, loading a JFS on hardy worked great it seemed.

---

