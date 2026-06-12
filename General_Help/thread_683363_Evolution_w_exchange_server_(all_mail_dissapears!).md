---
title: "Evolution w/ exchange server (all mail dissapears!)"
date: 2008-01-30
forum: General Help
---

### Post by Nick DC on 2008-01-30
This isn't the first time this happens to me and everytime I have to uninstall Evolution, delete all the mailbox files and re-install it to make it work. Simply removing the mailbox in evolution does not fix it. 

The problem: At a random instance in time (I cannot pin point where) my Inbox(and only my inbox) empties itself completely and shows no mail available even though on web mail everything is still there. Any subsequent new mail that comes in shows up but it shows only the new mail, ie it will show I only have 1,2,3,etc total messages.

Does anyone know how to fix this? this is driving me nuts.

thx!

---

### Post by kethanp on 2008-02-04
I am having the exact same problem as Nick. If anyone has a solution for this, it would be a huge help.

Thx!

---

### Post by dguy on 2008-02-06
Same thing happening here, any resolution for this? The way I fix it each time is to close Evolution, delete everything under ~/.evolution/mail/exchange/ and restart Evolution to make it download all the messages again.

I also usually need to restart evolution a few times before it can actually connect to our exchange server. Is the exchange plugin just flaky this way (by nature of needing to reverse engineer MS protocols) or am I doing something wrong?

Thanks,
Damien

---

### Post by kethanp on 2008-02-07
Damien,

I don't have issues with logging into the Exchange server. Initially I had to fiddle with the server address, login name and password settings until i found the right combo. But I'm assuming that not all servers are created equally.

As for deleting everything under the mail/exchange directory, that worked for me. I moved all the files out of the directory, and started Evolution and it updated properly. It is annoying to have to do this every time, but its a start.

---

