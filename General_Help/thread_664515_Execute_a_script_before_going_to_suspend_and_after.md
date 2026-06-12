---
title: "Execute a script before going to suspend and after waking up"
date: 2008-01-11
forum: General Help
---

### Post by schallstrom on 2008-01-11
Hi, I couldn't find any useful documentation on how exactly suspend works in Ubuntu 7.10 in the Wiki. The articles I found are either incredibly old (one for Ubuntu 4.10!) or just don't cover the information I need. I couldn't even figure out which suspend implementation Ubuntu 7.10 is using (swsusp, suspend2).

Well, the actual problem I have is that I want to execute some commands before Ubuntu goes to suspend. More precisely I want to unmount cifs and/or sshfs network devices because that alway has annoying effects after waking Ubuntu up again.

So where would be the proper location to add those commands?

---

### Post by rrwo on 2008-01-11
Try installing the hibernate package
```
sudo apt-get install hibernate
```
In the /etc/hibernate directory there are configuration files that allow you do do this.

---

### Post by schallstrom on 2008-01-13
Not good. When I install the hibernate package, uswsusp gets installed as a dependency, and then suspend (both to RAM and to disk) does not work any more at all.

There must be some easy way to run a script before suspending.

---

### Post by sisco311 on 2008-01-13
the suspend(resume) scripts are in the /etc/acpi/suspend.d(/etc/acpi/resume.d) directory

---

### Post by schallstrom on 2008-01-13
Great, thanks sisco!

---

