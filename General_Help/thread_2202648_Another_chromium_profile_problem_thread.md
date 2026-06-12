---
title: "Another chromium profile problem thread"
date: 2014-01-30
forum: General Help
---

### Post by GrouchyGaijin on 2014-01-30
Hi Folks,

Starting yesterday I began getting the following error the first time I launch chromium after signing into Google:

```
Your profile could not be opened correctly.

Some features may be unavailable.  Please check that the profile exists and you have permission to read and write its contents.
```

In the past when I've had this error I could solve the problem by deleting the chromium directory in ~/.config

This time however the problem returns when I restart the browser after I sign into Google. 

Has anyone else had this problem?  If so, how did you solve it?

---

### Post by Soft_Ginger on 2014-01-30
Go to ~/.config and type:

ls -l -a

and check whether you have files that you don't have permission to read write. If you have, type the following:

sudo chmod a+wr <filename>

---

### Post by GrouchyGaijin on 2014-01-31
Thank you for the suggestion.
What I actually did though was to restore a backup that I made three days ago, prior to when the problem began.
That still doesn't explain what caused the problem though.
Has anyone else had the same issue?

---

### Post by Soft_Ginger on 2014-02-01
Hello,
Well, I'm currently not using Chromium. But once I had some problem with X. X's output indicated that it cannot open or write to .Xauthority, which I changed and therefore fixing X. From what you've post it seems that you broke some file's permission status thus malfunctioning Chromium browser.
Something you could try:
1. Ctrl+Alt+T to open a terminal.
2. Type 'sudo chromium' to open chromium with root priviledge (DO NOT VISIT ANY OTHER WEBSITE OTHER THAN WHICH YOU EXTREMELY TRUST)
3. Login to Google and see if there's any error.
Post what you observe then.

---

### Post by GrouchyGaijin on 2014-02-01
If / when it happens again I'll do that   At the moment it seems the problem is gone.

---

### Post by sandyd on 2014-02-01
moved to general help

---

