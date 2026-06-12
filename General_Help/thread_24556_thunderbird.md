---
title: "thunderbird"
date: 2005-04-07
forum: General Help
---

### Post by brickbat on 2005-04-07
Hi, After setting everything up perfectly and transferring all of my data over, thunderbird stopped working.  It workecd perfectly for a full day.  Here is a screenshot.  I'm a noob so I don't know what to do to check out why its doing this.  It just sits there like this.  I tried restating the computer but when I run it again it does the same thing.  Can someone please give me some advice about what to check?  I don't even know how to check what processes are running.  What can I do to see whats going on?

ciao,
bb

---

### Post by Leif on 2005-04-07
Try reinstalling it. Does that help ? And don't worry, your setting will be retained.

---

### Post by Technoviking on 2005-04-07
Have you apt-get update|apt-get dist-upgrade to the latest Thunderbird? I was having the same problem till Thunderbird was upgraded to 1.0.2.


Also, are you using any extensions in Thunderbird? Message Faces use to cause me problems.

Mike

---

### Post by brickbat on 2005-04-07
UPDATE: Ok, here is what I did.  I used a backup prefs file and it worked perfectly but my databases were gone.  This suggests that something in my database or the profiles has gone pear-shaped.

Then I renamed the databases directories (I have 4) one by one and found that it was the main one that it was the main one that is causing the problem.

Is there any tool to verify/repair the databases in Thunderbird?

ciao
bb

---

### Post by brickbat on 2005-04-07
UPDATE SOLVED! - hERE IS HOW i DID IT.

Each mailbox has 2 files - a data file with no extension and an index file with an .msf extension. I just renamed it and found that thunderbird automatically rebuilds it.  Then it worked.

ciao,
bb

---

