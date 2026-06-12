---
title: "no useage of swap memory"
date: 2008-04-27
forum: General Help
---

### Post by sweeneytodd on 2008-04-27
can anyone help with anyway to activate swap memory, as it isn't being used at all, and would it be wise to have a smaller system partition so the swap partion is closer in the first place, main partition doesn't want to resize in partion editor, any other way?

---

### Post by NightwishFan on 2008-04-27
Tell me what it says about swap in:
```
free -m
```

---

### Post by sweeneytodd on 2008-04-27
swap total 2588, used 0, free 2588

---

### Post by sweeneytodd on 2008-04-27
total       used       free     shared    buffers     cached
Mem:           883        462        420          0         13        260
-/+ buffers/cache:        188        694
Swap:         2588          0       2588

---

### Post by Oldsoldier2003 on 2008-04-27
Well you have swap and its turned on. The fact that you are not using swap is a good thing, since swap is slower than RAM.

---

### Post by sweeneytodd on 2008-04-27
i ran a few things like music and firefox and checkedthe swap memory again and still 0% useage, so this is a good thing then

---

### Post by louieb on 2008-04-27
Swap not being used is a good thing. Like virtual memory in windows its only used when ram get full .  And like virtual memory when its used it has much slower access time. Your free command output looks fine.

As for the partition editor not being able to manipulate your Ubuntu install partition - the reason is the partition is mounted and in use. 

If you need to  resize the Ubuntu partition use the partition editor on the live CD. I use GParted on the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") or VisParted on the  [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic").

---

### Post by sweeneytodd on 2008-04-27
thank you for your help and time, but is it a good thing to do, have a smaller primary partition, will this bring the swap memory closer and in turn the sysem might use a bit,

---

### Post by NightwishFan on 2008-04-27
Sorry I had to pick up some food, that is why I did not reply. They are correct above, you have swap and it is not using it means you have good performance. (Sweeney Todd owns by the way :KS)

---

### Post by sweeneytodd on 2008-04-27
Anyhow if anyone wants to know what my computer is, it is a dualcaore amd 4600+ 1Gbram 128mbvideo l2 cache 512kb each i think

---

### Post by Ptero-4 on 2008-04-27
What the others basically mean is that your swap isn't being used because you still have some of your physical ram available, which is good since it means that you've got plenty of ram in your computer.

---

### Post by Ptero-4 on 2008-04-27
****. My DSL modem windows'd on me when I was posting.

---

