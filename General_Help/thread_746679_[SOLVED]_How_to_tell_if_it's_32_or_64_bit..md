---
title: "[SOLVED] How to tell if it's 32 or 64 bit."
date: 2008-04-05
forum: General Help
---

### Post by gulyman on 2008-04-05
So I need to know whether the version of Ubuntu I have is 32 or 64 bit. One guide told me to try uname -r in the terminal. Here is the guide.
[http://hydlaa.com/smf/index.php?topic=31776.0](http://hydlaa.com/smf/index.php?topic=31776.0)
It said that the last number in the sequence would tell me which one it was. But I get this 
2.6.22-14-generic
What does the generic mean?:confused:

---

### Post by LaRoza on 2008-04-05
I think that is 32 bit.

---

### Post by tamoneya on 2008-04-05
that is just telling you what version of the linux kernel you have and tells you nothing about your architecture.  Take a look in /usr.  If you see the directories:lib32 and lib64 then you have the 64 bit version otherwise it is 32 bit.

---

### Post by Butthead on 2008-04-05
Try "uname -a" instead.  Lots more info displayed (including current architecture). :guitar:

---

### Post by gulyman on 2008-04-06
When I look in /usr I find a folder called lib, but with no 64 or 32 after it.
When I try uname -a I get this
Linux my_computer_name 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux
What part would tell me what architecture it is?

---

### Post by zvacet on 2008-04-06
You have 32 bit version.

---

### Post by gulyman on 2008-04-06
Thank you. All I see when I look at it is random information.

---

### Post by niteshifter on 2008-04-06
Hi,

> What part would tell me what architecture it is?

This part (in bold) of uname -a output:

Linux my_computer_name 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 **i686** GNU/Linux

---

### Post by overdrank on 2008-04-06
> **gulyman said:**
> Thank you. All I see when I look at it is random information.

And this would be the output of the 64 bit
```
$ uname -a
Linux ubuntu 2.6.24-15-generic #1 SMP Fri Apr 4 03:10:59 UTC 2008 x**86_64** GNU/Linux

```

---

