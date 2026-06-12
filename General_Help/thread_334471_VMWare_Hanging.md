---
title: "VMWare Hanging"
date: 2007-01-08
forum: General Help
---

### Post by nhidog on 2007-01-08
I have VMWare setup with MS Windows VM on both my laptop and my workstation.  My workstation is stable as a rock (Dell Dimension 4600), but my laptop (Thinkpad T60) VM hangs up anywhere within 5-20 minutes of usage.  The computer itself is not completely dead as I can still see the process monitor which I have added on my panel still scroll, however all inputs cease to respond.  I have the same problem on VMWare Server as well as VMWare Player, so I'm out of ideas what to try next.  My laptop is completely stable when there is no VM running, but sometimes I need to do some work in a Windows environment.  Please help me as I do not wish to boot into my Windows Partition any longer.

Thanks,
Quang

---

### Post by lifeempowered.com on 2007-01-12
Yes, I have the same problem!  I've found that the hang lasts exactly 5 minutes every time.  It usually does it when I type a URL in IE and hit enter.  When my CPU monitor is up in linux I can see that CPU usage is at 0 % during this hang.  I've tried disabling the CDROM in my vmx file, changing memory size, debugging mode, etc., nothings seems to fix it.](*,)

---

### Post by ttias on 2007-01-12
I had the same problem. I solved it by upgrading to the 2.6.19 kernel. I've seen other people solve the problem by disabling speed stepping in the BIOS. see the following post [http://www.vmware.com/community/thread.jspa?threadID=59651](http://www.vmware.com/community/thread.jspa?threadID=59651).

---

