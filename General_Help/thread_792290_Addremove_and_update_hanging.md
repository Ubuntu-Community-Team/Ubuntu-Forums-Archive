---
title: "Add/remove and update hanging"
date: 2008-05-12
forum: General Help
---

### Post by InTheShires on 2008-05-12
Hello

I'm experimenting with 8.04 [32bit] but keep getting the same problem. 
I have reloaded about 5 times now & this always happens. 
It all seems to work perfectly for a short while & I can get any security updates, add & remove things with add/remove but eventually the same trouble starts again. 
I become unable to use add/remove, it hangs never doing a thing, and the same happns with package manager & update.
How can I over come this? 
Talk to me in simple terms plz.
If you need extra information I will try & give it to you.
Best Regards.

---

### Post by mmb1 on 2008-05-12
Does synaptic, or updating through the terminal work?

---

### Post by InTheShires on 2008-05-15
I got it sorted I think, from reading other messages here it seems I had to remove the domian name, which I did, and now it seems to be working again.
Regards.

---

### Post by studiosonic on 2008-06-05
What did you do to fix this? I can install programs and update fine from the console, but the add/remove programs gui just hangs when I try and do it there. Where did you remove a domain name from? I can't see it mentioned on other posts.

---

### Post by plucky on 2008-06-05
studiosonic,

From a terminal window,copy and paste these commands ```
cat /etc/hostname
cat/etc/hosts
```

---

