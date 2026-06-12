---
title: "System stalling on Mail Transport Agent (MTA) Sendmail"
date: 2008-06-08
forum: General Help
---

### Post by Thomas Tolleson on 2008-06-08
Hi!

My cat crashed my laptop running gutsy Gibbon and now I'm having a problem with the system startup stalling on 

Mail Transport Agent (MTA) Sendmail starting

If I let it sit for a few minutes, it will continue to startup, but this delay was not present before the crash.

Any advice?

Thanks

THT

---

### Post by Titan8990 on 2008-06-08
My advice: #apt-get purge sendmail

It is common for startup to hang on things such as MTA if the computer is not connected to the internet.

If you are not using sendmail then uninstall it with the command above.

---

### Post by Thomas Tolleson on 2008-06-09
Thanks for the advice. I ran the command, and it appeared to uninstall sendmail. I rebooted the machine, and it STILL listed

**Starting Message Transfer Agent (MTA) Sendmail**

and it stalled. 

When the system finally booted, I tried to uninstall sendmail again to make sure it was done, and the system told me that sendmail was no longer installed.

I rebooted the system, and yet again it listed

**Starting Message Transfer Agent (MTA) Sendmail**

And stalled.

This strikes me as very weird. Is my laptop haunted?

---

### Post by Titan8990 on 2008-06-09
There are other MTAs that use sendmail on the backend. So lets check to make sure there is not some other MTAs on the machine trying to use sendmail.

#apt-get purge postfix

#apt-get purge exim4

After that you can check you services list via System -> Administration -> Services

MTAs are often listed as "Mail Agents" in your services list. If there is still a MTA listed in your services list then uncheck it.

Good luck.

---

### Post by Thomas Tolleson on 2008-06-10
That worked! Thanks!!!

---

### Post by Titan8990 on 2008-06-10
Good to hear :).

---

### Post by talikarng on 2008-06-20
As well as uninstalling sendmail I found that I had to also uninstall sendmail-bin to fix the problem.

---

### Post by dmflad on 2009-03-25
Recently started having boot stall at MTA spot. I did 
> apt-get purge postfix exim4 sendmail
and of the three only exim4 was on LT.

---

