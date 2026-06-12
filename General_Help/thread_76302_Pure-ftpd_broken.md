---
title: "Pure-ftpd broken?"
date: 2005-10-14
forum: General Help
---

### Post by Swad on 2005-10-14
I did a fresh install of Breezy and went to setup my pure-ftpd server.  Low and behold--it won't start.  I can't find any log messages, error messages or anything--it just doesn't start..  I know it's setup just as before.  I've been running this ftpd for a few years now and it's never and issue to get going whether on Debian or Hoary.  Did some changes in breezy cause it to break?  Is there anyone else out there how uses it that can confirm this or not?

---

### Post by Hikaru79 on 2005-10-15
What does it output when you try: sudo /etc/init.d/pure-ftpd start ?

---

### Post by Swad on 2005-10-15
Absolutely nothing.  It returns to a blank line and returns no message.  I've tried to purge the install and just start the server with a fresh install and no dice.  I have scoured this system and I can't find any messages about what is going on.  I *can* start the server directly at the command line not using the init.d file, but then it totally bypasses my config files.  I think something is up with the init.d file.  I'm going to log into my work machine with the working pure-ftpd server and grab it's init.d file and see if that one works.

edit: no dice--that wasn't the issue.  i am about burnt out on this.  never has this ftp daemon been this much of a bear to setup and run.

---

### Post by codex22 on 2005-10-15
[QUOTE=Swad]I did a fresh install of Breezy and went to setup my pure-ftpd server.  Low and behold--it won't start.  I can't find any log messages, error messages or anything--it just doesn't start..  I know it's setup just as before.  I've been running this ftpd for a few years now and it's never and issue to get going whether on Debian or Hoary.  Did some changes in breezy cause it to break?  Is there anyone else out there how uses it that can confirm this or not?[/QUOTE]

Open /etc/default/pure-ftpd-common

Change STANDALONE_OR_INETD to standalone:
STANDALONE_OR_INETD=standalone

After that I was able to start/stop pure-ftpd with inet.d:

/etc/inet.d/pure-ftpd start

Hope this helps!

Michael

---

### Post by Swad on 2005-10-15
I think you meant init.d instead of inet.d ;)  Any which way, it was defaulted to "inetd" and I switched it to "standalone" and viola!  it works again!  I guess in the past that file either didn't exist or it was set to standalone as I have never had to mess with that file on any previous debian or ubuntu systems.  Wonder why they decided to change it now?  Oh well--it works and my frustrations are over.  Thanks!

---

### Post by codex22 on 2005-10-15
[QUOTE=Swad]I think you meant init.d instead of inet.d ;) [/QUOTE]

:oops: Of couse I meant init.d ...

Never used pure-ftpd before (and its my first Ubuntu installation also!), so I can't tell you about the history of the config files for pure-ftpd.

Glad I could help!

---

### Post by b3nw on 2005-10-15
this package in debian asks you if you want standalone or identd when you install but for some reason in ubuntu it doesn't. Beacuse of this just installing pure-ftpd leaves you with a non-working ftpd. /etc/default/pure-ftpd-common edit is the fix. I have submitted bug to motu group.

---

### Post by lucifeer on 2005-10-23
I guess the problem comes from Hoary using the inetd-server for handling some network-services. So pure-ftpd would get started automaticly in Hoary when inetd was started at boot-time. But in Breezy they seem to have removed inetd and probably just forgot to edit this part of the .deb-package when adding it to the breezy-rep

---

### Post by suoko on 2005-11-09
Hi there,
great men, you solved my problem.
I now was wondering what is the clearest way to tell pro-ftpd service that it has to start with the "-lpuredb:/etc/pureftpd.pdb" option.

many thanks

---

