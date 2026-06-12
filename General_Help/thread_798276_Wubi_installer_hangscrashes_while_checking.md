---
title: "Wubi installer hangs/crashes while checking"
date: 2008-05-18
forum: General Help
---

### Post by jamesbeatty on 2008-05-18
Running on Vista Ult 64 w/ Intel chip, the Wubi installer downloads the file without apparent failure, then starts "checking the file", all 697 mB of it. It does this at a rate of about 20 kb/s, so that takes about nine hours -- although for no reason I can deduce this sometimes kicks up to about 300 kb/s. I've tried to install this thing three times, and it fails differently each time. First, it just stopped responding about 80% of the way through. Then, it got to 100%, but then started over, and then stopped responding. The third time, it did the check at 300 kb/s the whole way through -- then when it was done it started over again, this time at 4 kb/s, which means it would have taken about 2 days.

At that point I figured I must be doing something wrong. I couldn't find any posts on this forum about a similar problem, does anyone have any ideas what might be going wrong?

---

### Post by ago on 2008-05-18
Is it slow downloading the file or checking the file? The md5checksum should take less than a minute.

---

### Post by jamesbeatty on 2008-05-18
The download is fine. It's the checking that takes a long time and never successfully finishes.

---

### Post by ago on 2008-05-18
There should be a couple of logs in C:\ubuntu and another wubi log in your user temp folder. Please post them all.

---

### Post by jamesbeatty on 2008-05-19
They're too large to post individually, so they are in this .zip file.

---

### Post by jamesbeatty on 2008-05-22
Does anyone with more knowledge than me about this sort of thing (which is to say, any knowledge about this sort of thing) have any ideas what the problem(s) might have been? I've tried it a couple more times, and it still isn't working. Downloading the ISO didn't help either. At this point I'm just going to partition one of my drives and install 8.04 the old-fashioned way, but I'm still curious if anyone has any insights.

---

### Post by ago on 2008-05-24
Try to download the ISO manually and place it in the same folder as wubi.exe

---

