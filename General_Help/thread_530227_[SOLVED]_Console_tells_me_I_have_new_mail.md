---
title: "[SOLVED] Console tells me I have new mail??"
date: 2007-08-20
forum: General Help
---

### Post by nvteighen on 2007-08-20
This is funny, and hopefully harmless, but weird:

If I login into a console (say tty1), I get this message:

```

Last login: (...)

The programs included in the Ubuntu system are free software (...)

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law
**You have new mail**

xxxx@xxxx:~$

```

Is that annoying "You have new mail" an easter egg, a joke or something is broken... or have I just missed it before? I don't have any CLI mail client installed and the only mail service I have activated is exim4.

It seems not to be something harmful, but it is quite strange!

---

### Post by heimo on 2007-08-20
> **nvteighen said:**
> This is funny, and hopefully harmless, but weird:

If I login into a console (say tty1), I get this message:

```

Last login: (...)

The programs included in the Ubuntu system are free software (...)

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law
**You have new mail**

xxxx@xxxx:~$

```Is that annoying "You have new mail" an easter egg, a joke or something is broken... or have I just missed it before? I don't have any CLI mail client installed and the only mail service I have activated is exim4.

It seems not to be something harmful, but it is quite strange!


Well. You have mail. That's the reason. It's probably some script - maybe run as a cronjob. Check /var/spool/mail/yourusername or run some command line mail reader.

---

### Post by nvteighen on 2007-08-20
This is funny. Yes, I have "mail": they are the outputs of rkhunter scans, sent by root to me... It says I'm the owner, but can't delete it. Do I blank the file or delete it using sudo?

---

### Post by heimo on 2007-08-20
> **nvteighen said:**
> This is funny. Yes, I have "mail": they are the outputs of rkhunter scans, sent by root to me... It says I'm the owner, but can't delete it. Do I blank the file or delete it using sudo?

You can leave it, or truncate it (empty it), but keep the owner, group and permissions the same as it's now. Or you can delete messages using mail reader. You could probably configure rkhunter to send those messages to another address or redirect your local mail to some address you read (or disable sending mail).

---

### Post by eentonig on 2007-08-20
use the command "mail" to read those mail.

To learn "mail", use "man mail"

---

### Post by nvteighen on 2007-08-20
I've blanked it, but I still get the "You have mail". What mail reader could do the work? mailx?

---

### Post by nvteighen on 2007-08-20
OK, I've installed mailx, used "mail" and it tells me "No mail for ...". But, if I login again, it still says "You have new mail". Looking at man mail, I see there's something about a fail /etc/mailrc (or similar) that regulates mail behaivor at startup, is that a safe way?

---

### Post by heimo on 2007-08-20
> **nvteighen said:**
> I've blanked it, but I still get the "You have mail". What mail reader could do the work? mailx?

As eentoniq says, mail is fine. It's "a bit" simplistic. ;-) I believe this "new mail" message is based on modification date (or similar) of your mailbox.

---

### Post by nvteighen on 2007-08-20
This gets funnier: I've run rkhunter again and it created no new mail. OK, maybe is like heimo says, that it depends on modification date. Well, I don't mind really about this very much, it just annoyed me to see that message.

---

### Post by nvteighen on 2007-08-20
I solved it! I renamed the file at /var/spool/mail and the message doesn't appear anymore. Could this mean that deleting it is safe?

---

### Post by BLTicklemonster on 2008-03-15
. Oh. Okay, so I haven't lost my mind after all. Whew. That was the darnedest thing. I was thinking, "when did AOL buy Ubuntu?"

---

