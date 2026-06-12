---
title: "chromium as default browser"
date: 2012-11-12
forum: General Help
---

### Post by thorbs on 2012-11-12
I am having problems with selecting chromium as default browser in xubuntu. I get the message Failed to execute child process "chromium" (No such file or directory)
But I have chromium and I am able to launch it from my applicationsmenu


What could be wrong?

---

### Post by ajgreeny on 2012-11-12
You have been using the wrong command if you've been trying just *chromium*.

The command is *chromium-browser*

---

### Post by Abhinav Kumar on 2012-11-12
> **thorbs said:**
> I am having problems with selecting chromium as default browser in xubuntu. I get the message Failed to execute child process "chromium" (No such file or directory)
But I have chromium and I am able to launch it from my applicationsmenu


What could be wrong?
Hi thorbs,
May be xubuntu may not find it in the usual directory.
Try getting the location of executable chromium-browser by typing in terminal
```

locate chromium-browser | more

```
Then, give the chromium location found from above.
:)

Regards,
Abhinav

---

### Post by jonzen on 2012-11-12
I have the same problem except both chromium and chrome start from the menu or cairo dock, but when i click a link on the irc or in an email or chose open link in browser i get the choose default browser box then the child process error.  Then it leaves me with no default browser.  The next time I open a browser it asks me if I want it to be the default again.  This happens no matter which browser I chose.

---

### Post by thorbs on 2012-11-23
I was able to make it work with the first reply, so I mark the thread solved. Please open new if your problem still persists

---

