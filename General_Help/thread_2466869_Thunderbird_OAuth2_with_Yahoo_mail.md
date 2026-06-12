---
title: "Thunderbird OAuth2 with Yahoo mail"
date: 2021-09-08
forum: General Help
---

### Post by btedm on 2021-09-08
I have been using Thunderbird with Yahoo mail and getting mail by POP using an OAuth2 password.  Yesterday every time Thunderbird tried to check the mail a new browser window was opened asking for a password.  This happened on two different computers.  I was able to restore the connection to Yahoo mail by generating a new password in Yahoo mail, and by switching the (Account Settings, Server Settings, Authentication Method) from OAuth2 to Normal Password.   Then when getting mail a window opens asking for the password and I entered the password from Yahoo and checked the box to save the password.  This seems to be a change in Yahoo because it started after Thunderbird had been open for over an hour with no problems up to that point.  Am I the only one, or have others seen this problem?

---

### Post by TheFu on 2021-09-11
I don't use yahoo mail or pop3.

I had to relax some TB TLS mandatory levels to connect to an email provider last week after a thunderbird upgrade.  Seems the newer settings were trying to force TLS v1.4 when it isn't released yet. I only patch on Saturday mornings. So it was sometime before Sep 4 that the update happened.

Oddly, the connection to the mail servers I run, didn't have this issue, so I suspect it is something that non-standard IMAPS servers do.

---

