---
title: "Thunderbird crash"
date: 2006-10-09
forum: General Help
---

### Post by dgorchak on 2006-10-09
I'm Edgy Eft user (Kubuntu), and I've installed **mozilla-thunderbird** from official edgy repo. But there is one problem - it crashes after every launch when it's configured, e.g.: I launch Tb at the first time, it starts OK, creates my mail account and then after pressing **Finish** in the wizard, Tb crashes. Starting it again doesn't help - it crashes just after launch. OK, if I delete my **.mozilla-thunderbird** folder, it starts OK, but crashes again after repeating described above steps.

The error is - DOUBLE-CLICK: 250 --> -1 THRESHOLD: 8 --> -1 Segmentation fault

](*,)  dunno what to do, I think about switching to Sylpheed-Claws... anyone knows why can Tb crash? No extensions installed, just configuring on a clean profile

---

### Post by seldon77 on 2006-11-03
i get the same crash and error.

i think theres a launchpad entry on this

---

### Post by forcotton on 2006-11-05
Just downloaded the binary from the official website. Works without a problem.

---

### Post by warp10 on 2006-11-08
I had this identical problem after installing italian locales.

I read on another topic that starting thunderbird as root goes ok. Infact, it is true.

I saw that some files into my profile folder were owned by root. Chowning to my normal user didn't solved anything. 

I solved the problem disabling the Thunderbird start page (default: chrome://messenger/content/start.xhtml) form Preferences/General. I suppose that this file is owned by root and starting TB as normal user causes the crash. Someone fo you knows where this file is in the filesystem. I am not been able to find it to check the owner.

---

### Post by lduperval on 2006-11-30
I am wondering if a library isn't at the root of this problem. I am seeing the same type of issue with Nvu, Kompozer and Thunderbird, which are all Mozilla-based applications which allow you to edit HTML code.

In all cases, when I try to edit some code (which used to work fine a couple of weeks ago) the application crashes. It looks like some library update at some point started causing this issue.

L

---

### Post by mmaathieu on 2006-12-09
Hi,

Same problem... I solved it by disabling the thunderbird home page. It works well, untill I check RSS feeds: it still craches on the load of some articles, but not all of them...

---

