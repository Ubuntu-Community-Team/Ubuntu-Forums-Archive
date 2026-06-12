---
title: "image editing"
date: 2006-11-23
forum: General Help
---

### Post by alanandhispc on 2006-11-23
Is there a Gnome application that can strip EXIF information out of jpeg's?

or how do you do it in GIMP?

reason for asking is i have a load of jpg's for the web that at the moment i have to batch process through psp5 in windows in order to achieve this. would ideally like to have the dependancy of windows removed for this sort of thing. psp5 doesn't actually give you the option to strip the exif info, it just does it.

IMO, for straight forward image editing, there doesn't seem to be a simple to use linux app that can do ALL of the following:

crop, resize, rotate, mirror, save with/without EXIF information,  save as multiple formats, compress image, adjust brightness/contrast.

i like browsing abilties of photo mangement apps, but i don't like to have to copy my images into albums, as i keep my own structure on things.

if im wrong and you know of an simple to use app that can do this, by all means let me know.


Many Thanks


Alan

---

### Post by Qew on 2006-11-23
You could install imagemagick's mogrify or convert commands, using the -thumbnail or -strip switches, to remove such info from your JPGs. Sure, imagemagick is a commandline tool, but it's perfect for this kind of job. (Yes, that k at the end is intentional. ;) )

---

### Post by alanandhispc on 2006-11-23
did play around with it, but the main reason for looking for a _Gnome_ app was my wife is not command line savvy and doesn't want to be.

thanks anyway


Alan

---

### Post by stani on 2007-06-01
I've started to work on a new graphic program especially designed for photo batching with a graphical user interface (GUI).  The first version will be fairly simple, no preview yet and only a few plugins (scale, rotate, save, invert, ...). I originally develop it for Ubuntu, but I might port it to Windows and Mac in the future. Progress is going fine, so beta testers will be welcome. If someone is interested in beta-testing my program at a later stage, please send me a private message with your email.
Stani

Everyone with knowledge of PIL (Python Image Library) can easily write plugins for it. There is no need for GUI programming, as my program will take care of it. So anyone who wants to write a plugin (as simple as rotate, invert, contrast, ...) please contact me as well.
--
[http://pythonide.stani.be](http://pythonide.stani.be)

---

### Post by stani on 2007-06-06
The very first alpha version of my photo batch processor is available for testing:
[http://ubuntuforums.org/showthread.php?t=466598](http://ubuntuforums.org/showthread.php?t=466598)

---

