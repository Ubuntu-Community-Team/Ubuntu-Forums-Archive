---
title: "XGL edge flipping"
date: 2006-08-24
forum: General Help
---

### Post by compwiz18 on 2006-08-24
Is there a way to turn of the way XGL/compiz flips around the cube if I put the cursor on the side of my screen and flip the wheel? It's going to drive me crazy... ](*,)

---

### Post by hopstah on 2006-08-24
open up gconf-editor

apps > compiz > plugins > rotate > allscreens > options

scroll down to rotate_left_wheel_button and rotate_right_wheel_button and change both values to 'Disabled'

---

### Post by compwiz18 on 2006-08-25
Thank you, worked great :D

---

### Post by closet geek on 2006-08-27
I have just tried the solution in this thread and it hasn't worked? Any ideas why?

cg

---

### Post by closet geek on 2006-08-28
Bump - has anyone else had problems disabling this via gconf?

cg

---

### Post by beerorkid on 2006-08-28
apps > compiz > plugins > rotate > allscreens > options

uncheck the top 3 boxes
edge_flip_dnd
edge_flip_move
edge_flip_pointer

or find the combo you like of the three

---

### Post by closet geek on 2006-08-29
Thanks, but that doesn't stop the cube from rotating when I scroll using the middle mouse wheel near the edge of the screen. My ideal setup would be for this behaviour to happen on the right, but not the left, edge. However even though I've followed the steps in this thread it still rotates on both edges when I scroll...

cg

---

### Post by beerorkid on 2006-08-29
> **closet geek said:**
> Thanks, but that doesn't stop the cube from rotating when I scroll using the middle mouse wheel near the edge of the screen. My ideal setup would be for this behaviour to happen on the right, but not the left, edge. However even though I've followed the steps in this thread it still rotates on both edges when I scroll...

cg

ahhhhhhh.... OK just a little more and you will be set, did not read very well apparently ;)

ok same place as before: apps > compiz > plugins > rotate > allscreens > options

you will need to know what buttons ubuntu thinks your mouse wheel is.  Roll up is #(mine 5), roll down is #(4).  to find out open a terminal and enter this:
```
xev
```
it will open up a little box, put your cursor in there and try to keep it steady (you will see why).  Roll the mouse up, then down, and look in the terminal for something like this:
```
ButtonRelease event, serial 31, synthetic NO, window 0x4200001,
    root 0x52, subw 0x0, time 1518474378, (47,122), root:(1254,207),
    state 0x1010, ****button 5****, same_screen YES
```  that will tell you the "buttons" of the scroll wheel.  mine was 5

now in the config editor edit rotate_right_wheel_button  same for left.
double click it to enable editing it.
just delete what is in there.

so with all this info you should be able to configure it any way you like.

---

### Post by closet geek on 2006-08-30
Thanks for your help, but as I said it's having no effect what-so-ever. Before reading your post I had Disabled in there. Now I have nothing and yet the cube still rotates when I go near the edge of my screen and use the middle scroll button. Argghhh!

cg

---

### Post by beerorkid on 2006-08-30
it might be possible updates to compiz reset them.
Once you get it to how you like it, you can comment out the compiz repo to avoid updates.

I just tested the setting out again and when I change them it works.  So I am a little confused why yours is not working.

---

### Post by closet geek on 2006-08-30
Could it be due to the fact I installed Compiz/XGL using Automatix Bleeder? I really can't see how this could be so but I'll mention it just incase.

In fact most gconf settings seem to have no effect, however gset-compiz stuff works but then it's nowhere near as comprehensive as gconf.

cg

---

### Post by beerorkid on 2006-08-30
well I did mine with bleeder as well, it is just sooooo easy.
it might depend on what version bleeder was on when you installed it, cuz they have changed it a bit I think.  

It is strange cuz when I mess with the edgeflip in gset-compiz it has no effect, and the settings do not stay.

I thought gset-compiz was not being worked on any more, but I see it is back in the repo.

sorry I cant help though :(

---

### Post by closet geek on 2006-08-31
No worries! I'll just have to put up with it I guess.

cg

---

### Post by simoncoul on 2006-09-01
If you change the default keys for any of the settings in the scale plugin it will turn edge flipping on again when compiz is restarted.   Use the "unset key" when you right click the binding setting to all the bindings, then remove the topedge, bottomedge.... and then close it and it will stay.

---

