---
title: "cups usb printing hogs cpu"
date: 2006-08-06
forum: General Help
---

### Post by ggw10 on 2006-08-06
I have a machine which I have connected to an Epson Stylus Photo R2400 
via usb. I also have an HP Laserjet 1300 printed to it via a parallel
port. Printing on the HP is fine, but when I try to print a test
page on the Epson, what happens is that
i) the load average goes up to 5.52
ii) over 90% of the cpu load is taken up by the usb cups backend
iii) gs-esp, which previously used to be a cpu hog, has been pushed down
to 2% of cpu
iv) In consequence, printing is extremely slow. 

All of this has happened since I updated to cupssys 1.2.2-0ubuntu0.6.06 

So, I have three questions here:
i) what is going on?
ii) how do I revert to a version of cups which actually works?
iii) which Linux versions have printing that works? 

I am not going to report this as a bug: I have previous spent a lot of
time reporting a load of ubuntu printing bugs, with no effect.

---

### Post by nix4me on 2006-08-06
Thats the wrong attitude.  You should report the bug as soon as possible.  How else do you expect it to get fixed?

nix4me

---

