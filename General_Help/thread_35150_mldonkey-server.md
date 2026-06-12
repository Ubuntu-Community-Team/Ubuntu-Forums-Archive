---
title: "mldonkey-server"
date: 2005-05-17
forum: General Help
---

### Post by crash369 on 2005-05-17
hello all.

i have been trying to install mldonkey-server, and i am not sure how to best do it.  most every howto, etc on the subject assumes that you are building mldonkey from source, while i am trying to get it through synaptic.

the biggest source of confusion comes from the whole "current dir" thing of mldonkey.

when i first installed mldonkey, i just ran "mlnet" in my ~, and there was a crap-load of new directories created right in my home dir which i really don't want there.

most of the howtos suggest creating a separate user for the mlnet daemon, and this is where i get completely lost.

can someone please please write a howto for installing/running mldonkey server in ubuntu?

edit:  also, during install, i am asked if i want to replace my /etc/default/mldonkey-server file.  i assume i do not, correct?

---

### Post by bored2k on 2005-05-17
[QUOTE=crash369]hello all.

i have been trying to install mldonkey-server, and i am not sure how to best do it.  most every howto, etc on the subject assumes that you are building mldonkey from source, while i am trying to get it through synaptic.

the biggest source of confusion comes from the whole "current dir" thing of mldonkey.

when i first installed mldonkey, i just ran "mlnet" in my ~, and there was a crap-load of new directories created right in my home dir which i really don't want there.

most of the howtos suggest creating a separate user for the mlnet daemon, and this is where i get completely lost.

can someone please please write a howto for installing/running mldonkey server in ubuntu?[/QUOTE]
 I'm not creating a howto because I hate that thing, but try this:
sudo apt-get install mldonkey-server mldonkey-gui gift
First run mlnet daemon then [while the other one is open] mlgui. Or what is it that you want ?

---

### Post by crash369 on 2005-05-17
[QUOTE=crash369]when i first installed mldonkey, i just ran "mlnet" in my ~, and there was a crap-load of new directories created right in my home dir which i really don't want there.[/QUOTE]
that's what happens when i run the mlnet daemon, and i don't want that to happen.

i want mldonkey stuff to be contained somewhere separate from my home dir.

do i simply have to create a directory somewhere and run mlnet from there?

---

### Post by bored2k on 2005-05-17
[QUOTE=crash369]that's what happens when i run the mlnet daemon, and i don't want that to happen.

i want mldonkey stuff to be contained somewhere separate from my home dir.

do i simply have to create a directory somewhere and run mlnet from there?[/QUOTE]
 Run mlnet from there ? it doesn't matter where you fire up mlnet really. I think that is why people suggest creating a separate user for it. It is also wise because you won't give this user sudo access, disabling any harm a possible breach could allow.

---

### Post by Klin'Targ on 2005-05-18
run mldonkey_server rather than mlnet, and it will start in ~/.mldonkey where it should.

---

### Post by crash369 on 2005-05-18
thanks a lot Klin'Targ!

---

