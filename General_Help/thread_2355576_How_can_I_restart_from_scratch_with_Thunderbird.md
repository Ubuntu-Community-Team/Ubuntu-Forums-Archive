---
title: "How can I restart from scratch with Thunderbird?"
date: 2017-03-14
forum: General Help
---

### Post by lysander6662 on 2017-03-14
Yesterday, out of curiosity [and we know how that can be a problem], I configured TB to work with Gmail. It ended up downloading [as IMAP - so I think it downloaded the headers and not the content?] all 45,000+ of my emails. Really what I wanted was it to do this only for the last 30 days or so. Is there a way of getting rid of everything locally and starting again [I don't want to delete things from the server, just my drive]? I think I would then have to start in offline mode and reconfigure it to work with the last 30 days.

---

### Post by slickymaster on 2017-03-14
*Thread moved to **General Help*** for a better fit.

---

### Post by dragonfly41 on 2017-03-14
You could create a *second* profile in Thunderbird (keeping your existing profile for a period).

[https://www-archive.mozilla.org/support/thunderbird/profile](https://www-archive.mozilla.org/support/thunderbird/profile)

Then when you are happy with the second profile, purge the original.

---

### Post by lysander6662 on 2017-03-14
That may be it. Thanks, I'll try that.

---

### Post by SeijiSensei on 2017-03-14
Or, simpler, if you want to start from scratch, just stop Thunderbird and rename /home/username/.thunderbird to /home/username/.thunderbird.old.  Now when you start Thunderbird the next time it will begin with a new profile and ask you to set up your email accounts again.  Once things are working to your liking, you can delete thunderbird.old.

---

### Post by lysander6662 on 2017-03-16
Worked perfectly, thanks.

---

