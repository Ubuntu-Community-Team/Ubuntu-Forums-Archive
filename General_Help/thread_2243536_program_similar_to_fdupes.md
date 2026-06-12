---
title: "program similar to fdupes"
date: 2014-09-09
forum: General Help
---

### Post by vikler on 2014-09-09
I need a program similar to fdupes to get rid of duplicate files. The problem is that:
fdupes -rdN dir/

means: preserver first file, delete other dupes
 So it will always leave the first copy (the oldest one).

I have the following problem: there are many loose .jpg files in ./dir
And also subdirectories which store the copies of loose .jpgs (but not all!) What I need to do is to remove these LOOSE jpg files. However my main problem is that not all of them are copied inside those directories, otherwise I'd just do rm *, thus removing jpgs, while keeping subdirectories. Fdupes will always remove jpg's inside the subdirectories, as technically these are copies... I know you can make a list of copies and compare versions, but I don't want to do it, there are way too many files!

So basically my desire is some program like fdupes, but one that removes original files, leaving copies.

Can anyone help me?

---

