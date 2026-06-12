---
title: "Killall Gimp"
date: 2019-07-20
forum: General Help
---

### Post by raleigh3 on 2019-07-20
Despite my saving images in Gimp, it shows a dialog box(Do you wanna save...) whenever I exit the program.

I consider that annoying at best, a bug at wor**.

Would it be ok, to do the following ?

killall gimp

Is there any things bad that can happen?

Thanks.

---

### Post by cruzer001 on 2019-07-21
Bet your using the "export" function to save a image to a foreign format.  It will then prompt you to save in standard gimp format (xcf) when closing.  Not a bug, built that way.

Guess you can use the kill command, never tried it.

---

### Post by ajgreeny on 2019-07-21
But there is still no need to use **killall** to close gimp; just shut it down in the usual way with the close X top right and choose "Discard changes" when you get that dialogue-box.

If you export the image first as a jpeg or png or anything else gimp still suggests you save the image as a xcf, something I have never done as far as I can remember as it is much more useful to save an image that is more generally able to be opened by other applications or viewers.

---

### Post by cruzer001 on 2019-07-21
Could create your own shortcut key for this.  I don't see anything wrong with using killall, except maybe forgetting to save (export) first and then its gone forever.

---

