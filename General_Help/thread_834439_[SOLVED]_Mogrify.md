---
title: "[SOLVED] Mogrify"
date: 2008-06-19
forum: General Help
---

### Post by DarkWinterNights on 2008-06-19
Good afternoon.

I was hoping someone might know how to use mogrify to scale a batch of images by their height.

I know for scaling by width I could use something like
[INDENT]mogrify -resize 640 *.jpg[/INDENT]

and if I wanted to give the exact specifications use something like
[INDENT]mogrify -resize 640×480! *.jpg[/INDENT]

But I'm uncertain how to do so for the height of the images.  Sure, I could rotate them 90' and then rotate them back after the operation, but it would be more convenient to simply know the correct execution of the command.

Thanks for your input in advance.  :)

E:  Bleh.  I meant to make that topic more specific, but I guess I must have erased the earlier parts without thinking about it.  My apologies.

---

### Post by manfer on 2008-06-19
I don't know how imagemagick and how that mogrify command works. I haven't yet use it. For that reason I can't tell you if there's options for the command to do that scaling by height you want the same way as there is an option to do it by width as you explain.

But if you know how to do it by width, and if you have options for rotation, why don't you just rotate clockwise, do it by width, and rotate it counter-clockwise?

rotate 90º ; scale by width ; rotate -90º

Lol, I think this solution was not on your message before. Or maybe I didn't read it carefully.

---

### Post by manfer on 2008-06-19
The correct way is this:

If only the width is specified, the width assumes the value and the height is chosen to maintain the aspect ratio of the image. Similarly, if only the height is specified (e.g., -resize x256, the width is chosen to maintain the aspect ratio.

mogrify -resize x480 *.jpg

---

### Post by DarkWinterNights on 2008-06-20
Ah, yes, that's exactly what I hoped to learn.

I would have continued with the rotating image, but since I tend to deal in large batches of files, I would rather just use the one command, go grab a coffee, and return.  :)

Thanks for your help.

---

