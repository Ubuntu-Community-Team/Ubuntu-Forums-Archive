---
title: "File is wouldn't Open with app"
date: 2008-03-09
forum: General Help
---

### Post by Ioky on 2008-03-09
Just few day ago, I realize sometime I can't open a file with any app. no matter it is a PDF, OGG, MP3 or what so ever. I just don't know what goes wrong, and Don't know where to check, I mean it is good to know what is going on. and lucky be able to fix it. 

Anyway, 8.04 come out in like a month or so. Looking forward to that. hope it gives less trouble than 7.10. 7.10 is like the worst version of ubuntu I have even use. Hope they can done better... and support ubuntu as always. excited too hehe

---

### Post by erginemr on 2008-03-10
This may or may not work, but...

1- You can try right-clicking on that file and check its owner and permissions. (You should at least have read permissions on it.)

2- You can also try right-clicking on that file again, select "properties" and choose "open with" tab to select the application to open it.

---

### Post by Ioky on 2008-03-15
no it is just simply wouldn't open, there is nothing to do with permission or anything because it is not just about one or two file, it is like all the file wouldn't open with any software. unless, you restart X

---

### Post by ibuclaw on 2008-03-15
> **Ioky said:**
> Anyway, 8.04 come out in like a month or so. Looking forward to that. hope it gives less trouble than 7.10. 7.10 is like the worst version of ubuntu I have even use. Hope they can done better... and support ubuntu as always. excited too hehe

I find this rather shocking, since 7.10 was the first version of Ubuntu that I was happy enough to migrate to. I myself coming from a Debian background, I've always seen Ubuntu as incomplete or not good enough/stable enough.
8.04 looks very exciting indeed, and I'm planning on installing it as soon as it comes out, and then keep it has my system/repository for the three year service. I'm going through some busy times and what I need at the moment is consistancy. :)

But back to your problem. Have you tried custom commands?

ie: on a file called "testfile.txt" you Right Click>Properties>Open With and click the Custom Command and enter in
```
 gedit %s 
```
where gedit can be replaced for the program you want it to open with and keep %s in the command, as that will pass the filename that you click on to the program.

Iain

---

### Post by Ioky on 2008-03-15
No, not yet, I will try it next time when this problem occur. though I have no idea when will it happen again.

---

