---
title: "what is the &quot;Web Content&quot; process?"
date: 2017-02-14
forum: General Help
---

### Post by marchello_lippi2 on 2017-02-14
Hi all, 

What is the "Web Content" process? 
It appears when I open firefox window. 
Whenever I perform killall "Web Content", the firefox tab crashes. 
Then I refresh firefox tab and the "Web Content" process appear again in top. 
What is that??? 

14.04 LTS

---

### Post by &amp;KyT$0P# on 2017-02-14
It's part of Electrolysis aka multiprocess Firefox.  Essentially, that "Web Content" process **is** the tab.

---

### Post by marchello_lippi2 on 2017-02-14
That's fine, but the "Web Content" is among the biggest CPU consumers... :-/ Is there any way to make it stop consuming so much?

---

### Post by &amp;KyT$0P# on 2017-02-14
What extensions do you have?
Is it so CPU-hungry if you disable all your extensions?

Is it so CPU-hungry in a new, clean [profile]("http://kb.mozillazine.org/Profile_folder"), with [Electrolysis enabled]("http://superuser.com/a/1108314") and everything else default?

---

### Post by marchello_lippi2 on 2017-02-15
I got no firefox extensions so far, at least from what I know.. Is there any way to have a kind of "hidden" extensions in firefox?? How do I check it then? 
Please advise.

---

### Post by &amp;KyT$0P# on 2017-02-15
That's OK, then you can skip that and go straight to this -
> **halogen2 said:**
> Is it so CPU-hungry in a new, clean [profile]("http://kb.mozillazine.org/Profile_folder"), with [Electrolysis enabled]("http://superuser.com/a/1108314") and everything else default?

If it still uses a lot of CPU, go back to your main profile.

How much does the CPU usage vary depending what website you're viewing?
Compare a simple site like [this]("http://www.catb.org/~esr/writings/unix-koans/"), to various pages on [this forum]("https://ubuntuforums.org/"), to something really script-heavy (likely your favorite news site will do).  I would also suggest watching how the CPU usage changes as you interact (or don't interact) with the sites.

---

### Post by marchello_lippi2 on 2017-02-16
I guess it was some temporary glitch, now it does not consume so much. 
Thanks for replies anyway.

---

### Post by gfe on 2017-11-19
I had problems with excessive Web Content resource usage (2.4 GB on a 4 GB machine with one tab open) after starting to use the "new" Firefox. Disabling the Ghostery add-on solved the problem.

---

