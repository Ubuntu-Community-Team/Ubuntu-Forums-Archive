---
title: "ubuntu 18.10 cursor edited"
date: 2019-03-08
forum: General Help
---

### Post by tropicaner1978 on 2019-03-08
[SIZE=5][FONT=arial narrow]Dear people![/FONT]

[FONT=arial narrow]Afterwards a long work I got a large big cursor which is pretty easy to see. [/FONT]

[FONT=arial narrow]Laptop:     DellG5 / 15-5587 [/FONT]
[FONT=arial narrow]System:    64-bit[/FONT]
[FONT=arial narrow]Ubuntu:    18.10 Gnome 3.30.1 [/FONT]
[FONT=arial narrow]Graphic:   GeForce GTX 1050/PCIe/SSE2 [/FONT]
[FONT=arial narrow]Prozessor: Intel® Core&#8482; i5-8300H CPU @ 2.30GHz × 8[/FONT]

[FONT=arial narrow]But I don't know exactly how I solved it. I tried a lot. It is the red cursor which comes with the system installation. I had no chance to install any other cursor theme. I am thankful I solved it. To fix the two different cursor I used this code: [/FONT][/SIZE][SIZE=5][FONT=arial narrow]
[/FONT][/SIZE]
[SIZE=5][FONT=arial narrow]sudo sed -ri 's/DMZ-White/Redglass/g' /usr/share/icons/default/index.theme[/FONT][/SIZE]
[SIZE=5][FONT=arial narrow]compiz --replace  [/FONT][/SIZE][SIZE=5][FONT=arial narrow]I got this error:   compiz (decor) - Warn: No default decoration found, placement will not be correct

[/FONT]I solved it with:  reboot. 
Thankfully it worked to my best. 

[FONT=arial narrow]Kindly, if anyone can explain me, what I did, many others visually impaired user would be lucky, too. It would be really useful, if the programmer would think about large cursor more. I think, the cursor doesn't appear on the photo. I took it to show how large it is. 

Thank you very much for your help[/FONT][/SIZE]

---

### Post by Dennis N on 2019-03-08
Another way to enlarge the cursor in Ubuntu is:

Settings > Universal Access > Cursor Size > (Choose Size)

This works with resizable cursors, including redglass, DMZ-White, DMZ-Black

---

