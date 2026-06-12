---
title: "HP desktop"
date: 2008-06-21
forum: General Help
---

### Post by noopypoop on 2008-06-21
Well, I tried installing Ubuntu via Wubi(but the problem isnt Wubi related which is why im not putting it in that section) But when I try to boot I get

```
dmi_save_oem_strings_devices: out of memory
```

 And when i get to the boot screen it freezes. I found this patch for it  > [http://lkml.org/lkml/2007/12/18/361](http://lkml.org/lkml/2007/12/18/361)  that says it has to do with HP PC's. How do I apply this patch so i can boot into Ubuntu?

---

### Post by noopypoop on 2008-06-21
*bump*

---

### Post by Sef on 2008-06-21
Do not bump your thread or any thread, unless 24 hours has gone by.  More frequently could lead to an infraction.

---

### Post by avtolle on 2008-06-21
Looking at the patch linked, you are going to have to "type" it in a text editor, and make it executable. Likely not what you wanted to hear.

---

### Post by noopypoop on 2008-06-21
> **avtolle said:**
> Looking at the patch linked, you are going to have to "type" it in a text editor, and make it executable. Likely not what you wanted to hear.

So then how am I supposed to be able to boot into ubuntu?

Heres what happens:


Select Ubuntu at startup

Shows up with that error

1st progress bar(the one that bounces) Starts going

The second one loads to ~15% then either freezes like that or reeboots. If it freezes then the caps lock and scroll lock lights flash.


I read somewhere that the flashing lights are an indicator of a kernal panic. Is this true?

---

### Post by avtolle on 2008-06-21
You are definitely having a kernel problem, and the flashing lights may well be an indicator of a kernel panic. I understand that you cannot boot into Ubuntu given the problem, but if that patch is the "fix", then someway, somehow, on another computer that patch will need to be placed in a script to make it executable, transferred in some form to the computer you are trying to boot and it will need to be executed at the time the kernel is being booted. All that is beyond my competence to do, or to explain to you how to do; I just know that it needs to be done.

---

### Post by avtolle on 2008-06-21
The tone of my last response was, unfortunately, a bit harsh. Sorry about that.

What I think you need to do is find some kind soul with the appropriate knowledge to compile a kernel with that patch included, or somehow put a boot cd together with the patch and kernel, together with the necessary apps to get your HP up and running. Failing that, or a new kernel with 8.10 (Ubuntu, Intrepid Ibex(?)) that overcomes that problem, it appearing that the problem is not Ubuntu specific, you may be able to find a distro of Linux that will boot on your computer other than Ubuntu. Good luck.

EDIT: [http://pclinuxos2007.blogspot.com/2008/05/tinyme-instilled-new-life-to-my-hp.html](http://pclinuxos2007.blogspot.com/2008/05/tinyme-instilled-new-life-to-my-hp.html) from a Google search looks promising, if you want to investigate it further.

---

