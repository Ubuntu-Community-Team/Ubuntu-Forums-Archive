---
title: "system program problem detected"
date: 2015-12-16
forum: General Help
---

### Post by Randymanme on 2015-12-16
A notification box saying "system program problem detected" keeps popping up Ubuntu 14.04's desktop.  How can I disable it?

---

### Post by XBNCPRk on 2015-12-16
Barring any desire to find out and fix the actual problem (which if that is your goal, we will need to know what the actual problem is), you can simply delete the crash logs created by the error. ```
sudo rm /var/crash/*
```  That will get rid of the notification box until the error occurs again.

---

### Post by Randymanme on 2015-12-23
All I need to do is login and those notification boxes start up and  continue to reoccur  for as long as I'm logged-in.  They can only be  seen on the desktop, i.e. not on top of any app GUIs or open windows  other than on top of other of the same notification boxes.

Interestingly,  when I click on the continue button to report the problem I get a  different notification box informing me that ". . . Ubuntu 14.04 has  experienced an internal error . . ."


Fix it?  I thought that I  was supposed to send in an error report and wait for someone else to  fix it as is suggested by following the prompts in the notification box  -- but of course that's the short answer while the long answer is fix it  myself.  Well, okay, I'm willing to give it a go with you folk's help  and direction.

---

### Post by ian-weisser on 2015-12-23
You cannot easily disable the crash notification. It's there for a reason.
If you want to try, uninstall the 'whoopsie' and 'apport-noui' packages. WARNING - your desktop is not designed to run without them.

A crash report might be due to a hard-to-fix-bug (somebody else's problem),..or an easy-to-fix bug (you can easily do it)...or a misconfiguration (your problem)...or a system problem (your problem).

If you're a Linux Registered User, one assumes you have the skills to read the crash report in /var/crash and decide if the issue is a reportable bug or a problem you must troubleshoot and fix yourself.

I worked eight bugs today at launchpad.net:
Two hard-to-duplicate bugs that will require a lot of work (started VMs for them)
Three easy-to-fix bugs: Simple missing LSB headers. In those three cases, I was "someone else". Anyone skills and a couple minutes can drive-by fix a lot of bugs.
Three non-bugs that I closed: Disk full, lost power, OS past EOL. The crash reporter can't tell if a crash is caused by a bug or not.

---

