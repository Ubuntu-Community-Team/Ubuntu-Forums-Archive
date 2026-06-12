---
title: "&quot;the system is running in low-graphics mode&quot; + can not log in from a command line"
date: 2013-05-24
forum: General Help
---

### Post by faargenwelsh on 2013-05-24
hi all!

I'm sorry if this description is too long - I was not sure what was potentially important and what wasn't.

I have an ubuntu 12.04 installed on lenovo x301. For a few days now, I get "the system is running in low-graphics mode" error (described [here]("http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error")) when I try to boot.

In my case, it is apparently due to the lack of free space left in my home directory (0 bytes free as of now).

To free up some space, I first tried to boot up from livecd (as discussed [here]("http://ubuntuforums.org/showthread.php?t=1745719")), but without success : "gksudo nautilus" did not work (some error messages appear when I try to install nautilus-gksu, and after spending several hours on that, I gave up), so I can only mount my linux partition in read-only mode.

therefore, I tried to boot into linux console to free up some space manually, using command line.

for that, I pressed Ctrl+Alt+F1 during the boot, which opened a command line login prompt, and entered my login and password. so far, so good - it worked like a charm and I could delete something like 200 mb of files in /home/myname/Downloads directory using "rm -r bla-bla-something". 

Nevertheless, "du -sh" were still showing 0 free space, even after "rm -rf ~/.Trash/*" and while "lsof" where not showing any one of the deleted files being in use by some process. 

After spending a night on that, I turned my pc off.

The next morning, when I tried to press Ctrl+Alt+F1 during the boot. the command line prompt was still there, but I could no longer log in : as soon as I enter my login and password (the same as before, obviously), I am prompted for my login again, and so on.

When I intentionnally misspell either my login or password or both, I get error messages, but there's no error message when I enter correct identifiers - it just asks me for my login name again, immediately after.

I have no idea where this could come from (I didn't remove or modify anything outside /home/myname/Downloads" or Trash) and will appreciate any kind of advice.

Thank you very much in advance and, again, sorry for my post to be so long.

---

### Post by HiImTye on 2013-05-24
if you want to mount your disk in write mode you have to remount it
[code]sudo mount -o remount,rw <location>[code]

---

