---
title: "Help! i can't even boot my computer!"
date: 2008-01-22
forum: General Help
---

### Post by robitor on 2008-01-22
Hi, i installed linux on to my external hard drive  about a year ago. 

My problem is that i can't even boot up my computer if my external hard drive isn't plugged in. 

What i get is a a message that says GRUB initializing... ERROR 21
Then my computer freezes until i reboot. 

Now, what happens when my external hard drive fails, or it becomes corrupt, or i decide to uninstall linux?

I can't even get to windows because GRUB won't load unless the external hard drive is plugged in.

This is a serious issue because i can't even get to windows without my external hard drive turned on. Please help!!

---

### Post by ew16301 on 2008-01-22
If linux is installed on your external, it will never boot if that drive isnt plugged in. The best solution would be to reinstall grub on your internal harddrive and set that drive to boot before the external.

Here is out to install grub on your internal (Assuming your internal is HD0)
Go into terminal and type "grub" then use this command:
```
setup (hd0)
```

---

### Post by slayer04 on 2008-01-22
I agree error 21 means it can't find you linux partition which is on your external hard drive so unless you permanently leave it connected or reinstall it on an internal hard drive that problem will stay

---

### Post by robitor on 2008-01-22
> **ew16301 said:**
> If linux is installed on your external, it will never boot if that drive isnt plugged in. The best solution would be to reinstall grub on your internal harddrive and set that drive to boot before the external.

Here is out to install grub on your internal (Assuming your internal is HD0)
Go into terminal and type "grub" then use this command:
```
setup (hd0)
```

alright thank you so much! Now do i need to uninstall grub first, or do i just use that command you showed me?

---

