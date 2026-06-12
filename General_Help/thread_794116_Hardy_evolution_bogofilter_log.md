---
title: "Hardy evolution bogofilter log"
date: 2008-05-14
forum: General Help
---

### Post by chewearn on 2008-05-14
I'm running Hardy, with evolution as my mail client.  The junk filter is enabled and bogofilter selected.

How do I check that spam is being correctly identified?  Is there a log file for bogofilter or evolution that I can look at?

I got a few spam mails daily, and thus far, none of the spam were properly identified as spam, or automatically moved into junk folder.

---

### Post by chewearn on 2008-05-15
** bump **

---

### Post by chewearn on 2008-05-16
After two days, I'm now quite convinced bogofilter is not working (despite evolution didn't show any error that I know of).

I'm now replacing bogofilter with spamassassin; hopefully spamassassin will work.

---

### Post by metapaso on 2008-05-30
When I upgraded from Gutsy to Hardy, Evolution selected the bogofilter plugin for me.  Because I haven't been satisfied with spamassassin (very slow, misses about 20% of my spam), I thought I would go ahead and give bogofilter a try.

But like you, I've been going with Bogofilter for about 2 weeks and so far it hasn't filtered anything...how long does the training take...I've been training it every day and it has now seen somewhat more than a couple hundred spam mails against about 120 ham mails.

Any thoughts out there?

---

### Post by chewearn on 2008-05-30
I have since found out the solution.

Basically, you need to give bogofilter at least one ham.

You do this by marking a ham as Junk, then re-mark it as Not Junk.  Somehow, the algorithm does not compute properly until you identify at least one ham.

.

---

