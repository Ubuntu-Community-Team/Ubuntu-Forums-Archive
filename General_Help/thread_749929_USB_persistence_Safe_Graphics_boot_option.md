---
title: "USB persistence: Safe Graphics boot option"
date: 2008-04-08
forum: General Help
---

### Post by Blind Tiger on 2008-04-08
I have successfully installed Gutsy to a 4GB flash drive.  The persistent boot option does not fully boot because of a video card issue.  I can boot successfully into the Ubuntu desktop using the safe graphics boot option.  

My question is how can I edit the xorg.conf file to make the necessary changes to boot using the persistent mode?  Any changes I make while in safe graphics mode are not carried over to the next boot, so I am caught in an endless loop.  Any help would be greatly appreciated.  Thanks.

--NOTE:  SOLVED--

I used the xforcevesa boot option with the default boot option (persistence) and was able to boot into persistent mode, and save all changes.  So I'm off and customizing my pendrive!

---

