---
title: "syslogd help?"
date: 2007-10-03
forum: General Help
---

### Post by eisublime on 2007-10-03
Hi, I've got Ubuntu 6.06 installed on a server with a RAID 1+0 setup and need to be notified if one of the drives fails.  I'm assuming that I can do this with syslogd, but I'm not sure which facility/severity would include a failed drive.  Can I do this with syslogd, or do I need to find another solution?

Thanks
Dylan

---

### Post by fjgaude on 2007-10-03
I think the way some do it is to use the line in /etc/mdadm mdadm.conf file at the MAILADDR line. But I'm not sure where you would want the email to go. Others may.

---

### Post by eisublime on 2007-10-04
I see, i hadn't heard of mdadm before - but you're right that looks like what i need.  I'm a little bit confused reading the docs for it, does it run as a daemon, or do you run it periodically in a cron job or something?

---

### Post by eisublime on 2007-10-04
nevermind, I see that in Monitor mode there's the -f option to run it as a daemon.  thanks for your help!

---

### Post by fjgaude on 2007-10-04
Trust you can get the email function working.

---

### Post by eisublime on 2007-10-05
If the raid array is not a software array configured by mdadm, can it still monitor it?

---

### Post by fjgaude on 2007-10-05
Well, not too experienced with anything other than fakeraid (which is software usually from the motherboard) and Linux software raid, md which is controlled by mdadm. Try the man pages for these two. Likely the monitor mode of mdadm will not see anything other than the arrays it had setup through md.

What kind of raid are you using?

---

