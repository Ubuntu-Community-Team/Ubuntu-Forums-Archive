---
title: "Running jar file via cron"
date: 2014-09-29
forum: General Help
---

### Post by Lyss_P._Hacker on 2014-09-29
Hi,

I have a Java application which is run at boot time via @reboot cron time specification. Application if updated very often, so it would be great if I could just change jar file and cron will automatically figure out the change and continue running the version of the application (jar file). I actually tried to replace existing jar file with the new version but cron continues to work with the old version until machine is rebooted.

Is it possible to somehow tell cron that it is supposed to work with new version of the app once it is changed?

---

### Post by ian-weisser on 2014-09-29
Cron is (deliberately) not smart enough to use it's own logic to figure out version changes or application changes.
But you can easily push changes to the crontab.

Instead of using an @reboot line in root's crontab, move the @reboot line to a separate file in /etc/cron.d/<application_name>
Every time you update, update/replace that file with the correct information.

This is, by the way, how native packages interact with cron, so the package manager is not trying to edit crontabs.

---

### Post by Lyss_P._Hacker on 2014-10-02
> **ian-weisser said:**
> Cron is (deliberately) not smart enough to use it's own logic to figure out version changes or application changes.
But you can easily push changes to the crontab.

Instead of using an @reboot line in root's crontab, move the @reboot line to a separate file in /etc/cron.d/<application_name>
Every time you update, update/replace that file with the correct information.

This is, by the way, how native packages interact with cron, so the package manager is not trying to edit crontabs.

Thanks for your reply.

Could you please provide more details on how could I realize what you summarized in your reply.

Since I'm not GNU/Linux expert, I have searched the web and tried to perform steps suggested [here]("http://klenwell.com/press/2010/11/cron-d/"), but without success. It seems like there is not a lot of newbie friendly info on the web about how to do what I need, so it would be great if you could provide some.

---

