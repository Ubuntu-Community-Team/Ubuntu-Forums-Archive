---
title: "Problems connecting thunderbird to a Lotus Notes Domino server"
date: 2007-02-08
forum: General Help
---

### Post by blacklobo on 2007-02-08
Question:
I am trying to get thunderbird (or another mail client for that matter) to connect to a Lotus Notes Domino's server that stores the e-mail server side.  Does anyone know how/if that can be done?


Background:
I don't like the Lotus Notes client and I would like to read my corporate e-mail in native Ubuntu.  Today I use VMware to give me a WinXP client and use Outlook with the domino's connector client to get my e-mail but I would prefer to cut the cord on WinXP all together.

---

### Post by koenn on 2007-02-08
depends on the Domino setup. 
Thunderbird uses standard protocols from the TCP/IP suite : SMTP , probably IMAP, etc. 
Domino uses its own protocols / communication mechanisms because it was primarily conceived as "groupware" - a collaboration suite based on databases and replication - and the email in Domino / Lotus Notes / ... uses that database/replication mechanism.

You could check with the Domino administrator if he can support SMTP or IMAP - that would probably work for Thunbderbird.

---

### Post by blacklobo on 2007-02-08
But there is nothing out there like the Domino's connector client for Outlook?  I know I have tried telneting to port 25 and it is not open.  Also not really in a position to ask the Notes Admins to support SMTP or IMAP.  So it sounds as if I am kinda out of luck?

---

### Post by koenn on 2007-02-08
> **blacklobo said:**
> But there is nothing out there like the Domino's connector client for Outlook?  I know I have tried telneting to port 25 and it is not open.  Also not really in a position to ask the Notes Admins to support SMTP or IMAP.  So it sounds as if I am kinda out of luck?
maybe there is a "connector" but i don't know it.

---

### Post by nihilocrat on 2007-02-08
> **blacklobo said:**
> Question:
I am trying to get thunderbird (or another mail client for that matter) to connect to a Lotus Notes Domino's server that stores the e-mail server side.  Does anyone know how/if that can be done?

Background:
I don't like the Lotus Notes client and I would like to read my corporate e-mail in native Ubuntu.  Today I use VMware to give me a WinXP client and use Outlook with the domino's connector client to get my e-mail but I would prefer to cut the cord on WinXP all together.

I've been able to connect to my college's lotus notes server through Thunderbird just fine. I'm bugged more by the fact that I have to download all my mail from the server and store it locally than by the Lotus Notes interface, so I don't actually really use it.

I had to tell Thunderbird to use **port 110** (not the standard SMTP port 25), treat it as a POP mail server, and disable TLS. I might be able to enable TLS if I want to, but I think that might require a bit more setup and I didn't have the patience for it, apparently. Your administrator might have to explicitly enable using POP email clients with the Lotus Notes server, so that's another variable.

---

### Post by koenn on 2007-02-08
> port 110 
yes of course, POP (Post Office Protocol). 
If the Domino is configured for POP, that would work as well

---

