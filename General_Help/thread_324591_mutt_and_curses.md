---
title: "mutt and curses"
date: 2006-12-24
forum: General Help
---

### Post by eklitzke on 2006-12-24
Hi everyone,

I like to use mutt with the sidebar patch, which means that I download the mutt tarball and apply the patch myself, and then compile mutt on my Ubuntu machine. I have noticed that under Ubuntu (Edgy) the sidebar doesn't look correct (e.g. it appears that mutt is not correctly calculating the width of the terminal). I am guessing this is an incompatibility between mutt and the ncurses that is shipped with Ubuntu.

Has anyone here experienced this problem, or similar ncurses weirdness? Are there any flags or anything else that I need to be passing when compiling? I know this is sort of a long shot, but I figure maybe someone else out there has experienced this problem.

Thanks,
Evan Klitzke

---

### Post by tbroderick on 2006-12-24
What width option did you out in your .muttrc? Does a smaller width work better?

---

### Post by kd7swh on 2006-12-24
my mutt sidebar looks great. are you using the latest version of everything?

---

### Post by srf21c on 2007-08-03
Was curious if there are any plans by Ubuntu to include a mutt w/sidebar package in the repos.  

Would be nice to have with feature without the hassle of patching and compiling mutt on your own.

---

