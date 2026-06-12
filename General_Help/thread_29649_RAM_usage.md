---
title: "RAM usage"
date: 2005-04-25
forum: General Help
---

### Post by ignavia on 2005-04-25
I have 384MB and it's always over 90% in use. All I have running are FF and Gaim. How do I free up some RAM? Am I maybe misunderstanding how Linux uses RAM? What's cache RAM?

---

### Post by Turin Turambar on 2005-04-25
Same here. My Ubuntu is running really fast, but 21% mem is available (of total 512). However, there's no swap file! :)
I guess it's just how Linux manages memory...

---

### Post by Stormy Eyes on 2005-04-25
[QUOTE=ignavia]I have 384MB and it's always over 90% in use. All I have running are FF and Gaim. How do I free up some RAM? Am I maybe misunderstanding how Linux uses RAM? What's cache RAM?[/QUOTE]

Cache RAM is where Linux puts files for faster access. Linux manages memory differently from Windows; it *will* use most of what's available, not just for apps, but for buffers, file caches, etc. Don't panic unless you see more than 20% of your *swap* in use.

---

### Post by Sam on 2005-04-25
In linux, "free ram is wasted ram".

The applications starts a lot faster if they already cached. That's a very nice feature that microsoft should envy.

---

### Post by tread on 2005-04-25
I was curious too, so I looked around and found this nice writeup on the gentoo-wiki:

[Linux Memory Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

