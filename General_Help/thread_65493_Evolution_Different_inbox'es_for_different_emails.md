---
title: "Evolution: Different inbox'es for different emails?"
date: 2005-09-14
forum: General Help
---

### Post by sneax on 2005-09-14
Hello, I have recently changed to ubuntu and decided to use Evolution too because it looked so good (i normaly use mozilla thunderbird). Evolution is a great program especialy with it's integration support into the gnome calendar and gaim! Though, I have a problem:
I have 3 email accounts on 3 different servers. I installed them all no problem, but all mails come into the same 'Inbox'. The emails from these 3 accounts should be in different Inboxes for each account. Better yet: each account should have it's junk, trash, inbox and sent folder. Here's a screenshot how I would like it:
[http://www.gnome.org/projects/evolution/images/screenshots/2.4/read-mail.png](http://www.gnome.org/projects/evolution/images/screenshots/2.4/read-mail.png)
Note the different mail adresses on the left pane!

Now in my situation I simply have 'On this computer' and then all mails drops into that Inbox! Very annoying because one email is for the University (which is VERY important) while the other is for my bussinesses and another for recreational purposes!

Regards,
Thomas

---

### Post by doclivingston on 2005-09-14
The reason that screenshot shows the different accounts seperately, is that they are probably  IMAP accounts, not POP accounts.

With an IMAP account the mail actually stays on the server, in the folders shown. With a POP account the mail is delivered to your computer, and then (usually) deleted from the server. An additional advantage of IMAP is that outgoing mail is stored on the server, so you can look at it from a different computer than the one that sent it.

The first thing to do, would be to see if the various organisations provide IMAP access to your mail, as well as POP3. If so, switch over to using that.

If not you will need to set up some filters to direct your incoming mail to the correct folder - I can't remember where they are set up under Hoary (Edit->Message Filters in Breezy), but there should be a fairly obvious menu item. First create a folder for each account called "XXX-Inbox", then add a new filters, which have the conditions set to "Source Account is XXX" and the action being "Move to folder XXX-Inbox".

---

### Post by darius_underhill on 2005-09-14
> 

Now in my situation I simply have 'On this computer' and then all mails drops into that Inbox! Very annoying because one email is for the University (which is VERY important) while the other is for my bussinesses and another for recreational purposes!

Regards,
Thomas

Hi you may want try using filters.  Just set the condition to recepient to your one of your email addresses then set a destination folder.

---

### Post by sneax on 2005-09-14
No IMAP support for 2 of those boxes (one has). Ok wait I don't want to go into the 'filters' thing yet (coz it's not completely what i want) thanks for the help so far though. Listen:
In thunderbird those 3 acounts were ALSO POP. What I did was tick 'leave messages on server after download' I also ticked 'only delete messages when deleted on my computer'. I don't find this in Evolution.

The server always kept the messages, like this when I go out and use webmail, my messages that I didn't delete yet are still on the server. It worked flawlessly and I'd like to recreate this situation. You are sure this is NOT possible? You are def. sure I have to give this up and start using filers? It's ok for me, I'm hooked on the Evolution calendar function ;) but for my email this could have been better.

---

### Post by doclivingston on 2005-09-14
"Leave mail on server" is under the "receiving options" tab of an account. I don't think there is a way to have POP accounts show up as IMAP ones do, but as all my accounts have IMAP support, I could be wrong.

---

### Post by sneax on 2005-09-14
No imap for the other accounts :( I'll make the filters then - though I'd like this as a feature to show POP boxes as IMAP boxes. Would this be a good feature request?

---

