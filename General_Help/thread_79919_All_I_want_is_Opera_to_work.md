---
title: "All I want is Opera to work????"
date: 2005-10-21
forum: General Help
---

### Post by kittcankitt on 2005-10-21
Again, I have to say I rarely post a question here but I am truly stumped.  I did a dist-upgrade from hoary to breezy a few days ago and things seemed fairly...uh, we'll call it "stable" until two days ago Opera decided to no longer load.  After reading everything I could possibly find in this and other forums, nothing worked so I decided (for other reasons as well) I'll try a fresh install and see how that goes.  Aside from getting everything back to the way I have my desktop, apps, sound, etc...all went fairly smooth.  NOW, back to Opera.  This is the error I get when trying to run it:

opera: Could not initialize M2: Store Init failed
opera: Could not initialize M2: Engine Init() failed
Segmentation fault

I have this same problem with ANY opera package, even with all the motifs you could want installed (from another thread I was reading here) static, etch, old, new, nothing seems to work.  If anyone has any insight into this little issue, I'd greatly appreciate a reply/suggestion.  Firefox just isn't doing it. 

Thanks ahead for any light you can shine my way.  KCK

There: before I even pressed post, I rechecked and indeed the M2: errors have to do with the mail settings in the opera6.ini file and I got that all taken care of now all I get is a segmentation fault?  

HELP PLEASE!?

---

### Post by kittcankitt on 2005-10-21
To further complicate/confuse things I might add that right after I installed breezy and took care of any updates, the first thing I did was install Opera (the etch deb for breezy) and it did indeed work.  I was using opera quite flawlessly with my old backed-up .opera folder even.  Bookmarks, prefs, everything was exactly the way it should have been and now "SEGEMENTATION FAULT" everytime.

Help anyone?

---

### Post by flyingbrass on 2005-10-21
I don't know the answer, but the same happened to me after a clean Breezy install.  I've tried several Opera versions.  In the beginning the etch/Ubuntu version worked.  After trying static, I went back to the shared version and got seg faults at startup.  So, I'm back to static. It's working fine except it crashes at the slightest whiff of java.  I've installed Sun's java, have it set up correctly in alternatives, and Opera is pointed to it, but no go.  

You might try the static deb.

---

### Post by Z0l on 2005-10-25
I've just found a solution, and updated the wiki, check it out
[https://wiki.ubuntu.com/OperaBrowser]("https://wiki.ubuntu.com/OperaBrowser")

---

