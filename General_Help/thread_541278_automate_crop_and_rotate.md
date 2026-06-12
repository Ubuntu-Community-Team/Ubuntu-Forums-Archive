---
title: "automate crop and rotate"
date: 2007-09-02
forum: General Help
---

### Post by MichaëlVD on 2007-09-02
Does anyone know a linux program that automatically rotates and crops scanned images? Something like this: [http://blog.thembid.com/index.php/2007/09/01/do-you-still-scan-photos-with-a-flatbed-scanner/](http://blog.thembid.com/index.php/2007/09/01/do-you-still-scan-photos-with-a-flatbed-scanner/)

Thanks!

---

### Post by kidders on 2007-09-04
Sounds like you want Imagemagick. Autocropping & rotating images is at the more basic end of its functionality, I suppose, but it should do the trick nicely for you.

---

### Post by MichaëlVD on 2007-09-04
Thanks. A command line tool would be perfect. I can't find that feature in imagemagick though... I can see autorotate, but only for digital pictures that have EXIF information, and autocrop, but I don't see an option to autorotate scanned images that are only a couple of degrees of being perfectly horizontal. Can you help me out? Or does anyone know another way to do this?

---

### Post by kidders on 2007-09-04
> **MichaëlVD said:**
> A command line tool would be perfect.Yeah... scriptable utilities are really handy. :-)

> **MichaëlVD said:**
> I don't see an option to autorotate scanned images that are only a couple of degrees of being perfectly horizontal.Yikes... I'm not familiar with anything that can do that. It never occurred to me that you might only be talking about maybe a 2 or 3 degree rotation, for some reason.

I know this is a bit lame, but my best suggestion would be to perform multiple rotations with a "for" loop, and choose the best result by inspection. I'm imagining a quick shell script that...
[LIST=1]
[*]Makes imagemagick perform a range of rotations from, say, -6 to +6 degrees in 2 degree intervals.
[*]Opens all the images independently in preview apps of some sort. You could maybe use compiz's scale plugin to inspect them all simultaneously, if you have a big monitor.
[*]Have the script wait for you to press a key or something, by which time, you'll have closed all image previews except the one you want to keep.
[*]Your script could then delete all the rotated images except the one that's still open.[/LIST]There may well be an app around that would make the job less ... well ... ridiculous sounding (frankly!), but I don't know of one. Sorry.

---

### Post by MichaëlVD on 2007-09-05
I can tell you have not seen the demo that I linked to, because, frankly, what you describe does not sound like the perfect solution, even if it was available today... Nice try though :-)

Anyone else? Currently, I'm manually rotating and cropping in Gimp, and that is not too bad... But now that I have seen that demo, I want more!

---

### Post by kidders on 2007-09-05
Hehe I noticed it alright. Off the top of my head, I don't know of anything that can auto-rotate that way out of the box though. If you have time on your hands (lots of it!), I have no doubt that imagemagick can be *made* to do it.

Sorry I wasn't much help.

---

### Post by cwaldbieser on 2007-09-06
> **MichaëlVD said:**
> I can tell you have not seen the demo that I linked to, because, frankly, what you describe does not sound like the perfect solution, even if it was available today... Nice try though :-)

Anyone else? Currently, I'm manually rotating and cropping in Gimp, and that is not too bad... But now that I have seen that demo, I want more!

I think I have worked out an algorithm that will do what you see in the demo, but I am making some pretty broad assumptions:

1) The scanned images are all rectangular.
2) The background color around the image is a uniform color (e.g. white).

I don't think it would be too hard to program with something like PIL (python imaging library).  I will try it out, but it may take me a number of days before I have the time.

---

### Post by cwaldbieser on 2007-09-06
> **MichaëlVD said:**
> I can tell you have not seen the demo that I linked to, because, frankly, what you describe does not sound like the perfect solution, even if it was available today... Nice try though :-)

Anyone else? Currently, I'm manually rotating and cropping in Gimp, and that is not too bad... But now that I have seen that demo, I want more!

OK, I tired this out on some simple test cases.  You need to put the shell script and the python script in the same directory.  Make the shell script executable.  Run it like:
```

$ ./rotate-crop.sh INFILE OUTFILE

```

I tried to optimize the shell script to compute the changes on a miniature of the image first, because computations took longer for large images.  Hopefully, small images don't suffer.

I didn't add any options or decent error checking.  Consider it a work in progress.

---

### Post by cwaldbieser on 2007-09-17
I worked on this a bit longer, and I managed to turn the script into a single bash script that uses the ImageMagick suite and some other common shell tools.

I also corrected some bugs I found, but I only have a few sample images I tested.

---

### Post by Benjamin2 on 2007-12-28
Hi,

I tried your script, and it works well on many files, but on some files it does bad things.
See the example:
[[IMG]http://img258.imageshack.us/img258/6072/dm006tp7.th.jpg[/IMG]](http://img258.imageshack.us/my.php?image=dm006tp7.jpg) (original)
[[IMG]http://img258.imageshack.us/img258/2579/outps9.th.jpg[/IMG]](http://img258.imageshack.us/my.php?image=outps9.jpg) (processed)

---

### Post by stani on 2008-01-14
There is a new application for this: Phatch 
You can download it at [http://photobatch.stani.be](http://photobatch.stani.be) > free download

It is already quite well documented (Help > documentation in the menu)

---

### Post by MichaëlVD on 2008-01-27
Phatch only rotates 90 degrees, which is not what we were looking for. Thanks anyway.

---

### Post by stani on 2008-01-27
Phatch can rotate any angle you wish:
[http://photobatch.wikidot.com/action-rotate](http://photobatch.wikidot.com/action-rotate)

Just press + to show the dialog to add an action and press the top-right button select. There you can select a different category of actions. Choose transform and rotate will be there.

Stani

---

