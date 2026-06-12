---
title: "Error On Load (Video Included)"
date: 2007-05-09
forum: General Help
---

### Post by whinub on 2007-05-09
Hey I just installed Wubi and am looking forward to runnign linux but after rebooting on Ubuntu i get this

[http://www.youtube.com/watch?v=NFeg1ItKneg](http://www.youtube.com/watch?v=NFeg1ItKneg)


Any help is appreciated

---

### Post by ago on 2007-05-09
Try appending "noapic nolapic acpi=off" to all the kernel lines in c:\wubi\boot\grub\menu.lst

---

### Post by whinub on 2007-05-13
How can I differentiate between between kernel lines and other lines?

---

### Post by ago on 2007-05-13
Append the above to all lines that start with "kernel"

---

### Post by whinub on 2007-05-13
Thanks, I did as you said but then  I booted it up and this time the scrolling thing kept going...is that normal? how long should i leave it like that? Thanks again for putting up with me.

---

### Post by whinub on 2007-05-16
Anyone?

---

### Post by ago on 2007-05-17
Can you be more precise in describing what is happening at the moment?

---

