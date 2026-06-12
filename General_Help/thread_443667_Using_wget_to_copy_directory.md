---
title: "Using wget to copy directory"
date: 2007-05-14
forum: General Help
---

### Post by HeavyAl on 2007-05-14
Hey All,

This isn't an Ubuntu specific question, but since I use Ubuntu as my primary OS I figured it wouldn't be too awkward asking it here anyway :)

Basically I have a server that I'm migrating the web directories from - there are several gigs of them spanning half a dozen sites and I need to copy them from one server to another. I figured wget -r would be the way to go but I can't find a good example of how to do this .. everything I read talks about mirroring and junk but I don't need to do that, I just need to grab everything rooted under /www and copy it to a new local directory.

So I've got server A with the files all located in /home/www and server B that I want to move them root /home/me/www 

Any suggestions on how to do this?

---

### Post by rich.bradshaw on 2007-05-15
Can you ssh into them?

You could use scp in that case...

scp user@host1:\home\www user@host2:\home\me\www

---

### Post by HeavyAl on 2007-05-15
scp? Hadn't heard of that one. Some other people mentioned using rsync. Guess I'll have to do some more reading :)

Thanks for the reply!

---

