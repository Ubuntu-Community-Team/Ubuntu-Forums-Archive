---
title: "Konqueror vs. Facebook"
date: 2007-09-01
forum: General Help
---

### Post by Apostata on 2007-09-01
Hello all,

  Am I the only one finding it harder and harder (especially over the last three weeks) to use Konqueror on Facebook? 

  Using v3.5.6 I can no longer "poke" friends, nor can I add friends, nor can I join groups - I click and nothing happens. I realise this probably something happening on the server-side, but is it Facebook's coding that's at fault or Konqueror's?

  Is this a continuation of the Java issue experienced [here]("http://ubuntuforums.org/showthread.php?t=506709") (w/ adding photos)?

---

### Post by Apostata on 2007-09-01
FYI - upgraded to v3.5.7 and it makes no difference.

---

### Post by spookylukey on 2007-09-03
I've discussed the problem, and a work-around, here:

[http://lukeplant.me.uk/blog.php?id=1107301676]("http://lukeplant.me.uk/blog.php?id=1107301676")

It is a problem with Facebook's code - they delete Object.prototype.eval for some unknown reason.  Remove a line of code and everything works again.

My solution involves about 10 minutes work, I reckon.  What we really need to do is set up a method for distributing/sharing fixes like this in an automated way.

Luke

---

