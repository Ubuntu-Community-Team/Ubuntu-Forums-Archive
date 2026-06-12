---
title: "NoMachine - Extremely high RAM usage"
date: 2013-09-28
forum: General Help
---

### Post by assaf-aviram on 2013-09-28
Hi,
I recently installed the NoMachine package on my home desktop and noticed a few occurances where my machine was completely out of RAM & swap space..

Looking at the gnome-system-monitor, I couldn't find any processes that take so much ram so I turned to the terminal and ran 'free -m' and 'top' to see more...
I found out that the NoMachine software has made a user called 'nx' on my system and that user is running dozens of instances of 'nxserver.bin'.. consuming all of my ram.

I'd completely ditch the software but it's the best remote-desktop solution I know of...  any help would be appreciated.

* I actually configured cgroups to stop nx from consuming too much ram.. I think it works for the moment but it doesn't seem like the appropriate solution.

I'm running Elementary OS (based on 12.04) with kernel 3.11.2.

Thanks!

---

### Post by QIII on 2013-09-29
Hello!

Is this machine the server or a client?

---

### Post by Gian_Filippo_Pinzari on 2013-09-29
> **assaf-aviram said:**
> I found that user is running dozens of instances of 'nxserver.bin'.. consuming all of my ram.

You didn't specify what "nomachine package" is showing this behavior, but I assume it is the new 4 released a few days ago. This is clearly a bug causing the nxserver.bin process to hang indefinitely. I suggest you contact the NoMachine support. I'm sure the developers will be more than happy to hear from you.

---

### Post by assaf-aviram on 2013-09-30
Yea, I'm trying to use their latest 'stable' 4 release.. as a server.
I had a thought that something went wrong between the nomachine package and a freenx installation I had causing problems with each other, I tried to install the nomachine package on a fresh elementary install and the same thing happened.

I'm not sure how to contact their devs, I think they only provide support to subscribed customers.

---

### Post by assaf-aviram on 2013-09-30
Well.. if anyone is interested, I contacted the devs, they requested logs and such, I'm now waiting to see what they say.
Since then I tried a few things and found out that this doesn't happen on the 'stock' 3.2 kernel that comes with Elementary, it happens with the 3.8 LTS kernel package and on the latest stable 3.11.2.

---

### Post by assaf-aviram on 2013-10-02
Another update - 
The NoMachine team was extremely helpful and quick to react. They found a bug and said that it will be fixed in their next patch/release.

In the meantime, if you want a workaround, change the NoMachine server port to 4008. I did that and everything's been running just fine since.

Here's the bug/error link : 
[http://www.nomachine.com/TR10K03702](http://www.nomachine.com/TR10K03702)

---

### Post by Gian_Filippo_Pinzari on 2013-10-07
Solved in 4.0.352.

Regards and thanks for reporting.

---

