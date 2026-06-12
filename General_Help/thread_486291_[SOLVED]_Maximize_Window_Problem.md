---
title: "[SOLVED] Maximize Window Problem"
date: 2007-06-27
forum: General Help
---

### Post by MrFSL on 2007-06-27
Having an interesting issue. When I am running Compiz (Desktop Effects) and I maximize any application or window, the title bar becomes unusable. Please help! I have to right click on the application in the title bar and select "UNMaximize" before I can get it working again.

Again, ... PLEASE HELP.

MrFSL

---

### Post by wjp.reg on 2007-06-27
That's considered a "feature" of beta software ;-)

---

### Post by speaker219 on 2007-06-27
> **wjp.reg said:**
> That's considered a "feature" of beta software ;-)

:(, no, that's not considered a "feature" and that's not a very helpful response. I'm not saying this reply is helpful eiether, but I use compiz fusion and i have never had ANY problems/bugs.

---

### Post by wjp.reg on 2007-06-27
> **speaker219 said:**
> :(, no, that's not considered a "feature" and that's not a very helpful response. I'm not saying this reply is helpful eiether, but I use compiz fusion and i have never had ANY problems/bugs.

It is beta software and your problem has been reported a number of times on this forum with no solution forthcoming.

---

### Post by Qu4k3R on 2007-06-28
You could remove compiz desktop effects.
If you want you can install beryl..
beryl might work..
If you are using GNOME, install also heliodor.

My repository for beryl are this ones:

> 
# Beryl
# deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy


If you want you can add them to your /etc/apt/sources.list
Use them at your own risk.

PS:
Beryl is in a Beta version.

---

### Post by MrFSL on 2007-06-28
Thank You All For The Replies.

I searched this forum without finding any specific post with this same issue.

I successfully used Beryl in the past on Edgy with no issues. This current issue has arisen since I switched to Feisty and used the built in Compiz implementation. 

I will see if Beryl behaves the same this evening.

Cheers.

---

### Post by MrFSL on 2007-07-05
Update

I added these repos.

```

deb http://download.tuxfamily.org/3v1deb feisty eyecandy 
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

```

then did an update which fixed my window maximization issues.

---

### Post by wjp.reg on 2007-07-05
> **MrFSL said:**
> Update

I added these repos.

```

deb http://download.tuxfamily.org/3v1deb feisty eyecandy 
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

```

then did an update which fixed my window maximization issues.

Good one!!

Maybe I'll give it a go now ;-)

---

