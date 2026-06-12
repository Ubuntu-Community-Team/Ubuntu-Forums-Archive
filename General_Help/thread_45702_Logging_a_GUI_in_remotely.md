---
title: "Logging a GUI in remotely?"
date: 2005-07-01
forum: General Help
---

### Post by tspec on 2005-07-01
Hope this is a simply one. I was vnc'd into a box running ubuntu, the vnc session froze and i couldn't get back in though i could still ssh to the box. I decided to reboot the box remotely but i still can't vnc in which i assume is due to the fact that it's probably sitting there waiting for me to log one of the accounts in. 

Is there a way from command line to log the GUI interface back in so i can start vnc'ing to the box again? 

Any help would be greatly apprecieated.

---

### Post by art on 2005-07-01
What I did the last time I had a similar thing, I removed the .vnc directory on the remote machine and ran vncserver again, setup again, and it worked... Stupid but did the job for me.

---

