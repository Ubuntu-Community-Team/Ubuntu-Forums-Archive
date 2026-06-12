---
title: "How to use Sylpheed to read local mail"
date: 2022-12-12
forum: General Help
---

### Post by Alex_Filonov on 2022-12-12
I'm trying to install some email client mostly to read local mail (in /var/mail/<username>). I want something lightweight and something which can be run remotely.
Tried balsa. Works great, but I had to reinstall system because of graphic card issues and after reinstall can't run it remotely. At all. No messages, no nothing, just doesn't appear. Please don't bombard me with answers "user ssh -Y", because that's what I'm doing. xclock works, most gtk+ programs don't.
Tried claws. Doesn't work remotely.
Tried sylpheed. But I can't set up local mail account. I have to choose between various POP3 and IMAP accounts when setting up, and after that I can't change to "None" in "receive" tab. Anybody knows how to work around?

---

### Post by matthewrkarlsen on 2022-12-18
Hello Alex_Filonov,

Have you tried Configuration -> Receive -> Check "Incorporate from local spool" (source: [https://users.fedoraproject.narkive.com/aZhT8UC1/how-do-you-read-sylpheed-local-mail](https://users.fedoraproject.narkive.com/aZhT8UC1/how-do-you-read-sylpheed-local-mail))

You can then navigate to set up a local account as follows: Configuration -> Edit Accounts -> Add -> Protocol -> None (local)

Regards,
Matthew

---

### Post by Alex_Filonov on 2023-05-03
Closing this thread. I gave up on Sylpheed. Set up an IMAP server and using Thunderbird to read.
It's a shame that Ubuntu can't provide normal UNIX functionality.

---

