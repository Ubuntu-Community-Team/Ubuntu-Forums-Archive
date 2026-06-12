---
title: "HD running continually when on Firefox"
date: 2017-02-09
forum: General Help
---

### Post by Autodave on 2017-02-09
Machine boots OK. Sits there OK. Open Firefox, and swap file goes to up and HD runs almost continuously. Go to Drpbox, and HD light stays on and swap constant at 50%. Mouse pointer barely moves or quits moving altogether for awhile.  Only way to get back is to reboot machine.

Thinking that I had a problem with motherboard or RAM, I swapped HD into another machine. Still same problem.

Current machine is 3.4 quad core, 2 gig RAM, 1 TB HD that is 90% empty.  Last machine was 2.8 dual core, 4 gig RAM. Same HD.

Any ideas?

---

### Post by ajgreeny on 2017-02-09
Close FF then try temporarily renaming the hidden **.mozilla** folder in your home (Ctrl+H to show hidden files/folders) as **.mozillabackup** then restart FF.

Is that any better?
Firefox should not, and does not, have that problem in my system so I wonder if this is profile problem; renaming that folder will give you a new FF profile.
If this is the case we can go from there to get back your bookmarks etc etc as you want.

Can't help with dropbox as I've never used it.

---

### Post by Autodave on 2017-02-09
It is running great now. How do I get my stuff back: especially passwords?

---

### Post by Autodave on 2017-02-10
Update: the problem appears to mostly be with Dropbox. When I go to Dropbox to d-l a file, before I even click on the DOWNLOAD button, my memory usage starts to climb and continues to climb all the way up until the whole 2 gigs are used. Then, the SWAP starts to climb until it is at the 2 gig mark. And then it sits there. Sometimes the mouse will move, sometimes not. Clicking on anything does nothing. Usually, the only thing to do is a hard shut down. I have let it sit there for over 10 minutes: memory maxed, swap at 2 gig, HD light on constantly.

Any ideas?

---

### Post by ajgreeny on 2017-02-10
No sorry I can't help with dropbox; never used it and no intention of doing so.

For your passwords saved in old profile see [https://support.mozilla.org/t5/Firefox/How-do-I-copy-the-file-with-my-saved-passwords-before-I-reset-my/m-p/967748](https://support.mozilla.org/t5/Firefox/How-do-I-copy-the-file-with-my-saved-passwords-before-I-reset-my/m-p/967748)

Your bookmarks are saved in a folder called, surprise, surprise, bookmarkbackups and you can choose the most recent of those in your old profile folder and import it.

Good luck!

---

### Post by howefield on 2017-02-10
> **Autodave said:**
> Any ideas? 

You could quit dropbox then delete/rename the hidden folder ~/.dropbox and restart dropbox. The daemon should download again and then sign into your account.

---

### Post by Autodave on 2017-02-10
Another update for what its worth. Replaced HD and computer. Copied .mozilla....the 2 files from old to new. Worked great. Downloaded 3 files from Dropbox: each 50-60 meg in size. Went to do 4th one, HD light lit up, mouse quit functioning. Memory usage went right up to 4 gig, swap to 4 gig.  Sat there like that for several minutes before I rebooted via power button. Upon reboot, came up on screen: removing orphaned inode files: there were about 8 of them. Back to Dropbox. First d-l was fine, second downloaded OK but then HD light lit up and same thing. Rebooted via power button. Got same message again: removing orphaned inode files: 3 this time. Files that were downloaded were all MP3 files.

If anyone has an idea, I would love to hear it: this one has me stumped totally.

---

