---
title: "USB mouse and Hibernate/Suspend problems in Hardy"
date: 2008-06-05
forum: General Help
---

### Post by lalilulelo on 2008-06-05
I have a couple pretty big problems with the Ubuntu Hardy release.

The first is that my USB mouse does not work correctly. It works for a minute or two after starting up, and then it ceases to respond. It's obviously still getting power, but the pointer on the screen does not move. The mouse works fine in Windows XP. I read the post about how to fix USB permissions in Ubuntu, but that seems to be an issue from this. I haven't tried it yet, though.

The other problem is that Hibernate and Suspend are completely broken. When I put the computer in either Hibernate or Suspend mode, the screen turns black and the HDD makes a click as if it's about to go into Suspend mode, but then it just hangs there and never actually turns off. I read about other people having similar problems, but I haven't yet heard of a solution.

Any suggestions?

---

### Post by rraj.be on 2008-06-05
i dont have any sugestion's to ur USB mouse problem.

But for hibernating i want to know ```
whether you are using a swap partition or not.
```

---

### Post by lalilulelo on 2008-06-06
Yes, I have a swap partition that's about 1200 MB, and I have 1GB of DDR2-800 RAM. Both Hibernate and Suspend have the same issue.

---

### Post by lalilulelo on 2008-06-06
Bump. Isn't there any way to fix these problems? The Hibernate/Suspend thing isn't that important, but the mouse thing makes Ubuntu pretty much unusable.

---

### Post by rraj.be on 2008-06-07
check this

```
[http://inquirer.philly.com/newsroom/faq/pages/fdb7df9-37.html]("http://inquirer.philly.com/newsroom/faq/pages/fdb7df9-37.html")
```

```
[http://ubuntuforums.org/showthread.php?t=189572&page=3]("http://ubuntuforums.org/showthread.php?t=189572&page=3")
```

```
[http://ubuntuforums.org/showthread.php?t=28173&page=2]("http://ubuntuforums.org/showthread.php?t=28173&page=2")
```

---

### Post by lalilulelo on 2008-06-07
Thank you very much rraj.be, that was exactly what I was looking for! I haven't tried any of them yet, but I'm almost positive that one of them will work since the problems these people are describing are exactly the ones I'm having.

---

### Post by rraj.be on 2008-06-07
try but be cautious not to remove any system thing's.

Get into forums if you have some doubt, clarify it, and then proceed.

---

### Post by lalilulelo on 2008-06-19
Well, my mouse seemed to be okay for a while, but now it's having problems again. It'll work for several minutes and then the power will just cut out from it and it won't work again until I reboot. This makes me think I need to change something in my bios. Any ideas?

EDIT: I think this is due to a problem with ACPI and/or APIC, but I don't know how to disable them. I have an ASUS P5N-SLI (nForce) motherboard.

---

### Post by lalilulelo on 2008-06-19
I read in another thread that there's a way to disable ACPI during the installation of Ubuntu. Could someone explain to me how this is done?

---

### Post by lalilulelo on 2008-06-21
Update: okay, so I installed Ubuntu 8.04 with ACPI disabled, but I'm still having problems with my mouse operating erratically. Can't anybody give me advice?

---

