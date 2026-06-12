---
title: "hangs at Creating User  (was: failed.....or? ahhh)"
date: 2005-05-25
forum: General Help
---

### Post by vega44 on 2005-05-25
i got the live cd to start every thing was working fine.... into i got to creating user... 

it got to 63% of creating user... and it never went on...? i let it sit for 10 or 15 minits and it just stood there? what is wrong?

this is my pc specs  [http://www.pcpitstop.com/techexpress.asp?id=YBGTNWCN0RQS0JA6](http://www.pcpitstop.com/techexpress.asp?id=YBGTNWCN0RQS0JA6)

---

### Post by jdong on 2005-05-25
MOVED to LiveCD forum.

Can you try reburning it? sometimes it's just a bad burn.

---

### Post by vega44 on 2005-05-25
[QUOTE=jdong]MOVED to LiveCD forum.

Can you try reburning it? sometimes it's just a bad burn.[/QUOTE]
well, i did it and it stops at creating user.... 63% again.

---

### Post by vega44 on 2005-05-25
[QUOTE=lowlux]well, i did it and it stops at creating user.... 63% again.[/QUOTE]
does any one know?

---

### Post by vega44 on 2005-05-26
[QUOTE=lowlux]does any one know?[/QUOTE]
bump  ](*,)

---

### Post by jdong on 2005-05-26
Please don't bump your threads, especially when it was the 3rd from the top anyway!


It takes time for someone to answer such a vague problem. Switch consoles with ALT+F1 through F8. Do any of the screens give any useful error messages?

---

### Post by vega44 on 2005-05-26
[QUOTE=jdong]Please don't bump your threads, especially when it was the 3rd from the top anyway!


It takes time for someone to answer such a vague problem. Switch consoles with ALT+F1 through F8. Do any of the screens give any useful error messages?[/QUOTE]
i just tride that...... every thing just stood there. not moving

---

### Post by jdong on 2005-05-26
Try booting with **livecd nodma nocddma noapic nolapic verbose**

---

### Post by vega44 on 2005-05-26
[QUOTE=jdong]Try booting with **livecd nodma nocddma noapic nolapic verbose**[/QUOTE]
now im lost........  =;

what does all that mean?

---

### Post by jdong on 2005-05-27
Type this at the BOOT: prompt; these are pretty common options for disabling various features of the BIOS.

The first two turns off all DMA support. The next two turn off the APIC, which is only necessary on multi-processor systems (a more efficient interrupt balancer). The last one makes the kernel spit out more error messages.

---

