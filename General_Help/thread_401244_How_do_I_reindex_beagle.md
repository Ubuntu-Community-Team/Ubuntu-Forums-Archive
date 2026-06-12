---
title: "How do I reindex beagle?"
date: 2007-04-04
forum: General Help
---

### Post by forrestcupp on 2007-04-04
I am using Feisty Beta with Beagle Search 0.2.16.3.  I started off setting it to index my home directory, which worked well.  Then I got the bright idea to just index the root directory, which includes /home.  When I did that, it wouldn't find things very well in the /home directory.  So I deleted my root index setting and reset it the /home directory (all using the settings gui).  When I did that, it lost all of what it indexed, and it didn't automatically try to reindex it.  So no matter what I searched for, it didn't find anything.  So using Synaptic, I completely removed beagle and reinstalled it, hoping that it would index again.  But it didn't.  No matter what I search for, it can't find anything.  So my question is now that I have it set back to my home directory, how do I get it to reindex?

I tried in a console
```
beagle-build-index  yada yada yada
```

and it still can't find anything.

---

### Post by TheWizzard on 2007-04-04
you have to stop the beagle deamon and delete the directory where the indexes are kept. i think it's called .beagle.

---

### Post by forrestcupp on 2007-04-04
Thank you very much.  That did it for me.  They really should just have an option to reindex to make it easier.  When I used Google Desktop on Windows, I noticed it had that option.

In case someone needs to know how to stop the beagle daemon, type this in a console:
```
beagle-shutdown
```

---

