---
title: "How to install email encryption using chrome"
date: 2020-09-16
forum: General Help
---

### Post by Ralph L on 2020-09-16
I am trying to set up encrypted email communications with my son.  I have installed Enigmail on my Xubuntu 18.04 Thunderbird email program and it seems to work fine.  I can send encrypted emails from one of my mailboxes to another of my mailboxes with no problem.  However, my son uses chrome (under windows) to read/write his email.  I googled "using chrome to read/write encrypted email" and got back a variety of possible solutions.  Some of these were:  S/MIME, FlowCrypt, Secure Mail for Gmail Extension, SendSafely, SafeGmail, ProtonMail, Mailvelop, Autocrypt, etc.  
I would like my son's encrypted email to work like Enigmail (Thunderbird) works.  
1.  It works with any email provider (gmail, hotmail, mediacom, etc)
2.  I would like to be able to send him my public key and have his system install it; and I would like him to be able to send me his public key and I install it.
3.  I would like both of us to use a secure signing system using our private keys.
4.  I would like him to be able to continue to use chrome for his email access.

I am sure many of you know exactly how to get chrome to support encrypted email, but I am struggling.  
Any help appreciated.........

---

### Post by SeijiSensei on 2020-09-16
Has he tried installing the Windows version of Thunderbird? Why must he use Chrome?

---

### Post by Holger_Gehrke on 2020-09-18
Chrome is not an email program, it's a web-browser. Using it for email means using a web-application as your actual e-mail program. Whether or not you can use encryption and what kind of encryption (s-mime or gpg or ... ? ) depends on the site, not on the browser.

Holger

---

### Post by TheFu on 2020-09-18
Browsers are a failure for secure email. There have been some attempts at browser-based gpg support, but I wouldn't trust these with family recipes.
Gmail only allows encrypted email when 3rd party applications are used.

Think about google's business model. They don't like encryption they don't control.

---

### Post by Ralph L on 2020-09-21
Thanks for the replies.  I appreciate it.  
I am making some progress on getting pgp encryption installed in a browser.  The two most promising browser add-ons for encryption, that I saw, were flowcrypt and mailvelope.  I picked flowcrypt and installed as an add-on to Firefox. (I have not tried installing it on chrome yet.)  I may also try mailvelope if I get a chance.  
I was successful in encrypting and signing messages (including multiple attachments) with Thunderbird (enigmail), sending them through my mediacom email server, and receiving and decrypting them on my gmail server using Firefox/ Flowcrypt.  I also was successful in doing the reverse--sending encrypted and signed email (including multiple attachments) from Firefox/ flowcrypt and receiving and decrypting them in Tbird/ Enigmail.  

Flowcrypt claims end-to-end encryption and I tend to believe them (unlike Zoom, who it's rumored decrypts data in the Zoom server making it vulnerable to theft).  To do end to end encryption Flowcrypt, when originating email, must encrypt it on the user's computer before transmitting it to the gmail server.  It must also download received email into the user computer before decrypting it.  Judging from the dynamic status indicators it seems to do this.  And flowcrypt must not forward the user's private keys to the gmail server.  I guess I'll just have to trust flowcrypt on this, since I know of no way to verify it.

There are some things I don't like about flowcrypt.  It has no way to bulk (batch) save multiple decrypted files to the users normal disk storage.  One of my tests had 20 files in it, and dragging and dropping them one by one into my file system was certainly tedious.  However, Tbird/ enigmail has this same problem, so I guess I can't complain too much.  Also, Flowcrypt, while it can decrypt received pgp/mime email, cannot encrypt to this newer standard.  Still another problem with flowcrypt is that it works only on gmail.  In contrast, Mailvelope is supposed to work on a variety of mail servers.

So that is where I stand so far.  A next step will be to try to install it on chrome in my son's windows computer.
Update:  My son got flowcrypt working on his windows chrome browser, so we are exchanging encrypted documents now.  Seems everything is working fine.

---

### Post by Dennis N on 2020-09-21
Easy way to send an encrypted message by email?

Write your message in a word processor and encrypt the file with the recipients gpg public key. Attach the encrypted file to an email message and send it to the recipient, who decrypts the attachment.

---

### Post by TheFu on 2020-09-21
My biggest concern is trusting browsers.  They are extremely complex and often fail to do what they claim to do.

In my mind, a false sense of privacy is worse than not using encryption at all. At least when we don't use encryption, we know that email is like a postcard to be read by anyone along the way.

---

### Post by Ralph L on 2020-09-21
Dennis N
What encryption/decryption program do you use in linux?  I used gpg (Terminal only) and it is somewhat awkward to use.  Is there a linux program with a gui??  Also, do you know of an encryption decryption program for Windows.  Obviously I would like the linux program and windows program to use pgp and be able to encrypt/ decrypt each other's files.

---

### Post by TheFu on 2020-09-21
Have you looked at non-email messaging systems for secured family communications?  

Something like RetroShare or Nextcloud talk or even wormhole just to exchange text files. 

I'm big on not using 3rd-party services, so take all this with that set of glasses. Self-hosting isn't for everyone. 

It is amazing what a raspberry-pi can accomplish. This stuff can be hosted for $5/month in almost any VPS provider too.  Amazon EC2 has a 1 yr free tier for a micro-instance that would run 1 of these things for a family. Whether it is an option or not depends on skills, 1 person's internet connection, the ability to remain patched, and desire to be secure. Most of these things aren't hard and don't need systems with much CPU/RAM. 

RetroShare isn't just messaging. It has files, bulletin boards and a few custom abilities based on those 3. Everything transferred is encrypted. I looked at it and ran a server for a few weeks with some friends before deciding to switch to Nextcloud and Wormhole transfers.  Nextcloud is locked down for only family IPs. I have to update those filters from time to time, but not as often as I would have thought. Perhaps once every 4 months. Maintaining some of these options is no different than weekly patching for any desktop.  Others, like nextcloud, need more hand holding and sometimes the simple upgrades/patching fails so manual corrective action and troubleshooting is required.

---

### Post by Dennis N on 2020-09-21
> **Ralph L said:**
> Dennis N
What encryption/decryption program do you use in linux?  I used gpg (Terminal only) and it is somewhat awkward to use.  Is there a linux program with a gui??  Also, do you know of an encryption decryption program for Windows.  Obviously I would like the linux program and windows program to use pgp and be able to encrypt/ decrypt each other's files.

The utility is a GUI plugin for the file manager, which is available in packages for Ubuntu and Ubuntu MATE. If you're using Xubuntu (XFCE), I don't think Thunar File Manager has this capability. I don't know about Chrome's capabilities. 

You can read about how the plugin (seahorse-nautilus) works here:
[https://www.techrepublic.com/article/how-to-enable-encryptdecrypt-menu-option-in-the-ubuntu-file-manager/](https://www.techrepublic.com/article/how-to-enable-encryptdecrypt-menu-option-in-the-ubuntu-file-manager/)
(The article doesn't mention MATE, but a MATE plugin (seahorse-caja) works in the same way.)

I can't recommend anything for Windows, since I haven't used it for several years now.

---

### Post by SeijiSensei on 2020-09-22
Thunderbird has native support for GPG via the EnigMail extension: [https://support.mozilla.org/en-US/kb/digitally-signing-and-encrypting-messages](https://support.mozilla.org/en-US/kb/digitally-signing-and-encrypting-messages)

Version 78 and later have built-in support for encryption. I believe only 20.10 (Groovy Gorilla) includes a version of TBird as recent as 78. My 20.04 installation has version 68.10.0 and would require using the EnigMail add-on to Thunderbird. [https://blog.thunderbird.net/2019/10/thunderbird-enigmail-and-openpgp/](https://blog.thunderbird.net/2019/10/thunderbird-enigmail-and-openpgp/)

---

