---
title: "Evolution and spam"
date: 2005-10-29
forum: General Help
---

### Post by dhess31 on 2005-10-29
I have used Evolution under another distro and it filtered spam VERY well.  But under Ubuntu, even with "include remote tests" checked under the "junk" tab of the preferences, I'm getting all of my spam in my inbox.  Is there a step I missed?

Don

---

### Post by magnusbb on 2005-10-29
I am also getting too much spam with Evolution under Breezy. A solution would be most appreciated.

---

### Post by craigmac on 2005-10-29
Don, I'm with you. As far as I am concerned, it has not filtered a single spam email since I installed Breezy. 

What are we doing wrong?

---

### Post by Riverside on 2005-10-29
Evolution has no intrinsic spam filtering capabilties, does it?  I believe though that many Evolution users also install SpamAssassin, and SpamAssassin then handles spam filtering.  Is spam filtering mentioned in the Evolution documentation?

---

### Post by dhess31 on 2005-10-29
I actually didn't see anything about this in the documentation.  It just mentions what the junk mail options are supposed to do.  I DID wonder though if there was a hook or something in Evolution for SpamAssassin as you mentioned.  But I'm not sure.  Either that, or some filters are missing or something.  Hopefully someone who knows a bit more about it can tell us whats up.

Don

---

### Post by Haegin on 2005-10-31
You need to install spam assassin from synaptic - to do this:

1. Install spamd and all the dependancies (including spamassassin).

2. ```
sudo nano /etc/default/spamassassin 
```

3. change "Enabled = 0" to "Enabled = 1"

4. It should work - I have just done this for myself but I haven't tested it yet. I think theoretically you start marking things as spam and it learns to recognise spam.

Hope this helps

---

### Post by dhess31 on 2005-11-01
OK.  I'll give this a hot and see what happens.  This should probably be done by default during the installation though.

Don

---

### Post by Haegin on 2005-11-01
I don't actually get enough spam to test this thing properly so it will take a few months for me to actually see if its working (bit ridiculous...) so please don't give my address to spam harvesters but if you get more spam than I do then can you post your results.

Thanks

---

### Post by hwbj on 2005-11-01
[QUOTE=Human Prototype]You need to install spam assassin from synaptic - to do this:

1. Install spamd and all the dependancies (including spamassassin).

2. ```
sudo nano /etc/default/spamassassin 
```

3. change "Enabled = 0" to "Enabled = 1"

4. It should work - I have just done this for myself but I haven't tested it yet. I think theoretically you start marking things as spam and it learns to recognise spam.

Hope this helps[/QUOTE]

I had the same problem...after I went back and installed the recommended and suggested programs listed by Synaptic, Spamassassin began working like a charm

Be sure to check those out, they made the difference for me

---

