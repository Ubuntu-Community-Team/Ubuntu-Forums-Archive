---
title: "Robust Bulk Imap Filter"
date: 2008-01-14
forum: General Help
---

### Post by watricky on 2008-01-14
Hey guys

Somehow my filters in Thunderbird went haywire, moving all my mail into a subfolder. I tried moving it back but instead I think it only copied the mail before eventually crashing, making the situation worse. I'm running Kubuntu Feisty.

The situation now is that I have 45000 emails (18GB) spread across my IMAP Inbox and a subfolder (60-240 notifications per day x 3 years). The notifications are the main thing that I need to get rid of since its making up about 95% of my inbox. I'm not too bothered about looking at the history of notifications. I'm only really interested in, at most, the last 3 days worth and, temporarily, I don't mind removing them all anyway. All the mails have very similar subject lines.

As you can guess just opening my mail is now a nightmare and I'm unable to delete any of these mails due to timeouts. The windows Smartermail imap server is on the local LAN. I do have administrative access to it but even Outlook Express on the server is timing out.

I'm trying to figure out what is the most robust way to get rid of these mails, even if I have to script something that'll take them out one at a time. I took a look at imapfilter but I'm having difficulty getting it to do anything (don't even know if it is connecting). If there's anything you guys can recommend, please let me know.

---

### Post by watricky on 2008-01-15
I eventually resolved to just move all the mail out of the folder on the server and start from scratch.

I can dump small bits (200-300MB at a time) of the mail into new subfolders and try filtering again from there. Bit of a schlep but its working already. I've also set up a filter server-side (should be more robust) to automatically remove mail older than 90 days from my notifications folder for future.

I've learned a thing or 2 out of this. :)
1: Don't keep lots of mail that you know you don't need
2: Imap doesn't have a "Move" command. Moving mail actually copies it and THEN deletes it.

I'd still like to know if there's a more elegant solution rather than starting from scratch.

---

