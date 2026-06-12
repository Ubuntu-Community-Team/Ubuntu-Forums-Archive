---
title: "On Startup: User's home/.dmrc file is being ignored"
date: 2007-04-26
forum: General Help
---

### Post by venator260 on 2007-04-26
As the subject indicates, when I boot Fiesty, I get an error message that says:

[COLOR="Red"]User's $Home/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's HOME directory must be owned by the user and not writable by other users[/COLOR]

Not sure what happened that this does this... this started before I upgraded to Fiesty from Edgy, and it started for no reason that I can think of in Edgy.

---

### Post by 289Shelby on 2007-04-26
Does this help?

[http://kubuntuforums.net/forums/index.php?topic=3080910.0](http://kubuntuforums.net/forums/index.php?topic=3080910.0)

---

### Post by az on 2007-04-26
That error message is cryptic.

It should be split into two differnt errors.  One concerning the .dmrc file permissions and the other about the permissions of the home folder.  You cannot make your home folder writeable by anyone other than yourself.

---

### Post by venator260 on 2007-04-26
289Shelby... I get an error message with that URL: "PHP has encountered an Access Violation at 02219AB5"

---

### Post by aidanr on 2007-04-26
[http://ubuntuforums.org/showpost.php?p=2427423&postcount=2](http://ubuntuforums.org/showpost.php?p=2427423&postcount=2)

---

### Post by venator260 on 2007-04-26
Thanks aidanr, that did it.

---

### Post by pete224 on 2008-03-11
I want too thank you, too. I was ready to reinstall ubuntu. You saved me a heck of alot of time.

---

