---
title: "Synaptic is stuck in launcher 14.04"
date: 2017-03-09
forum: General Help
---

### Post by rob18767 on 2017-03-09
I installed synaptic and when I type

sudo synaptic 

I get a prompt to enter password but the synaptic icon stays stuck in the launcher. 

Ubuntu version is 14.04.5 32 bit. 

Any ideas?

---

### Post by Paddy Landau on 2017-03-09
Synaptic automatically requests admin authorisation, so don't use sudo. You can just call it from the dash, anyway; you don't need to use the terminal.

Also, please **never** use sudo with GUI programs. You need to use either gksudo or, if configured, pkexec.

---

### Post by &amp;KyT$0P# on 2017-03-09
> **Paddy Landau said:**
> Also, please **never** use sudo with GUI programs. You need to use either gksudo or, if configured, pkexec
... or [FONT=Courier New]sudo -H[/FONT], right?

The [FONT=Courier New]-H[/FONT] option points [FONT=Courier New]$HOME[/FONT] to root's home directory, thus avoiding the problem of root taking ownership of files in a user home.

For more info, refer to [FONT=Courier New]man sudo[/FONT]

---

### Post by Paddy Landau on 2017-03-09
Indeed yes, you can use sudo -H. It's probably best to use gksudo as it reinforces the idea, because you could forget to add the -H with sudo.

---

