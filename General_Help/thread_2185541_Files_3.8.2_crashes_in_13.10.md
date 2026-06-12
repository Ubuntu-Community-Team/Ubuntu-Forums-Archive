---
title: "Files 3.8.2 crashes in 13.10"
date: 2013-11-03
forum: General Help
---

### Post by Packwood1 on 2013-11-03
I have a folder that when I select it Files (the file manager) crashes immediately.  There is no error message displayed.  How do I debug and fix this problem?  Some folders do behave correctly and can be navigated and files opened.

Thanks.

---

### Post by The Cog on 2013-11-03
First, have a look at the contents with the command-line for anything odd: ls -l foldername

Then I would probably make another folder and then start moving contents from one to the other using command-line mv commands to try to figure out which file (assuming it's a single file) is causing the problem.

Move everything to the new folder and then try, just to discover it it's the folder or the contents that is the issue.
Move half the contents back and then try again.
Move half the contents of whichever folder is still crashing, etc.
Eventually you might find one file that causes it.

---

