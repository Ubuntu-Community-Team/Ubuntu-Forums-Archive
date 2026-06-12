---
title: "Very strange problems with Ubuntu Hardy"
date: 2008-07-04
forum: General Help
---

### Post by ishmandoo on 2008-07-04
I just started having a very strange problem with Ubuntu 8.04. Firefox has essentially stopped working. My homepage is Nytimes.com and it loads but it a weird text only format. Also, when I try to go to any other site, it says that firefox is in offline mode. When I try to quit firefox it crashes and gives me the option to force quit or wait but after a second or two it crashes anyway. The bookmarks seem to be gone as well and I can't add new ones, it is very weird. Finally, if I clock on the red power button in the corner it disappears along with both the top and bottom panels. I tried to reinstall the firefox packages and it didn't help. Does anyone have any ideas?
Thank you very much for your help!

---

### Post by manfer on 2008-07-04
Maybe you could try to backup your config and profile files located in your home directory and let firefox start from scratch.

Close firefox.

prompt:~$ **mv ~/.mozilla ~/mozilla_backup**

Then start firefox.

---

### Post by ishmandoo on 2008-07-04
Hmm...now firefox doesn't seem to start. Any other ideas?

---

### Post by manfer on 2008-07-04
It should have started as it where the first time you run it.

I don't know what makes your firefox fail. If you run it from terminal do you see any error message:

prompt:~$ **firefox**

You could try to totally uninstall firefox and install it again.

prompt:~$ **sudo apt-get remove --purge firefox; apt-get autoremove**

prompt:~$ **sudo apt-get install firefox**

---

### Post by ishmandoo on 2008-07-04
Okay, I figured out what the problem was with firefox. There was literally no more room on my hard drive so I made some room. My other problem still exists though. Do you have any idea why the red power button would make the panels disappear?

---

### Post by manfer on 2008-07-04
You mean the windows with restart, close session, suspend... buttons does not appear, and your panels disappear when you click the red power button in top panel?

And when you use System->Exit..., does it works?

---

