---
title: "Deleting email messages from Thunderbird."
date: 2014-05-27
forum: General Help
---

### Post by Peter_Rogers on 2014-05-27
Hi,

Can anyone help?

I cannot delete emails from my inbox. The delete command does not work.

Peter.

---

### Post by ajgreeny on 2014-05-27
Are you using pop3 or imap for your email account in TB?

---

### Post by Peter_Rogers on 2014-05-28
Hi there,

POP3

---

### Post by ajgreeny on 2014-05-28
Strange !

Can you show the output of the terminal command ```
ls -R -al .thunderbird/*default
``` in order to check ownership of all the files and folders in your TB profile.  Everything should be owned by you and therefore show your username near the start of all the lines for files and folders.

---

### Post by Peter_Rogers on 2014-05-28
-rw-rw-r-- 1 peter peter     5240 May 27 11:47 Sent.msf
drwxr-xr-x 2 peter peter     4096 May 27 12:24 Trash
-rw-rw-r-- 1 peter peter     2620 May 28 11:46 Trash.msf
drwxr-xr-x 3 peter peter     4096 May 27 12:24 Trash.sbd

.thunderbird/y1ai7410.default/Mail/pop.british-gazette.co.uk/Trash:
total 12
drwxr-xr-x 2 peter peter 4096 May 27 12:24 .
drwxr-xr-x 4 peter peter 4096 May 27 12:24 ..
-rw------- 1 peter peter    0 May 27 12:24 test
-rw-rw-r-- 1 peter peter 2409 May 27 12:24 test.msf

.thunderbird/y1ai7410.default/Mail/pop.british-gazette.co.uk/Trash.sbd:
total 16
drwxr-xr-x 3 peter peter 4096 May 27 12:24 .
drwxr-xr-x 4 peter peter 4096 May 27 12:24 ..
drwxr-xr-x 2 peter peter 4096 May 27 12:24 test
-rw-rw-r-- 1 peter peter 1423 May 28 12:00 test.msf

.thunderbird/y1ai7410.default/Mail/pop.british-gazette.co.uk/Trash.sbd/test:
total 8
drwxr-xr-x 2 peter peter 4096 May 27 12:24 .
drwxr-xr-x 3 peter peter 4096 May 27 12:24 ..

---

### Post by ajgreeny on 2014-05-29
Everything seems to belong to you as user peter, and all files and folders seem to be read/write so I am baffled as to why those messages will not allow you to delete them.

You mention in your original post that the "delete command does not work".  I assume you are simply pressing the delete icon or hitting the Del keyboard key, not actually using a command in terrminal; am I correct?

---

### Post by Peter_Rogers on 2014-06-03
Yes. You are correct.

---

