---
title: "GTK3 File Chooser Box Crash"
date: 2016-12-10
forum: General Help
---

### Post by Brandon_MacEachern on 2016-12-10
I want to file a bug on Launchpad for this, but I'm not sure I know where this should be filed.  Originally I thought Nautilus, but it does it on Ubuntu Mate on another platform entirely which doesn't even have Nautilus.

Basically what's happening is, if you are in a GTK3 based application and are using the file chooser to open a file for example, and select multiple files, then drag away like you are going to unselect your selection, the entire program crashes.  I have tested it in gedit and Firefox for example, and Firefox on both X86_64 and ARM.

I made a video of what's going on.

[https://youtu.be/_Zl1p6hXNQ0](https://youtu.be/_Zl1p6hXNQ0)

Where exactly do I file this bug?  Both are Ubuntu 16.04.01, and no upgrading to a non LTS release isn't possible, I'm a first responder and rely on my radio's tools, which currently only support 16.04 LTS, not a non LTS release.  I can't take that risk.  Being it affects to entirely different architectures, I'm not sure where the bug should be filed.

---

### Post by cariboo on 2016-12-10
Looks like a nautilus bug to me. Use:

```
ubuntu-bug nautilus
```

To report it. Add as much detail as possible.

---

### Post by Brandon_MacEachern on 2016-12-10
Alright thank you, I have filed it under Nautius.  I did the report while on my ARM based desktop, but specified in the notes that it is affecting also X86 also.  I'm hoping that will do just fine and I won't have to re-file it for another platform.  I made sure to include a link to the video just in case.

---

