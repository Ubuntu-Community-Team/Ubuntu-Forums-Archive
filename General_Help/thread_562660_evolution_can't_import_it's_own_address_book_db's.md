---
title: "evolution can't import it's own address book db's"
date: 2007-09-29
forum: General Help
---

### Post by LuJo on 2007-09-29
Hello!
Before I reinstalled Ubuntu 7.04 I copied my personal folder (LuJa) from Home to an USB Stick, thinking I could just overwrite the newly installed Luja folder, including .evolution, so I could have my mails and address book again. The mails are there but the address book is empty! Trying to import the address book files with evolution's import function didn't work, because it doesn't accept the .db files. There was one thread suggesting I rename the evolution file before copying, but that didn't work, maybe I did something wrong.Does anyone have an idea?

---

### Post by dcstar on 2007-09-29
> **LuJo said:**
> Hello!
Before I reinstalled Ubuntu 7.04 I copied my personal folder (LuJa) from Home to an USB Stick, thinking I could just overwrite the newly installed Luja folder, including .evolution, so I could have my mails and address book again. The mails are there but the address book is empty! Trying to import the address book files with evolution's import function didn't work, because it doesn't accept the .db files. There was one thread suggesting I rename the evolution file before copying, but that didn't work, maybe I did something wrong.Does anyone have an idea?

Check the permissions on the files you copied across - they need to be set to match your new user credentials.

---

### Post by LuJo on 2007-09-29
That was it. Thanks! I wish all problems could be solved so easily.
Do you think it is a good idea to do frequent backups this way (copy home/user) to usb, or am I missing something important I don't know about?
And what about a total system backup (once or twice a year) in case the hard drive dies on me. It would take forever (almost) to figure out all those changes I made and the packages I downloaded. Some of it I printed, and sometimes I don't remember how I got things working. I am now Windows-free and would like to stay that way. What would you recommend?

---

### Post by Wolki on 2007-09-29
> **LuJo said:**
> Do you think it is a good idea to do frequent backups this way (copy home/user) to usb, or am I missing something important I don't know about?

It's not a bad way. Should be sufficient in most cases.

> And what about a total system backup (once or twice a year) in case the hard drive dies on me. It would take forever (almost) to figure out all those changes I made and the packages I downloaded.

Probably also not a bad idea.

You can get a list of packages and their status (installed/uninstalled) by doing "dpkg --get-selections", and of course you can use that to restore on another installation (man dpkg, or google, for more information). Things you installed from outside the repositories will not be automatically installed, though - the system doesn't know where to get them from.

---

### Post by dcstar on 2007-09-29
> **LuJo said:**
> That was it. Thanks! I wish all problems could be solved so easily.
Do you think it is a good idea to do frequent backups this way (copy home/user) to usb, or am I missing something important I don't know about?
And what about a total system backup (once or twice a year) in case the hard drive dies on me. It would take forever (almost) to figure out all those changes I made and the packages I downloaded. Some of it I printed, and sometimes I don't remember how I got things working. I am now Windows-free and would like to stay that way. What would you recommend?

I have a separate /home partition on my system, so this makes it easier to back up all my user data (and I do occasional backups to a USB stick) as well as make this data a little more protected from any potential filesystem corruption (because it is separated from the "/" partition).

I don't see much point of backing up the rest of an install, as the restore process from a major crash is almost as involved as doing a fresh install anyway - and you can muck up the system by copying/restoring things in critical system areas.

Anyway, you can do what you think is right for you, there are many, many options available!

---

