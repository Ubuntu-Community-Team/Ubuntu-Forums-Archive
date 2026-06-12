---
title: "Will mutt play nicely with gmail?"
date: 2005-04-16
forum: General Help
---

### Post by Ygramul on 2005-04-16
I'm looking for a way to get my email via SSH, and the best one I've seen so far is Mutt.  However, my primary email account is gmail, and I can't figure out a way to set it up.  I've tried to set up getmail, sendmail, etc, but I can't seem to get anything working.  

Is it even possible?  Sending mail isn't as large a priority as receiving, so getting mail is by far a priority.

If Mutt won't do it, is there a command line client that will?

Thanks for any and all help.

---

### Post by joshmachine on 2005-04-16
[QUOTE=Ygramul]I'm looking for a way to get my email via SSH, and the best one I've seen so far is Mutt.  However, my primary email account is gmail, and I can't figure out a way to set it up.  I've tried to set up getmail, sendmail, etc, but I can't seem to get anything working.  

Is it even possible?  Sending mail isn't as large a priority as receiving, so getting mail is by far a priority.

If Mutt won't do it, is there a command line client that will?

Thanks for any and all help.[/QUOTE]
 I think you mean SSL not SSH.  SSH stands for ssh and is a very nonstandard way to go about retrieving stuff (it can be done, but requires some pretty advanced stuff).

SSL is secure socket layers and there is a large amount of support for doing POP3 and SMTP (the most common recieving and sending protocols for using mail).  this is also encrypted and is how "https" works.

gamil by default will only allow ssl connections to do pop3 and smtp.  

Here's how to configure your gmail account to do this:
[http://gmail.google.com/support/bin/answer.py?answer=13273](http://gmail.google.com/support/bin/answer.py?answer=13273)

and here are the settings for you're client

[http://gmail.google.com/support/bin/answer.py?answer=13287](http://gmail.google.com/support/bin/answer.py?answer=13287)

you can use evolution or most any other email client as they support SSL encrypted mail retrieval

Cheers

---

### Post by Ygramul on 2005-04-16
Thanks for the help.

I, however, DID mean SSH.  I want to access my email remotely using SSH and mutt.  Evolution, as far as I can tell, does not have a command line client.

---

