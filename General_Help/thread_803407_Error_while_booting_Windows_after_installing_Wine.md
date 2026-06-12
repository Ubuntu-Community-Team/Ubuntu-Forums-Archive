---
title: "Error while booting Windows after installing Wine"
date: 2008-05-22
forum: General Help
---

### Post by ClaudioVC on 2008-05-22
Hello everybody!
I'm having a problem while booting XP.
My Dual Boot works fine. When I choose to boot WinXP, it restarts the computer, over and over(as WinXp is the default in the dual boot screen):(

I thinks it all began after I installed Wine this morning...Windows was working alright, I switched to Ubuntu and ran a few programs by Wine...now I can't go back to Windows.
Any suggestions of what may have caused that?
Thanks in advance.
Claudio

---

### Post by warp99 on 2008-05-22
Wine wouldn't do anything to the Windows partition, so that's not the problem. Do you see the XP splash screen when booting or not?

---

### Post by ClaudioVC on 2008-05-22
> Do you see the XP splash screen when booting or not? 

No..right after selecting Windows in the boot menu the pc is restarted...The next time I choose, it shows the screen of Safe Mode and then...restart again!
So, no chances it couldn't be Wine?

---

### Post by signseeker on 2008-05-22
Sounds like you might need to reinstall windows. Yeuck.

---

### Post by ClaudioVC on 2008-05-22
> Sounds like you might need to reinstall windows. Yeuck.
I know...By myself I wouldn't care of leaving it the way it is...but unfortunately i'm not the only one that uses this computer xD
Anyway, thanks a lot, **warp99** and **signseeker**!

---

### Post by warp99 on 2008-05-22
> **ClaudioVC said:**
> No..right after selecting Windows in the boot menu the pc is restarted...The next time I choose, it shows the screen of Safe Mode and then...restart again!
So, no chances it couldn't be Wine?

No chance it's Wine because Wine only installs locally to your Linux partition and there are no writes to the MBR as with GRUB or LILO. Personally I don't use dual boot to Windows XP anymore but instead use VMware Workstation/Player and a virtual XP image. 

If you don't us XP for any serious gaming this may be a better option since you can backup the virtual image and restore very quickly without having to reinstall anything. I use VMware because there are a lot of different images VMware likes to call "Virtual Appliances" with different operating systems and single use applications. Check out the list, pretty impressive:

[http://www.vmware.com/appliances/](http://www.vmware.com/appliances/) 

Gives more meaning to the words "try before you buy". I also heard that VirtualBox is suppose to be a good product, but I've never used it so I can't speak from experience.

---

