---
title: "glxgears: No output"
date: 2006-12-25
forum: General Help
---

### Post by Xyem on 2006-12-25
I am attempting to get Beryl to run on my laptop. I know it will be painfully slow ( running on a [ lspci output ] Neomagic Corporation NM2360 [MagicMedia 256ZX] ) but I think it would be interesting to see what results.

I have selected 'neomagic' as my device driver and glxinfo says direct rendering is a no-go. If I try and run glxgears it 'stutters' but I am not using this as an indicator as it 'stutters' on my nVidia 5700LE on my desktop. The thing is, glxgears is meant to output every 5 seconds its framerate. On my machine it is outputting nothing at all. ](*,)

Has anyone else had this problem? Any ideas as to a solution?
Thanks

---

### Post by pay on 2006-12-25
If you don't have direct rendering then you can't use beryl (unless if you're using xgl, then I **think** it comes up as false).

---

### Post by Xyem on 2006-12-25
Heh, it gets quite far ( window decorations vanish, beryl splash appears ) before X resets :)

Still the issue with no output from glxgears..

---

### Post by cjazz on 2006-12-25
Try

glxgears -printfps

---

### Post by r4ik on 2006-12-25
> **cjazz said:**
> Try

glxgears -printfps

Works thnx !

---

### Post by Xyem on 2006-12-25
Heh, seems Ubuntu does *everything* different from what I have experienced with Linux so far. Not that that is inherently a bad thing, of course.

I ran that and got 60~90 fps ( Stupid keyboard layout is wrong ](*,) ) which is nowhere near what it *looks* like it is running ( more like 0.75 fps ).

I am not sure if this is related or not but I ran an OpenGL test that I made ( SDL/Perl ) and it gives some very strange results. Firstly, on this very machine, in Windows it runs smoothly, no problems. On Ubuntu, it seems to run at about 1 frame a second and the window decorations are garbled. I would include a screenshot but I am currently trying to find the "Take a screenshot" button or shortcut or *something..* :p

EDIT:
Found the screenshot panel item.
Changed my xorg so that
-> keyboard layout is now correct
-> I am using the vesa driver for my neomagic chip instead of the neomagic one
--> my test program now runs fine for the first 3 seconds and then "stutters" badly. glxinfo now produces the error > X Error of failed request:  BadAlloc (insufficient resources for operation)

---

