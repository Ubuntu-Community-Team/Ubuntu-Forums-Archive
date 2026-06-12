---
title: "HPC with VT"
date: 2007-09-20
forum: General Help
---

### Post by ephracis on 2007-09-20
First of all, sorry if I am posting at the wrong place. Just after I registered here at Ubuntu forums I was overwhelmed with all the different areas and forums, and I had a hard time figuring out where to place my post. Anyway, here goes..


Many of you may have noticed that virtualization is the "new big thing" in computing. I am just beginning to explore what it is and what it can do. I remember playing with VMware when I was young, exploring the possibility to have more than one OS running on a single machine.

So I recently read an article in a magazine which explained virtualization technology (VT) a little bit. And I learned a new area of VT: the opposite of what I did with VMware as young. Not only can you run several OSes on a single machine, but you can run a single OS on multiple machines (question: how does this relate to clusters?).

So I was thinking and I thought that if I was to abstract the very physical computers from the actual operating systems I would have an extremely dynamic and adaptive server park. To explain: I want to have X machines running Y operating systems, but not tie the operating systems to a single machine, or even to their very hardware.

So to start I thought that if I created a cluster which would act as ONE machine, and then run VMware or some other VM on that "machine" I would achieve it (may not be the best solution, but it's a start).


Pros:
1)
Being able to change, modify, remove and add machines (cluster nodes) without it affecting the running operating systems.

2)
If you have, for example, a mail server running Windows 2003 Server and a web server running LAMP the actual load may vary in time. The web server may be using all it's power while the mail server is just standing there, idling - while the next day is the opposite. This will not be the case if you distribute the operating systems over a cluster.

Cons:
1) Is there actually a virtual machine that will take proper advantage of a cluster?


I have no prior experience of clusters. This is just an idea that popped in my head and I was hoping that the Ubuntu forums would have some intelligent people who could tell me why this will work/not work, what is wrong, how the idea can be implemented, improved, etc.

Of course I am not posting this on the Ubuntu forums because I want to run it on Gentoo. I was hoping that Ubuntu could run and manage the cluster and host the virtual machines.

Thanks for any answers,
Christoffer

---

### Post by Björn on 2007-10-16
Thats a very interesting question, and i don't have any answers. But since there has been three weeks now, i am wondering if you have made any progress. I am completely new to clustering and have searched the web for it the last few days, thats how i stumbled across your post. Do you have any idea which software you would use?

Waiting eagerly for answers

/Björn

---

