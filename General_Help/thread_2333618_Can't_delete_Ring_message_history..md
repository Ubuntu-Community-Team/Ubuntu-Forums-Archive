---
title: "Can't delete Ring message history."
date: 2016-08-11
forum: General Help
---

### Post by YQ002lc2 on 2016-08-11
I installed ring from ring.cx using the repository. 

I was able to make calls, etc. 

Now I'm unable to clear the message history. 

I go through the GUI options and it appears as though it should be cleared out.  
I've also resorted to deleting ring files from .local, .cache, and .config . 
And I even ran sudo apt-get purge ring* . 

Still when I reinstall and open the app, I get the same contacts and messages appearing. 

Any ideas?

---

### Post by wildmanne39 on 2016-08-11
*Thread moved to **General Help**.*

---

### Post by YQ002lc2 on 2016-08-11
My history was more than 1 day old. 

Through the GUI, I had it set to keep history for 0 days. 

I edited   
~/.config/ring/dring.yml
so that the keep history field was set to 1 day. 
When I restarted ring, I had a fresh instance with no chat history.


I thought I had fixed the problem. 
The screen displayed a new instance. 
I entered no username and clicked next. 
Suddenly, all my previous conversations appeared again, even though it's a different user. 

I realized, I had indeed been deleting the history, but not the "conversations" or chat logs.

I'm sad to say this remains an annoying problem.

---

### Post by wildmanne39 on 2016-08-11
Thank you for posting your solution.

---

