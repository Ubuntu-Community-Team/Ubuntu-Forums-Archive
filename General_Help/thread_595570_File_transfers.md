---
title: "File transfers"
date: 2007-10-28
forum: General Help
---

### Post by dondad on 2007-10-28
I had Fiesty installed on another partition, then installed Gutsy in dual boot on another drive. Both have separate partitions for /home. At first, I was using Fiesty most of the time, then gradually transitioned to Gutsy and am now at the release level and happy with the way that everything is working. I have most of the data from the Fiesty /home copied to the Gutsy one, but would like to copy anything left in the Fiesty that is not in the Gutsy /home directory. What would be the easiest way to do that? (What I want is only those files in fiesty that are not in Gutsy. If the file exists in Gutsy, I do not want to overwrite it.)

---

### Post by strabes on 2007-10-28
You could use the "mv" command, with the -i flag. "i" stands for "interactive," so it will prompt you to overwrite each file. You'll also want to use the -r flag, which stands for "recursive."

---

### Post by HermanAB on 2007-10-28
Rsync is your friend.  When used on a local machine, it works like a better copy command.

Cheers,

Herman

---

