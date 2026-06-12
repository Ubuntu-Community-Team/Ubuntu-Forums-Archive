---
title: "Thunderbird takes ages to load messages"
date: 2018-11-09
forum: General Help
---

### Post by xadder on 2018-11-09
When possible I prefer to access my IMAP-account email through Thunderbird, but more and more it takes minutes or sometimes longer to bring up the email. If I sign in instead through webmail I get instant access and fast responsiveness. I've trawled through the forum looking for similar problems but so far haven't found anything that helped.

When thunderbird (60) does work, it works great and is much easier to handle than webmail. But increasingly I have to go to webmail first while thunderbird is "spinning its icon".

Help appreciated!

---

### Post by ajgreeny on 2018-11-09
Try shutting T'Bird, renaming the hidden ~/.thunderbird folder in your home as a backup, then restarting T'Bird, entering your email account credentials etc etc, again, to see if it is a problem in your configuration.

I use T'Bird for gmail with no problems at all whether IMAP or pop3; could it be your email provider blocking or not providing the correct authorisations for T'Bird in some way?

---

### Post by xadder on 2018-11-09
Thanks for the suggestion. I can try that on Monday when I'll be in my office and sitting beside my office PC which has the same credentials. I read somewhere though that IMAP does store files (despite being IMAP) and I can see those in a subdirectory to .thunderbird. My reading also suggested that if I started to remove files from the huge ImapMail directory in there that these deletions would also  be transferred to the IMAP server. I have no idea how this works, but I'm a little nervous of doing trial-n-error on that directory.

(On the other hand, maybe a clean install of the new Xubuntu 18.10 would do the trick, and that would also remove that directory.)

I don't think it is the email provider though since  I have two very different accounts, and thunderbird shows the same problems for both.

---

### Post by xadder on 2018-11-13
Quick update. I moved the .thunderbird directories as suggested, and re-configured. Seems to have improved things a lot, phew! I'll give a few more days to make sure, then mark as SOLVED.
Thanks again ajgreeny!

---

### Post by MSGone on 2018-11-14
Fairly regularly:

1 Click "Clear recent history" under tools.
2 Under files - first click "empty deleted" and then "compact databases"

The system should tell you how much space was given back. I find this works well for me and hope it helps you.

---

### Post by xadder on 2018-11-27
Thanks. I'll try that also. After my initial re-installation things improved, but still Thunderbird hangs quite often. Something else is needed.

---

### Post by missmoondog on 2018-11-27
fwiw, and i know it isn't much, thunderbird has gotten so bloated/slow i can't stand it myself anymore and gave up on it a long time ago now.

i use the nice and light sylpheed mail in linux and windows now. of course, don't use isp mail much at all either and i prefer to just sign into my gmail account at their website and not through my e-mail app.

---

