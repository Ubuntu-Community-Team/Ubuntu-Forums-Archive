---
title: "sudo and authantification is slow when wifi is on (ubuntu 18.04)"
date: 2019-12-17
forum: General Help
---

### Post by 2iro on 2019-12-17
Hi all,

When starting my computer and if I am connected to the wifi it takes more than 1min to login. If I turn off wifi it is instantaneous. 
Same with sudo in the terminal. 

I tried several things but nothing helps for now so I am asking for your help!

Many thanks,
Best

I.

---

### Post by TheFu on 2019-12-17
Sounds like a DNS problem.  Without any networking, it times out quickly.
I would check that the /etc/hosts file is correct as a first step.  Ensure the **hostname** program and entry in /etc/hosts match.

---

### Post by 2iro on 2019-12-17
Thanks TheFu,

I already checked this and my hostname match /etc/hosts!

---

### Post by TheFu on 2019-12-17
Hate to ask, but can you prove it?

And I'd look into the resolv order. New releases have screwed that up, IMHO.  nsswitch.conf has it.

---

