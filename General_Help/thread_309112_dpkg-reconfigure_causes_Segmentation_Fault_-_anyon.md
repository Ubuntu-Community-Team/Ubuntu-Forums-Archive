---
title: "dpkg-reconfigure causes Segmentation Fault - anyone know why?"
date: 2006-11-29
forum: General Help
---

### Post by MJN on 2006-11-29
Hi all,

Recently decided to try a few tweaks to my graphics set up and so proceeded to run **sudo** **dpkg-reconfigure xserver-xorg** (as usual) however got a 'Segmentation Fault' error.

Indeed, if I just run **sudo dpkg-reconfigure **I also get the same error hence I don't believe it's anything to do with X, graphics etc.

Anyone know why? Anywhere to look for hints as to what's going wrong?

For what it's worth I'm not aware of any recent changes (perhaps the odd upgrade) so can't think what might be to blame...

Mathew

---

### Post by ajgreeny on 2006-11-29
Not sure I can help much, but just interested to see you're still using 5.10, and haven't upgraded to at least 6.06.  Perhaps a version upgrade might help.

---

### Post by junglepeanut on 2006-11-29
I have noticed a lot of complaints recently about dpkg, I do not have any recommendation, except to maybe try and upgrade. My server recently had to update dpkg, so you a change is on the way? Don't know, just guessing.

---

### Post by MJN on 2006-11-29
You're both right - an upgrade is in order anyway however as this is a production server I need to to take this step when next convenient as whilst I've upgraded my other machines with any hitches I've been round long enough to learn not to be complacent! I'd almost go as far as betting money that something won't go to plan...

Perhaps it's not worth the effort investigating until at least after the upgrade (as that might sort it as you say)... although I was thinking of a complete rebuild anyway which would undoubtedly nail it.

If anyone else has any suggestions - perhaps they've seen this before or can suggest any way of getting a more verbose explanation of what's gone wrong then that would still be gratefully received.

Mathew

---

### Post by MJN on 2006-12-04
Okay.. an update that might be useful if anyone else has this problem...

I decided to continue tackling the issue as it dawned on me that an upgrade to Dapper would likely require the use of dpkg-reconfigure in the process hence I couldn't rely on the hope of it being satisfactorily upgraded (and hopefully fixed in the process).

So, I happened to try **dpkg-reconfigure --frontend=dialog xserver-xorg ** and it worked! The --frontend option  states what interface to use. In my case (Kubuntu) it defaults to using a KDE window. So, running **dpkg-reconfigure --frontend=dialog debconf** I was able to set my default to dialog instead.

Quite why this has happened I don't know but at least now I'm back up and running and should be able to upgrade with ease when the time comes.

Mathew

---

