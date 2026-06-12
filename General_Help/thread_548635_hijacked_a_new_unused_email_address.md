---
title: "hijacked a new unused email address"
date: 2007-09-11
forum: General Help
---

### Post by sbms on 2007-09-11
I'm at a loss for how this happened (although I am not suprised). 

I created a new user account, and added the user name to my newaliases (postfix install) file so the user can begin to send/recieve mail.

I send a single email from my admin account (not root) to the new user account's email address from within the same server. Everything seemed fine end of request.

The next day hen  the user has a chance to test his mail (users cannot login to server (/bin/false in passwd file) using mozilla-thunderbird as client, for the first time, he is getting spam!!!

He didn't even give out the email address yet (so it can't be from a job board or web site).

I am at a loss for how this new address was farmed, and where I should look. The server is Ubuntu, running Postfix, and the only user login is my admin all the rest are turned off.

Can anybody give me some suggestions on where to look?

Thanks
Tom

 :confused:

---

### Post by mrxinu on 2007-09-11
Without more information it's hard to tell.  Was this a pre-existing domain?  Could it be the previous owner had already put that username out there?

---

### Post by Shazaam on 2007-09-11
Check the logs and see where they went.;-)

---

### Post by sbms on 2007-09-12
the domain has been around and there are 6 active email addresses. This email address was newly created and unique so it wasn't recycled. Looking in the log file I dont see any activity except the initial pop login for the first test message.

---

