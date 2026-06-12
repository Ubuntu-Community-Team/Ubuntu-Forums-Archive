---
title: "starting process as user xyz after resume from hibernate"
date: 2007-01-12
forum: General Help
---

### Post by casaschi on 2007-01-12
I'm trying "creative options" to go around some problems I have with skype when resuming after hibernate (whole system freezing when I try to make a call with skype after resume).

A possible attempt is to kill skype when suspending/hibernating ("killall -9 skype") and restarting after the resume.
While the kill step is easy to automate, the automation of the resume part is more challenging.
Assuming all resume scripts are run as root, I tried adding a resume script containing something like this:
   sudo -u username skype
or 
   su username -c skype

but I could not manage to get skype restarting automagically.

Any advise anyone how to restart a user process after hibernate/suspend and resume?

TIA

-- Paolo

---

