---
title: "greasemonkey firefox extension only works for root"
date: 2005-03-29
forum: General Help
---

### Post by 23meg on 2005-03-29
i've only been able to run [greasemonkey](http://greasemonkey.mozdev.org) when i install it after sudo'ing into firefox by typing
```
sudo -H firefox
```
so far; it's the first extension that i've seen which requires root access  :!: 

anyone had any luck with it? i really want to run it because i'm going mad with firefox under ubuntu; i can't find a combination of font sizes and display resolution that displays all pages properly... if some sites are displayed with too small fonts i set up a minimum font size of, say, 10 and then many other sites have huge fonts.. i'm hoping to remedy this situation using greasemonkey; i'd also appreciate help regarding font sizes in firefox in general  :smile:

---

### Post by 23meg on 2005-04-29
i've typed > sudo chmod -R o+r /etc/mozilla-firefox/profile to make sure i have read/write access to my profile directory upon suggestion, but that didn't help. anyone tried greasemonkey with 1.0.3? 

another question: would running firefox as root (via sudo) pose an important security risk? i really want greasemonkey, as you can tell.

---

### Post by tread on 2005-04-29
I guess running firefox as root might not be a good idea .. any script that tries to exploit firefox (which definitely wont be completely exploit-free .. nothing is) could get root access?

---

### Post by 23meg on 2005-04-29
that's what i thought would happen. i'll refrain from it just in case. but... greasemonkey.. grrr...

---

### Post by 23meg on 2005-05-24
Just upgraded to the backported 1.04 and it's working now.

---

### Post by mirshafie on 2006-02-10
I can't install Greasemonkey scripts with my default user since i reinstalled Ubuntu Breezy. I use Firefox 1.5.0.1 and Greasemonkey 0.6.4.
It works fine as root.

I'd really appreciate it if someone could help me solve this since I find Greasemonkey very useful.

---

