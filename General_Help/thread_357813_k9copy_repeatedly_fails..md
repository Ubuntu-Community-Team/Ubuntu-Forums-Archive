---
title: "k9copy repeatedly fails."
date: 2007-02-10
forum: General Help
---

### Post by Titus A Duxass on 2007-02-10
Despite functioning correctly for the last 15 DVD backups, suddenly k9copy consistently fails with:

An error occured while running DVDAuthor:
dvdauthor: dvdvob.c:1297: FindVobus: Assertion `p>=s->vi[i-1].sectpts[1]' failed.

I have changed nothing, there is plenty of room on the HDD both in / and /home.

It occurs with different DVDs.

Googling has not produce much in the way of help, has anyone else had the same experience.

---

### Post by Titus A Duxass on 2007-02-10
I have found a work round (or around).
I un-installed and re-installed the dvd packages using Automatix and everything appears normal now.

But I do no know what the problem was.

---

### Post by Titus A Duxass on 2007-02-10
Well the work around worked for one backup run.
Now I have exactly the same failure.

---

### Post by Titus A Duxass on 2007-02-13
Okay, after a bit of thinking and tinkering I have this idea: the only thing that is different is that the screensaver kicked in during the rip.

I put together another pc just for ripping and had the same problem with that pc.  Everything appeared to be ok so I left the machine. When I came back later, the screensaver had kicked in the k9copy showed the same failure.

I am on to something here or am I , as usual, completely mad and barking up the wrong tree?

---

### Post by g8m on 2007-02-13
....

---

### Post by Titus A Duxass on 2007-02-13
> Maybe.

Is it still maintained?

Looking at k9copy.sourceforge.net, latest release is about a year ago.

Maybe it's a configuration error.

Maybe it's a packet error.

Anyway, I dont know. - If you do not know then why post!

---

### Post by g8m on 2007-02-14
....

---

### Post by Titus A Duxass on 2007-02-15
Okay, made a bit of progress.
Apparently there is a bug in k9copy.
By checking "keep original menu" I can avoid the problem.

But it still does not explain why one of my boxes has no problem and the other two have the same problem.

My MythTV box rips DVDs without a glitch.

---

### Post by feffer on 2007-02-16
I've been using k9copy for about a year, and it seems to break occasionally. I think there's only one person maintaining it. After a recent dvdauthor update, I could no longer get k9copy to make complete copies. But honestly, I'm just guessing that this might be the problem. I went back to the previous version of dvdauthor and k9copy started working again for a while, but is now once more broken. I get failures whether I use "keep menu" or not. This is a very nice app when it's working. I even sent the developer a donation a while back. Hope it gets fixed.

Regards,
Ron

---

