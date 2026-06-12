---
title: "Command line prediction"
date: 2006-11-21
forum: General Help
---

### Post by zugvogel on 2006-11-21
Hello,

I was wondering if anyone knows how to make the command line more intelligent. I used a computer before where, if I was running evince, in a directory with 3 files (eg, "file1.ogg", "file2.pdf", "file3.odt") then I could type:

evince [tab]

and it would straight-away know that the only option was "file2.pdf" because it doesn't make sense to open the other files with evince.

I don't have access to that computer any more so I can't find out how it did it. Does anyone know how to make it do this? Thanks!

---

### Post by Jussi Kukkonen on 2006-11-21
/etc/bash_completion defines the file-application connections, and your ~/.bashrc should have something like this:
```

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
```

---

### Post by zugvogel on 2006-11-21
Ah, that's great. Many thanks!

---

