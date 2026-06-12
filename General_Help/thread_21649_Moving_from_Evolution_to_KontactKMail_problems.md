---
title: "Moving from Evolution to Kontact/KMail problems"
date: 2005-03-23
forum: General Help
---

### Post by thumper on 2005-03-23
Installed Kubuntu and decided to try to move to Kontact/KMail.

It says that you can import evolution mails using the tools, import.  Firstly there are two different evolution imports, and I have found that neither work.

Selecting either of them brings up the file select dialog.  Firstly none of the dot directories are show, so I set it to /home/tim/.evolution/mail/local/ and press Enter.  Hmm nothing happens.  Try again.  Nothing happens.  Press cancel, and it tries to import my Desktop as mails.  Arrggh.

Why doesn't this work?  Have googled and can't find references to it anywhere.

Anyone have words of wisdom?

Tim

---

### Post by thumper on 2005-03-24
Well, I had another hack at it last night, and managed to use the mbox import filter for KMail.

It was not ideal as all the "deleted" messages were imported as well, but it was sufficient to load the important mail that was in my inbox into KMail.  Left the list mails alone.

Very impressed with KMail in general.  Feels slicker to me than evolution.  Ditched spamassassin and using bogofilter.  Love it.

---

### Post by rjl on 2005-03-24
I tried bogofilter with kmail recently without much success.  Does bogofilter have a long training period or do you need to do more then just install it to activate it? (of course I set it up with Kmail's Tools/Antispam Wizard)

Thanks

---

### Post by thumper on 2005-03-24
[QUOTE=rjl]I tried bogofilter with kmail recently without much success.  Does bogofilter have a long training period or do you need to do more then just install it to activate it? (of course I set it up with Kmail's Tools/Antispam Wizard)

Thanks[/QUOTE]
 I had about 100 spam messages that I had imported from evolution, and am training on the fly when get false positives.

I also just used the antispam wizard to set it up.  I have other filters for my subscribed mailing lists which get applied prior to bogofilter.  You can get a reasonable understanding by looking at the filter setup to see what it is doing.

Bogofilter is catching 100% of the spam I am getting (after one night) but still trainging it to recognize real email.  I don't expect that to take too long though.

---

### Post by rjl on 2005-03-24
Thanks!  That answers my question.

---

