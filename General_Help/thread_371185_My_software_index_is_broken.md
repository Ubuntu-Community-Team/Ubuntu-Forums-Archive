---
title: "My software index is broken"
date: 2007-02-26
forum: General Help
---

### Post by pilot550 on 2007-02-26
I tired to install Java manually as shown on the Java web site. That didn't work very well so I was told to just install automatix. I did and now I'm getting a error message:
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

So I run "sudo apt-get install -f" in the terminal and I get a java install window but I can't click on "OK"

So I ran the code again and I get: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "

So now I have no idea how to run dpkg manually. Can someone help me please.

---

### Post by chggr on 2007-02-26
Type this command in a terminal and tell us what you get:

dpkg --configure -a

---

### Post by pilot550 on 2007-02-26
Oh I got it. I have to sudo -s first. Thanks.

---

### Post by jackrobinson on 2007-02-26
> **pilot550 said:**
> I tired to install Java manually as shown on the Java web site. That didn't work very well so I was told to just install automatix. I did and now I'm getting a error message:
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

So I run "sudo apt-get install -f" in the terminal and I get a java install window but I can't click on "OK"

So I ran the code again and I get: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "

So now I have no idea how to run dpkg manually. Can someone help me please.
you cant click ok.. you ned to hit **tab** to highlight **OK** and then hit "**enter**" to agree to the java EULA.

---

