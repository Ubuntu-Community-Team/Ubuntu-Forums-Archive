---
title: "Batch Photo Downsize"
date: 2007-06-15
forum: General Help
---

### Post by CallMeDerek on 2007-06-15
I need to find an app that I can point to a directory and batch downsize photos for web posting (across several subdirectories would be preferred).  I have looked at the scripting for GIMP – little over my head – just want a simple gui based batch image downsizer. 

There has to be one... Why cant I find it!

Thanks in advance!

~derek

---

### Post by Naegling23 on 2007-06-15
digiKam has an option to do this, but everytime I try it, I just get a blank image.  You can try it out, maybe you'll have better luck

---

### Post by thePsychologist on 2007-06-15
If you want to try a basic command line utility, install imagemagick:

```
sudo aptitude install imagemagick
```

Then for instance you can shrink an image down like this:

```
convert -resize 10% `find | grep jpg` thumbnails.jpg
```

Run this command in a directory, and it will search through every subdirectory, and output files called something like "thumbnails-xx.jpg" in the current directory. Replace 10% by your desired resize factor. See [http://www.perturb.org/display/entry/632/](http://www.perturb.org/display/entry/632/) for more information on resize.

---

### Post by MetalMusicAddict on 2007-06-15
Try [nautilus-image-converter]("http://www.bitron.ch/software/nautilus-image-converter.php").

```
sudo apt-get install nautilus-image-converter
```

---

### Post by mdurham on 2007-06-15
It's possible to do this with Picasa, using the 'Export' function it will export selected images in the preset size & compression.

---

### Post by stani on 2007-06-16
> **CallMeDerek said:**
> I need to find an app that I can point to a directory and batch downsize photos for web posting (across several subdirectories would be preferred).  I have looked at the scripting for GIMP – little over my head – just want a simple gui based batch image downsizer. 

There has to be one... Why cant I find it!

Because I just developped one: Phatch! (=Photo+Batch) I was missing this too in Ubuntu and to fill in the gap myself. There are a lot of command tools (such as mogrify) but I also wanted a GUI. To downsize with my application, just add these actions:
- image size
- save

Drop any files or folders onto Phatch and it will display a dialog with options (include subfolders, etc...) If you prefer you can turn Phatch in a droplet (View>Droplet), which you can use in combination with any image browser such as nautilus, konqueror, f-spot, ... You also have other actions for making shadows or rounded corners if you wish.

To download this application, please go to this thread and post your questions there:
[http://ubuntuforums.org/showthread.php?t=466598](http://ubuntuforums.org/showthread.php?t=466598)

Phatch is available in English and Dutch. A german and french translation are in progress...

---

