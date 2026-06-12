---
title: "Terminal freezing at MS installer agreement"
date: 2013-01-20
forum: General Help
---

### Post by grey1beard on 2013-01-20
I'm attempting an installation of playonlinux in 12.04, running **sudo apt-get install playonlinux**, and near the end of the process, during the installation of ms fonts, a window pops up asking for agreement to run the ms installer.
If I attempt to click on the 'OK' it doesn't respond, nor to any other attempt, like using the 'Enter' button.

Unable to progress, I then closed the terminal, and opened a new one.
When I tried running the command again, it said something along the lines that > a folder couldn't be unlocked, was someone else using it ?.
As I had no answer to this, I rebooted and tried again.
The downloaded packages were installed, but the same ms request opened, and once again, it didn't respond to any mouse or keyboard input.

Can anyone help me past this block ?

John

---

### Post by raja.genupula on 2013-01-20
you have cancelled the process for the 1st time it self.so I think something might be dropped already and stopping new one.

I mean you just uninstall it and reinstall it. Remember use purge while doing the uninstallation.

---

### Post by steeldriver on 2013-01-20
I think I know the screen you are talking about - if so the answer is to use the TAB key to navigate to the accept box and then press enter (or space works as well I think)

---

### Post by grey1beard on 2013-01-20
> **steeldriver said:**
> I think I know the screen you are talking about - if so the answer is to use the TAB key to navigate to the accept box and then press enter (or space works as well I think)

I'll give that a try before going raja's uninstall route, but if memory serves, the OK button was already highlighted, so I thought it would respond to just hitting the 'Enter' key.
Anyway, once more unto the breach....
Regards
John

EDIT
> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? is one of the hold ups if I just retry terminal before rebooting, so that is my next move.

---

### Post by steeldriver on 2013-01-20
'unable to get lock' errors usually mean that you have more than one package manager open e.g. trying to use apt-get in the terminal while Synaptic or Software Center is still running

---

### Post by grey1beard on 2013-01-20
Thanks steeldriver, that worked on two successive pop-ups. :)

John

---

