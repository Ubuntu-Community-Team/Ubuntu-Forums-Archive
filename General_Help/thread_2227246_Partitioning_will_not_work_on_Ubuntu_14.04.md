---
title: "Partitioning will not work on Ubuntu 14.04"
date: 2014-05-31
forum: General Help
---

### Post by imzack2 on 2014-05-31
I have tried both GParted and KDE Partition Manager and both are crashing.

I am trying to resize the partition on my Live USB drive.

Also tried re-installing but no luck...


Below is KDE Partition Manager Crash screenshot after trying to resize partition in GUI
[IMG]http://i60.tinypic.com/250tkk5.png[/IMG]


Below is issues while running GParted
[IMG]http://i61.tinypic.com/zk04kw.jpg[/IMG]

Below is screenshot of GParted crash after attempting to resize partition



Let me know if anyone has any suggestions.

Thanks,

Zack
[IMG]http://i60.tinypic.com/2hgtwzp.jpg[/IMG]

---

### Post by grahammechanical on 2014-05-31
Why are you launching the partition manager from the terminal?

By the way, that last image, with Glib-CRITICAL is a common error message we get when running and application with a gui from the terminal. Ignore that image. It is nothing to do with the problem.

Regards.

---

### Post by imzack2 on 2014-05-31
I need to be in admin mode, so I have been launching it via the sudo command....

Regardless of  the Glib-CRITICAL error, any thoughts why both partition managers are crashing on me?

Thanks

---

### Post by imzack2 on 2014-05-31
So I have tried running GParted again, without terminal, and this is what I get...

[IMG]http://i59.tinypic.com/zv294.jpg[/IMG]

[IMG]http://i59.tinypic.com/eo6r8.jpg[/IMG]

---

### Post by LostFarmer on 2014-05-31
you can not shrink a partition to the amount being used, there is over head that must be added to the size.  I do not have any idea of how mush over head is needed.  Would say try 4g. size but that is only a guess, and likely more then needed.  Have you defraged the partition ?

---

### Post by imzack2 on 2014-06-01
You were correct my good sir!

I just made the partition much bigger and it worked just fine.

Thank you all so much!

---

