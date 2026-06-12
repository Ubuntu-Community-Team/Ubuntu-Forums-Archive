---
title: "Alternative to Outlook for business use"
date: 2013-03-03
forum: General Help
---

### Post by mrgoodfox on 2013-03-03
I'm trying to make the switch from PC to Ubuntu and I'm not sure if I can fully replace Outlook yet. 
I use Outlook for my business, have 30+ email accounts on it, use the calendar, contacts, and pretty much all the options that Outlook has. What are my best options to replacing Outlook moving forward on Ubuntu? It looks like Thunderbird is the most advance one. Can it manage 30+ accounts or does it have a limit? Also is there any way I can import my Outlook data file o Thunderbird so i dont lose my old emails?

---

### Post by dcstar on 2013-03-04
> **mrgoodfox said:**
> I'm trying to make the switch from PC to Ubuntu and I'm not sure if I can fully replace Outlook yet. 
I use Outlook for my business, have 30+ email accounts on it, use the calendar, contacts, and pretty much all the options that Outlook has. What are my best options to replacing Outlook moving forward on Ubuntu? It looks like Thunderbird is the most advance one. Can it manage 30+ accounts or does it have a limit? Also is there any way I can import my Outlook data file o Thunderbird so i dont lose my old emails?

If you access Exchange 2010 servers for Calendar and Tasks then there is no viable Linux alternative. For Exchange 2007/2003 then Evolution still can access those systems.

---

### Post by kurt18947 on 2013-03-04
I know nothing about Outlook or Exchange servers but made note of this in case of need:  
 [http://davmail.sourceforge.net/](http://davmail.sourceforge.net/)

---

### Post by Lars Noodén on 2013-03-04
Unfortunately, Outlook is tied to Exchange.  It's a poor mail client, but it is the lock-in that makes it hard to switch.  On the client side you might try Thunderbird with the Lightning add-on for calendars.  I'm not sure if Exchange supports IMAPS at all or properly.  Microsoft makes it hard on purpose.  

Looking at a larger task, you might look at replacing the whole thing with [Kolab](http://kolab.org/) or [Citadel](http://citadel.org/).

---

### Post by Cheesemill on 2013-03-04
@mrgoodfox

Are you using Outlook connected to an Exchange server or are you using it as a standalone client?

---

### Post by mrgoodfox on 2013-03-04
Im using Outlook as a standalone client. Im not using the exchange part of it

---

### Post by Abhilashjoy on 2013-03-04
Hi

As per my suggestion the best alternative for Outlook is Thunderbird. 

Regards
Abhi

---

### Post by d4m1r on 2013-03-04
+1 for Thunderbird + Lightning (calender plugin). If you are using an Exchange server (2003 or 2007) underneath, that setup will be able to handle it!

---

### Post by mrgoodfox on 2013-03-04
Is the process to move all my email history from Outlook to Thunderbird pretty straight forward too?

---

### Post by Cheesemill on 2013-03-04
This all depends on what protocol you use to connect to your email accounts.

If you connect using IMAP then you don't need to move anything as all of the mail is still on the server, you just enter the account details and Thunderbird will download all of the mail.
If you use POP3, however, then it is a lot more difficult. There are different solutions depending on what version of Outlook you are using. A quick google for 'export outlook to thunderbird' should get you some answers.

---

### Post by mrgoodfox on 2013-03-05
ok. thanks. I'm indeed using POP3. I'll have to do some good research then

---

### Post by HermanAB on 2013-03-05
If you used IMAP  for mail, then simply configure Thunderbird and all your mail will be there. If you used POP for mail, then you need to bounce the mail through an IMAP server to convert it for you.

To convert mail, simply open a gmail account, set it up in Thunderbird, open Outlook, select all mail and click drag drop it to gmail in Thunderbird. Do not copy the mail. Do not forward the mail. Click drag drop it. Then go and get some coffee or watch a ball game. Once that is done, configure Thunderbird for the other accounts and ALWAYS use IMAP, not POP.

---

### Post by mrgoodfox on 2013-03-05
I have over 30 email POP3 emails in my outlook. I can't send them all to Gmail.

---

