---
title: "Shell history file saved by default - any others?"
date: 2006-10-19
forum: General Help
---

### Post by emarkay on 2006-10-19
Found this on the Ubuntu Idea Pool.
[https://wiki.ubuntu.com/IdeaPool#head-2710a9639a4d1880653fb847db3b41b42750d620](https://wiki.ubuntu.com/IdeaPool#head-2710a9639a4d1880653fb847db3b41b42750d620)

"Writing the shell history file to disk is clearly a security exposure. Use case:

Wilbert is a reasonably experienced system adminstrator. On call one night, he tries to log into an unfamiliar system and accidentally types his password instead of his account name. The next day his laptop is stolen, and the clueful thief reads Wilbert's history file and gains access to his account.

I have this in /etc/bash.bashrc:

unset HISTFILE
export HISTCONTROL=ignoreboth
(The second line is a BTW.) -- GraemeHewson"

Are there any other logs or history files that may have USER supplied data or other history data that could be problematic in the wrong hands?

---

### Post by Kateikyoushi on 2006-10-19
They could boot the livedisc and do a sudo passwd username anyway.

---

### Post by emarkay on 2006-10-19
Yes, but my queston was more focused on what other information is on a native system that could be used inappropriately?

---

