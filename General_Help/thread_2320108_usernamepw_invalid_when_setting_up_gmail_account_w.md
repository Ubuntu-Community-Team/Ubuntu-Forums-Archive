---
title: "username/pw invalid when setting up gmail account with Thunderbird"
date: 2016-04-10
forum: General Help
---

### Post by 1two3 on 2016-04-10
I know there's a lot of threads about this if you google the problem but none of those threads helped me. 

I want to download the emails from gmail to Thunderbird so I want to use POP3 instead of IMAP which I've also selected. 
I don't have two factor authentication for my gmail and I've checked that POP3 is allowed in my gmail settings. 
I've also sudo ufw allow..

in 995/tcp
and..
out 465/tcp

and disabled and then enabled ufw afterwards but it didn't make any difference.

---

### Post by lisati on 2016-04-10
Have you entered your full gmail address for the username?

Some further information can be found [here]("http://kb.mozillazine.org/Using_Gmail_with_Thunderbird_and_Mozilla_Suite").

---

### Post by 1two3 on 2016-04-10
> **lisati said:**
> Have you entered your full gmail address for the username?

Yes, I have

---

### Post by howefield on 2016-04-10
Using the Thunderbird account wizard should correctly populate the settings. Not sure if it helps but here are screenshots of gmail settings for a (working) POP3 set up..

---

### Post by 1two3 on 2016-04-10
Sorry, was going to show a screenshot, first time attaching a picture on this forum. Tried uploading to imgur but the upload failed, thought at first it might be because of the ufw but all outgoing ports are open so it can't be that.

---

### Post by howefield on 2016-04-11
> **1two3 said:**
> Sorry, was going to show a screenshot, first time attaching a picture on this forum. Tried uploading to imgur but the upload failed, thought at first it might be because of the ufw but all outgoing ports are open so it can't be that.

Use the paperclip icon to attach an image to your post, not available in the "quick reply" window only in the Reply to thread option or go advanced.

---

### Post by 1two3 on 2016-04-11
Good morning :-)


[ATTACH=CONFIG]268305[/ATTACH]

---

