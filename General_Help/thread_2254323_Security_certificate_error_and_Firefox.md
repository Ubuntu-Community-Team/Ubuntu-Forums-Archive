---
title: "Security certificate error and Firefox"
date: 2014-11-26
forum: General Help
---

### Post by Deanobats on 2014-11-26
Hi all,
as of yesterday when trying to connect to outlook.com via Firefox I get the message:

You have asked Firefox to connect securely to snt152.mail.live.com, but we can't confirm that your connection is secure.

Further details are:

snt152.mail.live.com uses an invalid security certificate. The certificate is not trusted because no issuer chain was provided. (Error code: sec_error_unknown_issuer) 

I'm on current Firefox (33.0) and Ubuntu 14.04. I don't have this problem on other machines (win 7). The certificate looks fine, the date on the laptop is fine, I've done all the usual stuff, cleared caches, removed cookies etc etc. It only started yesterday as well.

I can connect the first time by typing [www.outlook.com](www.outlook.com), and I get to my mail, but any refresh or seeing other folders and I get the certificate error.

Any suggestions?

---

### Post by bashiergui on 2014-11-26
Do you get an error in other browsers? Update Firefox, see if that resolves the error.

---

### Post by Deanobats on 2014-11-26
No, no other browsers, just Firefox, and I think it is the latest version...

---

### Post by bashiergui on 2014-11-26
There are some troubleshooting steps on this page involving deleting a corrupt database in ff.
[https://support.mozilla.org/en-US/kb/connection-untrusted-error-message](https://support.mozilla.org/en-US/kb/connection-untrusted-error-message)

---

### Post by Deanobats on 2014-11-26
Looks very promising, thanks for that, I'll check it out and report back!

---

### Post by Deanobats on 2014-11-27
Dang! No joy, deletion of the cert8.db file didn't work, I still get the same error. It's only for Outlook.com, no other https:\\ site generates the same error.

---

### Post by Deanobats on 2014-11-27
Whoa! Perhaps I spoke too soon, after two firefox restarts it now seems to be working! Interesting that the error I got, about no issuer chain, was not the one where the deletion of the cert8.db was suggested, but it does seem to have done the trick, at least for now. Now all I have to do is sort out the odd Chromium black screen and I'll be done :)

---

### Post by bashiergui on 2014-11-27
Glad it worked out.

---

