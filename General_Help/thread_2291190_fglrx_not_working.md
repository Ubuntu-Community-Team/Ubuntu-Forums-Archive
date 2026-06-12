---
title: "fglrx not working"
date: 2015-08-18
forum: General Help
---

### Post by pulpo692 on 2015-08-18
After a kernel update, fglrx don't work any more, only black screen. Wit the kernel update before it was the same thing. Ok there is a solution, going back to an older kernel, but it is a nasty bug, what unexperienced users do? With a black screen? I believe they delete ubuntu and switch to windows. So this bug shoud have a high preference and be fixed in very short time and not happen 2 times within 2 weeks.    Ubuntu Gnome 15.04 64bit

---

### Post by Simon_Tomoko on 2015-08-18
The inexpensive GPU (ATI Radeon 5450HD) that I bought a while back has been discarded by the software upgrades. You either spend your money like a fool buying the latest and greatest hardware or you are left eating dirt. So many have really failed this hardware. It seems that hardware more than a few years old is considered obsolete. 

AMD failed by not giving us an opensource driver. The driver software is not sold for any profit, it is to support the hardware, so why make your cards less attractive to purchase by using proprietary drivers? The Linux developers in general for catering to popular name brand and not looking into the broader spectrum of graphics processing. Sure there are a lot of people in the GPU business these days, but I am sure that the more affordable Asus, Intel, and AMD are somewhere in the top ten? I can understand the commercial developers who work for Microsoft or Sony, they get **told what to do** and do their job loyal to the company. But Linux developers are not working for the company but doing it to better the OS itself. I guess it all goes back to the getting motivated by money issue and not trying to better the world around you.

Link to [3D Acceleration on 5450 HD]("http://ubuntuforums.org/showthread.php?t=2288184")


Thanks for you interest, I hope in the future you find yourself a better solution than I did. I will continue using dual boot 14.04 and 12.04 until I actually need to buy a new box.

---

### Post by QIII on 2015-08-18
pulpo_692:  There are at least three bugs on Launchpad about this.  I'm on my cell phone right now, but I'll try to get back to this.  The quickest thing to do right now is boot to the previous kernel, 3.19.0.25, from GRUB.


Simon_Timoko:  your FUD is ill-informed, adds nothing to help the user and does not even address the real issue here.  If all you can offer is an opinion based on incomplete understanding, please refrain from responding.  FYI: The AMD developers work very closely with the open source developers.  NVIDIA does the same, although there have been some delays and problems in the last 6 months or so.  Things happen.  The problem pulpo_692 probably has is not related in any way to the AMD developers, the NVIDIA developers or the open source developers.  There is a problem in Canonical's packaging that slipped through the testing process into the main repository.  It happened first and was identified in the proposed repository on about July 30 and happened again on the 17th of August when that malformed package was accidentally pushed to main.

After reading your thread (which you linked to) I must say that your conclusion is likely incorrect.  I have tested and published results of the installation and operation of the proprietary AMD driver from 12.02 through 15.04. I am working on 15.10.  Over the course of those tests, the performance of the fglrx driver has been consistently good.  While the performance of the open source driver on the newer generation of AMD cards was initially poor because the open source developers are always trying to catch up, the release of the Hardware Enablement Stack (HWE) for 14.04.3 and the updates to the stack in the releases from which the HWE was backported have largely eliminated those performance problems.

To NVIDIA's credit, their proprietary Linux driver offers a richer set of hardware acceleration options than AMD.

Finally, it is not AMD's job to provide an open source driver.  NVIDIA doesn't.  Open source drivers are in the bailiwick of the open source community.  Despite that, AMD provides engineers to help the open source developers, as does NVIDIA.

---

### Post by QIII on 2015-08-18
pulpo692:

I see from the bug report on Launchpad that someone has confirmed that the build works with the kernel package 3.19.0.27.

If you are up and running right now, hold what you got.  I'll confirm that the build works when I get home this evening.

---

### Post by Theeboon on 2015-08-18
As I said in the other related thread ([http://ubuntuforums.org/showthread.php?t=2291217](http://ubuntuforums.org/showthread.php?t=2291217)), I just removed fglrx completely and now it logs in again. This is a very nasty bug though.

---

### Post by QIII on 2015-08-18
Again, however:  fglrx is affected (the module fails to build) but it is not the cause of the problem.  The failure to build is a symptom of the actual issue.

---

