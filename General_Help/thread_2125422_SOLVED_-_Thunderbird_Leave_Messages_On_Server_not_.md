---
title: "SOLVED - Thunderbird: Leave Messages On Server not working"
date: 2013-03-13
forum: General Help
---

### Post by cforput on 2013-03-13
I'm trying to get my messages to stay on Gmail's server when I download them to Thunderbird. I have the "Leave Messages On Server" flag ticked and the 2 options below that ("For at most nn days" and "Until I delete them" unchecked. I've set the flag, shut down Thunderbird, even rebooted. When I download my messages they are still being deleted off of Gmail. 

Anyone have any ideas? This is driving me nuts.

---

### Post by sgage on 2013-03-14
Are you sure the messages aren't just being tagged 'archive' by gmail? When you download a msg to a local email client, the msg will no longer appear in gmail's inbox. I don't think you even *can* remove messages from the gmail server from a client if you want to - at least I never could.

---

### Post by cforput on 2013-03-14
Well, I solved my own problem. Seems like after I do one of these posts, I invariably figure things out myself. I switched from POP to IMAP and that did it. After I did that thought I noticed a flag under Forwarding and POP/IMAP in the settings page that says "When messages are accessed with POP". One of the options is to leave a copy in your gmail inbox. It was set to delete the messages and since I had already switched to IMAP and it was working, I didn't bother seeing if it would work under POP.

---

### Post by cforput on 2013-03-14
I would mark the thread solved but I can't seem to figure out how to do that. I did put "SOLVED" in the title. Best I could do...............................

---

