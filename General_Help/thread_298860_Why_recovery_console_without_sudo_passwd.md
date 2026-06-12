---
title: "Why recovery console without sudo passwd?"
date: 2006-11-13
forum: General Help
---

### Post by terrax on 2006-11-13
Hello ubuntu/kubuntu users.

There is a question, i have thought about some time. Why don't you have to type somekind of a root password, when entering the recoverymode?

I think its very unsecure. But as for alot of linux stuff, there is always a reason. And ofcourse there is a reason for this also. But what is it?

If someone could explain it to me, I would be very happy.

Cheers, from the happy kubuntu user.

---

### Post by taurus on 2006-11-13
What if you somehow screw up your machine and your regular account can't use sudo anymore, how would you fix it if you can't sudo?  Therefore, you need to boot into the recovery mode to fix your system...  And if you're afraid it is a secure problem, then don't include the recovery mode in your GRUB and log your machine in a secure room with key...

---

### Post by Ramses de Norre on 2006-11-13
People need to have physical access to your machine in order to use grub, and if they do have physical access they can also pull out your hard disk and take it home.. So I don't think the recovery mode is a real issue and you can always remove it from grub and set a grub password anyway.

---

