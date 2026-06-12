---
title: "[SOLVED] FIrefox doesn't love me anymore :("
date: 2008-06-06
forum: General Help
---

### Post by knight666 on 2008-06-06
I upgraded Ubuntu after not having internet for several days, and now Firefox is being bothersome:

1) All my bookmarks are gone and restoring them from a backup doesn't work. The bookmarks tab is empty. :(
2) AdBlock Plus doesn't work anymore.
3) Firefox doesn't want to save passwords anymore.

But here's the strange thing: the Awesome Bar still remembers all the sites I visited!

Can anyone tell me how to fix this?

-knight666

---

### Post by pytheas22 on 2008-06-06
Look inside the .mozilla/firefox directory of your home folder.  Is anything missing?

You could also potentially solve the problem by renaming the above directory, which would force Firefox to recreate a profile for you using default settings.  You'd lose all of your bookmarks and things, but if this isn't a big problem for you, it could be the best solution.  You would do:
```

mv ~/.mozilla ~/.mozilla-old
```

Also, if you upgraded from Ubuntu 7.10 to 8.04, then you went from Firefox 2 to Firefox 3 beta.  Your settings should have been transferred transparently, but maybe something went wrong.  You can install Firefox 2 through Synaptic (it won't interfere with Firefox 3) and see if FF 2 works properly.

---

### Post by knight666 on 2008-06-24
I forgot all about this thread!

For future generations: the problem was that I had ZERO bytes available on /.
So check that first!

---

