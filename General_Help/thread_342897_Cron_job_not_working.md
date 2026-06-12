---
title: "Cron job not working"
date: 2007-01-20
forum: General Help
---

### Post by JustinAlf on 2007-01-20
25 * * * * totem 

I am trying to set up a crontab so that I can bring up a stream via totem.  I went to crontab -e, and edited it to say this command.  Totem doesn't open up though.  What Am i Doing wrong with the Cron?  Could someone please Help.  I'm not a linux newbie, just new to Cron.  Any help would be greatly appreciated.

---

### Post by dcstar on 2007-01-20
> **JustinAlf said:**
> 25 * * * * totem 

I am trying to set up a crontab so that I can bring up a stream via totem.  I went to crontab -e, and edited it to say this command.  Totem doesn't open up though.  What Am i Doing wrong with the Cron?  Could someone please Help.  I'm not a linux newbie, just new to Cron.  Any help would be greatly appreciated.

As has been posted many times, cron requires the **full** path to any command.

In addition, any command that requires the X system also needs an environment variable set, a search will reveal the details of such things.

---

