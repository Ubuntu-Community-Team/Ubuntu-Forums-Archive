---
title: "ImageMagick Issues"
date: 2006-08-04
forum: General Help
---

### Post by SteveF on 2006-08-04
I had a script I was running under Breezy Badger.  I haven't used the script since upgrading to Dapper, but now I need to run it.  I am having problems with the composite command.  I'm guessing it is related to the (probably) newer version of ImageMagick installed with Dapper.  I was wondering if anyone else is having a problem.  I tried emailing theimagemagick bugs list, but the email is not getting through and I am also not having success getting to the ImageMagick web site.

Here is the command I am using:
composite test.jpg test2.jpg testmask.bmp +matte test3.jpg

The output (test3.jpg) is an exact copy of test2.jpg.  It appears as if the mask is being ignored.  I have tried switching test and test2 (in which case test3 now looks like test).  I have tried converting the mask to jpg, png and tif (also used the colorspace Gray option).  None worked.

The closest I came to success was to convert the mask to a PBM file along with using the -colorspace GRAY option.  If I then used that file with the convert command (as opposed to the composite command) I got partial success (it worked, but because the PBM had a lot of dithering, the combining was not what I was after).  That command was:

convert -composite test.jpg test2.jpg -mask testmask.pbm test3.jpg

I do have a newer version of ImageMagick  running under Windows which seems to work, but I can't use that because other commands are producing off colors (I creating a sepia image with a border, the Windows version comes out way to yellow using the same RGB values).

The only option I currently have left is to do the composite in the GIMP.  This works, but being that I have a hundred files, this is time consuming.  I thought about grabbing the newest version from sourceforge, but I am not thrilled with compiling the app (will mae install overwrite the installed Dapper version??) and being out of sync with Dapper.

Anyway (after all of that).  Any ideas?

Thanks,

Steve

---

### Post by SteveF on 2006-08-08
After doing some research, this looks like it might be a bug in either this version of ImageMagick or in the DEB used by Ubuntu.  See the following link on the ImageMagick boards which describes a similar issue:

[http://studio.imagemagick.org/pipermail/magick-users/2006-June/017680.html](http://studio.imagemagick.org/pipermail/magick-users/2006-June/017680.html)

Is there a place to report bugs?

Steve

---

### Post by zxee on 2006-08-08
[https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs)

---

### Post by SteveF on 2006-08-08
Thanks.  I see this bug (or one related anyway) is already mentioned there.

---

### Post by richbl on 2006-08-10
I just ran into this same composite bug issue under Dapper. It is easily reproducible.

Until this bug is resolved, however, the good news is that I was able to build the latest release of ImageMagick from sources. Works great, no problems, and best of all... the composite bug is GONE!

Here's the procedure:

0) Uninstall Imagemagick if you have an official Ubuntu version installed
1) Go to [http://www.imagemagick.org/script/install-source.php#unix](http://www.imagemagick.org/script/install-source.php#unix) and follow the procedure there

That's it. 

It took about 10 minutes or so to compile and install.

No more ImageMagick composite bugs.

rich

---

