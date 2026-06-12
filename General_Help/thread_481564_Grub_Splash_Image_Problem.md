---
title: "Grub Splash Image Problem"
date: 2007-06-22
forum: General Help
---

### Post by SteveF on 2007-06-22
I followed all the web sites I could find about creating a splash image for grub.  I chose an image and converted it to 14 colors 640x480 xpm file.  I tried using Gimp to do this and ImageMagick (convert).

The resulting file looks fine from within Ubuntu.  I zipped the file using gzip.

When grub starts, the image displays, but the colors are way off.  Like a Leroy Neiman painting.

Nothing I do can get the colors correct.

Anyone have any ideas?

Thanks,

Steve

---

### Post by molly_001 on 2007-07-08
It has to be embedded in 14 colors, and with depth 8.
I also use ImageMagick to bring them down to 8 depth, and it has always worked - it looks good, that is.

---

### Post by SteveF on 2007-07-08
> **molly_001 said:**
> It has to be embedded in 14 colors, and with depth 8.
I also use ImageMagick to bring them down to 8 depth, and it has always worked - it looks good, that is.

What ImageMagick command options do you use?

Thanks,
Steve

---

### Post by molly_001 on 2007-07-09
First, I've made a quick web page for you to see the resulting image quality.
It might be that you don't like how the image turns out, in which case
you know it won't be worth your time to investigate further.

[Here's the page]("http://www.commonmancomputing.com/y/GRUBSplashimages/tabid/74/Default.aspx").
( [http://www.commonmancomputing.com/y/GRUBSplashimages/tabid/74/Default.aspx](http://www.commonmancomputing.com/y/GRUBSplashimages/tabid/74/Default.aspx) )

As for ImageMagick command, I use ...

... where MyOrigImage.png is already in PNG format and already 640x480 in size
... where outputImage.png will be the resulting PNG file, with colors and depth reduced

Use this command:

```
[php]convert -colors 14 -depth 8 MyOrigImage.png outputImage.png[/php]
```

---

### Post by SteveF on 2007-07-10
> **molly_001 said:**
> First, I've made a quick web page for you to see the resulting image quality.
It might be that you don't like how the image turns out, in which case
you know it won't be worth your time to investigate further.

[Here's the page]("http://www.commonmancomputing.com/y/GRUBSplashimages/tabid/74/Default.aspx").
( [http://www.commonmancomputing.com/y/GRUBSplashimages/tabid/74/Default.aspx](http://www.commonmancomputing.com/y/GRUBSplashimages/tabid/74/Default.aspx) )

As for ImageMagick command, I use ...

... where MyOrigImage.png is already in PNG format and already 640x480 in size
... where outputImage.png will be the resulting PNG file, with colors and depth reduced

Use this command:

```
[php]convert -colors 14 -depth 8 MyOrigImage.png outputImage.png[/php]
```

Thanks.  It may have been my not using -depth 8 (I thought using -colors 14 was enough when reading other posts).  It works now.  I've been converting to xpm.  Are you using PNG?  I hadn't heard that it could be used.

Steve

---

### Post by sugarland2k on 2007-07-10
You can use png files.  See [http://ruslug.rutgers.edu/~mcgrof/grub-images/](http://ruslug.rutgers.edu/~mcgrof/grub-images/)
or the Grub documents at [http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)  for more details.

Friends do not let friends run Vista!

---

### Post by molly_001 on 2007-07-10
> **SteveF said:**
> SteveF wrote . . .

I've been converting to xpm.  Are you using PNG?  I hadn't heard that it could be used.

Steve

Steve --
You're correct, I convert the image from .PNG to .XPM using GIMP.  Then compress it into .gz , and you know the rest of the story.

---

