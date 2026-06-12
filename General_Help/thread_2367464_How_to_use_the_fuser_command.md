---
title: "How to use the fuser command"
date: 2017-07-30
forum: General Help
---

### Post by l6griffin on 2017-07-30
I'm having a problem with thunderbird. I have 3 mail accounts in TB and when I try to compact the inbox in yahoo mail I'd get the error msg that it was in use by another program. I submitted the problem to mozilla support and received the reply to use the fuser command to see what processes were using the inbox. I use terminal change directory to mail directory under TB and have not been able to get the to work. Any help appreciated.

---

### Post by TheFu on 2017-07-30
Did you try a web search of "*fuser examples*" or reading the fuser manpage?  

Just trying to help you solve THIS and 1,000 similar questions, instead of just answering this single question.

Some other google-fu is to use the "fuser howto" in a web search or "fuser ubuntu" - but these are for more complicated setup solutions, not single cmd stuff.

Just be aware that every distro release will use slightly different versions of each command, so options change slightly over time.  To see the specific options on YOUR system, only the *fuser --help* or *man fuser* will provide the most accurate answers.

---

### Post by l6griffin on 2017-07-31
No I didn't that usually doesn't get you much. Mozilla did get back to me with the correct command fuser file_name without any options worked.

---

### Post by TheFu on 2017-07-31
> **l6griffin said:**
> No I didn't that usually doesn't get you much. Mozilla did get back to me with the correct command fuser file_name without any options worked.

Odd. I find those searches to solve many of the issues I have.  BTW, ran each of those for fuser and found they explained the tool very clearly and I learned some new things.  I normally use lsof for stuff like this, but fuser seems easier to use for this specific use-case.

Regardless, happy that you found a solution that worked for you.

---

