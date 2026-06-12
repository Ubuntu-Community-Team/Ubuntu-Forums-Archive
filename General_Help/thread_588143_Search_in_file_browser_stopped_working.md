---
title: "Search in file browser stopped working"
date: 2007-10-23
forum: General Help
---

### Post by erm4gh on 2007-10-23
I'm running Ubuntu 7.10. Searching no longer works in the file browser. I've even tried going to a directory, right clicking on a file, choosing properties, and copying and pasting its filename into the search field to eliminate any chance of error. It literally can't find anything.

Both locate and slocate work. I'm not running beagle (synaptic says its not installed). My problem is the nautilus file manager. I'm not sure when it broke, but when I was running 7.10RC I remember getting annoyed that if I searched for a thunderbird directory it would return all of the contents of that directory, but not the directory, and wondering if it was supposed to do that. Now it just returns no search results (for anything). 

I ran "sudo updatedb". It returned within about a second and didn't seem to have any effect. I also tried "sudo updatedb -v | more" and spotted filenames for many of the major directories so I know it was doing something. I took a quick look at /etc/updatedb.conf to see if there is anything weird but I don't know enough to tell. It had LOCALUSER="nobody" rather than my username.

Suggestions?

---

### Post by joonjoon on 2008-03-10
Same problem...

---

### Post by David Oxland on 2008-03-19
Same for me.

---

### Post by stryderjzw on 2008-03-21
Same!

---

### Post by dishayu on 2008-03-30
same....

---

### Post by ad_267 on 2008-03-30
Yup same for me.

Is there a bug on launchpad?

Edit: Looks like this might be it: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150379](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150379)

---

