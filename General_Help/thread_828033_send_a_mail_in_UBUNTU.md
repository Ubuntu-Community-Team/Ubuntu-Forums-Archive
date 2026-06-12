---
title: "send a mail in UBUNTU"
date: 2008-06-13
forum: General Help
---

### Post by big136 on 2008-06-13
Hi,
do you know what is the syntax to send a mail in UBUNTU ?
Many thanks.

---

### Post by metroplex on 2008-06-13
Syntax? If you're talking about syntax, I suppose you'd like to send a mail from a shell interface.. right? Otherwise, just use Thunderbird or similar mail client.

---

### Post by big136 on 2008-06-13
is'nt any command line like :
sendmail

in RED HAT.

Thank you.

---

### Post by MacAnthony on 2008-06-13
sudo apt-get install sendmail

---

### Post by DannyB2 on 2008-06-13
> **big136 said:**
> Hi,
do you know what is the syntax to send a mail in UBUNTU ?
Many thanks.


One way...

bash> mail [email]someone@somewhere.com[/email] -s "This is the subject"
This is the first
part of the body of
the message.

Type a period on a line
by itself to end the body.
.

bash>



Here is another way...

bash> echo "Body of message" | mail [email]somebody@somewhere.com[/email] -s "This is the subject line"


Yet one more way...

bash> cat message-body.txt | mail [email]somebody@somewhere.com[/email] -s "This is the subject line"

---

### Post by big136 on 2008-06-14
many thanks.

---

