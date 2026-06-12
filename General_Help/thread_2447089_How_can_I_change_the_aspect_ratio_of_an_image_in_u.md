---
title: "How can I change the aspect ratio of an image in ubuntu 18.04?"
date: 2020-07-12
forum: General Help
---

### Post by EngineerStrange on 2020-07-12
How can I change the aspect ratio of an image in ubuntu 18.04?

---

### Post by Dennis N on 2020-07-12
Use Gimp:

Image > Scale Image

Unlink the height and width (click icon to right of height and width settings), then you can change height and width independently, altering the aspect ratio.

---

### Post by cmcanulty on 2020-07-12
I have had great luck with several HP laptops

---

### Post by SeijiSensei on 2020-07-12
If you just change the aspect ratio without any sort of cropping it will not look right.  For instance, if you were trying to take a 4:3 image and make it 16:9 it would be horribly stretched.  Rather you would need to cut a 16:9 rectangle out of the 4:3 image then rescale the cutout.   So you'd be cutting out the area inside the box in this image:

[img]https://www.takinganimeseriously.com/images/upscale-example-with-box.jpg[/img]

GIMP has excellent tools for these tasks. You can set the horizontal selection tool to a specific aspect ratio to designate the area to capture.  Once selected, Edit > Copy > Edit > Paste As > New Image will give you a new image with the material inside the selection.

---

