---
title: "/boot partition full - Need help either re-partitioning or solving another way"
date: 2015-03-30
forum: General Help
---

### Post by max-perrello on 2015-03-30
[IMG]http://i.gyazo.com/e6014cb65c2c26d6f78b37475a686214.png[/IMG]

Any assistance would be greatly appreciated... I have a system76 Gazelle Professional if it helps, I'm running Ubuntu 14.04. I constantly get error messages about the /boot partition being full, and although I've seen [this]("http://ubuntuforums.org/showthread.php?t=1219270") thread, among others, I am nervous about messing something up. I'm also in a slightly different situation because my laptop runs solely ubuntu, so I have no Windows partition to borrow more space from. 

Thanks in advance for your help.

---

### Post by SeijiSensei on 2015-03-30
Have you run "sudo apt-get autoremove" any time recently?  You may just have some stale kernels in /boot that autoremove should fix.

---

### Post by max-perrello on 2015-03-30
> **SeijiSensei said:**
> Have you run "sudo apt-get autoremove" any time recently?  You may just have some stale kernels in /boot that autoremove should fix.

Thank you very much, seems to have worked. Apologies for such a stupid question :p

---

### Post by SeijiSensei on 2015-03-30
It's not a stupid question at all; many other people have asked the same question here before.  Some earlier versions of Ubuntu did not handle kernel clean-up very well, but recent versions do a better job.  Now, by default, a kernel upgrade should leave you with just two versions, the newly-installed one and the prior one.  

The "autoremove" option isn't very widely known either, I believe.  If you run apt-get with "upgrade" or "dist-upgrade" from the command prompt, you'll sometimes see a notice about software that is no longer needed and can be cleaned out with autoremove.  I don't know how well the GUI front-ends for upgrades handle autoremove since I do all system maintenance from the command prompt.

---

