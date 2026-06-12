---
title: "[SOLVED] Saving passwords"
date: 2007-04-28
forum: General Help
---

### Post by pappo on 2007-04-28
I have so many places, I log into, that require username and password.
I try not to use the same one all the time.

Is there a Linux app or script that will allow me to enter the paswords in plain text and then encrypt them.
Then when I can't remember the password I just need to decrypt the file and see what it is ?

Regards,
pappo

---

### Post by DeadEyes on 2007-04-28
There are a number of ways you could approach this depending on the level of security you want. Firefox has a master password manager, I'm not sure how secure it is. You could just put your login info  in anOpen Office document and save it with a password. At the other paranoid end of the scale you could use something like GnuPG. I personally use truecrypt for storing stuff, however the one in the repos doesn't work so you'd have to compile it yourself.

---

### Post by getaboat on 2007-04-28
Revelation password manager is in the repos. I use this on Linux after using Roboform on Windows.

---

