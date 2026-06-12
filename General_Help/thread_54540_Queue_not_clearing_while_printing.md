---
title: "Queue not clearing while printing"
date: 2005-08-05
forum: General Help
---

### Post by WhytTiger9 on 2005-08-05
Hi all,
    I've been working on setting up one of my computers as a file and print server.  I've had no problems setting up the file sharing, but unfortunately I've run into one snag with the printer setup.  I've decided to use Samba + CUPS to print, so that this box plays nice with the windows boxes I have.  After tinkering for a few hours, I have finally got everything close to the desired effect of having the OS be transparent as far as the windows boxes are concerned.  The one problem I have is, the print queue on windows (using XP...) doesn't clear for me when each job is completed.  If I manually cancel the job from windows, the next job starts fine, but I expect there has to be a better way.  Please let me know which config files I should post, and of course, thanks for your help!

Printer: HP DJ 6122 connected through USB

---

### Post by WhytTiger9 on 2005-08-05
I believe I have fixed the problem, although I'm not entirely sure.  In my case, I took some advice I found elsewhere on the forum (addressing a seperate issue... but I thought it might still have relevance) and installed "Print Services for Unix".  Once I did that, it allows me to print multiple things, and prints them much faster.

---

