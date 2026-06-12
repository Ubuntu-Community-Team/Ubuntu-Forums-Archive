---
title: "Evolution 3.10.4 stops getting some mail until reboot"
date: 2014-10-27
forum: General Help
---

### Post by cigtoxdoc on 2014-10-27
I have had this happen on two very different PCs running Ubuntu 14.04 64-bit with two differnt POP e-mail accounts.  Evolution 3.10.4 is e-mail client.  The first was a coxmail.com business e-mail account and the second was a bellsouth.net persoanl e-mail account.  Both of these accounts get 2 to 3 dozen e-mail a day and when they stop, you notice it.  In both cases, evolution appears to be fetching mail, but doesn't.  Once you reboot, start evolution, and go to receive mail, it comes in without problems.

Has anyone else had this problem?

John

---

### Post by tafthorne on 2015-06-04
I think I have come across this same issue.  Unfortunately the only reference to this behaviour I can find seems to be mentioned here.  Has anyone else noticed that Evolution will stop receiving emails after a while or perhaps after it has been closed once or twice without logging out?  I do have 1 POP account and 1 GMail account linked, so perhaps the POP is significant here.

---

### Post by cigtoxdoc on 2015-06-04
The best place for problems dealing with evolution is a post to [email]evolution-list@gnome.org[/email].  I can tell you from past experience that the first thing you are likely to hear is that 3.10.4 is obsolete as far as the developers of evolution are concerned (even though Ubuntu 14.04 thinks it is current).  Best approach I have found to solve many evolution-related problems is to upgrade to Ubuntu 15.04 and use evolution 3.16.0, which you need to install using synaptic from launchpad and add [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) vivid main to your repositories.  I am running 3 POP accounts and one IMAP account, where in my case the number of concurrent connections must be 1 for promptly getting mail from the server.

john

---

### Post by buzzingrobot on 2015-06-04
Older vesions of Evolution sometimes put themselves in offline mode because they do not reconnect to the server after the machine resumes from sleep.  If it is offline, the "File" menu will have an entry to bring it online.

---

### Post by tafthorne on 2015-06-10
Thank you for the advice.  I am not sure that moving off of the LTS version will be a popular move at work.  I can see if it is possible to get a more recent version of Evolution installed though.  I was using Debian before now and it was usually possible to try more recent versions of software... well when you didn't break a tone of stuff by doing it.  I shall give things a go.  Good to know that it might be better in the newer version though, that gives me some motivation to upgrade something.

---

### Post by tafthorne on 2015-06-10
> **buzzingrobot said:**
> Older vesions of Evolution sometimes put themselves in offline mode ...  If it is offline, the "File" menu will have an entry to bring it online.

I checked that it was not in offline mode. I even tried manually putting it into offline mode for a short while then brining it back into online mode to see if would unjam something.  No luck I am afraid.  Thanks for pointing out it sometimes goes offline by itself though.

---

