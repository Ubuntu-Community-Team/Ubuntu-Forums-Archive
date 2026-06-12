---
title: "[x64] Open Office - Out of the blue file access problems"
date: 2008-06-27
forum: General Help
---

### Post by SammyBoy247 on 2008-06-27
I use OOo every day and have never had any major problems until....

Today I did my usual process of opening my docs folder and double clicking a writer doc to edit.  The OOo Writer splash came up and the progress bar did its thing then the splash disappeared but left nothing behind not even a process.  I did some waiting updates and restarted the system.  Opened Writer from the main menu and opened my doc fine.  Thought the prob was a one off.

Spent 20mins writing a letter using an old letter as a template. Clicked File¬Save as and Writer stalled.  The writer window froze, no save as dialog appeared, nothing.  OOo managed to recover the doc but I'm still unable to save anything.

Did some testing across the suite and in Calc, Writer and Base the same two probs exist can't open files directly from Nautilus and can't save any files (save/save as).

I'm heavily dependent on OOo so any help much appreciated.



UPDATE: - sorry slow in updating but I followed the advice in the post below and am up and running again - I have several problems with some my macros/scripts in OOo but apart from that happy days.

---

### Post by SammyBoy247 on 2008-06-28
Bump - Any one with any ideas - I've purged and re-installed the whole OOo suite and the problem persists - It's looking like a problem with my file system of gnome although I've not come across any probs in other aps

---

### Post by Elfy on 2008-06-28
There do seem to have been some problems lately with some updates. I can't find the thread, but I believe it might be openoffice.org-gtk which is causing some of the problems.

However if you have reinstalled - that certainly sorted the problem I had a while back.

I can't offer much help but, when I had the problem with openoffice updates in the proposed repos in May I was using the 3 beta, that at least will allow you to work.

If you want try that then you can get the beta here

[http://download.openoffice.org/3.0beta/](http://download.openoffice.org/3.0beta/)

There is a thread which goes through installing it 

[http://ubuntuforums.org/showthread.php?p=4909323](http://ubuntuforums.org/showthread.php?p=4909323)

But basically I navigated to the download in terminal and did 

```
sudo dpkg -i *.deb
```

Then made a launcher for it running this

```
/opt/openoffice.org3/program/soffice
```


Edit - just so you know I have found the beta to be very stable and have had no issues with it myself and use it all the time now.

---

