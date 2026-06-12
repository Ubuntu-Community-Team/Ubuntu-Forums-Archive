---
title: "Thunderbird password trouble"
date: 2008-04-26
forum: General Help
---

### Post by RumorsOfWar on 2008-04-26
I have set up my ISP email account with thunderbird exactly the same as other email apps, and as its docs instruct. But it never asks for my password to connect to the ISP, so I get the  "failed to connect to shawmail.lb.shwcable.net"  error. (this is the servers name when using a router.)
The same info worked with Evolution.
What am I doing wrong?

---

### Post by gug@fnal.gov on 2008-04-26
Hi,
   It would be helpful to provide more information. How did you add the account in thunderbird? Did you change an existing account or add a new one? When I switched from a popserver to an imapserver account at work (RHEL 4), I first tried just changing setting and that didn't work. I then tried adding a new account and configuring it for imap right from the start and that worked. 
   Based on what you say it is hard for me to tell whether you are having a problem reaching the server (so address or port mis-typed) or you have somehow a saved password that is being pass automatically. First double check very carefully the address and port settings from Account Settings. Then go into Preferences -> Privacy and checked saved passwords. Delete any that look like they point to that server so you can see on your next try if the connect is made properly enough to get to the point of asking for a password. 
   Good luck.

---

### Post by RumorsOfWar on 2008-04-26
Ok, this is a fresh install of xubuntu, the thunderbird account was started as new, not transfered, and the server name was copy/pasted directly from the ISPs page; [here.]("http://www.shaw.ca/en-ca/CustomerCare/InternetSupport/Residential/RoutersandShawServerNames.htm")
"shawmail.lb.shawcable.net" and is the same as another email client uses. 
I have left it at port 110 (pop)/25(smtp) , same as other em client.
 Preferences/privacy/passwords contains no passwords at all.

---

### Post by RumorsOfWar on 2008-04-27
I just deleted that account and redid it. Then it asked for the password and works. :)

---

