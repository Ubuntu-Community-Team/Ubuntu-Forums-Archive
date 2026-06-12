---
title: "Thunderbird does not interact with googlemail"
date: 2015-09-11
forum: General Help
---

### Post by Erik Kaiser on 2015-09-11
Dear community !

This is the question how to send and receive messages with thunderbird from and to a googlemail account.

The following mistake occurred :

Sending of the message failed.
The message could not be sent because connecting to Outgoing server (SMTP) [smtp.gmail.com]("http://smtp.gmail.com")  failed. The server may be unavailable or is refusing Outgoing server  (SMTP) connections. Please verify that your Outgoing server (SMTP)  settings are correct and try again.

The entered data for password and username have not been accepted, a  failure was reported although it was me in person and my email account  was open.

Google has some info about how to define pop and imap for incoming and  outgoing messages in the googlemail account and the thunderbird  preferences but none have gone though, several options have been tested.

Do you have any recommendations how to start thunderbird and download my googlemail account to the computer ?

Some of the threads you can find online have remained unanswered.

Deinstallation and new installation of thunderbird has not helped, still a failure to enter the user.

Does this require to open a special account with a new email address we have to pay for ?

Kind Regards


Erik

---

### Post by TheFu on 2015-09-11
No need to pay.
Gmail has some "security settings" that default to preventing old-school IMAPS logins. You have to toggle that setting to allow insecure apps to allow access - that's from memory from about 6 moths ago, so don't expect the setting to be exactly that.  It is a setting controlled in the google-account preferences. Must use a web browser to change it first.

Then in the thick email client - 
Gmail settings:
**IMAP** - for reading
 imap.googlemail.com  port 993
 SSL/TLS
  Normal Password

**SMTP - for sending** 
smtp.googlemail.com  port 465
 SSL/TLS
  Normal Password

Always use the full gmail account - [email]thefu@gmail.com[/email] for userids.

This works from anywhere in the world that gmail isn't blocked, IME.

---

### Post by cariboo on 2015-09-11
I've have the following settings to access and send email via my gmail account in Thunderbird

Sever Name: pop.googlemail.com Port: 995
User Name: XXXXXXXXXX
Connection security: SSL/TLS
Authentication method: Normal password 

I've been using this for so long I actually forgot how I setup, as I just transfer the ~/.thunderbird directory to a new installation whenever I do one.

User name X'd out, just in case. :)

---

### Post by Erik Kaiser on 2015-09-24
Hi !

Thank you for your contributions. I have tried but was not successful yet. Opening thunderbird still begins with " unable to locate mail spool file ".

Can you recommend just any good software to create a backup in an internet shop, eventually even with another operating system ? It is really frustrating to discover how much effort is necessary to get a security copy of your conversation. 

Have a nice day.

Erik

---

### Post by TheFu on 2015-09-24
> **Erik Kaiser said:**
> Thank you for your contributions. I have tried but was not successful yet. Opening thunderbird still begins with " unable to locate mail spool file ".

This error would be expected if Thunderbird expected to get mail from local email files in /var/spool/mail and ~/Mail/ - Did you setup the mail server preferences to use gmail's servers?

---

### Post by buzzingrobot on 2015-09-24
When you uninstall and reinstall Thunderbird, be sure to manually check that the configuration files Thunderbird deposits in you home folder are also deleted, to prevent possible reuse of a bad config on the reinstall.  Look for a /<home>/.thunderbird folder.

In Thunderbird's menu, Edit->Account Settings should show an entry for the Gmail account, or any other account that's been added, as well as an entry for "Local Folders".  If the Gmail entry is not there, then Thunderbird has not been configured correctly. Click on the entries beneath the Gmail account entry ("Server Settings", etc.) to adjust and verify your configuration settings.

---

### Post by Erik Kaiser on 2015-10-01
Hello.

Thank you very much for your help.

I have downloaded a security copy of the conversation from googlemail takeout, a mbox file, 0,6 GB big. Unfortunately it can not be opened easily. Only a first email - which was not the first or last conversation can be displayed from the download, the rest is data salad, chaos, nonsense.

Any good idea how to open the conversation is appreciated.

Evolution has been downloaded, also MBoxImporter. MBox Importer I can not open, no idea why. Evolution does not recognise the file format.

Have a nice day.

Erik

Just for the eventual readers information, without any visible reason an Enigmail key has been generated on my computer. This one I neither can copy, nor did I order to generate it. It still is impossible to open the MBOX file.

---

### Post by TheFu on 2015-10-08
Enigmail is a front-end to gpg.  It stores the gpg keys for others and you and makes using gpg with Thunderbird pretty easy, unless the key expires, then it will warn about the expiration and keep the key only to open/read older emails.  This is excellent encryption. Without the passphrase for the private gpg key to unlock, you will not be able to access this data.

How did enigmail get installed on your system? It is NOT pre-installed and must be setup to be used.

If you have gpg working on the system, you may be able to manually decrypt each message with that tool. You'll need to know the gpg passphrase and you'll need to split out the specific messages for decryption. 

Another little detail ... it is possible to send encrypted emails to other people by only knowing their public keys, then, if you don't also use your private key for the "SENT" email, you will not be able to read what you sent - EVER. Could this be the issue?

---

