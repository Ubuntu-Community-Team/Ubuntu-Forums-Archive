---
title: "Firefox in separate processes"
date: 2008-02-15
forum: General Help
---

### Post by hgurol on 2008-02-15
Hello,

Since Im new to Linux & Ubuntu, Im suprised that every time I start a new Firefox window it runs on the same, single Firefox process.

I would like Firefox to run on different/separate process each time I run firefox.

Let me remind you the way MS handles this for IE....

All the tabs and new tabs runs on the same process and even all new IE windows, which has been started within an existing IE window by using the "Open link in a new window" menu, runs on the same process.

However, each time I click on the IE shortcut, it starts and runs on a separate process. And this is the exact way I would love the Firefox on Ubuntu to behave.

How can I configure it to work like that?

Thanks...

---

### Post by PeterJS on 2008-02-15
Firefox on windows also runs as a single process. That's just how Firefox works. Is there a reason you want it to run as seperate processes? That seems kinda like the sort of background detail you'd never need to worry about.

---

### Post by hgurol on 2008-02-15
> **PeterJS said:**
> 
Firefox on windows also runs as a single process. That's just how Firefox works.

I'm sure there must be a way to make that configuration; specially in Linux. I have huge expectations from Linux & Ubuntu; don't make me disappointed on my very first days :)


> **PeterJS said:**
> 
Is there a reason you want it to run as seperate processes?

Yeah, there is a very good one actually. When a Firefox window crashes, all of them do so. Im trying a couple of different streaming media players thru the browser, to experiment many and choose the most suitable ones for myself. Unfortunantly Firefox crashes A LOT during these tests(which is a different complaint for a different post). And Im tired and sick of having my all open Firefox windows crashing together with the one that has problems.


> **PeterJS said:**
> 
That seems kinda like the sort of background detail you'd never need to worry about.

Well, Im the GEEK that loves all of those background details ;)

---

### Post by PeterJS on 2008-02-15
Fair enough, good luck, that's well beyond the scope of my geekery.

---

### Post by JBAlaska on 2008-02-16
There are a couple of ways of doing this, I think lol

One is to set the env variable;
```
MOZ_NO_REMOTE=1
and start ff: firefox -ProfileManager
```

And the other (and possibly better) way is to start FF as so;
```
firefox -ProfileManager -no-remote

```

---

