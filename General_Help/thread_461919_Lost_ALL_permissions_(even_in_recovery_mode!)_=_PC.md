---
title: "Lost ALL permissions (even in recovery mode!) = PC useless"
date: 2007-06-02
forum: General Help
---

### Post by floke on 2007-06-02
Not sure what I have done, but I have no persmissions on my Feisty box. When trying to run as root I get a message saying I need to be suid root to perform the action. When trying to make myself root by using su - I enter my password but get a permission denied error. I discovered that I was no longer listed in my /etc/sudoers file, and managed to change this via recovery mode. But, when trying to edit my network configuration (gksu network-admin) I get a permission denied error - even when running as root in recovery mode!

What *may* have happened is that I altered the permissions of my home directory in my PCLOS partition so that a partition I use for documents could be shared whether I was in PCLOS or Feisty. To do this I had to alter the permissions from 501 to 1000, which is what Ubuntu uses. If my Feisty partition was mounted in my PCLOS home directory at that time, that could have borked something I guess.

Anyway, does anyone have any clue how I can restore my permissions?

---

### Post by floke on 2007-06-02
* EDIT * Sorry, stupid question.

---

### Post by floke on 2007-06-02
Right. Have isolated the problem - the output of ls -l /usr/bin/sudo is:

-rwxr-xr-x 1 1000 root 91508 blah blah

when it should be

-rwsr-xr-x 1 root root 91508...

Any know how I can change it back??

---

### Post by floke on 2007-06-02
Ok, so booted the liveCD and mounted my Feisty partition - then did

chown -R root:root - for all the root files and chown -R 1000:1000 - for all my home directory files

But still no luck...

---

### Post by Xbehave on 2007-06-02
using the live cd should guaranty root access, but i think your problem is that you may not have access to your sudoers so even root doesn't have the authority to do anything.
but i dunno how youd fix that

---

### Post by rillip on 2007-06-02
Similar issue here, maybe this will help you as well:

[http://ubuntuforums.org/showthread.php?t=461496&highlight=default+groups]("http://ubuntuforums.org/showthread.php?t=461496&highlight=default+groups")

---

### Post by floke on 2007-06-02
Thanks for the help.

To be honest I think it's hosed. Good job I have a separate feisty install on my pc - ready for gutsy testing, but now my main feisty OS. Remount home partition, install a few bits and pieces, and good as I was. Reckon my borked partition is destined for a fresh install of a gutsy build!

---

