---
title: "resizing images maybe with convert"
date: 2020-03-15
forum: General Help
---

### Post by Skaperen on 2020-03-15
i have a large bunch of images with varying sizes.  there are many different widths and many different heights.  i want to make each image 1/4 the original size.  but the **convert** command wants me to enter the exact final geometry.  **does anyone have a good way to do this?**  the images are in JPG and PNG formats.

---

### Post by freebird54 on 2020-03-15
Not sure what you're looking for, but the convert that I use (Imagemagick) doesn't require BOTH sides of the sizing command. In fact it is perfectly happy with a percentage. As an example:

original.jpg 1920X1080
so
*convert original.jpg -resize 25% output.png*
would give you a pic converted from a 1920x1080 jpg to a 480x270 png without having to figure the other side out, effectively 1/4 the size. With oddball resolution numbers much work is avoided! As for automating - I'll leave that as an exercise for the reader... :) 
( a bash for loop should handle it nicely)

Freebird54

---

### Post by Skaperen on 2020-03-16
that works.  percentage is useful.  i didn't see that in the man page.

---

### Post by freebird54 on 2020-03-16
I just looked at the man page, and I'm not surprised! I couldn't find anything there either...

I tend to just find out about the things I need it to do, and I use the "I wish it did this" method of feature discovery - so far it has never let me down :) 

For this, a google of linux imagemagick percentage will get you all you need - or lead you down the rabbit hole of things it can do that you're unlikely ever to need...

Freebird54

---

