---
title: "Evolution and Groupwise"
date: 2008-04-30
forum: General Help
---

### Post by pricetech on 2008-04-30
I haven't been able to get Evolution to work as a Groupwise client.  I can make it see the server as an IMAP, but then I can't access our address book.  I keep getting an authentication failed error when I try to use it as a Groupwise client.
Quizzed our Linux guru and he says he ran into an issue previously and hasn't tried since, but remembers that our Netware admin says that SOAP should be working and is not blocked by a firewall.  He also recalled there was an isuue with us not using SSL.
Also, it routinely crashes when I click OK after checking / changing settings for the account.
Not mission critical as I have Groupwise installed on this box, but I would like to use Evolution if I can make it work.  (just something about using the OS as "straight out of the box" as possible.
Running Ubuntu 8.04 on a Dell GX260
Thanks in advance for any input.

---

### Post by brimlar on 2008-05-02
On the Groupwise server, yeah, you need to make sure SOAP is active and running on a port that isn't being blocked.  SSL is **not** required for e-mail, however, SSL **is** required if you want to plug Pidgin into the Groupwise Messenger server for instant messaging.

During account setup, the wizard will ask you which type of account you want to use.  Select "Novell Groupwise" as the account type, and then on the following screens put in your username and password, whether or not to save your password (it works better if you choose to save your password) and you will need either the IP address or DNS name of the Groupwise server that hosts your mailbox.  Your admin should be able to tell you that.

The rest of the wizard is pretty self-explanatory.  By going through the wizard you will also get autoconnected to your Groupwise calendar.

Good luck.  If you have problems, Novell's Evolution forums are a good place to look as well (because Groupwise is their product.)  

[http://forums.novell.com/novell-product-support-forums/evolution/](http://forums.novell.com/novell-product-support-forums/evolution/)

---

### Post by pricetech on 2008-05-02
Been there, done that.  It just don't work.
Pidgin is working just fine though.  I do miss a couple of features in GXMessenger, so I'd like to make it work, but having trouble getting it to install. (nuther story)

Thanks for the input anyway and the link to Novell's forum.  I'll see what I can root out there.

---

### Post by Rico.is.FABOO on 2011-01-28
Hello
I just want to revive this thread because I am having the exact same problem as pricetech had back in '08.
Is there someone who could please help guide me through connecting to the Novell Groupwise 8 email server using Evolution client software.  I already successfully connected Evolution to a gmail.com and a gmx.com email server but it is a lot more difficult for me to connect to Groupwise.  
Thanks!

P.S.   I should mention that my computer has 32 bit Ubuntu 9.04 Jaunty Jackalope

---

