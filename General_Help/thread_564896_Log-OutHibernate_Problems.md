---
title: "Log-Out/Hibernate Problems"
date: 2007-10-01
forum: General Help
---

### Post by jbaerbock on 2007-10-01
I have had hibernate problems ever since I first tried linux and no distro seems to have it working. So if anyone has any clue how to fix it I would appreciate the information.

But recently I noticed I cannot log-off the system. I try and the system freezes and can't get anything. I think if an OS cannot even log-off sucesfully it isn't the OS for me but since I love Linux so much and have learned so much I wan't to continue trying it out. So please let me know how to fix this problem.

---

### Post by Bert Mariën on 2007-10-01
Are you still running Feisty, or did you install the Gutsy beta? I ask this because I'm having some slight problems with the beta myself: booting up, logging in, logging out, logging off, switching user...
All of these give me some minor screen problems, and sometimes on logging off, the system freezes a while after I clicked the botton.

---

### Post by scruff on 2007-10-01
Can you describe "hibernate problems"?

Any errors, what type of behavior do you see, etc. I myself am having hibernate problems on my Thinkpad x60, but I know the problem. I have only 512mb of swap, and 2gb's of RAM. So I run out of swap everytime I hibernate. Simple fix, resize the partitions, but I've been too lazy thus far :)

---

### Post by jbaerbock on 2007-10-01
I am running Feisty and the hibernate problem is that it won't come out of hibernation or so I have to do a normal start. Also suspend does not work for similar reasons where it will not come out of suspend.

And with logoff it just freezes on a black screen.

---

### Post by Bert Mariën on 2007-10-01
Screen issues have been reported at Launchpad. I found 4 reports in a few minutes and I didn't dare to look any further (I need to go to sleep as well).

Anyway, you might take a look at these bug reports:
   #144260
   #145893
   #147289
   #147816

---

