---
title: "pidgin default away message (&quot;i'm not here right now&quot;) not reset on returning"
date: 2018-06-04
forum: General Help
---

### Post by aztlan2k on 2018-06-04
Using pidgin version:

pidgin/bionic,now 1:2.12.0-1ubuntu4 amd64 [installed]

So this seems to be an old (very old) bug that has never been fixed.  I've seen references to it going back almost 10 years now.  

It's been discussed and closed previously in these forums...

[https://ubuntuforums.org/showthread.php?t=1097225](https://ubuntuforums.org/showthread.php?t=1097225)

and it looks like it's in the pidgin bug tracking:

[https://developer.pidgin.im/ticket/9046](https://developer.pidgin.im/ticket/9046)
[https://developer.pidgin.im/ticket/8826](https://developer.pidgin.im/ticket/8826)

but nothing has ever been done about it.  

To recap, when pidgin detects that I'm away it changes the status to "Away" and the status message to "I'm not here right now".  That's fine.  

On returning tho, the status is reset to "Available" but the status message is left as "I'm not here right now"... which is rather confusing.  I usually don't realize this until much later when I have to manually reset this.  I've come to realize that I can alter my default message on returning by creating a custom message and selecting it from the Preferences, but this seems like a hack.  The default really should be much more logical  (on returning set status to "Available" and simply clear the away message).

I was going to look into checking out the code and seeing if I could create a patch myself to submit back to the project but stopped when I realized the repo was a mercurial repo.  I'm not familiar with mercurial and to be honest I don't have the time to invest in it right now so I abandoned that idea.  

My question here is... does anyone know if this is simply operator error on my part and I'm simply missing the problem / solution?  Or is this really a bug that has gone on for nearly a decade without anyone feeling the need to address it?

---

