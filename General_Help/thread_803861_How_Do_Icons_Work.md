---
title: "How Do Icons Work?"
date: 2008-05-22
forum: General Help
---

### Post by gwm on 2008-05-22
Hi,
In another thread, It was explained to me that one can use either a jpeg or an svg file for an icon. Microsoft embeds the icons as ico images in the executable itself.Can anyone help with a source or perhaps the information itself?

How does Linux deal with this matter?

What are svg files? Gimp doesn't know them (most MS software doesn't know ico files either). I presume they are dual images - one for normal and one for clicked - but how does one create them?

I tried a png file and it worked like a jpeg does but I'm at sea with this transparency thing. I couldn't work out how to give it a transparent background from the Gimp help file.

---

### Post by NightwishFan on 2008-05-22
I do not remember much how to use gimp, I normally make single layer wallpapers. I know you can make a transparent layer though.

Scalable Vector Graphics (SVG) is an XML specification and file format for describing two-dimensional vector graphics, both static and animated. SVG can be purely declarative or may include scripting. Images can contain hyperlinks using outbound simple XLinks.[2] It is an open standard created by the W3C's SVG Working Group.

Gimp can read .svg if you convert it to another format like .png. (I just noticed open formats own)

To change icons in gnome I think it is similar to the Windows way, only no .ico files. If you like a .ico perhaps convert it to .png

[http://en.wikipedia.org/wiki/Svg](http://en.wikipedia.org/wiki/Svg)

---

### Post by kostkon on 2008-05-22
> **gwm said:**
> Hi,
In another thread, It was explained to me that one can use either a jpeg or an svg file for an icon. Microsoft embeds the icons as ico images in the executable itself.Can anyone help with a source or perhaps the information itself?

How does Linux deal with this matter?

What are svg files? Gimp doesn't know them (most MS software doesn't know ico files either). I presume they are dual images - one for normal and one for clicked - but how does one create them?

I tried a png file and it worked like a jpeg does but I'm at sea with this transparency thing. I couldn't work out how to give it a transparent background from the Gimp help file.
You can use any image file as an icon in Ubuntu, even .ico files. Anything will work as long as it's an image (that is suported, of course).

I assume they had recommended you to use SVG files because they are vector files and scale better than bitmap based formats (like jpg, png, ico, etc.)

You can define an icon for any file in Ubuntu. Just right click on it and go to its properties.

---

