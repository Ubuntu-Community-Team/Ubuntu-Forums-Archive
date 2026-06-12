---
title: "How can I force Beagle to re-index a directory?"
date: 2007-09-05
forum: General Help
---

### Post by tbraun on 2007-09-05
Hello!

In short: Is there a command or option, which allows me to force Beagle to re-index a particular directory?

I know about running it with the EXERCISE_THE_DOG environment variable, which forces a complete re-index of everything. However, for that I have to stop beagled, set the variable, re-start it, then stop it again once finished, unset the variable and restart. It seems to me as if there should be an easier way to do this, and also just for specific directories?

Just in case you are wondering why I would need this: I get the impression that inotify doesn't seem to work for Truecrypt container files. Beagle works well for everything else for me, but it doesn't seem to notice any changes I make to my encrypted folders. So, I guess there is a problem with inotify and Truecrypt. I could even live with it, as long as it is possible for me to occasionally easily force a re-indexing of some sub-directories...

Any help or insight is greatly appreciated...

Tom

---

