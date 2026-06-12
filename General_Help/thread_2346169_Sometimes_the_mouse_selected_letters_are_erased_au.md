---
title: "Sometimes the mouse selected letters are erased automatically"
date: 2016-12-12
forum: General Help
---

### Post by yys2 on 2016-12-12
Hi all, 
 I'm new to ubuntu and encounter a problem.

For example, I type some letters into an input box on a web page(I use Firefox). Then when I'm going to select some of these letters by pressing the LMB and draging the mouse, the selected letters are erased automatically. And I confirmed that I didn't press any key when this problem happened. 
I'm not sure whether this were a feature of ubuntu. 

What's more, sometimes this problem happened, and sometimes this problem did not happen.

If this were a feature, could you tell me how to disable this feature?
If this is not a feature, could you tell me how to deal with this problem?

Cheers
yao

---

### Post by vasa1 on 2016-12-12
Have you tried after disabling all Firefox extensions? 
[https://support.mozilla.org/en-US/kb/troubleshoot-firefox-issues-using-safe-mode](https://support.mozilla.org/en-US/kb/troubleshoot-firefox-issues-using-safe-mode)

Have you tried with a new Firefox profile?
[https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles](https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles)

---

### Post by yys2 on 2016-12-12
Thanks for your suggestion, vasa1.

Finally, I got it!

This problem depends on Firefox and the following two input sources:
Chinese(Pinyin)(IBus)
Chinese(Bopomofo)(IBus)

This problem occurs in Firefox SafeMode,
This problem occurs without Firefox plugins.
This problem occurs in Firefox profile(with or without plugins)
By now, this problem has not occured in other applications.

My system information is:
Linux version 4.4.0-53-generic (buildd@lcy01-28) (gcc version 5.4.0   20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.4) ) #74-Ubuntu SMP Fri Dec 2   15:59:10 UTC 2016
Firefox 50.0.2
IBus Pinyin 1.5.0

**How to reproduce it**
- In AllSettings>TextEntry
Add one or two of these input sources:
Chinese(Pinyin)(IBus)
Chinese(Bopomofo)(IBus)
- Open firefox and switch input source to the Chinese(Pinyin)(IBus) or Chinese(Bopomofo)(IBus)
- Type some letters into URL bar. Then select some of these letters by mouse (pressing the LMB and  draging the mouse), the selected letters are erased automatically.

---

### Post by vasa1 on 2016-12-12
I use only English and so can't help much. But I came across [http://www.pinyinjoe.com/linux/ubuntu-10-chinese-input-pinyin-chewing.htm](http://www.pinyinjoe.com/linux/ubuntu-10-chinese-input-pinyin-chewing.htm) which may give you some pointers. (I googled for *ibus fcitx*).

---

### Post by yys2 on 2016-12-12
Thanks for your reply.
It is solved with your links.

---

### Post by vasa1 on 2016-12-12
You're welcome and, if you come by here again, please mark the thread [SOLVED] as described here: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

