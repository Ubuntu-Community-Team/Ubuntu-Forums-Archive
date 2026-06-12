---
title: "KMail broken - alternate email client ?"
date: 2017-01-12
forum: General Help
---

### Post by oygle on 2017-01-12
Installed Kubuntu 16.04.1 about 3 months ago. Plasma problems still there and KMail problems still not fixed.  :(

KMail is definitely **BROKEN** in version 16.04.1

These are just _some_ of the problems ..

* Constantly hangs or resource problems. ONLY workaround is exit KMail, then **akonadictl restart**, then back into KMail and hope it works. But many times it doesn't, so exit KMail, restart ,etc,etc ...... This type of problem goes on for at least 30 times per day.

* There are ghost emails in a number of folders ?

* Searching does NOT work at all

* Folders are often not updated

Can Thunderbird do all that KMail can do ? By that I mean, the functionality that does work in KMail. What about other email clients in Kubuntu ?

---

### Post by speartip on 2017-01-13
Thunderbird is probably your best bet for a linux Email client. You can add xul-ext-lightning for calendar support.
If you insist on KDE then the Neon LTS project is very good, & based on Ubuntu Repos. I've been using it for several weeks without issue. Being on the 5.8 LTS branch it's probably as stable as Plasma 5 gets at present.
[http://files.kde.org/neon/images/neon-userltsedition/current/](http://files.kde.org/neon/images/neon-userltsedition/current/)

---

### Post by oygle on 2017-04-16
Does anyone know when these bugs will be fixed please ?

---

### Post by vasa1 on 2017-04-16
> **oygle said:**
> Does anyone know when these bugs will be fixed please ?
Subscribe to the bugs. You'll be informed.

---

### Post by oygle on 2017-04-16
> **vasa1 said:**
> Subscribe to the bugs. You'll be informed.

Thanks; is there a specific bug reporting system for KDE or does it all show at [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)  ?

---

### Post by SeijiSensei on 2017-04-17
KDE has its own bug-tracking system at [https://bugs.kde.org/](https://bugs.kde.org/).

I've used Thunderbird and KDE together for well over a decade now.  I took a look a KMail every so often and saw no reason to switch.

---

### Post by oygle on 2017-04-18
> **SeijiSensei said:**
> KDE has its own bug-tracking system at [https://bugs.kde.org/](https://bugs.kde.org/).

I've used Thunderbird and KDE together for well over a decade now.  I took a look a KMail every so often and saw no reason to switch.

Thanks, I will look into [https://bugs.kde.org/](https://bugs.kde.org/)

KMail is the MailDir format (unique file name for every message). Is Thunderbird MBox or MailDir ?  Yesterday I was right in the middle of a phone conversation and needed to check something in KMail, but it crashed. So, wanting to change now to Thunderbird. Hopefully by dropping KMail, I can also drop any use of  Akonadi , which has been problematic for years and uses causes high load on the CPU.

---

### Post by SeijiSensei on 2017-04-18
Thunderbird keeps its local copies of remote folders in mbox format.  If you're connecting to an IMAP server, whether the server uses mbox or Maildir is of little import, since the server presents the messages in the same way regardless of the storage method chosen.  If you have local archives in Maildir that don't have corresponding messages on the server, then I don't know how Thunderbird will handle those.  

It might be possible to write a simple script in bash to compile the individual messages into an mbox file.  It has the following structure:
```

From sender@example.com  Tue Apr 17 23:00:00 2017
Return-Path: <sender@example.com>
Message headers and body

From ...

```
Each message begins with a "From" line, importantly without a colon to differentiate it from the "From:" header, followed by the entire message, then followed by a blank line.  You'd have to parse the top-most Received: header to get the correct date and rewrite it into the format above.

---

### Post by oygle on 2017-04-18
> **SeijiSensei said:**
> Thunderbird keeps its local copies of remote folders in mbox format.  If you're connecting to an IMAP server, whether the server uses mbox or Maildir is of little import, since the server presents the messages in the same way regardless of the storage method chosen.  If you have local archives in Maildir that don't have corresponding messages on the server, then I don't know how Thunderbird will handle those. 

I have never used IMAP. Most of our emails are in Maildir format as it is hosted by us and *nix. I'd prefer to keep using MailDir as it is very convenient copying single emails here and there, and not have to worry about some huge file with everything in it. I see Thunderbird now has MailDir, but it seems unstable for now.  Thanks for the tips on consolidating single maildir files to one file.  :)

---

### Post by oygle on 2017-04-24
Have been trialling Evolution and Claws. Found out today that what KMail displays and shows as the number of emails within a folder is not the same as on disk. Does anyone know how to extract **ALL** emails out via akonadi ?

Also, after I have transitioned to another email client, is it possible to completely uninstall akonadi ?  Without affecting anything else I mean.

---

### Post by zbyszko43 on 2017-04-24
My solution: sudo apt install thunderbird, (important: do not start Thunderbird yet!) when finish installation: sudo apt thunderbird -p, create new profile, choose folder (best way on other partition, can be ntfs, remember add that partition to automatic mount on start system, System Settings, Removable Storage, Removable Devices) You can created new one folder, then start Thunderbird. When You will be install new Kubuntu edition or other Linux edition, You can repeat installing Thunderbird this same way but choose this same folder on other partition You created then start Thunderbird. All Your accounts You created first time gonna be working. You do not have to create Your e-mail accounts again.
I doing that way by years and every thing working good.

---

### Post by oygle on 2017-04-24
> **zbyszko43 said:**
> My solution: sudo apt install thunderbird, (important: do not start Thunderbird yet!) .....

Thanks, but for various reasons I want to use MailDir format. It seems Thunderbird does have MailDir, but it is buggy.

---

### Post by oygle on 2017-04-24
Currently looking at Claws and Evolution. Claws support seems very good; the mailing list is active.

---

### Post by oygle on 2017-04-29
Whilst the problems with KMail/akonadi are **NOT** fixed, there is finally a workaround solution - [https://ubuntuforums.org/showthread.php?t=2359701&p=13639546#post13639546](https://ubuntuforums.org/showthread.php?t=2359701&p=13639546#post13639546)

Went with Claws email. The support on their mailing list is great.  :)

Also, this thread as a reference to the major problems with KMail/akonadi  - [https://ubuntuforums.org/showthread.php?t=2349281](https://ubuntuforums.org/showthread.php?t=2349281)

---

