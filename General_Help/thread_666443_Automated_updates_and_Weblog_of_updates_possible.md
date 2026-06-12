---
title: "Automated updates and Weblog of updates possible?"
date: 2008-01-13
forum: General Help
---

### Post by Dark Savant0 on 2008-01-13
I am deploying a server for a local business but I won't be around to manage the server (simple file-server, with more features in the future). But I'd like to auto-update the system (apt-get update && apt-get upgrade -y) and then view a log on a website of the updates (whether anything failed). For example, run a cron job once a week that updates the system and then sends the Terminal log to an ftp server, or even to an email address of my choosing. Is there any package that has this functionality or a series of scripts I can use to do this?

---

### Post by erpo on 2008-01-13
I wouldn't update a server without reviewing the updates first since that can result in breakage. Trust me. Install an ssh server and do the updates remotely if you don't want to visit the customer site.

If you absolutely have to run a weekly command without first checking to make sure the updates aren't harmful, you can pipe the standard output to the mail command:

update_command | mail -s "Update output for `date` on Foobar Co file server" [email]your@email.addr[/email]ess

Note those are backticks around the command date. If your keyboard is like mine, the backtick is on the same key as the ~.

---

### Post by Dark Savant0 on 2008-01-13
> **erpo said:**
> I wouldn't update a server without reviewing the updates first since that can result in breakage. Trust me. Install an ssh server and do the updates remotely if you don't want to visit the customer site.

If you absolutely have to run a weekly command without first checking to make sure the updates aren't harmful, you can pipe the standard output to the mail command:

update_command | mail -s "Update output for `date` on Foobar Co file server" [email]your@email.addr[/email]ess

Note those are backticks around the command date. If your keyboard is like mine, the backtick is on the same key as the ~.
I can't think of anything that would break because the machine won't be used for anything but serving files, but I suppose this is still possible.

Is there a tutorial somewhere to setup an ssh server?

---

