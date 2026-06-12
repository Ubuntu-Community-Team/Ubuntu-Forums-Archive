---
title: "Is there a tool to dynamically layout a grid of images for scrapbook cutouts?"
date: 2015-10-10
forum: General Help
---

### Post by johnpharrell on 2015-10-10
I'm looking for a tool that will layout images into grids ***dynamically*** **without altering their proportions**.  
The purpose would be to make cutting image printouts much faster for  scrapbooking. I know a lot of 
websites can layout images dynamically,  taking each image size into consideration. Is it possible to run 
a  commandline tool to achieve something like this? If possible, a grid  without borders would be much better.


  There is an extension for photoshop that achieves something like this: [URL="http://lumens.se/tychpanel/"]http://lumens.se/tychpanel/
[/URL]
However, from what I can see, other options in linux aren't dynamic  and require that all images have the 
same aspect-ratio. It would be ok  if there is a little space left over at the end of a page (as in the  example).
The priority is to maintain each images' aspect ratio whilst  using as much space as possible on the page.
  An example:

[IMG]http://i61.tinypic.com/qoywcl.jpg[/IMG]

---

### Post by coldraven on 2015-10-11
I had a little search around the web and found a couple of things that might be of use. Firstly, if you don't already have it, install imagemagick.
```
sudo apt-get install imagemagick
```
This installs a few image processing tools including convert and montage.
I just downloaded some images to experiment with, all in the 400x 600 pixel range. I saved them as 01.jpeg etc.
I then used the convert utility to create a file called 1_tile.png. This example has three images in two rows. You can add more images between the brackets or more brackets to get more rows, just copy the format.
```
 convert \( 01.jpeg 02.jpeg 03.jpeg +append \)    \( 04.jpeg 05.jpeg 06.jpeg +append \) -append 1_tile.png
```

I found this here:
[http://stackoverflow.com/questions/29974401/how-can-i-create-an-imagemagick-montage-without-empty-space](http://stackoverflow.com/questions/29974401/how-can-i-create-an-imagemagick-montage-without-empty-space)

You might want to look at the montage utility because it can create borders between the images.
[http://www.imagemagick.org/Usage/montage/](http://www.imagemagick.org/Usage/montage/)

---

### Post by tgalati4 on 2015-10-11
Lots of tutorials on how to do it [manually]("http://emptyeasel.com/2008/08/29/how-to-create-a-photomontage-in-gimp/").  I couldn't find any automatic tool.  There are photo montage screen savers.  How could one of those screen saver algorithms be turned into batch tool?

There is a very old graphics viewer, *feh*, that has a montage mode.  It would be worth installing and playing with it.

> Montage mode forms a montage from the filelist.  The resulting image can be viewed or saved, and its size can be limited by height, width or both.

```
sudo apt-get install feh
man feh
```

---

