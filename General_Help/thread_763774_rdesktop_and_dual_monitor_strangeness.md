---
title: "rdesktop and dual monitor strangeness"
date: 2008-04-23
forum: General Help
---

### Post by DaveHartburn on 2008-04-23
After some effort, I have managed to configure my ATI radeon card to support multiple desktops, however I have a very strange rdesktop problem as a result.

After first powering up, I can rdesktop to windows hosts without a problem. However after the screen saver kicks in for the first time, whenever rdesktop is running, the left (main) screen goes blank! It knows what is supposed to be there as the pointer (which you can see) changes as it moves over various icons and dialog boxes. The screen is just black. The right screen is fine and usable.

Now, if I kill rdesktop, the left screen comes back to life. On starting rdesktop again, the screen instantly goes black. If you leave it for a while, every so often you get a split second flash of what the left screen should look like.

If (even straight after a cold boot), I try to set my screen saver preferences, the window hangs. After experiencing the rdesktop problem this morning, I killed off my screen saver processes and still have the problem.

As far as I can tell, rdesktop is the only app which triggers this problem.

I'm on 8.04.

Any ideas on how I can start to debug this one?

---

