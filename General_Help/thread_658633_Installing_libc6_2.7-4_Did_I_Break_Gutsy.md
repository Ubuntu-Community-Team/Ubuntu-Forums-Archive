---
title: "Installing libc6 2.7-4: Did I Break Gutsy?"
date: 2008-01-04
forum: General Help
---

### Post by GenuineXP on 2008-01-04
In my frustration I installed libc6 2.7-4ubuntu1 (amd64) which seems to be meant for Hardy on my Gutsy box. I've been trying to get this brickos package to install and discovered it couldn't resolve the libc6 dependency because mine is too old.

Well, I installed the package and it failed. Now it says my old libc6 packages are broken. Synaptic won't let me solve the problem without removing virtually every critical piece of software on my system! How can I reverse this? Removing the new libc6 also results in Synaptic wanting to remove all of my system.

Is there a way around this, or did I just break my OS with a few (admittedly stupid) mouse clicks?

Thanks!

---

### Post by phidia on 2008-01-04
Have you tried to use dpkg to remove the libc6 package? How exactly did you install that package in the first place? There is a package to help installing libs check it out [here]("http://ubuntuforums.org/showthread.php?t=474790&highlight=lib32").
So even if you do have to reinstall perhaps getlib will help you in the future.

---

### Post by GenuineXP on 2008-01-04
Thanks for the reply, phidia.

I installed a Hardy package found [here]("https://launchpad.net/ubuntu/hardy/amd64/libc6/2.7-4ubuntu1"). This didn't seem wise to me in the first place, but I really wanted to get the brickos package to install. I probably would've faired better if I forced the brickos install with dpkg, now that I think about it.

Anyway, would lettings Synaptic do it's thing from a terminal (without logging into Gnome, etc.) be the best way to go? No matter what I try, Synaptic insists on removing hundreds of megabytes of core software!

Thanks again.

---

### Post by GenuineXP on 2008-01-04
I'm going to try forcing the version of libc6 in Synaptic. I think that'll solve the problem; I completely forgot the manager had that feature. I'll see what happens...

---

### Post by GenuineXP on 2008-01-04
Problem solved.

Thank goodness for Synaptic's robustness. It can withstand idiots like me, it seems. :-)

Thanks for the help.

---

### Post by phidia on 2008-01-05
> **GenuineXP said:**
> Problem solved.

Thank goodness for Synaptic's robustness. It can withstand idiots like me, it seems. :-)

Thanks for the help.

I'm glad that worked for you, and you helped others by describing this too.
Synaptic's features have always made debian outshine, for me, the many distros out there.

---

### Post by mikecomua on 2008-01-09
I don;t get it, sorry. What does "forcing a version" mean?

---

### Post by mikecomua on 2008-01-09
I don;t get it, sorry. When I try to force libc6 to version gutsy it tells me to remove loads of other software.

---

### Post by hengie on 2008-01-30
I had exactly the same issue as GenuineXP and resolved the problem with:```
sudo aptitude install libc6
``` Aptitude discovered the conflict and offered to downgrade libc6 to a stable version```
Downgrade the following packages:
libc6 [2.7-5ubuntu2 (now) -> 2.6.1-1ubuntu10 (gutsy-updates)]

```

---

