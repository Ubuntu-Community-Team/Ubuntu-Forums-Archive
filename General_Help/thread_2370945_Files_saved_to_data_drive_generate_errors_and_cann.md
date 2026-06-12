---
title: "Files saved to data drive generate errors and cannot be opened again."
date: 2017-09-08
forum: General Help
---

### Post by Paulgirardin on 2017-09-08
I have just encountered a problem saving files to a particular drive.
My system (17.04) has 3 drives.The OS is on sda,data is on sdb and sdc is a backup of sdb.
Just recently I have discovered that trying to save anything on sdb creates problems.
If I save a file with LO Calc, Gedit or as a PDF or an image off a web browser I cannot reopen it.I usually get some kind of "unidentified file type" error.
Sometimes the application crashes.If I copy a file from another drive to sdb, I can't open the copy.Sometimes the file opens but, in the case of a spreadsheet,was a page full of # characters.I can open copies of older files on sdb but saving them creates the same problem.
Saving anything on sda or sdc works fine.If I copy a file from sdb to the other drives I can't open it.
This seems to have happened in the last few days.
The only abnormal thing I have done recently was to used the "open as root" option in Nemo file manager to delete trash on a usb drive (Mounted as sdd).
Any suggestions would be appreciated.
It may be a few days before I can respond to any posts.

---

### Post by HermanAB on 2017-09-09
Run fsck and buy a new disk to copy your data to.

---

### Post by Paulgirardin on 2017-09-09
So you are saying the drive is faulty?
What is your reasoning? Seems unlikely to me as everything works fine an SMART checks are good.

Edit: I ran fsck on that drive and it did find plenty of stuff to correct.A quick trial of saving a file seems to work but I will do some further tests.
So I think you were onto something there,Herman.
Many thanks.
I will mark as solved if tests prove true.

---

