---
title: "How do I setup Thunderbird or Evolution to filter spam?"
date: 2005-03-27
forum: General Help
---

### Post by Strid on 2005-03-27
Hi. I'm fairly new to Linux and Ubuntu. I installed mozilla-thunderbird, spamassasin and spamc using apt-get. Then I changed the settings in Thunderbird to throw away junk mail (Tools menu > Junk Mail Controls).
It doesn't seem to filter spam very effectively and neither does Evolution, even though  I set it to filter Junk Mail aswell.

Do I have to enable spamassasin in some way or should it just automatically integrate into Evolution or Thunderbird? How do I make all this work together? I've been searcing the forum alot, but I haven't found a solution to my problem. Also, if there are other ways to counter massive spam, I would like to hear about it.

Thanks,
Anders Christensen :)

---

### Post by Leif on 2005-03-27
Spamassassin integrates with evolution, but just apt-getting it should be enough to get it working. Thunderbird has its own built-in spam filter. Both of these may take some time to work correctly for you. You may want to train them on some stored spam and non-spam mail to get them started. In evolution you can also turn on remote tests for spamassassin that might improve performance. 

Mainly, though, give it time to adapt to your needs, and never expect it to be a magic bullet - there will always be some mistakes, so make sure you check your spam folder once in a while !

---

### Post by clb137 on 2005-03-27
Hi,

As the previous post has already stated you have to make your mail clients learn what to stop and what to let through.  In Evolution you can go  one step more in the setup  and 'include remote test' in the 'filter options'

keep with it


clinton

---

### Post by Strid on 2005-03-27
Hi,

Thanks for the replies, I really appreciate it. It seems like Thunderbird filters most of 'my' spam. I think I'm going stick with Thunderbird as my e-mail client. I guess free spam protection can only take me so far. It's far enough, though.  I can live with deleteing a couple of mails, not having all filtered.
I guess there is no such thing as a spam free inbox. Thats what you get from watching porn on the internet 24/7, haha...   :oops: 

Thanks again,
Anders Christensen

---

