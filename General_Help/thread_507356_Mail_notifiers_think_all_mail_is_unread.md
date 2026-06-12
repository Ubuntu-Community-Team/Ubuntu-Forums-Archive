---
title: "Mail notifiers think all mail is unread"
date: 2007-07-22
forum: General Help
---

### Post by PurplePenguin on 2007-07-22
I have a web-based email address at inbox.com, who provide free POP3 access.  What I was hoping is to have a POP3 notifier tell me when I get new emails in my inbox.

I've tried about 10 different email notifiers - you name it, I've tried it - via apt-get/synaptic (I'm using Debian Etch) and compiling from source, all with the same result:

I get notified of my email, but the notifiers can't tell the difference between read and unread mail! Right now I have three emails in my inbox.  One is read, two are unread.  Each POP3 notifier program says I've got three emails in my inbox.  I can mark all of them read and refresh the notifier, but no difference.

Inbox.com makes it really easy to set up pop3 access, too, so I'm sure I've got things set up on that end correctly.

Is this some sort of problem/incompatibility with inbox.com's pop server?  Is there anything I can do?

If all else fails, I'm just going to make a READ folder and put everything there once I've read it, but I'd really rather figure this out and avoid that extra step.

---

### Post by MEW on 2007-07-22
In POP3, there is no way of marking messages as 'Read' on the server. Marking an email read in your client (Evolution?) only affects that client. I think that the notifiers are expecting you to have your email client download the messages, and delete them off the server (because that's what was intended when the POP3 protocol was written).

---

### Post by PurplePenguin on 2007-07-24
Thanks for the reply!

OK, here's the strange thing: I've got an account from inbox.com and gmail.com.  The mail notifier works perfectly with gmail... I see I've got mail, I go to mail.google.com and read it, then it disappears from the mail notifier since it's been read.  Inbox.com refuses to see that it's been read.

Maybe I've just got to stick with gmail on this one.

---

### Post by MEW on 2007-08-03
This is just a guess, but maybe gmail stops listing email messages through POP3 once they are read, because it is designed for keeping mail for a long time. (I don't know, though -- I don't have a gmail account).

---

