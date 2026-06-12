---
title: "[SOLVED] Slide Show program needed"
date: 2008-07-07
forum: General Help
---

### Post by pmulgaonkar on 2008-07-07
Is there any way to (a) either run glslideshow as an application (i.e., not as a screen saver) or (b) any equivalent slide show program that I can run from a command line that will display photos in a maximized window? I can run glslideshow as a screen saver, but that does not allow other programs to display occasional pop up information windows. 

If this is the wrong forum for this question, please let me know what forum would be better.

Thanks.

--prasanna

---

### Post by sayakb on 2008-07-07
[GQview]("http://gqview.sourceforge.net/") should work for you:
```
sudo apt-get install gqview
```

---

### Post by Vadi on 2008-07-07
Apt links make lazy people happy: [click]("apt:gqview")

---

### Post by sayakb on 2008-07-07
> **Vadi said:**
> Apt links make lazy people happy: [click]("apt:gqview")
:lolflag: Cool trick!

---

### Post by Vadi on 2008-07-07
Yeah, saves time. Please spread the use of it :)

---

### Post by sayakb on 2008-07-07
apt:moo
;)

---

### Post by pmulgaonkar on 2008-07-17
Thanks folks. I will give that a try.  --prasanna

---

### Post by pmulgaonkar on 2008-08-15
[SOLVED]

After much digging through Python manuals, I put together a Python script to do what I wanted. As a way to give back to the community to make up for the knowledge I have received over the past few months, here is the script I came up with.

If any Python gurus know a better way to do this, please feel free to let me know.

TAGS to help Google: image display, slide show, python script

```
#!/usr/bin/python
##
#   Python script to cycle through and display image files in a directory
#   Date: August 8, 2008
#
#   Author: Prasanna Mulgaonkar
#   Based on various manuals and example code on the web.
#   Particular thanks to tutorials from:
#       kevin at cazabon dot com for image resizing code fragment
#
#   License: GPL
#
#   I am publishing this because I spent an indordinate amount
#   of time, trying to figure out how to display a graphic window on the
#   screen, but *not* wait in the tkinter main loop for input.
#   The application I wanted was a standalone image display, with no user
#   interaction, to cycle through a bunch of photos.
#   All the google searches through PIL, tkinter, etc. led to examples
#   that end in something like root.mainloop(). It wasn't clear to me
#   what the minimum set of instructions would be to create an window,
#   load it with an image, and display it on the screen. This example
#   serves that purpose.
#
#--------------------------------------------------------------------------

import os
import time
import PIL
import random

from sys import argv
from Tkinter import *
from PIL import ImageTk, Image
    
def maxSize(image, maxSize, method = 3):
    """ im = maxSize(im, (maxSizeX, maxSizeY), method = Image.BICUBIC)

    Resizes a PIL image to a maximum size specified while maintaining
    the aspect ratio of the image.  Similar to Image.thumbnail(), but allows
    usage of different resizing methods and does NOT modify the image in place."""

    imAspect = float(image.size[0])/float(image.size[1])
    outAspect = float(maxSize[0])/float(maxSize[1])
    #print "input size ", image.size , " aspect ",imAspect
    #print "output size", maxSize, " aspect ", outAspect
    if imAspect >= outAspect:
        #set to maxWidth x maxWidth/imAspect
        #print "set to " , maxSize[0], "x", float(maxSize[0])/imAspect
        return image.resize((maxSize[0], int((float(maxSize[0])/imAspect) +0.5)), method)
    else:
        #set to maxHeight*imAspect x maxHeight
        #print"set to ",maxSize[1], "x", float(maxSize[1])/imAspect
        return image.resize((int((float(maxSize[1])*imAspect) + 0.5),maxSize[1]), method)
#
#--------------- start of main program
#
path = "PATHNAME TO PICTURES DIRECTORY"
win = Tk()
can = Canvas(win)
can.pack(fill=BOTH)
sw = win.winfo_screenwidth()
sh = win.winfo_screenheight()

while 1:	# iterate forever, each time through while loop re-read directory contents
	dirlist = os.listdir(path)
	numfiles = len(dirlist)
	for i in range(numfiles):
	

		f = dirlist[int(random.uniform(0,numfiles))]

    		try:
        		image = Image.open(path + "/" + f)      # for Unix style pathnames
    		except:
        		continue

    		stats = os.stat(path + "/" + f) 
		strdate = time.strftime("%d %B %Y", time.localtime(stats[8]))
    		creationstring = os.path.splitext(f)[0] + " sent on " + strdate
    		win.title(creationstring)

    		image = maxSize(image, (800,800), 3)
    		photo = ImageTk.PhotoImage(image)   

    		can.config(width=photo.width(), height=photo.height()) 
                # Determine where to center the window on the screen
    		top = win.winfo_toplevel()
    		w = photo.width()
    		h = photo.height()
    		x = (sw - w)/2
    		y = (sh - h)/2
    		geom = '%dx%d+%d+%d' % (w, h, x, y)
    		top.geometry(geom)
       
    		can.create_image(2, 2, image=photo, anchor=NW)

    		win.update()
    		time.sleep(3)
	#end for
#end while

win.destroy()
#
```end

---

