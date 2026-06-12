---
title: "Gmail IMAP errors in Evolution"
date: 2008-05-05
forum: General Help
---

### Post by Joshua on 2008-05-05
I have two accounts that are configured the same way in Gmail, but when I try to connect to them with IMAP in Evolution one of them works fine, while the other one keeps giving me a strange error.  Upon connecting, I'm asked for a password for each account.  I enter the first one, and it connects, and then I enter the second one, but rather than connecting to the second one I get an error that says something like:

Unable to authenticate to IMAP server.
IMAP command failed: [ALERT] Invalid credentials (Failure)

Please enter the IMAP password for
[EMAIL] on server imap.gmail.com
[Password Space]
[ ] Remeber Password
                  Cancel  Ok

It doesn't matter what I put in there.  I keep getting the error.

It's similar to the problem described at this site:
[http://www.mail-archive.com/evolution-list@gnome.org/msg07690.html]("http://www.mail-archive.com/evolution-list@gnome.org/msg07690.html")

When I start Evolution from command line I get the following line each time I try to submit a password for the error box that I described above:
```
e-data-server-ui-WARNING **: Key file does not have key 'imap:[EMAIL]'
```

I don't think the order for entering the passwords matters.  I've reconfigured the accounts multiple times for different orders and with only single account setups in Evolution.  The working account always works, and the broken account never works.

Also, I think that when I finally cancel out of the error box above, there is some sort of problem in the background, because Evolution starts running slower, and will sometimes lock up when I try to close it.

Anyone know what's wrong here?  I'm using 8.04, and AMD64.

---

### Post by Joshua on 2008-05-05
Also, I'm pretty confident that this is a problem in Evolution, but maybe there is something new in Gmail that is causing it.  The account that works is several years old, while the account that doesn't work is only about a year old.  Also, the account that works has very little email in it, while the one that doesn't work has about 300 emails.  Don't know if any of that could be related.

---

### Post by jeSah8ci on 2008-09-17
> **Joshua said:**
> Also, I'm pretty confident that this is a problem in Evolution, but maybe there is something new in Gmail that is causing it.  The account that works is several years old, while the account that doesn't work is only about a year old.  Also, the account that works has very little email in it, while the one that doesn't work has about 300 emails.  Don't know if any of that could be related.

I'm having the same problem. Did you find any workarounds or solutions Joshua?

---

### Post by alecz20 on 2008-10-23
I have a similar problem, but with only one account.

Evolution starts fine, and connects, but after about 24 hours, it gives me that error message, if I re-enter the password, it reconnects.

---

### Post by chikorita on 2011-10-19
I had this problem and this worked for me:
[http://www.mydigitallife.info/fix-gmail-imap-invalid-credentials-or-web-login-requires-failure-error/comment-page-2/#comment-937869](http://www.mydigitallife.info/fix-gmail-imap-invalid-credentials-or-web-login-requires-failure-error/comment-page-2/#comment-937869)

Hope it works for you!

---

