---
title: "Suggestions for combining mail from multiple computers?"
date: 2007-09-11
forum: General Help
---

### Post by Old *ix Geek on 2007-09-11
Over time I've become very disorganized in terms of letting my mail get scattered all over the place.  This happened by circumstance, not design, but the net result is one big mess.

Basically, I'd start using one computer as my ONLY one for e-mail, then when I'd get a newer, better computer I'd copy over the e-mail files to it and start using it instead.  But I'd also use other computers (laptops, the older computers, etc.) occasionally for checking mail, and even though I was leaving incoming messages on the server, copies of anything I sent ended up only on the other computers.  Then, to complicate matters, when a computer would go down and need to be repaired--such as my most recent laptop which, at 3 months old had a complete power failure--I'd switch entirely to using a different one for mail temporarily.

It's SeaMonkey e-mail we're talking about here, by the way.  I now have 3? 4? (I'm not sure right now) SM mail directories on different computers, each containing SOME of the same e-mails, but no two containing EXACTLY the same e-mails.  Make sense?

I realize this isn't a Ubuntu question, per se, but I thought the clever folks here might have some ideas as to how I can BEST combine--and condense--this huge mess!  If you're not familiar with how SM stores its mail, there are directories AND files; the files are actually accumulations of e-mail messages in a form that SM knows how to parse into intelligible, discrete messages.  But that complicates things because it's not like you can do a simple compare to see if two (or more) files are identical and then only keep one of them.  Even if two (or more) files match up for certain strings, they're definitely NOT going to match up all the way through (I'm 100% certain on this).

What I want to do is merge all of these files, eliminating duplicated messages, and end up with one mail directory that will go into a centralized location on the network and be used (and backed up frequently!) by all computers.  But I can't see any EASY, elegant way of doing this.  Of course I can just copy all of it into one location and then MANUALLY merge and purge from within SeaMonkey, but I really, really don't want to do that...we're talking about tens of thousands of e-mails.

Any ideas?!  ](*,)

---

### Post by rsambuca on 2007-09-11
I know this doesn't help your current situation, but GoogleMail is perfect for packrats like yourself who cannot bring themselves to delete anything. 

You might be able to set up some sort of script that searches for specific header info and flags/deletes duplicates/triplicates/quadruplicates.  I personally don't know how, though.

---

### Post by Old *ix Geek on 2007-09-11
Your reply made me chuckle. :)  It's not so much that I'm a packrat, it's just that these e-mails really do need to be kept--in an accessible place, not just archived off somewhere.  But, yeah, I've created a hell of a mess for myself by letting them get splintered off all over the place!

---

### Post by rsambuca on 2007-09-11
After backing up the files, maybe just try appending the files together (with the 'cat' command) into one big file to see if it opens up.

---

### Post by Old *ix Geek on 2007-09-13
But if I combine them like that...I'll have zillionuplicates! (Who cares if that's not a real word? :) )

I suspect the only way I'm going to sort out this mess is to do it manually from within SeaMonkey, i.e., pull all the mail in and then sort by [whatever], eyeball it  to find like messages, and then delete the extras.  I'll probably be bald by the time I get done...  :shock:

---

### Post by rsambuca on 2007-09-13
Yeah, but if you sort it by date then, all of the copies will be together, so it gives you a starting point for group deletions.

---

