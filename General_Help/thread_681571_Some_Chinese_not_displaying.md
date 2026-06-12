---
title: "Some Chinese not displaying"
date: 2008-01-29
forum: General Help
---

### Post by hudsonhauck on 2008-01-29
Greetings!

Ubuntu is having a hard time with Chinese for me these days... It used to work fine, but everything seemed to go wrong after I upgraded to Gutsy.

Not only is Chinese input strange, but it does not all appear correctly either. Take for example the following three characters: &#37085;&#23459;&#27491;. They appear fine in the textarea I am typing right now. But if I paste them into gedit, only the first displays. Firefox does the same thing on the page I got them from.  So, Chinese display is fickle.

On top of that, input is strange as well. Scim seems to not be able to display many words and so it displays a whole bunch of weird box things. I will try to post a picture if you don't know what I mean. 

At a loss for what to do; help would be nice. Thanks!

---

### Post by hudsonhauck on 2008-01-29
Here are the weird blocks I was talking about:

[IMG]http://lh3.google.com/matthauck/R57-oXV78-I/AAAAAAAABP0/c-KKCKiwO4M/weird%20blocks.png[/IMG]

If picture above doesn't show: [http://lh3.google.com/matthauck/R57-oXV78-I/AAAAAAAABP0/c-KKCKiwO4M/weird%20blocks.png]("http://lh3.google.com/matthauck/R57-oXV78-I/AAAAAAAABP0/c-KKCKiwO4M/weird%20blocks.png")

I got this after I typed &#12563;&#12584;&#715; (zhu4)

---

### Post by hudsonhauck on 2008-02-17
Nobody has this at all?

---

### Post by happyhamster on 2008-02-17
Perhaps an encoding issue? What does this command show:

cat /var/lib/locales/supported.d/local

---

### Post by hudsonhauck on 2008-02-17
```
matt on mattop [~] $ cat /var/lib/locales/supported.d/local
en_US.UTF-8 UTF-8
```

Hmm...How do I go about adding BIG5 to that?

---

### Post by happyhamster on 2008-02-18
Hmm, weird. For me, cat /var/lib/locales/supported.d/local also gives en_US.UTF-8 UTF-8, but I have no problem seeing/manipulating those characters (&#37085;&#23459;&#27491;). When I do a search in synaptic for 'chinese', the only installed font it finds is:

ttf-arphic-uming

(I also have msttcorefonts installed BTW.)

---

### Post by hudsonhauck on 2008-02-20
Well, I iinstalled msttcorefonts; it didn't seem to change anything.

I switched over to [gcin]("http://cle.linux.org.tw/trac") which works much better than I ever got scim to work. So, I'm happy; problem solved!

---

