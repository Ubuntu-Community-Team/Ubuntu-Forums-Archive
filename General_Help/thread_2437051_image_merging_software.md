---
title: "image merging software"
date: 2020-02-18
forum: General Help
---

### Post by Skaperen on 2020-02-18
on a website i have specific access rights on i can view parts of a very large image in a window on the web page.  that widow is nearly as large as the browser window it's in, but it is only a small percentage of that giant image. i can manually drag the giant image around as desired.  what i want to do is screen capture enough views to complete the giant image and have the giant image reconstructed from all those screenshots.  is there any open source software around that can do this? it is related to image stitching.

---

### Post by Impavidus on 2020-02-18
There's the hugin panorama stitcher – install the **hugin** package. It's meant for panorama pictures, but with the right settings it should be fit for your task too.

---

### Post by Skaperen on 2020-02-18
the kind of result i want would be like a digitally created panorama.  the only difference compared to a photographic one would be that the digital one is all in a perfectly flat plane.  now that i think more about it, all i need to do is crop the subwindow out of each image and feed that to a program that figures out the alignment and stitches the pieces together.  for the web site i'm accessing via my paid account there, i just need to move the image around and take screen shots enough for it to see every pixel of the big image.  i'll need to get enough that it can "see" where to align the various pieces.  it should be smooth since every offset is exact pixel alignment, unlike real world camera shots.

so, i'll try **hugin** this way.  and here is the panorama i made many years ago:  [http://ipal.net/vance/](http://ipal.net/vance/)

---

### Post by Skaperen on 2020-02-20
i installed and tried **hugin**.  it seems to be completely non-functional.  most buttons do nothing.  not what GUI should be like.

i had some paid software many years ago.  i quit paying for support and it would not run on more advanced kernels.  but i wasn't doing any panos with my cameras (more into macro) so i just gave up on it.  i can't remember its name.

---

### Post by sdsurfer on 2020-02-20
So you want to do this manually or is it something you would need automated or on a regular basis?
Manually couldn't you just paste the screen shots in GIMP or equivalent and save a separate file?
Automated I would turn to iMagick/imageMagick and put something together on the command line.

---

### Post by Skaperen on 2020-02-20
if i need to do it manually i will.  it would be nice to have a command that can just do it.

by manual i mean interact with a GUI app.  i expect the app to automatically align the images as pieces of the panorama.  i expect this because it is years old technology.  i am not aware of any such feature in GIMP or imageMagick.

---

### Post by dragonfly41 on 2020-02-21
I have previously installed DarkTable but only played around with it briefly.

[Could this meet your requirements?]("https://www.mail-archive.com/darktable-user@lists.darktable.org/msg02646.html")

---

### Post by sdsurfer on 2020-02-21
> **Skaperen said:**
> if i need to do it manually i will.  it would be nice to have a command that can just do it.

For automation ImageMagick is pretty powerful, I have used it with Perl and PHP. I can imagine an app where you dump your images in a directory then

- walk through the image list, get sizes of each
- create new image = total of widths
- calculate location of each image and drop into new image
- save new image

Execution could be yourscript [directory name]

For manual,
>  i am not aware of any such feature in GIMP
One of the great things about GIMP is the abundance of available plugins. Here is one of them that looks promising (I did not download or test it.)

[http://stitchpanorama.sourceforge.net/](http://stitchpanorama.sourceforge.net/)

---

### Post by Skaperen on 2020-02-22
>  calculate location of each image and drop into new image

this is the major step i need done.  in this case it should be much simpler since it needs to be shifted pixels in a shifted perspective of view.  most cases of stitching photographs, where each is from the same perspective of view, involves a change of partial rendering angle so that the individual photos can be merged at the correct positioning.  even though the perspective is unchanged (in theory) the image still gets morphed, more so the further it is from the center, so that the result looks like a single ultra-panorama shot.  lens distortions of the taking lens a best taken into account at this critical stage.  but in my case, no morphing is needed and direct pixel storing is not only fine, but preferred.  in cases of pixel conflict, completely different logic may be needed to avoid fuzzy objects in the result.

edit:

even though it will look correct to us humans, a "rectilinear" (the most common) lens actually creates a substantial amount of distortion.  a pinhole "lens" does this distortion, too, if the image is formed on a flat surface.

---

### Post by HermanAB on 2020-02-23
Are you sure you need to go to all that hassle?

I would look in the browser cache for the largest file.

---

### Post by Skaperen on 2020-02-23
it really fetches images slices from the server.  the logic generates them when you go beyond a certain point.  if there is a massively large image with everything, its on the server.

---

### Post by HermanAB on 2020-02-23
In that case, GDAL (and QGIS) can likely do what you need.

---

### Post by Impavidus on 2020-02-23
Image stitching software isn't necessarily limited to stitching images taken from the same position, with different orientations. If you know that the subject is a flat plain, it can also solve for the camera position to reconstruct the 2D subject. For example, [http://hugin.sourceforge.net/tutorials/Mosaic-mode/en.shtml](http://hugin.sourceforge.net/tutorials/Mosaic-mode/en.shtml). I never used that software for that purpose, but have used it a number of times to stitch panoramas. In your case, you don't even have to solve for pitch, roll, yaw, lens distortion and distance, only for x and y position. Note that finding control points can be done automatically.

Otherwise, gimp can be used, but I think you may have to align the images manually. Best to use subtractive blending for that, so that the overlapping parts turn black when alignment is perfect.

> even though it will look correct to us humans, a "rectilinear" (the most  common) lens actually creates a substantial amount of distortion.  a  pinhole "lens" does this distortion, too, if the image is formed on a  flat surface
Every projection from the surface of a sphere to a flat plane will be distorted, because they have different curvature. The nice thing about perspective a.k.a. rectilinear projection is that if viewed from the right spot, i.e. the position of the lens/pinhole, the image appears identical to the original scene. Viewing a plane from a point is the exact reverse of projecting something on that plane through that point.

---

### Post by monkeybrain20122 on 2020-02-23
gimp?

[https://daviesmediadesign.com/project/stitch-panoramic-images-gimp-2-10-2-two-methods/](https://daviesmediadesign.com/project/stitch-panoramic-images-gimp-2-10-2-two-methods/)

---

### Post by Skaperen on 2020-02-25
i have tried hugin. a window pops up but nothing works.  clicking on things that look like they could be clicked on does nothing at all.  i can end hugin by clicking in the rightmost button in the title decorator.

---

