---
title: "Too much security"
date: 2015-08-12
forum: General Help
---

### Post by Silvernail on 2015-08-12
I am  the only person living in my house.
I am the only person using  this computer.
I wash my own dishes.

I do not want nor need the security Ubuntu version 15.04 is imposing on me.

I get 'permission denied' on various apt when I try to save them, ie 'gedit' 'gimp' 'librecalc', to  name a few.

What do I need to change to get rid of this problem?


Thanks in advance for your help.
Dave

---

### Post by Bucky Ball on 2015-08-12
When you are trying to save files to a particular partition, the same partition, you are getting a permission denied error and needing to type in your password is what you're saying? Please confirm. Sounds like the permissions on the partition not an issue with Ubuntu. We can change permissions.

---

### Post by bab1 on 2015-08-12
> **Silvernail said:**
> I am  the only person living in my house.
I am the only person using  this computer.
Although you may be the only **mortal** user of the system you are NOT the only user of the system.  The permissions set up prevents you from damaging those files that are owned by the **system** users.  > 
I wash my own dishes.

I wash my own dishes too!  The wife has assigned that job to me.  :-( 
> 
I do not want nor need the security Ubuntu version 15.04 is imposing on me.

Yes you do want those limitations.
> 
I get 'permission denied' on various apt when I try to save them, ie 'gedit' 'gimp' 'librecalc', to  name a few.

What do I need to change to get rid of this problem?

Thanks in advance for your help.
Dave
Learn how to use the system correctly.  If you find the need to alter the system files use sudo to have the root user make the alterations.  See [here]("https://help.ubuntu.com/community/RootSudo") for how and why you use sudo.

If you have a specific problem; I will walk you through what needs to be done.  Just remember that for all files outside of your home directory you are most likely not the owner so you need to have the root user make the changes.

---

### Post by monkeybrain20122 on 2015-08-12
I do my own dishes too and that's why dirty dishes are piling up in the sink at this moment. :)

---

### Post by QIII on 2015-08-12
You're not the only user:  Malware and security vulnerabilities like to have root privileges, too.

---

### Post by col48 on 2015-08-12
Permission is denied for a reason.

Files which are important to the smooth working of the OS are owned by root, not by you.  If you need to change them, having to use sudo should encourage you to be cautious.
Having users running without administrative privileges as the norm is one of the fundamental advantages of Linux over Windows because even if malicious software is able to masquerade as you it does not thereby gain the right to touch the vitals of the OS.  Same goes for buggy software you may run.

If your computer is never connected to the internet, never has any external media (DVD, HDD, USB) mounted, and never needs to be repaired by a third party then the only vulnerabilities are 
1. oops, you might make a mistake (human error)
2. someone might steal the computer (malicious human)
3. there might be a software bug (human error)
3. something we haven't thought of (human error)

It's all too easy to rush into making a change to short-circuit some issue only to find that it has caused bigger and harder-to-solve issues elsewhere.  It's part of being human but in the design of Linux at least there is some protection for the soft underbelly of the files the OS needs, without them being completely inaccessible if they really do need to be upgraded/updated/repaired.

---

