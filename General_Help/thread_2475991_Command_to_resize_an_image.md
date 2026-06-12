---
title: "Command to resize an image"
date: 2022-06-14
forum: General Help
---

### Post by satimis on 2022-06-14
Please advise how to resize an image on Terminal?

Original size: 4092(w) x 1960(h)

Final size: 2527(w) x 1815(h)

Thanks

Regards

---

### Post by ajgreeny on 2022-06-14
The simplest answer is to install imagemagic if not already on your system then read ***man co vert*** to get full details of how to use it.

Very quick and simple with many options available.

---

### Post by yancek on 2022-06-14
You can use the convert command from Imagemagick as explained in the link below.

[https://www.howtogeek.com/109369/how-to-quickly-resize-convert-modify-images-from-the-linux-terminal/](https://www.howtogeek.com/109369/how-to-quickly-resize-convert-modify-images-from-the-linux-terminal/)

---

### Post by satimis on 2022-06-14
Hi,

I got it done.  Thanks.

A further question;
Can I use IM to crop image?

Example:
I start GIMP to crop the image

Original image: 4032x1960
Cropped image: 2527x1915

Pls refer to attached photos

Thanks

Regards

---

### Post by Holger_Gehrke on 2022-06-14
Of course IM can crop.
```

convert -crop widthxheight+xoffset+yoffset infile outfile
example
convert -crop 2527x1915+300+20 image.png cropped-image.png

```
See the ImageMagick documentation for all the details on the geometry specification you can give, there's a lot of possibilities there beyond the simple case I give.

Holger

---

### Post by Dennis N on 2022-06-14
Just wondering why you would look for terminal commands to resize or crop an image, rather than using a capable GUI application (gthumb, for example)?

---

### Post by satimis on 2022-06-14
> **Holger_Gehrke said:**
> Of course IM can crop.
```

convert -crop widthxheight+xoffset+yoffset infile outfile
example
convert -crop 2527x1915+300+20 image.png cropped-image.png

```
See the ImageMagick documentation for all the details on the geometry specification you can give, there's a lot of possibilities there beyond the simple case I give.

Sorry, no.
```

$ convert -crop 2527x1915+300+20 original.jpg original_crop.jpg 

```

The result is completely different to that I did on GIMP.  Please refer to attached photo

I have tried it before posting.  I don't know how to find x and y starting point

Regards

---

### Post by satimis on 2022-06-14
> **Dennis N said:**
> Just wondering why you would look for terminal commands to resize or crop an image, rather than using a capable GUI application (gthumb, for example)?
Yes, for several images I can do it on GIMP.  But for hundreds of images I need to perform batch cropping.

I'm going to scan old photos on smartphone.  All scanned images will be similar to the original image on my OP.  I need to crop them afterwards.

Regards

---

### Post by TheFu on 2022-06-14
> **Dennis N said:**
> Just wondering why you would look for terminal commands to resize or crop an image, rather than using a capable GUI application (gthumb, for example)?

Because you need to do it for 1000-100,000 files?

---

### Post by Holger_Gehrke on 2022-06-14
You didn't mention that the image needs rotation, too, so I didn't rotate it in my post. I played around with your posted image a bit and using some of the additional tricks possible with geometry-specifications in ImageMagick arrived at
```

display -rotate 90 -gravity center -crop 69%x98.5%-5%+1% original30.jpg

```
As you can see I used relative sizes (that's what the '%' means) and set the gravity to center (which actually means that I set the point from which all these measurements are calculated to the middle of the image). 'display' is another part of the ImageMagick family, it takes the most of the same options as convert and mogrify, so it's a great way to preview what a combination of options will do. With a bit of tweaking these options should be pretty close to what you need.

Holger

---

### Post by satimis on 2022-06-14
> **Holger_Gehrke said:**
> You didn't mention that the image needs rotation, too, so I didn't rotate it in my post. I played around with your posted image a bit and using some of the additional tricks possible with geometry-specifications in ImageMagick arrived at
```

display -rotate 90 -gravity center -crop 69%x98.5%-5%+1% original30.jpg

```
As you can see I used relative sizes (that's what the '%' means) and set the gravity to center (which actually means that I set the point from which all these measurements are calculated to the middle of the image). 'display' is another part of the ImageMagick family, it takes the most of the same options as convert and mogrify, so it's a great way to preview what a combination of options will do. With a bit of tweaking these options should be pretty close to what you need.

Holger
Thanks for your advice.  No, the image is in right direction, no need to rotate.

Following command works for me.
```

$ convert -rotate 90 -gravity center -crop 69%x98.5%-5%+1% original.jpg original_crop.jpg

```

But I have to rotate the output image -90 again

Please explain 69%x98.5%-5%+1%
What are their functions?
How to get their values?

Thanks

Regards

---

### Post by HermanAB on 2022-06-14
Hmm, you can play *20 Questions* on the forum, or you can read the man page.

Linux man pages are online too, so you could simply type *man convert * in a web browser and click the first link.

---

### Post by Holger_Gehrke on 2022-06-14
> **satimis said:**
> 
Please explain 69%x98.5%-5%+1%
What are their functions?


69% width of the original image, 98.5 % height, with the reference point (set by '-gravity center' to the middle of the image) moved by 5% of the width to the left and 1% of the height down. I arrived at these values experimentally with repeated runs of 'display' with these options.

@HermanAB: the man page wouldn't be very helpful for this. It just says '-crop geometry - cut out a rectangular region of the image'. One needs the full ImageMagick documentation as either found in the package imagemagick-6-doc (and good luck reading html documentation in /usr/share/doc/ with a browser from a snap ... I'm currently re-learning using eww (web-browser built into emacs) for the express purpose of reading local documentation ...) or online at [https://legacy.imagemagick.org/Usage/](https://legacy.imagemagick.org/Usage/) . Neither is exactly meant for quickly finding this kind of information. It takes some familiarity with the format of the documentation to find the specs for an ImageMagick geometry and then it stretches on for several screens full of details ...

Holger

---

### Post by TheFu on 2022-06-14
> **HermanAB said:**
> Hmm, you can play *20 Questions* on the forum, or you can read the man page.

Linux man pages are online too, so you could simply type *man convert * in a web browser and click the first link.

+10. 

or use **xman** <---- like my forums image says. This way you'll see the answers based on the exact version of the program installed on your system.
And if you need an explaination for what each part does, there's explainshell.com  But explainshell doesn't seem to know about imagemagick stuff, so it is of limited use in THIS situation, but very handy for commands like **find**.

---

### Post by satimis on 2022-06-14
> **Holger_Gehrke said:**
> 69% width of the original image, 98.5 % height, with the reference point (set by '-gravity center' to the middle of the image) moved by 5% of the width to the left and 1% of the height down. I arrived at these values experimentally with repeated runs of 'display' with these options.

@HermanAB: the man page wouldn't be very helpful for this. It just says '-crop geometry - cut out a rectangular region of the image'. One needs the full ImageMagick documentation as either found in the package imagemagick-6-doc (and good luck reading html documentation in /usr/share/doc/ with a browser from a snap ... I'm currently re-learning using eww (web-browser built into emacs) for the express purpose of reading local documentation ...) or online at [https://legacy.imagemagick.org/Usage/](https://legacy.imagemagick.org/Usage/) . Neither is exactly meant for quickly finding this kind of information. It takes some familiarity with the format of the documentation to find the specs for an ImageMagick geometry and then it stretches on for several screens full of details ...

Holger
Hi,

Lot of thanks for your explanation and your time spent helping me.  So to get those values is not based on calculation but on experiment.

Now I have another photo scanned on smartphone.  Pls refer to attached photos;
1. original
2. cropped on GIMP

I tested cropping on IM command as follow;
$ display -rotate 90 -gravity center -crop 95%x68%-0%+5% paa_32_linz.jpg

Is it correct?  Still I'm not very clear of the function -0%+5%

In these 2 months I have been searching online to find documents re explanation on the use of ImageMagick without result.  Also I have subscribed their discussion forum;
[https://github.com/ImageMagick/ImageMagick/discussions/](https://github.com/ImageMagick/ImageMagick/discussions/)

I have been asking their forum for documents re using IM with examples of illustration but without result.  In reply they said that they don't have such documents.

IM is a powerful application but we need documents guiding us to use this powerful application.

Regards

---

### Post by Holger_Gehrke on 2022-06-15
[This part of the ImageMagick documentation]("https://legacy.imagemagick.org/script/command-line-processing.php#geometry") explains the geometry type of parameter that '-crop' and several other options to IM take. The '-0%+5%' is an offset, it moves the cropped region in the image from the center of the image down by 5. According to the documentation the '%' in offset values is useless, offsets are always in pixels. Sorry, my mistake ...

The man pages to all the ImageMagick commands have links to the online documentation in the section 'OVERVIEW'. The problem with these is that they lead to the current version of the documentation (ImageMagick 7) while the version in the repositories is still version 6.x which is documented at [https://legacy.imagemagick.org](https://legacy.imagemagick.org) . There's plenty of examples and details in that documentation. The real problem is finding the relevant parts in all that information.

Holger

---

### Post by TheFu on 2022-06-15
To read local HTML documentation, I use lynx or dillo browsers.  About 5 yrs ago, most of the so-called "modern" browsers made opening local HTML files much harder. I think they did this for security reasons.  I happened to be using HTML + Javascript to create presentations with pandoc (easier to publish on the web that way) and noticed this change.  Chromium actually requires a special command option to allow it.

---

### Post by Holger_Gehrke on 2022-06-15
@TheFu: with Firefox as a snap it goes beyond annoying: you can load a file with ctrl-o or enter a 'file://'-url into the address-bar and it will actually load (as far as I can tell it copies the selected file - and only the selected file, so no external scripts, external style sheets, or external images - to /run/user/$(id -u)/doc/some-random-looking-8-hex-digits/filename) but of course it doesn't display right (remember: no style sheets, no scripts, no images ...) and if you try to follow a link you get a "file not found"-error. 

I'm not familiar with dillo, but prefer w3m to lynx and neither is a good way to read the ImageMagick documentation, which - by the nature of its topic - needs a lot of images. Since I quite often have emacs open anyway, splitting its window and doing M-x eww-open-file is fine for me (and before you ask - yes, emacs in a graphical environment can display images).

Holger

---

### Post by satimis on 2022-06-15
> **Holger_Gehrke said:**
> [This part of the ImageMagick documentation]("https://legacy.imagemagick.org/script/command-line-processing.php#geometry") explains the geometry type of parameter that '-crop' and several other options to IM take. The '-0%+5%' is an offset, it moves the cropped region in the image from the center of the image down by 5. According to the documentation the '%' in offset values is useless, offsets are always in pixels. Sorry, my mistake ...

The man pages to all the ImageMagick commands have links to the online documentation in the section 'OVERVIEW'. The problem with these is that they lead to the current version of the documentation (ImageMagick 7) while the version in the repositories is still version 6.x which is documented at [https://legacy.imagemagick.org](https://legacy.imagemagick.org) . There's plenty of examples and details in that documentation. The real problem is finding the relevant parts in all that information.

Holger
Thanks for your reply and links.

I have IM7 running on Ubuntu22.04 VM.  I installed it from source.  The operation differs to IM6 which is running on Ubuntu20.04 here.

I still have problem running batch processing to crop the scanned images because I can't place the photo in 100% exact position as its previous photo. Please refer to the attached photo of the fixture.  In the photo the plastic clips are for indexing.

BIMP and G'MIC, the plugin of GIMP, are also for batch processing of images.  Their advantage is able to see the photos.  But running IM command for batch processing I can't see the photo.

Following document is quite helpful to me;

How to crop an image using imagemagick convert
[https://infoheap.com/crop-image-using-imagemagick-convert/](https://infoheap.com/crop-image-using-imagemagick-convert/)

Regards

---

### Post by TheFu on 2022-06-20
As powerful as convert and imageMagick are, for simple rotations, I think jpegtran is the better choice. Rotations are lossless.

Convert works for nearly all image types. jpegtran is only for jpeg, so that could be a big issue. It does cropping, but not resizing, so convert will still be needed.
jpegtran is a filter, so the resulting output is sent to stdout and we need to redirect that to a file to be useful. Think that was covered in another thread.

---

### Post by bobunderwood99 on 2022-06-20
Perhaps a 4 blade enlarging easel would improve your setup.

---

