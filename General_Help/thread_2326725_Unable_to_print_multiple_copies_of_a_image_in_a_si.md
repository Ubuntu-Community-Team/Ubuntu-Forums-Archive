---
title: "Unable to print multiple copies of a image in a single page"
date: 2016-06-04
forum: General Help
---

### Post by leozinho29_eu on 2016-06-04
Hello

I am trying to print multiple pages in only one, however I am having issues with it. My printer is a HP Deskjet F2050. It shows as HP-Deskjet-2050-J510-series and searching at HP site I have not found the F2050, just the 2050-J510a ( [http://support.hp.com/br-pt/product/HP-Deskjet-2050-All-in-One-Printer-series---J5/4027463/model/4027468/product-info](http://support.hp.com/br-pt/product/HP-Deskjet-2050-All-in-One-Printer-series---J5/4027463/model/4027468/product-info) ). Looks like it is the same.

There are no issues when printing single pages: everything works as expected. The issue is that we often need to print many images (.png, .gif, .jpg, ...) in one page and this simply don't work. It produces a very problematic output, which can be seen in this image: [URL="http://i.imgur.com/jEWOpZA.png"]http://i.imgur.com/jEWOpZA.png
[/URL]
This output was produced using the Eye of Mate image viewer. Eye of Gnome produced the same. 

Printing images this issues always happen. Printing text documents sometimes this issue happens. When I try to print multiple pages in one using gedit, the preview has the same error that printing images but the result is correct (as can be seen here: [http://i.imgur.com/RUj7vF0.png](http://i.imgur.com/RUj7vF0.png) ). With LibreOffice there is no issue: it prints as expected. Evince nearly always work, it fails sometimes doing the same that happens with images.

Here is a link with a digitalized image of a test page: [http://i.imgur.com/XCSypbH.png](http://i.imgur.com/XCSypbH.png)   The driver version I am using today is 3.16.3.

I searched about it and found some instructions to do it using terminal ( [http://askubuntu.com/questions/433236/how-to-print-multiple-copies-of-an-image-on-a-single-page](http://askubuntu.com/questions/433236/how-to-print-multiple-copies-of-an-image-on-a-single-page) ), but this will hardly be a suitable solution in this case, because the users that need this have difficulties even to double click in a icon to open, so using terminal to print every time is not a option here...

The ideal situation would be a program/window/option which allows to easily configure printing as there is one in Windows 7 (I think I am asking too much).

Thank you.

---

### Post by leozinho29_eu on 2016-06-24
Have someone found a solution to this? The montage command has inconsistent results (ex.: from 15 copies of the same image in one page, 6 are problematic).  

Edit: I am asking again because I need this and only my notebook is working at the moment. 

I don't understand what I am doing wrong with the montage command: sometimes a few images appear pixelated, other times the images occupy very small spaces in the page, other times it occupies a lot of space and other times the image is cut. Printing a lot of pages to test is expensive and with the way it is working right now nothing grants the exports to pdf would have the same results from actual printing.

---

### Post by Dennis N on 2016-06-24
Maybe one of these is what you are looking for:

Depending on the source material:

1) Contact Sheet (example: a number of camera images): use **gthumb** to create it.
2) Photo collage = Mixed pictures of varying size: I import individual images into **Inkscape** and arrange the images on the page, then export to png file which can then be printed.

---

### Post by leozinho29_eu on 2016-06-24
Thank you for the answer

When configuring printing, the 1, 2, 4, 9, 16 options appear, but they do not have the desired effect.

Example: I have one image and want to print 9 smaller copies of it in only one page.

What I believe that should happen: if I choose to print 9 pages and configure to 9 pages per sheet in the printing configuration, it should use one sheet and print 9 smaller images on it. 
What happens: it uses 9 pages to print 9 smaller images. The size is (I suppose) correct, but it prints 9 pages of paper, all of them with a lot of unused space. 

I suppose the printing system do something wrong about the unused space, as if it was still part of the image. This is clearly visible in the second link from the first post. The size is ok, the unused space and page count isn't.

Edit: about the montage command: I have searched more, and found that a part of the issue I was having was because of some problematic images (.ico files with multiple sizes).

I have found a way to print correctly. I export the images with montage, then I open the .ps file in Gimp, print the gimp image as a pdf and then I print it using evince. Shortening this steps makes some of the smaller images be cropped. While I can print the file correctly, I think this is too much things to do.

I will not mark the thread solved due to the problematic behaviour the options to choose 4 pages per sheet have. I believe this is a bigger issue.

---

