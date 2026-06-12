---
title: "Automatic image stitching software?"
date: 2024-06-03
forum: General Help
---

### Post by fire-chicken-2 on 2024-06-03
Is there something in Ubuntu that I can run on several hundred overlapping images that will stitch them together automatically for me?

I know that there is software out there that can create a 3d model out of a bunch of images... I assume / hope that there is something that can assemble multiple 2D images into one big image

---

### Post by fire-chicken-2 on 2024-06-03
Sorry, my Google-Fu is weak.
So I learned that the proper term is "photo merging".
I also learned that image magik can do it Horizontally and Vertically... but I still need something else that can do both horizontally AND vertically automatically at the same time.

---

### Post by fire-chicken-2 on 2024-06-03
I tried fotoxx. Total FAIL! can't even correctly horizontally combine 4 simple images of a circuit board

---

### Post by currentshaft on 2024-06-03
PTGui, Hugin, AutoStitch all look promising and mostly open source. ImageMagick might have some options to do this as well.

---

### Post by fire-chicken-2 on 2024-06-03
Hugin was a fail.

I keep seeing one common theme here. Panoramas. Hugin tries to map my images onto a Sphere ( very poorly BTW )
I'm not dealing with panoramas. I'm dealing with flat 2D images that simply need to be stitched together properly.

Specifically I'm taking like 300 pics of a circuit board under a microscope and need them auto merged together to make one giant image of the board.

Still checking out the others that you suggested.
As previously mentions ImageMagick can only merge in one direction ( horizontal or vertical ). I need both, at the same time.

---

### Post by currentshaft on 2024-06-04
You could probably write a short Python program using the Pillow library (PIL) if the images are similar and a predictable pattern ...

Edit:
Here's a quick little ditty, will do 12 images in 3 colums and 4 rows. 
No warranty, use at your own risk!

```

import glob
from PIL import Image

filenames = sorted(glob.glob("*.jpg"))[:12]
images = [Image.open(filename) for filename in filenames]
width, height = images[0].size
output = Image.new("RGB", (width * 3, height * 4))

for i in range(4):
    for j in range(3):
            output.paste(images[i*3 + j], (j*width, i*height))
            output.save("output.jpg")

```

---

### Post by phatton1 on 2024-06-04
I always use hugin. Easy to use and works well

---

