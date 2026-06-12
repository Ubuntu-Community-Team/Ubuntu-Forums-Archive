---
title: "Evolution: &quot;Timed out trying to get lock file&quot;"
date: 2008-01-25
forum: General Help
---

### Post by stefangachter on 2008-01-25
I came across the following message on another forum, but no solution has been posted. So, maybe somebody here has an answer to the following problem. Thanks in advance for any hint.

Hi

I use a number of computers in different locations and carry my recent data
on a USB stick drive. By linking certain directories on the machines (eg,
/home/gjj/documents) to the stick drive, I have seamless access to my
documents wherever I am.

I have tried to do this to my email but have consistently hit problems.
These are described below. Any suggested solutions are most welcome.

1 When copying the existing data (/home/gjj/.evolution) to the stick,
certain files refuse to copy.

2 I then link back to the hard drive from the stick the .evolution directory

3 When I then try to use evolution it opens but when I try to open a
message or receive mail to the inbox I get a message as follows;

Timed out trying to get lock file on /home/gjj/.evolution/mail/local/inbox.
Try again later.

4 Even when I delve down into the file structure and only copy across
the (eg) /mail/local/system/ folder and link these lower level directories
back to the hard drive I get the same problem.

I thought it might be permissions but having tried all sorts of permission
combinations I do not think it is that. Is it something to do with the
internal database. Does anyone have any ideas?

Hope someone can help me.

Geoff

---

### Post by dcstar on 2008-01-25
> **stefangachter said:**
> 
.........
1 When copying the existing data (/home/gjj/.evolution) to the stick,
certain files refuse to copy.
.........

I have no problem copying my whole .evolution tree using Nautilus - even if Evolution is running.

---

### Post by stefangachter on 2008-01-26
Thanks for the comment. I am wondering why I have this problem. I tried to copy the evolution tree several times, also with Nautilus. Each time I had a problem with some "locked" files.

Stefan

---

### Post by dcstar on 2008-01-26
> **stefangachter said:**
> Thanks for the comment. I am wondering why I have this problem. I tried to copy the evolution tree several times, also with Nautilus. Each time I had a problem with some "locked" files.

Stefan

Rename the .evolution tree and then restart Evolution, it will create a whole new tree with a fresh configuration.

You can then copy various files from the old to the new to recover your data - make sure the permissions of the new folder are retained.

---

