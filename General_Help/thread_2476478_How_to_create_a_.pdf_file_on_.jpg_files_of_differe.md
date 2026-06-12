---
title: "How to create a .pdf file on .jpg files of different sizes"
date: 2022-06-27
forum: General Help
---

### Post by satimis on 2022-06-27
Hi all,

Create PDF file.  On Terminal run
```

img2pdf *.jpg --output combined.pdf

```

But if the .jpg files are of different size, what command shall I run?

Thanks

Regards

---

### Post by #&amp;thj^% on 2022-06-27
First do you want them to be different size's
I'll use something like this:
```
sudo img2pdf image01.png image02.png -o output_img.pdf
```
img2pdf will need to be installed for this use.
Here is what it will look like in a random fashion: [https://drive.google.com/file/d/1gLFAjWKY4GuSZ8DwWWIvRjUQrUDNkXD2/view?usp=sharing](https://drive.google.com/file/d/1gLFAjWKY4GuSZ8DwWWIvRjUQrUDNkXD2/view?usp=sharing)

---

### Post by HermanAB on 2022-06-27
Imagemagick can of course do it all.  Just study ‘man convert’ for a few days. ;)

---

### Post by yancek on 2022-06-27
I'm not sure hat the problem is with different image sizes.  If you just want a pdf file with the images in it you can scroll through and access, the following will do it, using the convert command from Imagemagick.

>  convert img1.jpg img2.jpg output.pdf
 

---

### Post by Impavidus on 2022-06-27
There's no requirement for the pages in a pdf document to be the same size.

@1fallen: What's that sudo doing in your command?

---

### Post by #&amp;thj^% on 2022-06-27
Why being sudo of course That's my method....use it how ever you see fit.
[https://linuxhint.com/convert-image-to-pdf-command-line/](https://linuxhint.com/convert-image-to-pdf-command-line/)

---

### Post by deadflowr on 2022-06-27
> But if the .jpg files are of different size, what command shall I run?

What's the endgame here?
Do you want them to be of the same size or is having them all different sizes okay?

---

### Post by satimis on 2022-06-27
Hi all,

Thanks for your advice.

I have img2pdf installed

**[COLOR="#FF0000"]Output .pdf file[/COLOR]**
I need each .jpg file (different size) of the same size on each page, Landscape format.

Thanks

Regards

---

### Post by mIk3_08 on 2022-06-28
> **satimis said:**
> Hi all,

Create PDF file.  On Terminal run
```

img2pdf *.jpg --output combined.pdf

```

But if the .jpg files are of different size, what command shall I run?

Thanks

Regards
In  my case... I use pdftk and its something link this below.
```
sudo pdftk '/home/compname/Pictures/filefolder/filename.png' '/home/compname/Pictures/filefolder/filename2.png' cat output single_document.pdf
```
But you can also convert the image file to pdf  using image application software like Imagemagick, gimp etc. Regards and cheers.

---

### Post by satimis on 2022-06-28
> **mIk3_08 said:**
> In  my case... I use pdftk and its something link this below.
```
sudo pdftk '/home/compname/Pictures/filefolder/filename.png' '/home/compname/Pictures/filefolder/filename2.png' cat output single_document.pdf
```
But you can also convert the image file to pdf  using image application software like Imagemagick, gimp etc. Regards and cheers.
Thanks for your advice.

pdftk is on repo of Ubuntu 20.04 and I can install it.

Why should I run pdftk with sudo ?

Besides I have about 50 .jpg files in the same folder.  Each of them is of different size.  I expect to combine all of them in the same .pdf file in batch.  Each .jpg file takes up one page on the same .pdf file.  The format of the .pdf file is on Landscrape.  What will be the command line?

Thanks and regards

---

### Post by mIk3_08 on 2022-06-28
> **satimis said:**
> Thanks for your advice.

pdftk is on repo of Ubuntu 20.04 and I can install it.
Why should I run pdftk with sudo ?

You can ignore the sudo anyway. Its not necessary. Regards and cheers.

---

### Post by #&amp;thj^% on 2022-06-28
Agreed with  mIk3_08 sudo is not needed for a GUI app like pdftk, seems I've caused some confusion with sudo and img2pdk only.
To be clear img2pdf is not a GUI it is a system utiliy, nor do you have sudo there either.
I have different permissions between ImageMagick and img2pdf on "my" system.
Hope that clears things up a bit.

---

### Post by deadflowr on 2022-06-28
try using the imgsize parameter
```
img2pdf *.jpg -s 800x600 --output combined.pdf
```
I just picked a ranndom(ish) size.
The default sizing is in pt sizes but can be set to cm, mm, or inch as well.

They are other options too, you can see them all by scrolling down the man page for img2pdf.
It also lists some examples toward the bottom.

---

### Post by ActionParsnip on 2022-06-28
> **mIk3_08 said:**
> In  my case... I use pdftk and its something link this below.
```
sudo pdftk '/home/compname/Pictures/filefolder/filename.png' '/home/compname/Pictures/filefolder/filename2.png' cat output single_document.pdf
```
But you can also convert the image file to pdf  using image application software like Imagemagick, gimp etc. Regards and cheers.

Why are you using sudo here? The user has full access to it's home....?

---

### Post by #&amp;thj^% on 2022-06-28
> **ActionParsnip said:**
> Why are you using sudo here? The user has full access to it's home....?

I felt he redeemed himself with:
> **mIk3_08 said:**
> You can ignore the sudo anyway.**_ Its not necessary._** Regards and cheers.

---

### Post by yancek on 2022-06-28
>  But if the .jpg files are of different size, what command shall I run?


I'm not sure what you want here.  If you want the images to retain their size run the following command, you need ImageMagick installed:

>   convert image1.jpg image2.jpg image3.jpg -gravity center -extent 1240x1753 -units PixelsPerInch -density 150x150 image.pdf


If you want to change the size and have them all the same size run this (change the size to what you want):

>  convert image1.jpg image2.jpg image3.jpg resize 1024x755 -gravity center -extent 1240x1753 -units PixelsPerInch -density 150x150 image.pdf 

If you have 50 jpg files in the same folder, use *.jpg.  You can also try to change the other options to get what you want.

---

### Post by satimis on 2022-06-29
> **yancek said:**
> I'm not sure what you want here.  If you want the images to retain their size run the following command, you need ImageMagick installed:

I already install ImageMagick

I expect running "img2pdf" to combine all *.jpg to .pdf file, each image taking up one page on the .pdf file

Regards

---

### Post by satimis on 2022-06-29
> **deadflowr said:**
> try using the imgsize parameter
```
img2pdf *.jpg -s 800x600 --output combined.pdf
```
I just picked a ranndom(ish) size.
The default sizing is in pt sizes but can be set to cm, mm, or inch as well.

They are other options too, you can see them all by scrolling down the man page for img2pdf.
It also lists some examples toward the bottom.
Your advice works for me.  Thanks

It is not easy to read and understand on man page.  Just found following link
How to Use Image2PDF
[https://www.qnap.com/en/how-to/tutorial/article/how-to-use-image2pdf](https://www.qnap.com/en/how-to/tutorial/article/how-to-use-image2pdf)

It is a good tutorial

Regards

---

### Post by yancek on 2022-06-29
>  I expect running "img2pdf" to combine all *.jpg to .pdf file, each image taking up one page on the .pdf file


That's exactly what the 2 commands in post 16 do, the first retaining the original size, the second having the images all the same size.  Wasn't aware that you didn't want any other software than img2pdf.

---

