---
title: "Email Error Notifications on Cron Bash Script mv cp rsync"
date: 2017-02-03
forum: General Help
---

### Post by jeff140 on 2017-02-03
Wondering if anyone can point me to an example of how to setup a bash script that excutes cp mv and rsync commands and only sends an email if there were errors with any of those commands and what the errors are.  In addition it should email if the cron event to execute the script fails, or in other words if the bash script doesn't run at all or exits prematurely with an error.


Thank you!

---

### Post by TheFu on 2017-02-03
cron sends output to the local MTA, if configured.  If you don't want all the output sent, just errors, then redirect stdout to /dev/null and let only stderr get emailed.  So you must setup a correctly working and configured MTA if you expect any email from cron.

On Unix-like systems, every program sets a "return code" variable which says whether it worked or there was some issue.  Working is normally set to 0 (zero).

Whether an MTA will send email or not has a whole different set of rules. For example, if a server is really busy, the MTA will not send email. This is by design.  I think that's over 90% CPU utilized, but you'll want to check the manpage for your MTA to get the specific %.  When the server isn't so busy and the MTA "wakes up" later, it will send any queued emails.

Error handling is something all scripts should do, but most don't because failures happen so rarely.
Anyways, the ABSG will have example of each part of these things.  Google "ABSG bash" to find it.

Run some command .... the check the return code.
```
if [ "$?" -eq 0 ] ; then
  echo "fine"
else
  echo "error."
fi
```
[http://tldp.org/LDP/abs/html/exit-status.html](http://tldp.org/LDP/abs/html/exit-status.html) - exit status

Make sense?

---

