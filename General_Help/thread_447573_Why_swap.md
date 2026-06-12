---
title: "Why swap?"
date: 2007-05-18
forum: General Help
---

### Post by toasterofirony on 2007-05-18
I've noticed something odd happening recently, *something* is using swap memory when I have hundreds of megs of physical memory sitting around as cache. I've never seen this before in any other incarnation of ubuntu. I've attached a little screenshot to illustrate my point.

Does anyone have any ideas what might be going on?
 
Personally I suspect Firefox, as it has been buggy for me of late, either crashing apropos of nothing or going through periods when the whole program will stutter as I try and scroll down a page.

---

### Post by vikramsharma on 2007-05-18
> **toasterofirony said:**
> I've noticed something odd happening recently, *something* is using swap memory when I have hundreds of megs of physical memory sitting around as cache. I've never seen this before in any other incarnation of ubuntu. I've attached a little screenshot to illustrate my point.

Does anyone have any ideas what might be going on?
 
Personally I suspect Firefox, as it has been buggy for me of late, either crashing apropos of nothing or going through periods when the whole program will stutter as I try and scroll down a page.

Go to the terminal app and try top there you should know the %age cpu and ram being used by apps, ps -aux is equally helpful

---

### Post by toasterofirony on 2007-05-18
Thanks for the advice, I'm just a little confused which one of the stats I should be looking at to see what is using swap, rather than physical ram.

---

