---
title: "Kmail to Evolution migration"
date: 2005-05-12
forum: General Help
---

### Post by caspar_wrede on 2005-05-12
I have all my emails in Kmail (MailDir format). I want to import them to evolution.

I tried doing it via IMAP (dovecot), however this didn't work. Kmail could copy emails to the IMAP server, however, evolution couldn't read them. It just says "scanning folders in IMAP server" and stays that way for ever. And Ever. Amen.

So does anyone have any better ideas?

Caspar

---

### Post by df-sean on 2005-05-31
You might wanna try using a remote IMAP account.  I did this yesterday and it worked well.  Just stop your mail clients from popping your remote email account, then switch your remote email account from POP to IMAP.  Then drag all your mail into the IMAP account for your remote IMAP account.  It may take a while and requires that you have a lot of space on your hosting account (and email quota), but it eliminates the possibility that your just having local config problem.

---

