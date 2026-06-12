---
title: "Synaptic broken..? Wtf?"
date: 2007-05-21
forum: General Help
---

### Post by transatlant1c on 2007-05-21
Hey, new user here and I have a problem.. Just recently my synaptic/add remove programs menus have just died. Whenever I go to install the updates waiting on my computer I get a message saying:

--

Software index is broken

It is impossible to install or remove any software. Please use the package manager 'Synaptic' or run 'sudo apt-get install -f' in a termnial to fix this issue at first.

--

It did that but I don't know what it did.. Not sure if anything :( Can someone please help me out, and tell me what I did or can do? I'm very new to this and I don't really know what I'm doing.. :(

---

### Post by heimo on 2007-05-21
Please rerun it in terminal and copy paste output here.
```
sudo apt-get install -f
```

---

### Post by transatlant1c on 2007-05-21
The output was:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

So I did that.. and I got this:

```
dpkg: requested operation requires superuser privilege
```

What do I do from here?

---

### Post by total wormage on 2007-05-21
> **transatlant1c said:**
> The output was:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

So I did that.. and I got this:

```
dpkg: requested operation requires superuser privilege
```

What do I do from here?

then you'll need to do a:
```
sudo dpkg --configure -a
```

:]

---

