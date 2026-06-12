---
title: "[SOLVED] How to schedule downloading files with firefox over night"
date: 2008-03-13
forum: General Help
---

### Post by IanB2 on 2008-03-13
I'm moving to a new ISP that offers unlimited downloads between midnight and 8am and recently been downloading iso images for use in virtualbox from http sites.

I'd like to set up firefox to schedule a download between these times but have not be able to find anything so far (firefox extensions etc)

Any tips on how to do this would be fantastic.

---

### Post by Distro Jockey on 2008-03-13
Your best bet is to use **wget** and **cron**. (check **man wget** and **man cron** for options)

An example wget line would be:
wget --directory-prefix=/path/to/download/folder --input-file=ListOfFilesToDownload.txt

Then use cron to schedule that command. (sorry, never played with cron, so can't give an example at this time :)

---

### Post by Distro Jockey on 2008-03-13
Actually, **at** would be a better option over **cron**. (see **man at**)

---

### Post by ibuclaw on 2008-03-13
Hi, just a small suggestion, but perhaps setting up a cron job to do the task may help?

It would require having to edit your cron file every day, and perhaps limit yourself to one or two downloads, but something like this should do it.

```
 0 21 * * * root wget http://releases.ubuntu.com/gutsy/ubuntu-7.10-desktop-i386.iso -P$HOME/ISOs 
```

You can use "man cron" and "man wget" to find out what this does fully, but in short:
Everyday at 9pm (21),  as root you download (wget) the ubuntu desktop iso and save it to your $HOME/ISOs folder (-P).

You can change it to your needs. ie: instead of root, have your username and instead of 21, perhaps 1 or 0. (1am/0am)

All you need to do is create a text file in your "/etc/cron.d" folder. Make sure that you include **#!/bin/sh** at the top.

Give it a try and tell us if it works!

Iain

[EDIT]
Oops, someone beat me to it...
Too slow...
[EDIT]

---

### Post by kpkeerthi on 2008-03-13
> Your best bet is to use wget and cron. (check man wget and man cron for options)

An example wget line would be:
wget --directory-prefix=/path/to/download/folder --input-file=ListOfFilesToDownload.txt

In addition, you may want to use wget with -c switch so it resumes from where it left previous night. And you need another cron entry to gracefully kill wget just before 8 am.

Also try aria2. It supports segmented downloads.

See [http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)

---

### Post by IanB2 on 2008-03-15
> **tinivole said:**
> Hi, just a small suggestion, but perhaps setting up a cron job to do the task may help?

It would require having to edit your cron file every day, and perhaps limit yourself to one or two downloads, but something like this should do it.

```
 0 21 * * * root wget http://releases.ubuntu.com/gutsy/ubuntu-7.10-desktop-i386.iso -P$HOME/ISOs 
```

You can use "man cron" and "man wget" to find out what this does fully, but in short:
Everyday at 9pm (21),  as root you download (wget) the ubuntu desktop iso and save it to your $HOME/ISOs folder (-P).

You can change it to your needs. ie: instead of root, have your username and instead of 21, perhaps 1 or 0. (1am/0am)

All you need to do is create a text file in your "/etc/cron.d" folder. Make sure that you include **#!/bin/sh** at the top.

Give it a try and tell us if it works!

Iain

[EDIT]
Oops, someone beat me to it...
Too slow...
[EDIT]

Brilliant although I've not had chance to try this as I'm one of the lucky Redten broadband customers without a connection at present ...... but will try this as soon as I'm able. Your explanation of the command is much appreciated as I'm new to this 'command line' thing but getting up to speed as I need to do things!

---

### Post by asteinmetz on 2008-04-06
I have had sucess with **[Webmin]("http://www.webmin.com/")**, a web administration tool with a free version.  I am a running a couple of Ubuntu servers in the basement administered from my Windows machine upstairs.  With Putty I could remotely make a cron job and use WGET but I am a pointy-clicky sort of guy.  Webmin allows scheduled downloads.  The relevant tab on the web interface has this description.

[INDENT]*This form allows you to download files or web pages from HTTP or FTP URLs to the system running Webmin. The download can be done immediately, or scheduled for some time in the future.*[/INDENT]

No reason you can't run Webmin locally.

---

