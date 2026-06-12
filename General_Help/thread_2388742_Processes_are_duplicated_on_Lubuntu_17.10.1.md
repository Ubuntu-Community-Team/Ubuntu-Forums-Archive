---
title: "Processes are duplicated on Lubuntu 17.10.1"
date: 2018-04-06
forum: General Help
---

### Post by THE Ghost2 on 2018-04-06
Is this normal behaviour of modern distribution?

Here is a screenshot of htop

[https://s14.postimg.org/lxzg6pib5/2018-04-06-164151_1366x768_scrot.png](https://s14.postimg.org/lxzg6pib5/2018-04-06-164151_1366x768_scrot.png)

EDIT: 

As the replies say, this behavior is normal. Sorry for the noob question.

---

### Post by TheFu on 2018-04-07
Hard to read. Please use text (copy/paste usually works great) and wrap the text here in 'code tags' so things line up.  That's Adv Reply (#) or you can manually do it.

Segmenting tasks by either using a different thread or different process is normal.  Spawning a process is fairly light on Unix systems, unlike with Windows.  So, yes, this is normal.

---

### Post by THE Ghost2 on 2018-04-08
Thanks, I thought there was something wrong because NetworkManager is duplicated too(in the taskbar, bottom right). 

This is the default LIVE environment of Lubuntu 17.04.1
EDIT: Its 17.10.1 not 17.04.1(typo).

---

### Post by TheFu on 2018-04-08
17.04 support ended a few months ago. Shouldn't be used.

[https://developer.gnome.org/NetworkManager/stable/NetworkManager.html](https://developer.gnome.org/NetworkManager/stable/NetworkManager.html)

I don't know much about NM.  Had issues with it years ago and always purge it from my systems.  I have non-trivial networking which always confused it or static IPs, so it isn't useful. I don't use the gdisks thing either. Actually, I go out of my way to handle mounts manually because I found the GNU tools to ruin disk performance.  Plus, I consider allowing normal users the ability to mount a huge security problem.  Nothing on my systems allows mounting of any storage automatically or by end users.

Of course, others seem to have different opinions about these things.  To me, they don't pass my "smells bad" test.  I don't do things that smell bad if I can avoid it.  There are probably 100+ things that people commonly do which I won't because they fail my smell test (also common sense).

---

### Post by THE Ghost2 on 2018-04-12
Sorry, I meant 17.10.1

But thanks for the reply.

---

### Post by HermanAB on 2018-04-13
Linux is a multiprocessing system and many processes run multiple threads.  What you see is normal.

---

### Post by THE Ghost2 on 2018-04-18
Okay, thank you, this question will be marked as solved.

---

