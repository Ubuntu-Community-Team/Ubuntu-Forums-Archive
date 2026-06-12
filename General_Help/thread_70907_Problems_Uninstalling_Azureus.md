---
title: "Problems Uninstalling Azureus"
date: 2005-10-01
forum: General Help
---

### Post by ale_mza on 2005-10-01
Hi. I don't like to ask every problem I find in my Ubuntu, because I know that with some searching and reading in the forums, i'll might find the solution to my problems. 
But after reading all threads about azureus, I can not solve my problem. 

I installed latest version of azureus, from the command line. Very simple process, and got it "working", since the program would load, and everything, but when I try to open a torrent, it does not download, and gives nat error. I use cable modem, don't have a router, and neither a firewall, and when checked on pcflank, all my ports appeared as open. The same happened to me with ABC and G3. But Gtorrent, or Bittornado, works. So I gave up on them, and now I want to uninstall azureus, and don't know how. From the packages repository doesn't work, because it doesn't know azureus is in the system. 
And when I type "sudo make uninstall" in the command line, it gives me this error: "there's no rule to make the objective *uninstall* (no hay ninguna regla para construir el objetivo uninstall).
Any ideas? Thank you very much, sorry to bother all of you!

---

### Post by mlomker on 2005-10-01
Azureus is just a java program and everything is in the one directory.  Deleting the directory should do it.

---

### Post by ale_mza on 2005-10-01
Thank you very much mlomker! Didn't know that about java programs!! good tip!!

---

