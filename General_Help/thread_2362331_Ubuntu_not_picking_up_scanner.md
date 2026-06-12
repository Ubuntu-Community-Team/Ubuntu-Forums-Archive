---
title: "Ubuntu not picking up scanner"
date: 2017-05-26
forum: General Help
---

### Post by agemini68 on 2017-05-26
I got a print-scan-copy, HP Deskjet 2652. The printer is working great, but I get scanner not found when I try to scan something. How do I get this to work?

---

### Post by agemini68 on 2017-05-26
The Scanner does work with my android, but it's a pain in the butt when I can't send it to my computer.

---

### Post by ajgreeny on 2017-05-27
What version of hplip do you have installed?  I can not find the exact model on the hplip site; the nearest is [http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_2640_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_2640_series.html) which may be OK, but only you can test this.

What application are you using to search for the scanner.

---

### Post by agemini68 on 2017-05-28
I will check that out. For the scanner, I tried simple scan and one called Aquire Image, neither could find the scanner. I was wondering if it had to do with the shared USB port

---

### Post by ajgreeny on 2017-05-28
> **agemini68 said:**
> I will check that out. For the scanner, I tried simple scan and one called Aquire Image, neither could find the scanner. I was wondering if it had to do with the shared USB port
That could certainly be the problem as shared USB connections or USB hubs can often upset connection of devices.

---

### Post by pqwoerituytrueiwoq on 2017-05-28
If it works directly with the computer you could share the scanner via the network, if you want to go that rout there is a link in my signature

---

### Post by agemini68 on 2017-05-29
Okay, I'm not a computer expert by any means. I'm reading through PHP Scanner server and I'm just confused.

---

### Post by agemini68 on 2017-07-01
Is there a simpler solution?

---

### Post by sp40140 on 2017-07-02
I have Brother All in one. I am not sure about Aquire Image. But I had to run "simple scan" with sudo for it to detect the scanner. But the proper drivers have to be installed beforehand.
You only need to run this the first time. Once the scanner is detected, you don't need to run it with sudo everytime.
Command:
```

gksudo simple-scan

```
or install "xsane".

---

### Post by Autodave on 2017-07-02
xsane is worth trying. I have had luck with that when all else has failed.

---

### Post by agemini68 on 2018-04-16
I upgraded to 18:04 Beta, that picks up both functions of my all in one.

---

