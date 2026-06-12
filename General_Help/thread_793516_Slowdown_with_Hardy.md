---
title: "Slowdown with Hardy"
date: 2008-05-13
forum: General Help
---

### Post by ksauber on 2008-05-13
I've occasionally noted an extreme slowdown with Hardy Heron.

Checking the process table I found that all available memory (ram) was used along with ~80% of swap space.   Checking the process table I found that "gtk-gnesh" was sucking up all the system resources ... in this case over 500 MB of system ram on a 768 MB system and over 2 GB of swap.

Killing that process freed up memory and the system seemed to be none the worse for my doing that.

At times there also appears to be multiple copies of "gtk-gnesk" running.  Frequently using large amounts of CPU.

What is "gtk-gnash" and what does it do when it's working correctly???

---

### Post by joshsmith on 2008-05-14
[http://www.google.co.uk/search?q=gtk-gnash&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-GB:unofficial&client=firefox-a](http://www.google.co.uk/search?q=gtk-gnash&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-GB:unofficial&client=firefox-a)

---

