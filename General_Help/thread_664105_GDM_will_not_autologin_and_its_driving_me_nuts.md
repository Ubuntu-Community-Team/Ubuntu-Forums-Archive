---
title: "GDM will not autologin and its driving me nuts"
date: 2008-01-10
forum: General Help
---

### Post by gregh on 2008-01-10
Hi,
I have a fresh install on gutsy with mythubuntu loaded from the repository.
I am trying to get it to auto login and this is the issue.

I have set the auto login fromthe gdmsetup and it does not work - however timed logins do.

I have checked the conf files etc and it all looks fine.

Where do I start debugging this? I can find references in the messages file or syslog

Thanks,

Greg

---

### Post by zvacet on 2008-01-11
Did you try **system>administration<login window>security tab>enable automatic login>select user**?

---

### Post by gregh on 2008-01-11
yes, it is set in there it just does not do it though.

I have also checked in the /etc/gdm/gdm.conf-custom an confirmed it is actually set in the file and it is.

I don't understand why it does not auto login with everything set correctly so i need to try to find out how to debug what is going on.

Thanks,

Greg

---

