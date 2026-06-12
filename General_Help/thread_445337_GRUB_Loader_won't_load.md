---
title: "GRUB Loader won't load"
date: 2007-05-15
forum: General Help
---

### Post by peedeeramone on 2007-05-15
okay...

i was running ubuntu fine by itself (with a dead windows install)

in my futile attempts to restore a busted windows installation i messed with the MBR from the windowsxp cd (fixmbr maybe..?)

so basically it wouldnt boot at all after that so i tried to reinstall grub

the first time i did it didnt give me the typical grub loader i was used to (1.5 or something like that) it was more of a command line which i wasnt sure how to use but after a bit of research i figured it out

so basically long story short i have the loader up but it gives me an error saying the file cant be found or something

i have tried to manually set it up but the i dont particularly know where the kernel is located.

i am not a total linux n00b, ive used linux for about 4 or 6 months or so, but i am not used to the grub setup, as i have never messed with my grub setup manually.

i have seen a few articles saying to use a ubuntu live cd and go halfway through the install or whatever, but i dont have a live cd around, but i can get one in a few days. so if thats the easiest way to do it ill just live off a live cd untill then (im trying puppylive right now)

so yeah any help is much appreciated

let me know if i havent given enough information

---

### Post by confused57 on 2007-05-15
You "should" be able to reinstall grub with the puppy live cd, from a terminal:
```
grub
find /boot/grub/stage1
```
this should return your root partition, e.g. (hd0,1)...using this info, you would:
```
root (hdx,y)
setup (hd0)
quit
```

I believe you should be able to reinstall grub from any live cd.

---

### Post by peedeeramone on 2007-05-16
thanks for the reply,

that solution didnt really help me, but i was able to fix it, so thanks anyways

now i have another problem... sorta

more of a question: now i got it back booting into ubuntu, but i lost the ubuntu splash screen and i just look at the text as its booting

im sure theres a thread somewheres that explains how to put it back, but i looked a bit and couldnt find it.

also i thought i remember reading a way to make the grub loader screen all purrdy like with a picture and maybe some other things, but dont remember where i saw that

so basically just looking for some links is all, no real biggie, cuz im back in the buntu agaainn (im BAAAAKK)

---

