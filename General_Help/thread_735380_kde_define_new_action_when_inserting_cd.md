---
title: "kde: define new action when inserting cd"
date: 2008-03-25
forum: General Help
---

### Post by stephan0h on 2008-03-25
Hi group,

I've got kubuntu gutsy. When I insert a CD a window pops up in kde asking me what I want to do: open konqueror, copy it, etc.

I want to have a new item in the list for copying the whole contents of the cd to my local disk, specifically to a directory like ./cd_archive/<cd-name>/*

For testing I defined a new entry in the list "Copy to HD" with the following command:

cp -r %U ~/cdtest/.

Unfortunately when I choose my new action when inserting a cd nothing happens. Does anybody know why this does not work and how to define it correctly?

And another question: how can I get the CD's name to use it as a directory name? I know how to shell-script but I don't know how to get the CD's name programmatically.

Thanks,
stephan

---

