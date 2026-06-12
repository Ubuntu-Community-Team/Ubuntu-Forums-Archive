---
title: "cp/mv Progress Bar"
date: 2008-03-30
forum: General Help
---

### Post by fermulator on 2008-03-30
Is it possible to upgrade ubuntu's cp/mv commands to include the "-g" option to show a progress bar when copying files?  The Gentoo distro of Linux has such an option, but ubuntu does not.

I've done some research and many have written their own scripts for this, which works, but ultimately this functionality should be included as an option to the exiting coreutils package for cp/mv commands.  It doesn't make sense why the Gentoo distro would have but ubuntu does not.

---

### Post by mcduck on 2008-03-30
All you need to do is to create an alias for the command:
```

alias cp='cp -g'
alias mv='mv -g'
```

To make these permanent, add them to the end the .bashrc file inside your home directory.

edit: Sorry, I had never even noticed that Ubuntu's cp and mv commands do not have the '-g' option at all :o Having that would be quite nice, but perhaps the '-V' switch would work for you?

---

### Post by fermulator on 2008-03-30
well the -v (verbose) is good when copying many files (or directories recursively) because yes it shows you what its copying.  But still, it would be great to see an overall progress bar.

i.e.

 * When copying a single large file:  Show progress bar for single file
 * When copying many files: Show an *overall* progress bar for the total files/size.

---

### Post by y-lee on 2008-03-30
I found this on the forums, [ HowTo: make coreutils-6.7 with gentoo's progress patch]("http://ubuntuforums.org/showthread.php?p=2061158") 

I haven't tried it so....

Anyway, maybe it will help.

---

