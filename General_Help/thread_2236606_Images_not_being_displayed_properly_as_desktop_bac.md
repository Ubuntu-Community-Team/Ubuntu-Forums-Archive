---
title: "Images not being displayed properly as desktop background?"
date: 2014-07-27
forum: General Help
---

### Post by r0d3nt on 2014-07-27
Hi All,

I normally use Mate as my window manager, but I ran into what I thought was a bug with displaying Vertical images as Desktop Backgrounds, but it turns out it affects the default window manager in Ubuntu.

I've noticed that when I take a picture that was taken with a camera that has been held vertically and then set as a Desktop background, the image usually ends up being displayed horizontally instead of vertically.

The image displays with the correct orientation when viewed through the Desktop Appearance selector when the image is chosen and that is how I am expecting it to look:
[ATTACH=CONFIG]255096[/ATTACH]

However when the image is set as the background it is set horizontally instead of vertically:
[ATTACH=CONFIG]255097[/ATTACH]

I think I know why this is occurring. I ran jhead against this image, and the orientation setting is set to rotate 90 so that the image will be vertical when normally viewed:

```
uquevedo@intelc2d:~/Desktop$ jhead IMG_5788.JPG 
File name    : IMG_5788.JPG
File size    : 1934947 bytes
File date    : 2014:06:13 17:21:04
Camera make  : Apple
Camera model : iPhone 5s
Date/Time    : 2014:06:13 17:21:04
Resolution   : 3264 x 2448
Orientation  : rotate 90
Flash used   : No
Focal length :  4.1mm  (35mm equivalent: 30mm)
Exposure time: 0.067 s  (1/15)
Aperture     : f/2.2
ISO equiv.   : 640
Whitebalance : Auto
Metering Mode: pattern
Exposure     : program (auto)
JPEG Quality : 96
```

It would seem that when this image is set as a desktop background image, the Orientation metadata is being ignored and the original orientation of the image is what is being displayed?

I'm running Ubuntu 14.04 LTS with Mate 1.8. I believe this started occurring after the upgrade of both Ubuntu and Mate because I don't remember this problem with Ubuntu 13.10, Mate 1.6.x, or the window manager in 13.10

I don't want to have to modify my images in order for them to display properly as desktop background images.

Anyone have any ideas why this is occuring?

---

### Post by grahammechanical on 2014-07-27
In my opinion, if the image was displayed vertically then the height of the image would be cropped and the width of the image would be stretched to fit the dimensions of the screen. The image does not match the aspect ratio of the screen.

The Ubuntu Gnome developers have a competition going for the background images for the next release of Ubuntu Gnome. Notice the requirements under the heading Aspect Ratio and Screen resolution. The height of your image should be its width and the width of your image should be its height.

Regards.

---

### Post by r0d3nt on 2014-07-27
The image displays correctly in all other viewers:
[ATTACH=CONFIG]255102[/ATTACH]

Why is it that the Desktop Background app can't handle the orientation properly?

It's just very frustrating since I don't remember having this problem in previous versions of Ubuntu.

---

### Post by r0d3nt on 2014-08-15
For anyone still following this thread, I think I've solved my problem with jhead.


Using jhead's autorot feature, it re-orientated the original dimensions of the image to the correct orientation:
```
jhead -autorot *
```
The time stamps got all mucked with though, so I then ran jhead's command to make the file date be the exif creation date:
```
jhead -ft -v *
```
So far everything seems to be orientating the way I'm expecting it to display.

---

