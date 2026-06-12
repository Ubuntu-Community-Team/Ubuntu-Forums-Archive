---
title: "Hopefully simple Gnome Schedule question"
date: 2007-10-10
forum: General Help
---

### Post by hibit on 2007-10-10
Learned ladies and gentlemen,

I am attempting to use Gnome Schedule (and therefore anacron) to set up goldenpod to grab any new podcasts each evening. When run from the command line goldenpod uses the config from .goldenpod to determine the list of podcasts to grab. However it appears that when run by anacron, goldenpod executes but grabs no podcasts.

Do programs run by anacron execute as root or some other user (and therefore goldenpod is not seeing the config in my home directory)?

Any ideas appreciated. Thanks.

---

### Post by dcstar on 2007-10-10
> **hibit said:**
> Learned ladies and gentlemen,

I am attempting to use Gnome Schedule (and therefore anacron) to set up goldenpod to grab any new podcasts each evening. When run from the command line goldenpod uses the config from .goldenpod to determine the list of podcasts to grab. However it appears that when run by anacron, goldenpod executes but grabs no podcasts.

Do programs run by anacron execute as root or some other user (and therefore goldenpod is not seeing the config in my home directory)?

Any ideas appreciated. Thanks.

Things run in cron do not have the environment set as in a terminal session, everything has to be specifically set up - usually in a separate executable script that cron runs.

---

### Post by scruff on 2007-10-10
As user, run this command:

```
crontab -l
```

And post the output here. I am assuming this Gnome Schedule app uses crontab of course... As stated by dcstar, you have to be sort of explicit with cron as your normal shell environment isn't available as it is from a terminal. A really common error for instance, is not changing directory (or using the full path) to where your script lives, or where you want the output (or in this case, the downloaded podcasts) to be saved. I see this a lot when users state running the command or script manually works, but it doesn't through cron.

---

