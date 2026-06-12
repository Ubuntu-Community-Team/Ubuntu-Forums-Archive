---
title: "How do I know what's new in linux-image update?"
date: 2007-06-22
forum: General Help
---

### Post by xp_newbie on 2007-06-22
I am currently running kernel 2.6.15-28.53:
> 2.6.15-28-686 #1 SMP PREEMPT Tue Mar 13 20:55:53 UTC 2007 i686

I got a message from Update Manager that new version 2.6.15-28.55 is available.

I looked at the description provided by Update Manager, but there is no description of "What's Different in this latest version".

Where can I find a description of the difference between kernel 2.6.15-28.53 and 2.6.15-28.55?

Thanks,
Alex

---

### Post by 5-HT on 2007-06-22
You can check the changelog. It sometimes takes a bit for the repos to sync up though. Another way to go would be to take a look at: [http://ubuntuforums.org/forumdisplay.php?f=13](http://ubuntuforums.org/forumdisplay.php?f=13)
cheers,

---

### Post by xp_newbie on 2007-06-22
> **5-HT said:**
> Another way to go would be to take a look at: [http://ubuntuforums.org/forumdisplay.php?f=13](http://ubuntuforums.org/forumdisplay.php?f=13)
Thanks. This indeed lead me to the following:

[[USN-464-1] Linux kernel vulnerabilities]("http://permalink.gmane.org/gmane.linux.ubuntu.security.announce/552")

Which suggests that this update is some kind of a security fix ("critical" in Windoze world). No details about the nature of the vulnerabilities, though.

> **5-HT said:**
> You can check the changelog.

What changelog? Is there a URL for it?

Thanks,
Alex

---

### Post by 5-HT on 2007-06-22
> **xp_newbie said:**
> Thanks. This indeed lead me to the following:

[[USN-464-1] Linux kernel vulnerabilities]("http://permalink.gmane.org/gmane.linux.ubuntu.security.announce/552")

Which suggests that this update is some kind of a security fix ("critical" in Windoze world). No details about the nature of the vulnerabilities, though. 

Scroll down a bit in that link, the reason for the update and details about the changes are in there. 


> **xp_newbie said:**
> 
What changelog? Is there a URL for it?

Thanks,
Alex

It's just a small file detailing the who, why, and what of an update. You can view changelogs in Aptitude, Synaptic, Update Manager, etc...
You can also view the changelogs by visiting [http://changelogs.ubuntu.com/](http://changelogs.ubuntu.com/) (might be a bit outdated though)

---

