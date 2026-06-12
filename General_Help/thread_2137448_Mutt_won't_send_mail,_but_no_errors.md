---
title: "Mutt won't send mail, but no errors"
date: 2013-04-20
forum: General Help
---

### Post by joetait on 2013-04-20
Hi



Firstly, if this is probably not the best place to post this, so I am open to suggestions of better places to ask this.

I have configured mutt via the muttrc files to (try to) send and receive via IMAP and SMTP. The muttrc file is here - [http://pastebin.com/ShvAKbgP](http://pastebin.com/ShvAKbgP)

The issue is that I can only send emails to the email address in the muttrc file, not any other email address. Interestingly the mail that does comes through as being from $username@$computername.lan


There is no error when I send the messages, so I am not sure what to do :s

Thanks for any help

---

### Post by andrew.46 on 2013-04-20
I do not use mutt directly with smtp or IMAP so I am not completely sure of the problem with your setup but I notice that you ~/.muttrc is missing a few standard identifiers. Perhaps borrow some ideas from here:

[http://www.andrews-corner.org/mutt.html#reading](http://www.andrews-corner.org/mutt.html#reading)

You can see from that page that my own experience is unfortunately with the *old* way of using Mutt :(.

---

