---
title: "Square with unicode code inside instead of character"
date: 2008-03-27
forum: General Help
---

### Post by Superkoop on 2008-03-27
Here is a screenshot of what they look like. 
[[IMG]http://img520.imageshack.us/img520/8234/screenshotgf0.th.png[/IMG]](http://img520.imageshack.us/my.php?image=screenshotgf0.png)
(thumbnail)
I have seen these since I have first started using Ubuntu, I first saw them online, which is what peaked my curiosity. But I haven't even looked in the Character map until now, and I realize that they are in place of characters. So my question, why are they there? And, how can I get the correct characters to show up?

Thanks.

---

### Post by scottro on 2008-03-27
Usually, when you see squares, it means that the input manager can't find the right font.  I've never been able to solve this when I have the fonts installed--at times, when I didn't have the proper fonts installed, it was an easy fix, just install them.  :)

However, there have been other times when the fonts are there, the path is correct in xorg.conf and scim or whatever still can't find them.  I haven't figured out how to solve that one yet.  

Sometimes, even though it's indicated that you have a particular language support package installed, you still have to do something like
sudo apt-get install language-support-<whatever_language>.
Hope this helps, but I'm not sure it does.

---

### Post by Superkoop on 2008-03-27
Can't say that it really helps me, but thanks for the ideas at least. :|
Because I really have no idea what I would have to all install, or change to make the correct characters show up where they should. :\

---

### Post by VinceJohn on 2008-03-31
I have the same problem using Kubuntu 7.10. I did not have this problem in Kubuntu 7.04: scim works beautifully on Feisty Fawn. Somewhere in between it seems someone decided to do something to fonts, their paths, or substitution tables? 

Unfortunately I am not clever enough to fix this myself any time soon, without help. Can some font expert kick a few hints my way, please? 

Thanks!

---

