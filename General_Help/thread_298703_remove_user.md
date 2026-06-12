---
title: "remove user"
date: 2006-11-13
forum: General Help
---

### Post by zmartant on 2006-11-13
I ran the following command:
sudo adduser johndoe disk

I did so thinking I could use the cdrw, only to find out that the media was bad.  After I changed the media the command from the CLI worked (sudo cdrecord dev=/dev/cdrw blank=all).  So now I am trying to revert back by removing the user I added to disk.
Can someone tell me what the command "sudo adduser johndoe disk" does and if there is a reversal for this command.  I have tried sudo removeuser johndoe disk, but that give me an error.  I have tried several others and failed. ](*,) I have googled for hour and could not find an answer.

Thanks!

---

### Post by bollix47 on 2006-11-13
Take a look at:

man deluser

---

### Post by zmartant on 2006-11-13
> **bollix47 said:**
> Take a look at:

man deluser

Thank you bollix47, that did the job!
-Zmartant

---

