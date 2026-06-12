---
title: "Repairing broken Gutsy"
date: 2008-04-28
forum: General Help
---

### Post by Jonatan_w on 2008-04-28
Hi

The other day I decided to switch computer chassis and did so, while I was at it I removed one hdd I wasnt using. Upon booting Gutsy again the system came to a complete halt right after the loading bars were completed and the screen goes "Signal lost" then comes back up again. Screen turns black and keyboard refuses to respond to any command (no ctrl+alt+del, no ctrl+alt+esc and no numlock led activity.) I thought it might be a hdd wiring issue and tried rewiring most things without any success. Ive tried to boot in safe mode and it locks before login is made available however it doesnt freeze my keyboard so upon pressing ctrl+alt+del the system reboots properly. 

I have tried updating the system to hardy by chroot:ing into my system from the live cd then doing:
apt-get update
apt-get upgrade
apt-get dist-upgrade

First two works properly and third command just says "nothing to do". After the whole update thing I decided to try booting again with no success and system locks at the same place. Ive been going through all of the logs to see if I can find anything that differs from the logs before when the system was booting properly, havent found anything that looks like its the cause but then again im not sure exactly what im supposed to look for.

I would greatly approciate some assistance and I bet you need some logs posted but since I dont know which one of the logs is most relevant I dont want to post them all here atm, please let me know which logs you need to help and I will provide.

---

