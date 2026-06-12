---
title: "[SOLVED] Skype or Skype Static"
date: 2007-08-10
forum: General Help
---

### Post by evolving_monkey on 2007-08-10
I have added the medibuntu repositories. I want to add skype but I'm not sure which package to add: Skype or Skype Static. I am assuming that skype static is referencing a static ip but I could be assumong wrong. The descriptions are the same for either package. I scanned the website at [http://www.skype.com/](http://www.skype.com/) but I couldn't find any info. Just curious if anyone had an idea of the difference. I am not currently using a static ip.

Thanks for your time.

---

### Post by true_friend on 2007-08-10
You can simply install skype. skype static is seemed to be a dummy/sub package of the 'skype' one.

---

### Post by apetresc on 2007-08-10
> **evolving_monkey said:**
> I have added the medibuntu repositories. I want to add skype but I'm not sure which package to add: Skype or Skype Static. I am assuming that skype static is referencing a static ip but I could be assumong wrong. The descriptions are the same for either package. I scanned the website at [http://www.skype.com/](http://www.skype.com/) but I couldn't find any info. Just curious if anyone had an idea of the difference. I am not currently using a static ip.

Thanks for your time.

The "static" has nothing to do with a static IP; it has to do with whether the Qt library gets statically linked or dynamically linked.

Basically the choice boils down to this:
1) Do you already have Qt installed on your computer? (Or are you willing to install it?) Then choose the dynamic (non-static) one.
2) Do you want to keep your computer Qt-free for some reason? Then install static, and it will carry its own "copy" of the Qt library just for Skype's use.l

I personally recommend method 1.

---

### Post by true_friend on 2007-08-10
good. that was the reason.
thnx

---

### Post by evolving_monkey on 2007-08-10
Thank you for clearing up the static question. 

By Qt library I (here i go again with the assuming) assume you mean quick time libraries. (libquicktime0 in repositories) When you ask if I am I willing to install it is that to infer there might be a problem or are you referencing the licensing? I don't want to make things unstable or trash security. I will probably just take your advice on installing the the "skpe " package as you recommended. Just want to make sure I'm not doing anything blatantly stupid.

Pardon my ignorance. I'm an advanced noob at best.

Thanks again

---

### Post by evolving_monkey on 2007-08-10
One more question. Is there a performance difference with the two install options?

---

### Post by apetresc on 2007-08-10
> **evolving_monkey said:**
> By Qt library I (here i go again with the assuming) assume you mean quick time libraries. (libquicktime0 in repositories)
Nope :) I am referring to the "Qt" GUI toolkit. If you've ever used KDE, you've seen it in action, because KDE is written in Qt (whereas Gnome is written in GTK). You can get more information about Qt here: [http://trolltech.com/products/qt](http://trolltech.com/products/qt)

> **evolving_monkey said:**
> When you ask if I am I willing to install it is that to infer there might be a problem or are you referencing the licensing? I don't want to make things unstable or trash security.
Hehe, nope, there's no security or licensing issues with Qt at all. In fact, every Kubuntu user (me included) has it, and it is an integral part of our systems. But some Gnome users do not like installing Qt, preferring to stick to a pure Gnome box. There's no good reason for that, it is absolutely harmless (and in fact, very useful) to use Qt apps with Gnome. Skype is another Qt app.

At any rate, if you install Skype, you are using Qt whether you like it or not. The difference between static and non-static is that in one case, you're using Ubuntu's build of Qt, and in the other you're using Skype's.

> **evolving_monkey said:**
> Pardon my ignorance. I'm an advanced noob at best.

Thanks again
No problem, keep learning! Good luck!

EDIT: Oh, and about the performance difference, not really. They should be about the same, assuming that Skype does as good a job of optimizing their Qt builds as Ubuntu does.

---

### Post by evolving_monkey on 2007-08-10
Thankfully the forums save me from my assumptions...hehe

Cool...it doesn't seem like it will be a problem as I have installed kde-core already. I like using both for different reasons. There seem to be advantages with either.

This monkey evolves with every post. 

Thanks again.

---

