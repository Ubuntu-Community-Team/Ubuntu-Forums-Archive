---
title: "i560 prints only part of page with GIMP of inkscape"
date: 2006-12-08
forum: General Help
---

### Post by johanjpk on 2006-12-08
Hi, 

I have this strange printing problem. I have a Canon i560 installed with drivers from here: [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/) 
It works really well when I get the gnome dialog. But with GIMP and inkscape i have to print with this command: |lp  -d 'PIXUS-560i-ver.2.4'   
It works, but the problem is that it can only print on a part of the page, like the first 10 cm (4 inch) of the page. It is not that it stops but is like the drawing is moved to the top of the page. Very strange and I think it is not a big problem (I hope). I think the options are not set right or something. Could you give me a hint? 

Johan

---

### Post by johanjpk on 2006-12-08
Solved... 
I tried to put the size in de lp command but I needed to do this: 
lpoptions  -d 'PIXUS-560i-ver.2.4' -o PageSize=a4 

Johan

---

