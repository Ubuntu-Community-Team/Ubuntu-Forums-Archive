---
title: "Outlook email and Thunderbird"
date: 2014-10-16
forum: General Help
---

### Post by col48 on 2014-10-16
I have an Outlook email account which is set to forward all emails to a POP account which I access using Thunderbird.

Maybe I should say access_ed_ - I think the email account provider may have gone belly-up - Thunderbird can't access the server in the last 4 days, their support phone is permanently advising emailing ("all our advisers are busy"), their website won't initiate the process of getting a new account (not that I need one!).....

So I now want to cut out the middle man and get Thunderbird to import directly from Outlook (which is storing everything in the Cloud) without any need to reimport old emails.

This link - 
[https://duckduckgo.com/l/?kh=-1&uddg=http%3A%2F%2Fanswers.microsoft.com%2Fen-us%2Foutlook_com%2Fforum%2Foemail-osend%2Fhow-to-set-up-thunderbird-to-sync-your-outlookcom%2F266ddd8f-250c-4e8a-9799-009d992be8e3](https://duckduckgo.com/l/?kh=-1&uddg=http%3A%2F%2Fanswers.microsoft.com%2Fen-us%2Foutlook_com%2Fforum%2Foemail-osend%2Fhow-to-set-up-thunderbird-to-sync-your-outlookcom%2F266ddd8f-250c-4e8a-9799-009d992be8e3)
  - looks good for a Windows user and IMAP, but I'm an Ubuntu user with a Thunderbird regime set up for POP.
[B]
So are there differences I should catch?[/B]
For comparison,

INCOMING SERVER
[TABLE="width: 500"]
[TR]
[TD]The Linked page says...[/TD]
[TD]but I have[/TD]
[/TR]
[TR]
[TD]Server name: imap-mail.outlook.com[/TD]
[TD]mail.xxxxxx.co.uk[/TD]
[/TR]
[TR]
[TD]Port: 993[/TD]
[TD]110[/TD]
[/TR]
[TR]
[TD]Connection Security: SSL/TLS[/TD]
[TD]no security[/TD]
[/TR]
[TR]
[TD]Authentication: Normal password[/TD]
[TD]password, transmitted insecurely[/TD]
[/TR]
[/TABLE]
 
OUTGOING SERVER
Outgoing email is still working (via a server from the ISP, a different company from the email account company) so I see no reason to change it (**is there any?**)
[TABLE="width: 500"]
[TR]
[TD]The Linked page says...[/TD]
[TD]but I have[/TD]
[/TR]
[TR]
[TD]Server name: smtp-mail.outlook.com[/TD]
[TD]smtp.yyyyyyy.net[/TD]
[/TR]
[TR]
[TD]Port: 587[/TD]
[TD]25[/TD]
[/TR]
[TR]
[TD]SSL: STARTTLS[/TD]
[TD]no security 
[/TD]
[/TR]
[TR]
[TD]Authentication: Normal password[/TD]
[TD]no authentication[/TD]
[/TR]
[/TABLE]

Appreciate your help.

---

### Post by buzzingrobot on 2014-10-16
I'd leave the POP account in Thunderbird alone for the time being, and set up an IMAP account in Thunderbird. The info you have -- servers, ports, etc. -- is what you need to do that, regardless of OS.

Once you're satisfied the IMAP account is working satisfactorily, you can delete the POP account, if you wish.

---

### Post by col48 on 2014-10-17
Thanks - that worked very straightforwardly.  Thunderbird defaulted most of the values, so that was easy.  

Being cautious, I did not want to start down a road which might guarantee failure because of something I did not know.
So your reassurance was very important.

---

