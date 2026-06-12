---
title: "postfix as MTA"
date: 2007-12-18
forum: General Help
---

### Post by vanderkerkoff on 2007-12-18
Hello everyone

I've installed Ubuntu 7.10, first time using it, coming over to the light from fedora.

I didn't install any options in the install, and now I need an MTA.

As we're using a new op system I though I'd use a new MTA, so I've ran

sudo apt-get install postfix

during the install I chose sattelite system, as it's a web server and only needs to send mail.  I entered the domain name that the server sits in, and also the relay host name.

Can someone show me how to test that I can acutally send mail using postfix from the command line?

With sendmail i used to use the sendmail command to send mail, I haven't got a clue how to do it with postfix.

I've just noticed that I can still run the sendmail command.

I had insalled sendmail then removed it with apt-get.  Getting confused now.


Any help, greatly appreciated.

---

### Post by vanderkerkoff on 2007-12-18
ahh

now it's starting to make sense

I uninstalled postfix and the sendmail disappeared, so postfix uses the sendmail command. ok.

I'm going to reinstall postfix now.


Right, it's resintalled and picked up my relay host setting, sweet.

Now to try and send some mail.  Wish me luck.

---

### Post by vanderkerkoff on 2007-12-18
Hmm, not quite there yet.

can someone tell me how to test my postfix config to see if I can send mails from the command line?

---

### Post by vanderkerkoff on 2007-12-18
I got it

For some reason there was as sendmail process running that was stopping the postfix from starting.

I killed the sendmail process and it's all started up and I can now send mail, woohoo.

Nex thing to sort out is how to permanently change the senders address, and the reply to address.

I've followed the instructions on this page [http://www.cyberciti.biz/tips/howto-postfix-masquerade-change-email-mail-address.html](http://www.cyberciti.biz/tips/howto-postfix-masquerade-change-email-mail-address.html)

That only masks the sending address though, I need to change the from and the reply to address.

We'll get there, famous last words :)

---

### Post by vanderkerkoff on 2007-12-18
I've done some more digging, the solution that I tried earlier, that is using a generic file, is suggested in a number of places

[http://www.postfix.org/STANDARD_CONFIGURATION_README.html#fantasy](http://www.postfix.org/STANDARD_CONFIGURATION_README.html#fantasy)

The problem with this method is that the email shows up in my Apple Mail inbox, and my Gmail inbox as coming from

username <new email address signified in generic file>

I don't want to show the username of the user that is sending the messages from the web server, it's a security risk.

Can anyone give me a hand here?

In sendmail this was a piece of piss, you just changed the setting in the config file.

If there's no way of doing it I'm going back to sendmail, which is a real shame.

Any tips or guidance most welcomed, going to look into aliases now.

---

### Post by vanderkerkoff on 2007-12-18
ok, giving up

going back to sendmail

---

