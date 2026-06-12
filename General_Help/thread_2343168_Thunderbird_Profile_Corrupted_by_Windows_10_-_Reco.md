---
title: "Thunderbird Profile Corrupted by Windows 10 - Recovery Help Needed in Ubuntu"
date: 2016-11-14
forum: General Help
---

### Post by skanger on 2016-11-14
My Thunderbird profile is years old and was created within Windows XP. I decided to make the profile portable and copied it to a USB flash drive to use with a Windows 10 tablet, the XP machine, and multiple Ubuntu computers.

However the Windows 10 tablet constantly gave me problems  with my USB flash drives. It repeatedly messaged me that my flash drives  had problems, were corrupt, needed repair and/or reformatting. I used  these drives and their files with WIndows XP, Ubuntu and with printers,  never having a single issue.

I found that after allowing Windows 10 to  "correct" the non-existent problems, my files had been corrupted,  particularly my Thunderbird profile! A number of in-boxes and sent mail  folders are empty due to the corruption. 

Should I work to restore the corrupted folder in  WIndows XP (where they were created and used for years) or Ubuntu?

I have the original backup but its now out of date by a few days worth of email that came through before the USB drive was corrupted. I'm hoping to recover everything in the corrupted profile so I don't lose recent mail.

Also, since getting the profile to be found by Thunderbird on my 16.04 computers (thanks to oldfred here) I now have even more new mail. Should I move this most recent mail to another folder while attempting recovery?

Thank you for any help with this problem.

---

### Post by oldfred on 2016-11-14
I do regularly back up my Thunderbird & Firefox profiles. But have not used them with Windows 8 or 10.

Is issue perhaps related to Windows always on hibernation. It leaves all NTFS partitions mounted when it has fast start up on.
And seen others with external drives have issues. Not sure even if unmounting an external drive with Windows 10 whether NTFS has hibernation bit checked or not?

Because my wife & I are not always at same desktop computer before I copy profiles back, I do find Comcast will redownload about 5 days worth of emails. Only if I go online and delete from Comcast directly will emails not download again.

---

### Post by skanger on 2016-11-15
Are you saying that I should use the backup and try to pick up the recent messages instead of trying to recover the corrupted inboxes?

About Windows 10, its no longer on any of the computers here so I can no longer check any of its activities. About hibernation, I turned it off on all Windows machines here. Its always given me trouble.

What I experienced was a series of non-stop messages as soon as any drive was plugged in. Even running the different recommended operation made no difference. Some searches on this subject turned up a lot of similar stories. Apparently its an internal problem with Windows 10.

---

### Post by oldfred on 2016-11-16
If backup is recent I would restore it and see if your email provider still downloads missing email.

If Windows ran chkdsk and moved some files from standard locations it may be difficult to fix.
You may be able to use Meld or other comparison tools to see what changed between backup & broken version. I would expect some files to be updated.

---

### Post by SeijiSensei on 2016-11-16
If you're using IMAP, then all your mail should still be on the provider's server.  If you're using POP3, it depends on whether you checked the "leave mail on server" option in Thunderbird.

---

