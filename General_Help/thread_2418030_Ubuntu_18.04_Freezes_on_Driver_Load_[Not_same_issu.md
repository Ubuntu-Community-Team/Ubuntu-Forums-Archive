---
title: "Ubuntu 18.04 Freezes on Driver Load [Not same issue as is common]"
date: 2019-04-30
forum: General Help
---

### Post by mrcharl3s on 2019-04-30
The problem:
On the first couple of installs I was logging in and after about 2 seconds the mouse froze and I was unable to do anything. So I restarted the machine in recovery mode for Ubuntu 18.04 uninstalled and reinstalled some drivers switched between Nouveau and Nvidia and discovered I still couldn't do anything if I booted Ubuntu normally. 

So I wiped the boot drive and reinstalled it. Same issue arises except this time when I switched from Nouveau to Nvidia Ubuntu freezes in recovery mode as well - which is a bit of an issue considering the root shell cannot install new modules (!).

I've scoured some number of forums and similar questions and tried all their suggestions but it just doesn't seem to fix the problem.

My PC:
Intel 4690k 
Nvidia 970
Gigabyte Board.
A generic SSD.

-Bonus Information-(that's relevant)
Back when I was using windows I had horrendous driver issues whenever I installed a new update. Took the thing in to get repaired at the local store. The blokes there said I had a driver incompatability with the Intel onboard graphics and the Nvidia graphics... even though both monitors were and still are cabled on HDMI and DP2 to the graphics card itself. They said they disabled the Intel graphics to fix the issue. Which of course was some BS cause it certainly was not disabled. But the thing did function. 

Unlike windows (even with Intel graphics enabled in the BIOS) I cannot see the Intel graphics as an option for graphics in the proprietary drivers section. It does show up doing grep VGA in terminal however.

----------

Any help with this issue would be fantastic. Going back to windows is not an option and the only other distros I tried failed fantastically. (Kali never made it to boot and Debian froze at some generic boot screen.)

***Update*** 
Enabled networking and used the Ubuntu recovery options to do a package fix thing. 
Anyway that made things worse. When attempting to boot regular ubuntu the screen freezes at the pink. 
When attempting to boot after recovery screen it simply flashes a cursor at the top of the screen. 

-> another reinstall now needed.

---

### Post by mörgæs on 2019-05-01
Hi, welcome to the fora.

It will be helpful to see all hardware details. Please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it to the command line, run it and paste lshw.txt here in CODE tags.

---

