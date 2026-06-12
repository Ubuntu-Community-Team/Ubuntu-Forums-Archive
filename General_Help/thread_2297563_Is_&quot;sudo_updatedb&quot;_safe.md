---
title: "Is &quot;sudo updatedb&quot; safe?"
date: 2015-10-05
forum: General Help
---

### Post by vasa1 on 2015-10-05
I was finding some icon files (in */usr/share/icons*) using *locate*. I deleted some icons I didn't need and then ran *locate* again. Those deleted files were still listed.

After reading a bit, I got the feeling that *updatedb* runs once a day as directed by *cron*.

My question is how can I run *updatedb* additionally whenever I want? There are suggestions that *sudo updatedb* will do the trick but I would like to know whether it's safe to run *sudo updatedb*.

Edit: one more question

*locate -e* finds existing files (as opposed to leaving out *-e* which shows even deleted files if updatedb isn't run in the meanwhile). And it does it fast! How does it do that?

---

### Post by matt_symes on 2015-10-05
Hi

I've been running sudo updatedb from the command line for years with no issues.

I actually removed the cron job that automatically updates the mlocate database.

Kind regards

---

### Post by vasa1 on 2015-10-05
> **matt_symes said:**
> Hi

I've been running sudo updatedb from the command line for years with no issues.

I actually removed the cron job that automatically updates the mlocate database.

Kind regards
Thanks for that! I didn't want to "sudo" something which I'd regret later.

Marking this "Solved"  :)

---

