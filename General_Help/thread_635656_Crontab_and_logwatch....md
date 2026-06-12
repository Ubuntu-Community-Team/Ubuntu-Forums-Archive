---
title: "Crontab and logwatch..."
date: 2007-12-08
forum: General Help
---

### Post by Snakob808 on 2007-12-08
I was wondering if anyone could help me get cron to e-mail a summary of my logs (via logwatch) daily?  

I created a crontab for root and did the following entry...

> 0 0 3 * * * logwatch --mailto [address] --detail low --range all

This is not working.

> logwatch --print --detail low --range all

Will work from the command line, but...

> logwatch --mailto [address] --detail low --range all

will not.

Any help would be greatly appreciated.

---

### Post by Anduu on 2007-12-09
Try creating a script and running it through cron.

---

