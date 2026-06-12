---
title: "Help: Updating to 8.04 broke Compiz"
date: 2008-05-02
forum: General Help
---

### Post by Anthony0857 on 2008-05-02
I had been running Ubuntu v7.10 on my laptop, and Compiz was working fine.  My graphics card isn't good enough to run the most advanced features, like desktop cube, but I was still able to do a lot.

I've now updated to Ubuntu v.8.04, and now, nothing works.  In the appearance preferences, there is no longer an option to select a custom set of effects, and whenever I try to select anything other than none, it tells me that desktop effects could not be enabled.  I tried just going into the compiz-config settings manager and changing things, but none of the changes made any difference at all.  How can I make compiz work again?

---

### Post by PinkFloyd102489 on 2008-05-02
Hit Alt+F2 then enter this:

```
compiz --replace
```

If that doesnt work, then enter the same command into a terminal and post the output here.

---

### Post by Anthony0857 on 2008-05-02
I tried it, it didn't work.  Here's what I got from terminal.

```

anthony@anthony-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity 


```

[http://yoonkit.blogspot.com/2008/04/compiz-works-on-heron.html](http://yoonkit.blogspot.com/2008/04/compiz-works-on-heron.html)

I found this page, and I think it might have the solution to my problem, but I'm not certain, and I don't want to risk messing things up even worse.  Do you think the instructions there would solve my problem?

Edit: I just noticed the error message on that page is exactly like mine, that's enough to convince me to try that solution.

---

### Post by Anthony0857 on 2008-05-02
That page was the solution, compiz is working fine now.

---

### Post by Johnathannn on 2008-07-02
Hey guys, when I typed that command in the terminal I got this...

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

I have the same problem here... ANY ideas on how to fix this?:(

---

