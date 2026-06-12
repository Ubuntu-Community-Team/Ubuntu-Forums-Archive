---
title: "Back in Time"
date: 2019-12-31
forum: General Help
---

### Post by Richard_Mockler on 2019-12-31
I have been using Back in Time successfully to back up my system for three years.  I did a complete install for Ubuntu Mate 19.04 then installed the Back in Time package.  I ran the backup for the first time and it appears that everything was successful.  Then when I attempted to open the backup folders, they did not have read/write permissions assigned during their creation by Back in Time.   I don't recall this predicament in my previous install three years ago.  I did a sudo caja and changed the backup folders and contents to read/write and the folders and files were then accessible.  But, on my next backup run, the backup folders and files were like the first backup, no read/write permissions.  Could someone kindly tell me what I must do stop this behavior?
Thank you,
rmockler

---

### Post by TheFu on 2019-12-31
Support for 19.04 ends in a few weeks.  Best to move to 19.10 now. If getting a clean backup was part of your migration plan - and it should be - I'd do an **rsync** for *this one time* just before the **do-release-upgrade** attempt.  Then come back to getting B-i-T working under 19.10.

Many things changed in 19.10 around snapd and restricted areas of disk.

BTW, when it comes to permission issues, please just post the **ls -al /path/to/directory** wrapped in forum _code tags_, including the full line WITH the command and prompt. We know how to read that.  Use the Adv Editor, then select multiple lines of pasted text and choose the "#".

Running some GUI programs with sudo can have undesirable outcomes.  The mitigation for that is:
**sudo -H caja** which will force the HOME directory to be changed to /root/ and prevent a normal userid's settings from being hosed.

---

