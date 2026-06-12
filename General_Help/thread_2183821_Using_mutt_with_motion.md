---
title: "Using mutt with motion"
date: 2013-10-26
forum: General Help
---

### Post by G0HXT on 2013-10-26
Hi

Ubuntu server 13.10 but had the same problem on 13.04
Using motion and mutt to send e-mail
When running as deamon no e-mail gets sent.
if I pipe the output to a file I get "unable to send message" so the trigger to send the mail is working
Enabling debug (-d 2) on mutt gives no information
I think that motion is running under the user of motion
If I load motion whilst logged in as myself it works so I'm sure its access rights but can't work out what.
Can anyone help or have similar experience with this?

Thanks in advance

---

### Post by G0HXT on 2013-10-26
Further testing....
If I login with terminal and load motion with "sudo motion" and then logout everything works as it should.  If I start motion with "sudo service motion start" no e-mail is sent.

---

