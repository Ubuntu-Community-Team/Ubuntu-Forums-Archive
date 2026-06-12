---
title: "Evolution and Exchange - Cannot send messages"
date: 2007-10-19
forum: General Help
---

### Post by encoad on 2007-10-19
Hi everyone,

I'm a Windows system administrator for a large company who's secretly switched to Ubuntu 7.10 on his work laptop.  I have no Linux experience other then what I've learned since yesterday. (which is alot...!)

One problem I cannot seem to resolve is Evolution (2.12) with our Exchange Server (2003 SP2).

I am able to get Evolution to download all the messages and calendar items through the WebDAV.  ([https://webmail.ourserver/exchange](https://webmail.ourserver/exchange)).  So I can read email without issue.

I am not however able to send a message.  When I click "New", I am prompted for a LDAP password.  It fails to authenticate even with the correct password and correct domain controller listed.  If I Cancel the password prompt, write the email and send it, it goes to Sent folder, but the message never arrives.  I do not see it in the Exchange Queue.

I have a feeling this may not be an Evolution problem, and it may be related to Active Directory, but any help would be greately appreciated.  (I once had to get a Mac with Entourage on with Exchange, and it exhibited similar behavoir, though it COULD send messages, even though it could not query LDAP).  All of the solutions our there have been "Consult your systems admin for info"... well that's the problem, I am the sysadmin in this case.  FYI, I'm using WebDAV, not IMAP and SMTP.

Any help would be greatly appreciated!  (is there any other clients that can use Exchange?)

Thanks.

---

### Post by ddrichardson on 2007-10-20
Yes it's related to active directory, there is a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/25106"). It appears to be broken in 7.10 but may have been working in 7.04.

---

### Post by encoad on 2007-10-21
> **ddrichardson said:**
> Yes it's related to active directory, there is a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/25106"). It appears to be broken in 7.10 but may have been working in 7.04.

Hi there,

Thanks for the reply.  I appreciate the suggestion, but my situation appears to be different.  I am able to receive mail with Evolution.  But when I try to access the Global Address List (GAL) through LDAP, it tell me my password is wrong.  

Also, when I send messages, they aren't delivered even though they go from the Outbox folder to the Sent folder.

I'm willing to pay a bounty to either fix this problem in Evolution or help me figure out what I need to do on the Client, or Server end. (as I am the sysadmin for the exchange server in question).  Any takers or anyone have a suggestion where I can find higher end support for Evolution?  (paid support)

Thanks!

---

### Post by ddrichardson on 2007-10-22
Is "Evolution Exchange" installed?

Make sure the "Exchange plugin" is enabled under "Edit | Plugins". 

Also from Evolution's FAQ:

> Evolution Exchange only supports Microsoft Exchange 2000/2003 with OWA turned on (for WebDAV access). If you would like to connect to an Exchange 5.5, 2000, 2003 or 2007 server via MAPI (as would Outlook), get the Evolution Brutus Plugin at [http://www.omesc.com/node/22](http://www.omesc.com/node/22). Evolution Brutus supports complete access to your Exchange mail, calendar and tasks. If this still does not work, make sure you use "domain\user" and not "domain/user" in the "Evolution Account Editor > Windows Username".

---

### Post by encoad on 2007-10-22
Hi there,

Yes, Evolution Exchange is installed.  I believe it came installed by default.  Unfortunately, we cannot run MAPI in our environment for security reasons.

Thanks!


> **ddrichardson said:**
> Is "Evolution Exchange" installed?

Make sure the "Exchange plugin" is enabled under "Edit | Plugins". 

Also from Evolution's FAQ:

---

### Post by jpietari on 2007-10-31
Using the following account settings works for me with Ubuntu 7.10 and Evolution 2.12:

1. Connect to Exchange to send/recieve mail/Calendar
  Server Type: Microsoft Exchange
  Username: ~domain\user~
  OWA URL:  [https://webmail.ourserver/exchange](https://webmail.ourserver/exchange)
2. Enable Global Address List
  Global Catalog Server Name: See post [http://ubuntuforums.org/showthread.php?t=195239]("http://ubuntuforums.org/showthread.php?t=195239")
  The server name can be found by right-clicking "Global Address List" and selecting Properties when searching for names in Outlook.  i.e. new mail->To... button->Select Names dialog

---

