---
title: "Outlook and Microsoft Exchange Server"
date: 2008-02-28
forum: General Help
---

### Post by eorteg01 on 2008-02-28
I recently switched my work machine over to Ubuntu 7.04 and have everything but my work email working right now, and am unsure of how to proceed.

In XP I connect to my email using Outlook and a Microsoft Exchange Server. There is no webmail access to this email. This is the information listed in Outlook under the email account:

Microsoft Exhange Server : sr-tre-exch02.company.internal
'Cached Exchange Mode' is checked
'Kerberos/NTLM Password Authentication' is selected.

Any help would be greatly appreciated.

---

### Post by eriqjaffe on 2008-02-28
Is IMAP a possibility?

---

### Post by chrisjsmith on 2008-02-28
Use evolution for email - that will connect to exchange.

---

### Post by eriqjaffe on 2008-02-28
> **chrisjsmith said:**
> Use evolution for email - that will connect to exchange.IIRC, Evolution relies on Outlook Web Access, which he already stated wasn't available.  If IMAP is an option, though, he should be able to use pretty much any mail client (Evolution, Thunderbird, Sylpheed) to connect.

---

### Post by igknighted on 2008-02-28
I think the best options are Outlook via wine or Kontact (it uses a more proper connection to exchange IIRC, though I don't use exchange and could be way off)

---

### Post by chrisjsmith on 2008-02-28
Ah yes good point - forgot about the poisonous beast of OWA.

If IMAP fails, you can only rely on bribing your exchange administrator in some way...

---

### Post by eriqjaffe on 2008-02-29
> **igknighted said:**
> I think the best options are Outlook via wine or Kontact (it uses a more proper connection to exchange IIRC, though I don't use exchange and could be way off)According to Kontact's home page, they have partial support for Exchange 2000 - basically, just the calendar.  Mail still goes through IMAP, and the contacts and free/busy don't work at all.

---

### Post by civic_si on 2008-02-29
Start the Imap service on the exchange server and then connect to it that way. Its the easiest way in my opinion. I have connect Mac and Linux machines with Imap. Or you can just setup a Linux email server which is free and works better.

---

