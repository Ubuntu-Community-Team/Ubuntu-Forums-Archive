---
title: "add/remove problems"
date: 2007-06-17
forum: General Help
---

### Post by maitresse on 2007-06-17
I am trying to use add/remove to install k3b, but i am getting this message

Cannot install 'k3b'

This application conflicts with other installed software. To install 'k3b' the conflicting software must be removed before.

Switch to the advanced mode to resolve this conflict.

any idea what this is about?

---

### Post by maitresse on 2007-06-17
just found out, it is doing it when i try to install anything

---

### Post by charleseddy on 2007-06-17
Are you using Ubuntu or Kubuntu.  That is, to say, Synaptic Package Manager or Adept?

---

### Post by maitresse on 2007-06-17
synaptic. i am on ubuntu.

---

### Post by charleseddy on 2007-06-17
Sounds like a failed package getting in the way.  Try closing synaptic, opening a terminal and typing:

sudo apt-get install -f

It might give you a list of packages in the terminal and tell you, "Use 'apt-get autoremove' to remove them."  In the terminal, simply type

sudo apt-get autoremove.

Then try again.

---

### Post by charleseddy on 2007-06-17
Did this work, or not?  If no, we should move on to troubleshooting further.

---

