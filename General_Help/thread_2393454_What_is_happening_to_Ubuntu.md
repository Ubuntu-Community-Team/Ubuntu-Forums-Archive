---
title: "What is happening to Ubuntu?"
date: 2018-06-03
forum: General Help
---

### Post by trash1464 on 2018-06-03
I hardly know where to start. For the last 8 months or so it seems my once rock solid 16.04.4 LTS system is getting less and less reliable. System lockups and crashes are a weekly occurrence. Doing a clean reinstall has not helped. Apps like Photoscape and Finewoodworking Archive no longer work. K3b is installed but will not run. Brassero is supposed to be installed by default but is nowhere to be found.  Apps installed via the Software center seem to install but will not run. Vuescan no longer works with a local USB attached Epson V600 Photo scanner. Lastpass has become unreliable. Any type of blank optical disk media shows only 2K free space.   

I seem to be spending more and more time troubleshooting problems than ever before and not finding solutions. Am I the only one having this type of experience?

---

### Post by TheFu on 2018-06-03
Yes.

Issues like this are usually due to failing hardware.  Check the system logs, especially the SMART data on any storage drives, but also look for cable failures and controller issues.

---

### Post by Perfect Storm on 2018-06-04
Sounds like some hardware in your computer is going south. You might want to try another HDD or the cables.

---

### Post by mohicann on 2018-06-04
Indeed, your hardware may be packing up. Of course, it may happen that accumulating tones of applications and dependencies doesn't keep your computer from unexpected crashes and lower performances, and that's probably one of the rare issues I could complain about Ubuntu. however once reinstalled it's rather a sign something is probably getting rotten somewhere.

---

### Post by TheFu on 2018-06-04
> **mohicann said:**
> Indeed, your hardware may be packing up. Of course, it may happen that accumulating tones of applications and dependencies doesn't keep your computer from unexpected crashes and lower performances, and that's probably one of the rare issues I could complain about Ubuntu. however once reinstalled it's rather a sign something is probably getting rotten somewhere.

If doing weekly **sudo apt update && sudo apt upgrade** and there aren't any errors, then it isn't a dependency problem.  Adding PPA or straight .deb installs from unmaintained/untrusted sources is asking for issues.  Usually those issues happen in 3-6 months.  I have systems that have been carefully maintained for over a decade now and have never run into dependency issues with them.  It is only the systems where I go crazy using PPAs or manually installing a random .deb file where problems arise.

My email server started out on Ubuntu 8.04 and hasn't had any dependency issues all these years. It is running 14.04.5 today, but will be moved to 16.04.x before Xmas. New is the enemy of stable.

---

### Post by trash1464 on 2018-06-06
Interesting last couple of days. A memory test ran for 24 hrs with zero errors. All SMART tests also ran with no errors so it looks like the hardware is solid. Executing sudo apt update returned a boatload of references and errors for hplip. There were no hplip entries in /etc/apt/sources.list. Going through the GUI Software & Updates showed two hplip entries on the Other Software tab. Deleting those, now sudo apt apt update and upgrade execute as expected with no errors. Sudo apt autoremove was also executed and things are now becoming more stable.  
Another problem exists with the Ubuntu Software application in that it does not reliably indicate successful completion of an application installation which resulted in redundant  installations of some applications. Cleaning up all that, now things like K3b are working again. Everything not being used (even default apps) is being un-installed to get the machine as lean as possible. Things are looking up. There is still work to do but it looks like I am on the right path. Stability is priority one. Thanks everyone for the advice and pointers!

---

