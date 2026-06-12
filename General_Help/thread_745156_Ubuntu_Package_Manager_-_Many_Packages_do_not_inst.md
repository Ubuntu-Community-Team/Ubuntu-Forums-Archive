---
title: "Ubuntu Package Manager - Many Packages do not install"
date: 2008-04-04
forum: General Help
---

### Post by GCoffee on 2008-04-04
Hi,

I'm getting annoyed at this problem. Say there is some software in the package manager I like (example Gambas) I check it, click apply and a error comes up telling me to switch to synaptic package manager. So I do. When I select my software it tells me some of the dependencies can't be resolved or can't be installed. This is getting frustrating. It doesn't happen for EVERY package in the package manager. But I would say a good majority of them. Is this to do with my sources.list file? If so, can someone give me the link to the original one? I'm using Ubuntu Gutsy Gibbon 7.10. Thanks.

Am I the only one having this problem?

Cheers,
Gcoffee.

---

### Post by plucky on 2008-04-04
You need to make sure all the repositories are available.

**System > Administration > Software Sources** and on the first page make sure the top four boxes are selected.Disable the CDrom box in the the window.

Then go to updates tab and select the top two boxes.When you hit **Close** you will be asked to reload your source indexes, do so.


You should be good to go.  


If you still have a problem open a terminal and ```
cat /etc/apt/sources.list
``` Cut and paste to the forum so we can have a look.


Good Luck

---

### Post by GCoffee on 2008-04-04
Thankyou! DankaShun! You have no idea how much you have just helped me! I owe you one! :D:D:D

THANKYOU,
GCoffee:):):):)

---

