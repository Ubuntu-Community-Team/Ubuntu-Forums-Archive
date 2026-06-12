---
title: "Hardy : Evolution's custom header junk filter doesn't work"
date: 2008-05-18
forum: General Help
---

### Post by kensuguro on 2008-05-18
I'm not sure if I have this set up right.  I know that all my mails with a custom header of:
X-Biglobe-spamcheck: 100.00%
Are all spam mails.

The mails are already in my mailbox.  I enter the information in Evolution's junk setting, select all messages, and select "check for junk" and nothing happens.  I also tested with a X-???? custom header that I know exists, but "check for junk" still does nothing.

Is there a specific way to set this up?  Or is it just broken?

Also, if I create a filter that does pretty much the same thing, it works fine. (detect custom header and value, and marks it as junk)

---

### Post by kensuguro on 2008-05-20
bump

---

### Post by chewearn on 2008-05-20
I was struggling with Evolution junk mail filter for a while now.  I'm still investigating, but I found one "stupid" thing which help a bit.

Apparently, bogofilter need at least one hit of "not junk" before it can work properly.  That means, get a legitimate mail, mark it as junk, and mark as not junk.  Else, all junk mails will continue to land into the inbox, despite you mark it as junk everytime.

I read that this is due to the way bogofilter works, it need a contrasts between good vs bad mails.

I'm still continuing with setting up Evolution filters.  At the moment, junk filter seemed to finally work, but the custom mail filters still acting weird.  Unfortunately (or fortunately) I got too little spam per day to be able to speed this up.

.

---

### Post by PRMan on 2008-05-30
Hey, thanks a lot for the info.  I saw your other thread and I'm glad you got it solved for both of us.  I use PopFile on Windows but I thought it would be nicer built-in.

I can't believe that it comes that way by default!  Completely broken with no obvious way to fix it no matter what you do.

I have an idea.  For the next release, put the "Welcome to Evolution" e-mail in there by default and then take it back out and ship Evolution with the files already like that.

---

