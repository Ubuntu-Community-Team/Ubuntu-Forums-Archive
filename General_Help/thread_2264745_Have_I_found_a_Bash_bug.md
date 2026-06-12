---
title: "Have I found a Bash bug?"
date: 2015-02-09
forum: General Help
---

### Post by netcom61 on 2015-02-09
I tried to look at some files on my USB-flashdrive, which is/was labeled Bill'sUSB.

When I tried to cd into it, I arrived at a command prompt instead of directory.   The drive was mounted at /media/Bill'sUSB and, if I can attach a screenshot, you'll see that trying to get a directory listing with cd, results in a bash command-prompt?

Is this a bug, do you think, or just the result of a broken rule in volume naming? Should I report it to gnome-terminal or bash?

thanks...

[ATTACH=CONFIG]259881[/ATTACH]

---

### Post by yancek on 2015-02-09
No.  You have an apostrophe in the name and it sees it as a quote and is looking for the closing quote.  Try replacing the apostrophe with a dash or an underscore

---

### Post by Impavidus on 2015-02-09
It's a quotation mark. By using a single quote in the directory's name bash thinks that you're not done typing the name and that the newline character is part of it. You have to escape the single quote (apostrophe) by prefixing it with a backslash: Bill\'sUSB

---

### Post by netcom61 on 2015-02-09
Ok... 
Thanks for the replies...

---

