---
title: "apport needs to die"
date: 2008-03-19
forum: General Help
---

### Post by Locke2053 on 2008-03-19
A process named "apport" just ate up 100% of my CPU and all of my available RAM for several minutes. It killed my ability to use my computer... I just barely managed to type "top" to see what was happening as I waited for the process to stop.

I never started this process and I did not have anything crash, to my knowledge. Even if I did, this reporting tool (as I gather it is) should NEVER have run at a high priority and DoS my PC. Availability should always a top priority it design... much much higher than convenient crash dump reporting.

How can I uninstall this app and ensure it does not get reinstalled? This thing is not ready for prime-time and should never have left the QA lab. 

Ubuntu 7.10 64bit Intel. 

Thanks in advance...

---

### Post by chrisccoulson on 2008-03-19
Apport is the crash reporting service. It was running because an application had crashed, and it was writing information about the crash to allow you to open a bug report on Launchpad. There is no use saying 'this thing is not ready for prime-time and should not have left the QA lab', when most people on here have no issues with it. If you let Apport run, you will find crash dumps in /var/crash. I suggest you use these to find out what applications is crashing.

---

### Post by Arthur Archnix on 2008-03-19
Uninstall it through synaptic. Search for apport and completely remove it and gtk-apport.

Best pose questions first, then gripe about stuff. Otherwise you risk having threads moved to "testimonials" which would be bad for actually getting help.

---

### Post by chrisccoulson on 2008-03-19
Do you have any idea what application is crashing? If Apport is intrusive enough to consistently disrupt workflow on your machine, then you need to sort out the problem application.

---

