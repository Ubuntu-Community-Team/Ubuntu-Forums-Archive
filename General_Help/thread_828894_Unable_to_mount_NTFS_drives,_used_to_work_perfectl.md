---
title: "Unable to mount NTFS drives, used to work perfectly..."
date: 2008-06-14
forum: General Help
---

### Post by tmcarson1 on 2008-06-14
Normally upon starting Ubuntu, I have 2 ntfs partitions on a hard drive for storage.  Ubuntu would automatically mount these and allow me access to the files on them without me doing anything than double clicking the drive icon on my ubuntu desktop.

Now, the drive icons no longer appear on my desktop, they are in my 'places' menu, and when I click on them I get:
Cannot Mount Volume
You are not privilieged to mount the volume 'volume name'.

Any ideas what may be causing this?  Used to work fine.  I have tried rebooting but didn't help any.

Thanks for taking time to read this.
Tom

---

### Post by rraj.be on 2008-06-14
```
HADN'T YOU SHUT DOWN YOUR WINDOWS PROPERLY WHEN YOU USED IT LAST TIME?
```

    or 

```
Had you hibernated your windows at last usage?
```


When windows is not properly shut down or when hibernated it will lock its NTFS disk's.

You cant open it in ubuntu.

The solution is very simple.

```
Just get into your windows.

Wait untill it load's.

shut it down completely.
```

Now boot you'r windows.

May i know if any more problems further?

---

### Post by tmcarson1 on 2008-06-14
That was exactly the problem.  After going in and shutting down windows properly, it let me have access to the drives again in ubuntu.

Thanks so much for your help!:guitar:

---

