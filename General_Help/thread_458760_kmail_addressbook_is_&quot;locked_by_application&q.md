---
title: "kmail addressbook is &quot;locked by application&quot;"
date: 2007-05-30
forum: General Help
---

### Post by Jack H on 2007-05-30
Hope someone can help -- When I try to edit or enter a new address in the addressbook I get the message:
     /kde/share/apps/kabc/std.vcf is locked by application
Otherwise the kmail program works just as it always has.
Thanks in advance  --  Jack

---

### Post by Crafty Kisses on 2007-05-30
You should go in terminal and type:
```
top
``` 
And look for the application, and possibly try to end it.

---

### Post by Jack H on 2007-05-30
Thank you for the reply -- I entered the top command and got a lot of info, however, I feel a little dense as I do not know how to identify the culprit.  There are at least 30 lines, a few with program names and many I can only guess at their meaning.  But I can see you lead me to new territory.  Please explain and I will try to learn.  Thanks again

---

### Post by Crafty Kisses on 2007-05-30
> **Jack H said:**
> Thank you for the reply -- I entered the top command and got a lot of info, however, I feel a little dense as I do not know how to identify the culprit.  There are at least 30 lines, a few with program names and many I can only guess at their meaning.  But I can see you lead me to new territory.  Please explain and I will try to learn.  Thanks again

Yeah it can be complicated, there should be a column called %CPU, and see what's taking the most percent.

---

### Post by Jack H on 2007-05-31
The most used or highest %CPU is Xorg at about 5 to 7 %.  Followed by Konsole or Konqueror at half that reading or less.  I do not recognize Xorg.  The column it is in is labeled Command.  The line with the Xorg has a  large number under Time+ at 189:03.15.  Hope this is a clue.  Thanks again.    Jack

---

### Post by Jack H on 2007-05-31
**FIXED !!**
Thank you very much for your interest in this mean little problem.
   The story is that others have had the same problem and it is a recurring flaw that pops up after updates.
    The fix is to follow the path to the lock directory where the std.vcf file resides and delete the lock file.  Then it works.
     The other trick is to put the Kmail program to bed before exiting the session (restarting or shutting down or I suppose switching from KDE to Gnome) otherwise the problem is apt to return.
      The whole thing was beyond my scope, but I had help from someone who tracked it down on some postings elsewhere.
      Thanks much for your help.     Jack

---

