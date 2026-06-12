---
title: "Firefox issue"
date: 2007-04-19
forum: General Help
---

### Post by BaronVonBraun on 2007-04-19
I've been using Ubuntu for quite some time with no real problems except for one small aggravation that drives me nuts.

In Ubuntu, Firefox's shortcuts are a smidge different than they are in my Windows environment - the only one that really effects me is backspace.

In Windows I can use backspace to go back a page, whereas in Ubuntu it is simply a scroll-up key.  I've tried using keyboard shortcuts extensions in Firefox to no avail.

Any ideas how to fix this?  I do realize that there are a million other shortcuts for going back a page, and I do also use mouse gestures, but I would really love my backspace key back.

Thanks in advance!

---

### Post by qpwoeiruty on 2007-04-19
Type "about:config" into the address bar.
Type "backspace" into the search and change "browser.backspace_action" from 1 to 0

Now it will go back a page instead of up!

---

### Post by bwhite82 on 2007-04-19
Hello, this is a fairly simple change. First, in the URL box, type in "about:config", this will take you to a page with a ton of options (many of which you don't want to mess with). In the Filter box type in, "backspace" (without quotes) and press enter. It will display the option that you seek. Right click on the option and select "modify". Change the "1" to a "0" and click OK. You should be all set.

EDIT: qpwoeiruty beat me to it.

---

### Post by BaronVonBraun on 2007-04-19
Thank you guys so much, I didn't even think of that.

Fantastic!

---

