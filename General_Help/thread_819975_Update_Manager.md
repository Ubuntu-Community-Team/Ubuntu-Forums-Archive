---
title: "Update Manager"
date: 2008-06-05
forum: General Help
---

### Post by craiger45 on 2008-06-05
Hi, I'm having trouble with the Update Manager. When there is an update indicated in the upper panel and I click on it, the Update Manager window opens listing all available updates and descriptions as it should.
I then click on install updates and instead of asking for my password, I get the circular working cursor, but nothing more happens.
It seems it has been doing this since I installed the latest version(8.04).
I have to switch to the root user and it will update like normal. Anyone have this problem also? Thanks.
P.S. I have to go into system monitor and kill the process, (update manager) to close the window.

---

### Post by iaculallad on 2008-06-05
Instead of switching as a root user, had you tried the command on your terminal if it works?

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by craiger45 on 2008-06-05
Thanks for the reply. Yes both commands worked in the terminal box, but I would still like it to work as it should by clicking the red update arrow.

---

### Post by Bubba64 on 2008-06-05
After running those commands it should work normally you can also use reload in synaptic to get updates and the install. I have random update manager issues but, they are usually fixed for awhile after either update upgrade.

---

### Post by Dale Sexton on 2008-06-15
> **iaculallad said:**
> Instead of switching as a root user, had you tried the command on your terminal if it works?

```
sudo apt-get update && sudo apt-get upgrade
```

I tried that and got this:

sudo: unable to resolve host   127.0.1.1 Val

Where Val is my computer.

Dale

---

### Post by Nepherte on 2008-06-15
Check this thread out: [http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

---

### Post by Loonygrizzly on 2008-06-15
> **iaculallad said:**
> Instead of switching as a root user, had you tried the command on your terminal if it works?

```
sudo apt-get update && sudo apt-get upgrade
```
How do I get to that terminal to type the command in? (noob)

---

### Post by Dale Sexton on 2008-06-15
> **Nepherte said:**
> Check this thread out: [http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

I fixed it, but it's very strange. I have 2 computers (actually more, I'm switching them all to Linux), In /etc/hosts one used host
127.0.1.1 Mal
the othe just wants to see
Val
What gives?

Dale

My original computers name is Hal (open the pod bay door Hal).

---

### Post by Dale Sexton on 2008-06-15
> **Loonygrizzly said:**
> How do I get to that terminal to type the command in? (noob)

From the Desktop:
Applications >> Accessories >> Terminal

Dale
A noob myself

---

### Post by Dale Sexton on 2008-06-15
I was able to update everything but 6 module. When I try to get them< this is what I get:
Reading package lists ... Done
Building dependency tree... Done
Reading state information... Done
The following packages have been kept back:
  f-spot linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic ssl-cert
0 upgraded, 0 newly installed, o to remove and 6 not upgraded

Still not getting updates from the desktop.

What next?

Dale

---

