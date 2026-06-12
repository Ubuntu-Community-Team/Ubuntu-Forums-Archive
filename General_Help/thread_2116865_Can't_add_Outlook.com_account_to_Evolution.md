---
title: "Can't add Outlook.com account to Evolution"
date: 2013-02-17
forum: General Help
---

### Post by deltatux on 2013-02-17
Hi everyone,

Not sure if this is the correct place to be posting this but lately I've been trying my hardest to add my Outlook.com account to Evolution.

It keeps trying to add it as a imap+ account even though Hotmail/Outlook.com does not support IMAP access. It only supports POP3/Exchange and I haven't figured out how to manually tell it that it's wrong and use the Exchange support that it has.

I've tried searching many places but have not been able to find anything.

Please help.

Cheers,
deltatux

---

### Post by lisati on 2013-02-17
I agree that lack of IMAP support is annoying. I've had success with POP3 settings:

**Receiving mail settings**
Server type: POP
Incoming server: pop3.live.com, port 995
User name: *(your full outlook.com email address)*
Secure connection: ssl encryption

**Outgoing settings**
Sever type: SMTP
Server: smtp.live.com, port 25
Secure connection: TLS
User name: *(your full outlook.com email address)*

Edit: if this is the first time you've used Evolution, you might want to cancel the start-up wizard and add your details manually via Edit->Preferences

---

### Post by dcstar on 2013-02-17
> **deltatux said:**
> 
...........
It keeps trying to add it as a imap+ account even though Hotmail/Outlook.com does not support IMAP access. It only supports POP3/Exchange
..........

It actually only supports "Exchange" on Outlook with the Outlook.com plugin that only works on Windows. Just another example of typical Microsoft non-standard bastardry.

Use the POP settings as specified in the other post.

---

### Post by deltatux on 2013-02-17
> **lisati said:**
> I agree that lack of IMAP support is annoying. I've had success with POP3 settings:

**Receiving mail settings**
Server type: POP
Incoming server: pop3.live.com, port 995
User name: *(your full outlook.com email address)*
Secure connection: ssl encryption

**Outgoing settings**
Sever type: SMTP
Server: smtp.live.com, port 25
Secure connection: TLS
User name: *(your full outlook.com email address)*

Edit: if this is the first time you've used Evolution, you might want to cancel the start-up wizard and add your details manually via Edit->Preferences

For some reason the version of Evolution (version 3.6.2) doesn't allow me to specify POP/IMAP/Exchange manually, it forces me to have it detect the type of server connection.

Any ideas how to get around it?

Cheers,
deltatux

---

### Post by dcstar on 2013-02-18
> **deltatux said:**
> For some reason the version of Evolution (version 3.6.2) doesn't allow me to specify POP/IMAP/Exchange manually, it forces me to have it detect the type of server connection.


And then allows you to select what connection type you are using......

---

### Post by deltatux on 2013-02-24
> **dcstar said:**
> And then allows you to select what connection type you are using......

Unfortunately, I don't see it, it jumps to the account creation summary with no server nor other settings filled in under the Incoming section of the screen. There's no edit button for me to fix it manually...

deltatux

---

### Post by howefield on 2013-02-24
Do you have this screen from which you can select the server type ?

---

### Post by deltatux on 2013-02-26
> **howefield said:**
> Do you have this screen from which you can select the server type ?

No I do not, when it detects Outlook.com, it thinks it knows better and not even give me that screen. However, if I choose to add my own domain name's email address, since it doesn't know about the settings, it lets me choose.

Thanks,
deltatux

---

### Post by zx2gsxr on 2013-04-03
Resurrecting the thread...Has anyone had success, once they've added Exchange support (the OP may have been missing the package), in getting Evolution to use MAPI with Outlook.com?I've found this on an Android forum:> Use \[address]@outlook.com for domain\username and snt-m.hotmail.com as the server.but I cannot seem to get it to work for me.  Anyone solve the remainder of the puzzle?

---

### Post by lasm2000 on 2013-07-04
Resurrecting this old thread I have a simple doubt. Unlike IMAP which only downloads headers, POP3 downloads the full message, is there any way to avoid evolution from downloading my years old mails? I just want to receive any future mails not making a full collection of mails from 10 years ago!

---

### Post by dcstar on 2013-07-08
> **zx2gsxr said:**
> Resurrecting the thread...Has anyone had success, once they've added Exchange support (the OP may have been missing the package), in getting Evolution to use MAPI with Outlook.com?I've found this on an Android forum:but I cannot seem to get it to work for me.  Anyone solve the remainder of the puzzle?

Why not use** the settings that work** in post #2?

---

### Post by dcstar on 2013-07-08
> **lasm2000 said:**
> Resurrecting this old thread I have a simple doubt. Unlike IMAP which only downloads headers, POP3 downloads the full message, is there any way to avoid evolution from downloading my years old mails? I just want to receive any future mails not making a full collection of mails from 10 years ago!

The POP protocol does not allow this sort of thing, that is why IMAP was invented. Just let the POP client empty the mailbox and your problem will be solved if you only care about new messages.

If Microsoft allowed non-MS clients to have decent access to **your** e-mail this wouldn't be an issue, but it is for the same old MS reasons....

---

