---
title: "Black screen windows 7 Ubuntu wont load"
date: 2013-02-06
forum: General Help
---

### Post by emptyvessal on 2013-02-06
Hi will keep this brief but any help would be very very very welcome!

Installed ubuntu on windows 7 using windows installer.
Worked fine.
The windows did a check disc and it was posting this

[B][URL="http://www.google.co.uk/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&ved=0CDIQFjAA&url=http%3A%2F%2Fbeconfused.com%2F2008%2Freplacing-invalid-security-id-with-default-security-id-for-file%2F&ei=VH0SUd7wDojB0gXF9oHYCw&usg=AFQjCNFSVTY2s0Hgc6Z-eex6KnK86UImtw&bvm=bv.41934586,d.d2k"]Replacing *invalid security* id with default security id etc 
[/URL][/B]


Now after reboot windows will not get past a black screen with just a cursor,  safe mode is the same and cant use cntrl alt del etc 

Ubuntu also wont load and just shows Grub tab for options etc ..........

I tried using the boot repair tool via the terminal and did the recomended setting to fix the boot for ubuntu but it did nothing.

So now i have windows 7 i cant run and also Ubuntu that i can only run using a Live cd i made.

I can see all my windows files through the ubuntu file manager but i cant save them as i dont have external drive my samsung turned into a brick.


If any one knows a solution that actual works please let me know.    Ubuntu 12.04   32 bit versions. windows 7 64 bit.

I realy losing it on this as nothing i try seems to fix the problem.

---

### Post by oldfred on 2013-02-06
So is this a wubi install inside the Windows NTFS partition that uses the Windows boot loader?
       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

