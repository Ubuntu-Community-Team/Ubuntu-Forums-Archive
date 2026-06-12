---
title: "grsync odd results"
date: 2015-10-20
forum: General Help
---

### Post by cmcanulty on 2015-10-20
I am backing up all of / (the entire computer) with grsync and am getting odd results. At first I thought it was failing because in the backup /home was empty, then I noticed /librarian has all my home files. Why would the grsync backup put /home files under /librarian instead of /home/librarian as it should be, see screenshot. Thank you

---

### Post by ra7411 on 2015-10-20
> **cmcanulty said:**
> I am backing up all of / (the entire computer) with grsync and am getting odd results. At first I thought it was failing because in the backup /home was empty, then I noticed /librarian has all my home files. Why would the grsync backup put /home files under /librarian instead of /home/librarian as it should be, see screenshot. Thank you

Yes, why *would* it send backups to strange places?
I had the same results trying to backup my user directories under my Home directory to a second HD.

I had to experiment a few times to determine what I should use as the "source" and what I should use as "destination" - it was driving me batty for a while.
Experiment w/ a test directory and file a few times, then *write down* what works so you remember it next time. It's not particularly intuitive.

---

### Post by cmcanulty on 2015-10-20
I have used grsync for a long time and pretty well understand it but putting my home folder in the / instead of /home/ really baffles me it does seem to have everything there anyway

---

