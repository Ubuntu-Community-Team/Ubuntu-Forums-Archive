---
title: "Help aptitude problems"
date: 2007-06-10
forum: General Help
---

### Post by Milner_07 on 2007-06-10
When ever i try to install any thing via aptitude (or apt-get) i get this error message -
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?

What does that mean?

How can i fix it?

TM

---

### Post by tpg on 2007-06-10
This either means you aren't running the process as root - solution - prepend the command with sudo.

Or another process is trying to perform package operations. Make sure synaptic etc. isn't running at the same time.

---

### Post by Irti on 2007-06-10
do you leave your synaptics window open when trying to do this???? close your synaptics window before trying to install anything using terminal..............you can go to root using sudo -i

---

