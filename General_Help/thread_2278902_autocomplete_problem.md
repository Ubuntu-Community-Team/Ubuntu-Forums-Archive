---
title: "autocomplete problem"
date: 2015-05-19
forum: General Help
---

### Post by andrew-krohn on 2015-05-19
I have no idea what has happened.  Today as I was using my system (writing python script), autocomplete completely changed its nature.  

Previously, I could tab-autocomplete commands and any subsequent filenames or paths I might try to call.

Now I can autocomplete the initial command, but cannot for subsequent filenames/paths.  If I double tab, a list of possibilities appears, but I still have to type the whole thing out.  In a word, this change in behavior is maddening.  I tried rebooting and it is still the same.  I found this post ([http://ubuntuforums.org/showthread.php?t=1865538](http://ubuntuforums.org/showthread.php?t=1865538)) but its solution does not work.  Any ideas on why this may have spontaneously happened or how to fix it?

---

### Post by andrew-krohn on 2015-05-19
I'm pleased and embarrassed to say I found the problem.  My script output a file with some kind of non-ascii character in the name.  I deleted it via nautilus and all is working again.  Sheesh!

---

