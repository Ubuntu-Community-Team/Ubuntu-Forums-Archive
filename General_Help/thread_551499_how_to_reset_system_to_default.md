---
title: "how to reset system to default?"
date: 2007-09-15
forum: General Help
---

### Post by Dogbertd on 2007-09-15
Okay, before I re-install Ubunti Feisty I'll just check that there's nothing obvious I could do to fix this.

In trying to install Slimserver I reset some of the file permissions to my Home/dogbertd folder. This seems to have screwed several bits of my system, and despite my best efforts to re-set those permissions I'm getting nowhere.

Is there a way to rest Ubuntu to a factory default/reset my Home permissions to default?

Or is reinstallation of the entire system the best we can do?

Thanks,

Dogbertd

---

### Post by Slim Backwater on 2007-09-15
I know nothing about slimserver, but in general if you just screwed up /home/dogbertd then it should be pretty ease to fix, it's just a home directory.

Login under a different account and sudo chmod -R u+rwx /home/dogbertd then clean up from there (by clean up I mean remove the x attribute from non-executable, and non-directory, files).

 But if the screw up was that files/ folders outside of /home/dogbertd got their permissions changed (ala chmod -R o-r .*) then I'd forget about it.

---

