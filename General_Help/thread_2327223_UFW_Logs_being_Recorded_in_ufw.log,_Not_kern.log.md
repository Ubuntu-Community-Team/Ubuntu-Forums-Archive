---
title: "UFW Logs being Recorded in ufw.log, Not kern.log"
date: 2016-06-08
forum: General Help
---

### Post by ulrichkenneth on 2016-06-08
Hello All, 

First off I know that if I want to stop logging to uncomment the line that says "& stop" in the /etc/rsyslog.d/20-ufw.conf or the 50-default.conf but that is not what I want. 


I want any and all logs dealing with UFW to go to the /var/log/ufw.log. 

I tried the following and can't get it to work.
:msg,contains,"[UFW ", "[UFW AUDIT]" /var/log/ufw.log

Any assistance would be appreciated.

P.S. Granted I've seen several articles/posts/websites dealing with similar. I have not seen one that wants to do what I want it to do.  The main thing was to do "alias dmesg="dmesg | grep -v "UFW""

I also tried to append the "& stop" and "& ~" at the bottom of the 20-ufw.conf with no success.

---

