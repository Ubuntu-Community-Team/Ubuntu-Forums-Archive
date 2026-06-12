---
title: "Evolution and Mail2web LIVE - Exchange Server!"
date: 2007-08-05
forum: General Help
---

### Post by Buzbe on 2007-08-05
Hi all,

Mail2web Live has a product called "personal exchange" - its great - and it allows me to have my push email straight to my phone, with an outlook webmail interface etc..

However it doesnt include a MAPI interface - which is annoying, so I cant run Outlook without paying a bit more..

However it does give a webmail interface which allows you to login and use Entourage - and in theory - Evolution to access your exchange account (sounds crazy but I've managed it in Entourage).  

So trying with evolution - with the debug level up on its highest i can see it logining into the exchange server successfully over OWA, but it doesnt let me click the "forward ->" button whilse setting up the account.

Has anyone had any more luck with this?

---

### Post by testdasi on 2008-07-12
No luck, just "cheating" :D
The problem is that the exchange plugin of Evolution does not allow you to enter [email]XYZ@mail2web.com[/email] as username for logging in. So I found a work around after about an hour messing around :D

1. Set up an IMAP account as though you are setting it up as an exchange server. Basically enter everything the same, except choose IMAP instead. I chose this arbitrarily because IMAP is similar to exchange in a sense that the mail is not stored "On this computer". You can try something else YMMV.
2. Close Evolution
3. Press Alt-F2, type in gconf-editor to run it.
4. Find the "Accounts" key in apps/evolution/mail within the gconf-editor.
5. Double click the Accounts key and then double click the last entry (your IMAP account you just created). Copy the content to a text editor for easy editing.
6. Look carefully, you will see 2 <url> [something] </url> (one for incoming, one for outgoing). Replace the first one with this
> <url>exchange://MYNAME%40mail2web.com@exchange.mail2web.com/exchange;auth=MYNAME@mail2web.com;user=MYNAME@mail2web.com;auth=MYNAME@mail2web.com;save-passwd=true;owa_url=http://exchange.mail2web.com/exchange</url>
Of course, replace MYNAME with your username without the @mail2web.com
7. Restart Evolution and voila!!!

I have no need to send emails out of my mail2web so I have never tried to correct SMTP setting. You can try it for yourself.

---

