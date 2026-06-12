---
title: "Update to 24.01.1 LTS fail."
date: 2024-09-01
forum: General Help
---

### Post by versss on 2024-09-01
my horror story of "updating" the system


I'm new ubuntu user. 22.04 was first version I ever used. Installed it from bootable stick, all worked fine, managed to fix all the problems with AI and google search while using it. Had it configured great for work, everything worked.


Today I was noticed that there is new ubuntu released and available for update: 24.04.1 LTS
Wrongly assumed it's gonna be smooth transition.
Tried to update via GUI - failed, I think I only partially upgraded.
Went to terminal and did "update + upgrade", around 300MB downloaded and installed
reboot, ubuntu loaded, software didnt (ie. vpn client - reinstalled, it worked)
went to terminal, did: 


sudo dpkg --configure -a
sudo apt --fix-broken install


Another 600MB of files downloaded (?). Reboot, it seems like system tells me I'm on 24.04.1 LTS, background changed to black crown (I assume this is 24.04.1 LTS style?)


When I go to "software upgrade" GUI now, it tells me "not all updates can be installed", I have an option to "run a partial upgrade" unfortunately it fails tellin me: 
"Can not upgrade
An upgrade from 'noble' to 'jammy' is not supported with this tool.


Hold on, I thought I was updating from jammy to noble? 


Why all of this is so confusing. I'm not sure what I did wrong. Why there is a prompt on stable 22.04 telling me to update when this is the outcome? What am I supposed to do now?

---

### Post by grahammechanical on 2024-09-01
The black background with a less black crown is indeed one of the default backgrounds that are part of on upgrade to Ubuntu 24.04 LTS.

The offer to do an online upgrade from 22.04 LTS to 24.04 LTS has only just been released. It should have been released several days ago but was delayed for a few days.

You say the that upgrade by the GUI failed. How did it fail? What happened? This information will help us try to understand what happened. What can I suggest? Run Software and Updates regularly. Things might sort themselves out. Are you happy using the terminal?

```
sudo apt update
sudo apt upgrade
sudo snap refresh
```

If there are error messages please add the message to your thread. The partial upgrade option appears if the are conflicts between packages/libraries. Partial Upgrade solves conflicts by removing packages. This might or might not improve things.

Regards

---

### Post by bloozguy on 2024-09-07
You miss-spelled "refresh". Not a big deal unless someone is copy/pasting

---

