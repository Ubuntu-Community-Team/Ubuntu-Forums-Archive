---
title: "how to write an application"
date: 2008-04-18
forum: General Help
---

### Post by evaristegalois on 2008-04-18
I want to write multiple choice quizzes for my students. I can do so in html (perl cgi) and upload them to my server, but I want to learn how to write something like that which will execute on a local computer. So, how do I write a perl program that will translate into a multiple choice quiz for my students, NOT on the command line (html is great, but I guess there are other GUI type interfaces). My students are blind, so if it's screenreader accessible (like html) that would be a bonus.

---

### Post by Tomosaur on 2008-04-18
> **evaristegalois said:**
> I want to write multiple choice quizzes for my students. I can do so in html (perl cgi) and upload them to my server, but I want to learn how to write something like that which will execute on a local computer. So, how do I write a perl program that will translate into a multiple choice quiz for my students, NOT on the command line (html is great, but I guess there are other GUI type interfaces). My students are blind, so if it's screenreader accessible (like html) that would be a bonus.

Check out the [programmer's forum](http://ubuntuforums.org/forumdisplay.php?f=39), and also check whether something like this already exists (I have a feeling it might), where you can just pop in the questions you'd like it to ask, and provide the answers for the multiple choices. Seems like something a lot of educators would be interested in, so it could exist already.

If you're going to write your own, however, I would suggest using Python, since it is really VERY good for things like this, and is very simple to learn. I'm not sure if it will work with screenreader though, but it wouldn't hurt to ask in the programming forum to see if anyone has experience using it.

---

### Post by pseudo-random on 2008-04-18
What about making use of espeak?
Its a handy little command line tool try:
```
espeak "this is a test of ee speak"
```
Combine that with some random number selection, a text file of Q and A's and you've got yourself a random audio quiz.

---

