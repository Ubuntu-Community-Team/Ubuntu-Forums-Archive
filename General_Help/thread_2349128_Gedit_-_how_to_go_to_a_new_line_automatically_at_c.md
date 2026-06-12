---
title: "Gedit - how to go to a new line automatically at column 80"
date: 2017-01-11
forum: General Help
---

### Post by Tom_Carr on 2017-01-11
How do I set up Gedit so that when I am typing general text and get to column 80, the typing automatically goes to the next line and I don't have to hit Enter?  It used to do this, but the version I installed on a computer  recently does not.

---

### Post by vasa1 on 2017-01-11
Please provide the output of ```
apt-cache policy gedit
```

I have```
gedit:
  Installed: 3.18.3-0ubuntu4
  Candidate: 3.18.3-0ubuntu4
  Version table:
 *** 3.18.3-0ubuntu4 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
1
``` but I don't see any provision for defining where a line break, which seems to be what you want, should occur :???:

Based on this oldish blog, [http://www.thelinuxdaily.com/2010/02/adding-hard-word-wrapline-break-feature-to-gedit-tutorial/](http://www.thelinuxdaily.com/2010/02/adding-hard-word-wrapline-break-feature-to-gedit-tutorial/), you may need to add a plugin.

On reading that link more carefully, it seems to be a sort of "post facto" formatting and won't give you line breaks as you type.

Geany has line breaks the way you seem to want.

---

### Post by ajgreeny on 2017-01-11
Is column 80 also your window width with word-wrap enabled in your gedit profile on the version where it works for you?

---

### Post by Tom_Carr on 2017-01-11
My mistake.  The version on the older computer doesn't do it either.  I will check out Geany and close this thread.  Thanks for your help.

---

### Post by vasa1 on 2017-01-11
> **Tom_Carr said:**
> My mistake.  The version on the older computer doesn't do it either.  I will check out Geany and close this thread.  Thanks for your help.
For Geany 1.27, look under Menu > Edit > Preferences.

---

