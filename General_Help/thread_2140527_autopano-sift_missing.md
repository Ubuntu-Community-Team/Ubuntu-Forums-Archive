---
title: "autopano-sift missing"
date: 2013-04-30
forum: General Help
---

### Post by Dapilot1 on 2013-04-30
So I use hugin a lot because I love stitching panoramas together, but now autopano is nowhere to be found.
It used to be a checkbox under hugin as a add-on.
I've tried apt-get install on autopano, autopano-complete, autopano-sift, but it's always unable to locate package.

Can anyone help me install this [here]("https://launchpad.net/ubuntu/raring/+package/autopano-sift")?
Says it was deleted because it is dead upstream, but I don't think that makes it obsolete. It was amazing.

If it was removed because it doesn't work with hugin right away, I have the necessary changes memorized.
Set the program to "autopano-complete" and pass it "-p %p -o %o %i"

---

### Post by Dapilot1 on 2013-04-30
Well I forgot how to internet. There problem is sort of fixable.

There are debs through that link that will bring back autopano (yay!)

autopano-sift-c is supposed to replace this version because it relies on mono.
Sadly sift(-mono) was removed and sift-c never added.

If anyone knows how to get the faster autopano-sift-c working please let me know.

---

