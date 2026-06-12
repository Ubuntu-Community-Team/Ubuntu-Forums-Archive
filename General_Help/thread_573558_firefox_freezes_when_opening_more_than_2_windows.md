---
title: "firefox freezes when opening more than 2 windows"
date: 2007-10-11
forum: General Help
---

### Post by aseem_mal on 2007-10-11
That's right. If I open any more than 2 instances of firefox, it simply freezes over.
Then I have to open the Process Manager, and Kill the firefox-bin process, which now shows a cpu-usage of 100%.
I am using:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20071008 Ubuntu/7.10 (gutsy) Firefox/2.0.0.6

Please help.

Thanks,
A

---

### Post by raja on 2007-10-11
Firstly, you should never need to have two instances of firefox running. Change your preferences to force new windows to open as tabs.
Memory problems with firefox are often related to the extensions. So you can try disabling all of them and then see if the problem persists. If it disappears, then re-enable the extensions one by one and test.
Thats all I can think of.

---

### Post by mverbist on 2007-11-15
I'm having the same problem.
Even without starting firefox 2 times.
Just asking a new window within firefox does the trick.
File -> New Window 
File -> New Window 
and firefox freezes.

I know I can open them in tab pages, but this shouldn't happen.
It started after upgrading to 7.10

Has anybody found a solution for this bug?

---

### Post by mverbist on 2007-11-15
searching some more, I found that the Google toolbar might be the problem:
[https://bugs.launchpad.net/ubuntu/+source/mozilla-firefox/+bug/140885](https://bugs.launchpad.net/ubuntu/+source/mozilla-firefox/+bug/140885)

I will try this later.

Did any of you have the Google toolbar installed as well?

---

### Post by aseem_mal on 2007-11-15
Yes, Its confirmed. It happens only when Google Toolbar is installed as an addon. Problem goes away if you remove/disable the toolbar.

Hope google knows of this....

---

