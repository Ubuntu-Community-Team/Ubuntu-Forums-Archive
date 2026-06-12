---
title: "thunar crash error"
date: 2022-04-12
forum: General Help
---

### Post by vivid-potato on 2022-04-12
Every time I log into xubuntu i get a crash message asking me to report a problem with a program. On using "ls /var/crash" it shows "_usr_bin_thunar.0.crash". I am new to linux. Any idea on how to find and fix this error?

---

### Post by guiverc on 2022-04-12
You haven't provided any release details.

You can submit the bug report using

```
ubuntu-bug /var/crash/_usr_bin_thunar.0.crash
```

and after it's been submitted, you'll notice a **.upload** and/or **.uploaded** added to the /var/crash/ directory which will prevent you from being told about that report anymore.  You can also stop the request to file the bug by deleting that .crash file too.

See [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) for more details.


FYI:  The .crash metadata will tell you when the crash occurred, the start of the .crash file is reasonably easy to understand, though as you get further into it'll will be harder to read as it'll contain memory dumps. After it's uploaded to launchpad the fields will be more easily found (ie. *the results of the upload can be read via a browser on launchpad*).

---

