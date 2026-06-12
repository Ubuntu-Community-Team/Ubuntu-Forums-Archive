---
title: "question on sudo apt-get autoremove"
date: 2016-03-07
forum: General Help
---

### Post by Eanruig on 2016-03-07
The command sudo apt-get autoremove reports a number of packages with three different prefixes.

man apt-get doesn't explain the meaning of these three prefixes.

Examples of the three prefixes are:

Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://deb.opera.com](http://deb.opera.com) stable InRelease                                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                           
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease [65.9 kB]      


Where can I find out what they mean? Are they giving instructions to follow, or simply passing along some information?

Thanks for help.

---

### Post by Bucky Ball on 2016-03-07
These are repositories, they're not commands, and bit confused about your question.

Are you asking what 'sudo apt-get autoremove' does, what the lines you have quoted do, or both? They look like they come from an update command.

They are not giving instructions to follow, they are just telling you what is going on during update. That is all. Ignore ... unless you have issues updating, and even then that output will probably not be relevant. You can find out what they mean [here]("https://duckduckgo.com/?q=ign+hit+get+meaning+ubuntu") and, for future reference, best to have a look around for an answer before posting a question. Thanks.

Which release are you running?

---

### Post by vasa1 on 2016-03-07
Maybe OP meant *sudo apt-get update* and not *sudo apt-get autoremove*?

---

### Post by Bucky Ball on 2016-03-07
> **vasa1 said:**
> Maybe OP meant *sudo apt-get update* and not *sudo apt-get autoremove*?

Makes sense. Anyhow, what ign, hit, get mean is readily available in many places on the interwebs. I have provided a link in last post.

---

### Post by vasa1 on 2016-03-07
Here's someone who dug really deep: [http://www.bleepingcomputer.com/forums/t/597106/discussion-apts-output-codes-hit-get-ign/](http://www.bleepingcomputer.com/forums/t/597106/discussion-apts-output-codes-hit-get-ign/)

---

### Post by Bucky Ball on 2016-03-07
> **vasa1 said:**
> Here's someone who dug really deep: [http://www.bleepingcomputer.com/forums/t/597106/discussion-apts-output-codes-hit-get-ign/](http://www.bleepingcomputer.com/forums/t/597106/discussion-apts-output-codes-hit-get-ign/)

Ha. Yea. Could have saved a lot of time and effort and hair pulling. Post #14 in that thread says it all. Seems like they actually bothered to get out the spade!

---

### Post by Eanruig on 2016-03-07
First, thanks to all who looked and responded.

I quickly realized that the query should have been about "upgrade", and not "autoremove". When I came back, there were three replies already. I started to respond, then the browser crashed at 1:00 AM. I went to bed.

So, problem resolved. Just one thing to wonder at. I wonder why these responses aren't in the man page for apt-get.

---

### Post by vasa1 on 2016-03-07
> **Eanruig said:**
> ... Just one thing to wonder at. I wonder why these responses aren't in the man page for apt-get.

You'll just have to get used to it or help fix it. Mostly, the information is somewhere, not necessarily in the man pages.

If you're new to Linux or planning to move to Linux, you may want to read this: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm). It's a bit old, but many, if not all, points are still valid.

---

### Post by Bucky Ball on 2016-03-07
Glad you got it fixed. Please mark as solved. Instructions in my signature at bottom of post. This does not close the thread to further discussion.

---

