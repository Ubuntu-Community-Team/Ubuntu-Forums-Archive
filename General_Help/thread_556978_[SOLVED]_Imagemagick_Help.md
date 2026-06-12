---
title: "[SOLVED] Imagemagick Help"
date: 2007-09-22
forum: General Help
---

### Post by Mongo5000 on 2007-09-22
I've come to the conclusion that Imagemagick is the software I need to do the job.

What I need to do is batch optimize images for use on the web.  I don't need to resize them, just cut the file size down to web acceptable levels.

So I have it installed, have no IDEA how to use imagemagick on the command line.

How do I batch optimize images in a directory with mogrify?

---

### Post by fppl on 2007-09-22
Try to re-save them with IM.

---

### Post by DirtDawg on 2007-09-22
Hi, I actually had to do something very similar to this recently. I wrote a down'n'dirty python script to get the job done.

Copy and paste the script below to a new file and call it whatever you like, just be sure to use the '.py' extension. For example imageresize.py. 

**Make sure to make a backup of the folder of images you intend to change.** This is important as there's no undo.

Next, change the line "/path/to/folder/" to whatever the path is to the folder with the desired images. For example: "/home/Mongo5000/Desktop/images/"

Next, change the part of line 12 where it says, ' -scale 50%' to whatever size you would like. I know you do not think the images need to be "resized", but if you want to optimize for the web, that is likely what you need. If not, you can change the "convert" and " -scale 50%" to whatever command you need. Enter "man imagemagick" into the terminal to get a list of possible options. 

Finally, navigate to the folder where you saved the file (use 'cd /path/to/folder') and enter 
```
 python ./imageresize.py 
``` to run the script. This will likely take a few moments and you may need to experiment some with the percentage to get the desired effect.

I'm sure there's an easier/better way to do this, but this is what I've got to share. I hope you find it useful. 

Here's the script:
```

#!/usr/bin/python

import os

### Enter traget folder path below ###
foldername= "[COLOR="Red"]/path/to/folder/[/COLOR]"

imageque= os.listdir(foldername)

for image in imageque:
	### Change 'command' and 'scale' percentage to suit needs ###
	command= "[COLOR="Red"]convert[/COLOR] " +foldername+image+ " [COLOR="Red"]-scale 50%[/COLOR] "+foldername+image
	os.system(command)

```

EDIT: I highlighted the parts of the script you would need to change in an attempt to make myself a little more clear.

---

### Post by Mongo5000 on 2007-09-22
> **DirtDawg said:**
> Hi, I actually had to do something very similar to this recently. I wrote a down'n'dirty python script to get the job done.

Copy and paste the script below to a new file and call it whatever you like, just be sure to use the '.py' extension. For example imageresize.py. 

**Make sure to make a backup of the folder of images you intend to change.** This is important as there's no undo.

Next, change the line "/path/to/folder/" to whatever the path is to the folder with the desired images. For example: "/home/Mongo5000/Desktop/images/"

Next, change the part of line 12 where it says, ' -scale 50%' to whatever size you would like. I know you do not think the images need to be "resized", but if you want to optimize for the web, that is likely what you need. If not, you can change the "convert" and " -scale 50%" to whatever command you need. Enter "man imagemagick" into the terminal to get a list of possible options. 

Finally, navigate to the folder where you saved the file (use 'cd /path/to/folder') and enter 
```
 python ./imageresize.py 
``` to run the script. This will likely take a few moments and you may need to experiment some with the percentage to get the desired effect.

I'm sure there's an easier/better way to do this, but this is what I've got to share. I hope you find it useful. 

Here's the script:
```

#!/usr/bin/python

import os

### Enter traget folder path below ###
foldername= "/path/to/folder/"

imageque= os.listdir(foldername)

for image in imageque:
	### Change 'command' and 'scale' percentage to suit needs ###
	command= "convert " +foldername+image+ " -scale 50% "+foldername+image
	os.system(command)

```

WHOOSH!  that went WAY over my head LOL.  I very much appreciate the information but I don't need them resized, just optimized.

The closest thing I could find that might work for me is 

```
mogrify -resize 320x140! /nameof/directory/*jpeg
```

But I don't need them resized, just their filesize made smaller

---

### Post by DirtDawg on 2007-09-22
Okay, I get it. mogrify overwrites files where convert makes a new file. I was unclear on that. 

As far as going over your head, sorry but i tried to make it simple step-by-step. If you let me know what needs clearing up, I will do my best. 

As far as optimizing, I'm confused. Do you need to change the filetype? Are the files too big, as in they are 20 megs apiece? Maybe you can clarify.

EDIT: If we can clear up exactly what needs to be done, I can pretty easily rewrite the script and try to make it more painless for you.

---

### Post by DirtDawg on 2007-09-22
LOL! I see what you're trying to do and I'm making it way to complex.

Sorry about that.

What is the exact problem with the files? How big are they and how small do they need to be?

---

### Post by Mongo5000 on 2007-09-22
I appreciate the awesome help DirtDawg!

I get about 40-60 full size pictures zipped up and sent to me every day to be put on the web.  What I do is take those full size pictures, make thumbs and create a page that has the thumbs that link directly to the full size pics and upload it to my host.  I optimize the full size pics so they don't take forever to load on the surfers side.

Sometimes the pics are about 200-300K in size and I like to keep them under 100 just for usability so I batch them through Fireworks right now and lower the file size.  Works good but I hate having to load VMware just to do that.

I hope that clears things up and again, I really appreciate te help.

---

### Post by Mongo5000 on 2007-09-23
anybody?  I can usually find my answer for issues, but this one is totally evading me.

---

### Post by mcduck on 2007-09-23
> **Mongo5000 said:**
> anybody?  I can usually find my answer for issues, but this one is totally evading me.

Just use the above script, but instead of using 'scale' or  'resize' option use '-quality 86' where the number is between 0 (small file, horrible quality) and 100 (good quality, big file).

You would probably want to at least check the quality setting suitable for your use before running the script on all your images. You can try it with only one image without overwriting the original file with the 'convert' command:
```

convert image.jpg -quality 86 image_new.jpg
```

Also note that 'mogrify' overwrites the original file, while 'convert' will create a new file..

---

### Post by Mongo5000 on 2007-09-23
> **mcduck said:**
> Just use the above script, but instead of using 'scale' or  'resize' option use '-quality 86' where the number is between 0 (small file, horrible quality) and 100 (good quality, big file).

You would probably want to at least check the quality setting suitable for your use before running the script on all your images. You can try it with only one image without overwriting the original file with the 'convert' command:
```

convert image.jpg -quality 86 image_new.jpg
```

Also note that 'mogrify' overwrites the original file, while 'convert' will create a new file..

Worked like a charm!

Thank you very much :guitar:

---

### Post by stani on 2007-09-23
> **Mongo5000 said:**
> I've come to the conclusion that Imagemagick is the software I need to do the job.

What I need to do is batch optimize images for use on the web.  I don't need to resize them, just cut the file size down to web acceptable levels.
There is a brand new application which might help you as well as it target is to batch manipulate images easily. It comes with a graphical user interface and can batch recursively folders with images. For more info:
[http://photobatch.stani.be](http://photobatch.stani.be)

You can download a deb installer for Ubuntu there.

Give it a try!
Stani

---

### Post by Mongo5000 on 2007-09-24
> **stani said:**
> There is a brand new application which might help you as well as it target is to batch manipulate images easily. It comes with a graphical user interface and can batch recursively folders with images. For more info:
[http://photobatch.stani.be](http://photobatch.stani.be)

You can download a deb installer for Ubuntu there.

Give it a try!
Stani

thats is one slick little program!  Did the trick very easily.  Man, didn't think I would have two options to use this morning!  Both solutions work awesome :)

Thanks all for the suggestions!

---

