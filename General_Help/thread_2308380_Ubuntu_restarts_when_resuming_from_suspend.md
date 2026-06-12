---
title: "Ubuntu restarts when resuming from suspend"
date: 2016-01-02
forum: General Help
---

### Post by matthew108 on 2016-01-02
whenever i attempt to resume, the screen will go black, sometimes flash or show the lock screen, then in a total of about 6 second be suspended. when i try to resume it acts like it was suspended (opening it or pressing a key wakes it) but it goes through grub and then boots normally, with anything i had been working on lost. whenever i do this i get the "Ubuntu has experienced an internal error" dialog, (which doesn't go away, i get a new one every time i try to suspend but the old ones too, but i can deal with that later), which i will attach a screenshot of below. this is on a laptop, so i kind of need to be able to suspend. I have a [ASUS N550JX-DS71T TOUCH]("http://ASUS N550JX-DS71T TOUCH") . any ideas on how to fix this? 

. [ATTACH=CONFIG]266511[/ATTACH]

---

### Post by Dreamer Fithp Apprentice on 2016-01-02
From the report it looks like you just installed that. Is that correct? What was it running before and did you have the same problem then? You might try updating.```
sudo apt-get update
```Respond to the various prompts and wait till it is all done. Then:```
sudo apt-get dist-upgrade
```and if there are any error messages, copy and post them. It probably won't help but it is worth a try. 

If updating doesn't do it, you might try the opposite - on the grub menu should be options to try booting with an older kernel. See what happens when you do that. If that fixes the problem, there are ways to hold the kernel version for a while, until you have reason to think a further update may have fixed it.

I suspect you've found a bug that manifests in your particular kind of hardware. If that is the case, if you can find and subscribe to the bug report, maybe somebody will post a work-around before it actually gets fixed.

If none of that works, don't give up too quickly 'cause there are some bright people here who might think of something more helpful, but I suspect that if you can't simply live with it until it gets fixed, your best bet might be to install something else.

Does suspend work when booted from the live disk version of what you are running? If it doesn't, try the live disk version of Lubuntu and some other 'nixes altogether (PClinuxOS is pretty user friendly and is not Debian derived, so it would be a good one to try) and see if it works on one of them. If it doesn't work on the live disk version of what you are presently running but DOES work on some other live disk, that would be strong evidence that the other system would work once installed to the hard drive as well. If you want to keep the current installation and you have the disk space, just install a second system if you find one that works. You can always boot into Ubuntu occasionally to update it and see if the problem has gone away or if you want to use it for a while without the option of suspending.

---

