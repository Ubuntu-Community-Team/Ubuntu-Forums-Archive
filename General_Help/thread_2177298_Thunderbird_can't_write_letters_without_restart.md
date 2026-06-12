---
title: "Thunderbird can't write letters without restart"
date: 2013-09-28
forum: General Help
---

### Post by sudodus on 2013-09-28
After the update Sept 19 2013 I have a problem with ***Thunderbird***. I run Ubuntu 12.04.3 LTS and I use lubuntu-desktop most of the time.

The window to write letters (or reply to letters) is borked. There is no cursor, and although it is focused, the active window is still the main Thunderbird window, so I can't write anything. This happens after running Thunderbird for a while, and I had to close and re-open Thunderbird to be able to write a letter again.

Now I have found that it is simpler and also more successful to ***close the main window of Thunderbird***. Then the cursor will appear in the 'Write' window, and I can write the letter or reply/forward the letter as intended.

I have seen a similar problem in my other mozilla application, ***Firefox***, if I have two windows open. I can live with the Firefox problem, but I mention it, because it is similar, and it could be caused by the same bug. This problem in Firefox has been there for months, but the problem in Thunderbird is new, it started Sept 19 2013.

What can I do to fix it? [COLOR=#696969]I hope I need not start all over with a fresh install of Thunderbird.[/COLOR]

If you have the same or a similar problem, please click '[[COLOR=#006400]This bug affects you[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1228002/+affectsmetoo")' at the Launchpad bug report

[URL="https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1228002"]https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1228002
[/URL]

---

### Post by ajgreeny on 2013-09-28
19 Sept was when TB updated from v17 to v24, bringing with it quite a lot of changes to the look and feel of the application, however, I also use 12.04.3 (Xubuntu, but that is immaterial, I think) and I have not seen any of the problems you are getting on your setup.

I suspect a configuration that is borked somehow, and suggest you try renaming the **~/.thunderbird** folder in your home as a backup **~/.thunderbirdbak**, then try a restart of TB.  All your mail etc etc will not show at this time, nor your email account details which you will need to enter again, but mail will still be in the old renamed folder and can be copied across later with all your contacts as well. However, let's go one step at a time and see if my suggestion works first.

---

### Post by sudodus on 2013-09-28
Thanks for the tips *ajgreeny* :-)

I feared that I have to redo the setup and tweaking of Tbird. Anyway, I have started with backup of **~/.thunderbird** and with some house-cleaning: I moved old mails to archive folders, and I have tried in the little end by deactivating the ImportExportTools extension. I have also tried Unity instead of LXDE or lubuntu-desktop. It made no difference.

Do you know if ~/.thunderbird is different between the 32- and 64-bit versions? With a backup I dare try even if the files will be borked.

---

### Post by sudodus on 2013-09-28
Next step:

I ran from another user id in the same computer and set up a fresh configuration for Thunderbird. It looked nice, and worked well in the beginning, but after writing a couple of mails, the same problem occured again. Closing the main window (and reopening it while the 'Write' window is open) worked also for this user id.

So my conclusion is that the problem is not in the .thunderbird directory :-(

---

### Post by sudodus on 2013-09-29
Next step:

I purged and reinstalled Thunderbird, but the problem persisted.

Next step:

I started to suspect the nvidia proprietary drivers. I tried another one (the default current one as well as 173 and 304). The problem persisted.

Solution:

Now I'm using the built in driver nouveau.

I have an nvidia graphics card: NVIDIA Corporation GF108 [GeForce GT 430] (rev a1), and it has worked well since I bought it some year ago. But now the nvidia proprietary drivers bork Thunderbird :-( I managed to write/reply ten letters in a row without issues, which has been far from possible after the upgrade of Thunderbird Sept 19.

New problem:

But the solution for Thunderbird breaks the possibility to use VDPAU with mplayer to play HD video (1080-50p) without issues. The computer, an hp xw8400 workstation, is not powerful enough to manage it without help of the graphics card and a proprietary driver.

There are also nvidia driver versions 310 and 319 in the repos. I might try them later on, but I have little hope ...

---

### Post by sudodus on 2013-09-29
It was not a solution:

Now that I write the next letter (not a testing letter but a real one), the bug pops up its ugly face again, so nouveau seems to improve the situation, but it does not solve it. (I had to close the main Tbird window to get the cursor and write that letter).

---

