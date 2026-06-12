---
title: "poppler utils - Identify images giving transparent/shadow effect"
date: 2017-02-14
forum: General Help
---

### Post by amitsavani on 2017-02-14
I am using poppler utils' ```
pdftohtml -xml
```  It extract all images and refer them in generated xml. Few images are used to give a shadow effect to the images.

Can anybody tell how to differentiate images which are used to such effects? Basically I want to delete all such images.

Please refer [http://press.nationalgeographic.com/files/2016/04/May-2016-Highlights-grid-copy.pdf](http://press.nationalgeographic.com/files/2016/04/May-2016-Highlights-grid-copy.pdf). pdftohtml extract 9 images out of which only 4 colorful  images are useful for me.

I used ```
pdfimages -list
``` to get details of images which give me some info that could to differentiate such images. I identified color, comp and ratio info.But  color data cannot help here because I have [another PDF]("https://www.dropbox.com/s/i41vj9sngek7naj/AUSTIN.pdf?dl=0") where many images are gray scale having no shadow/special effects but are useful.

Basically I want to extract text and images and place image annotations(eg. [image]path to image[/image] to relevant(nearest) text for each image in the text file. I am using pdftotext and pdftohtml -xml to achieve this. I could place images annotations in text file with 50% + accuracy that is good for now. My immediate problem is to remove unusable images.

---

### Post by dragonfly41 on 2017-02-14
Could you run a script to sort the jpg images by size and choose the top 4 in size?
The shadow images seem to be small (under 20kb).
If sorting by size is too crude a filter, one more thought is cycle through all images using an image scanner such as Sikulix to eliminate targets with shadow?

---

