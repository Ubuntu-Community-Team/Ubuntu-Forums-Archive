---
title: "Python save jpg with time and date."
date: 2014-05-02
forum: General Help
---

### Post by timsdeepsky on 2014-05-02
Hello,,
I am not able to successfully make this python code save the jpg with the current date and time....
```
#!/usr/bin/python

import Image
import ImageChops
import sys
import glob
import os


try:
    dir_images = sys.argv[1]
    dir_results = sys.argv[2]
except IndexError:
    print "No directories specified."

images = []
os.chdir('/media/SamsungDisk3/uhvo_replacement_test/images' )

for files in glob.glob("*.jpg"): 
    images.append(files)
    if len(images) is 2: 
        print images[0]
        background = Image.open(images[0])
        overlay = Image.open(images[1])
        
        print images[1]
        background = background.convert("RGBA")
        overlay = overlay.convert("RGBA")
        
        ImageChops.lighter(background, overlay).save('/home/tim/Desktop/final_stacked_images/final'+"result_%06d.jpg")
        
  
```
The above code works for me and saves the jpg as "finalresult_%06d.jpg"....
I try to integrate this code and it throws syntax errors.
```
ImageChops.lighter(background, overlay).save('/home/tim/Desktop/final_stacked_images/final'+result_{}.jpg'.format(datetime.datetime.now().strftime('%s')) 
```
Here is the error.
```
File "/media/SamsungDisk3/uhvo_replacement_test/images/script_2.py", line 31 ^ SyntaxError: invalid syntax 
```
It seemt to not like the very end of the code,,like i am not closing it right....
Thanks for any help you may have....

---

### Post by steeldriver on 2014-05-02
You could try either

```
filename = "/home/tim/Desktop/final_stacked_images/final_result_%s.jpg" % datetime.datetime.now().strftime("%s")
ImageChops.lighter(background, overlay).save(filename)
```

or simple string concatenation

```
filename = "/home/tim/Desktop/final_stacked_images/final_result_" + datetime.datetime.now().strftime("%s") + ".jpg"
ImageChops.lighter(background, overlay).save(filename)
```

---

### Post by timsdeepsky on 2014-05-02
Thanks for your reply....
I tried them both and they generate this error....
```
Traceback (most recent call last):
  File "/media/SamsungDisk3/uhvo_replacement_test/images/script_2.py", line 31, in <module>
    filename = "/home/tim/Desktop/final_stacked_images/final_result_" + datetime.datetime.now().strftime("%s") + ".jpg"
AttributeError: type object 'datetime.datetime' has no attribute 'datetime'
tim@tim-quad-core:/media/SamsungDisk3/uhvo_replacement_test/images$ 



```
I added ```
from datetime import datetime, date, time
import time
``` to the script and it did'nt help either....
I will keep on studying it....
Thanks steeldriver....

---

### Post by steeldriver on 2014-05-02
I think you need to do **either**

```

**import datetime**
.
.
.
**datetime.datetime.**now().strftime("%s")

```
**or **
```

**from datetime import datetime**
.
.
.
**datetime**.now().strftime("%s")

```

---

### Post by timsdeepsky on 2014-05-03
I have had some luck and now this is working....
At first i had the 
```
import datetime
# get the date to add to caption and file name
datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")

```
in the wrong place....
This is the working code 
```
#!/usr/bin/python

import Image
import ImageChops
import sys
import glob
import os
import datetime
# get the date to add to caption and file name
datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")

try:
    dir_images = sys.argv[1]
    dir_results = sys.argv[2]
except IndexError:
    print "No directories specified."

images = []
os.chdir('/media/SamsungDisk3/uhvo_replacement_test/images' )

for files in glob.glob("*.jpg"): 
    images.append(files)
    if len(images) is 2: 
        print images[0]
        background = Image.open(images[0])
        overlay = Image.open(images[1])
        
        print images[1]
        background = background.convert("RGBA")
        overlay = overlay.convert("RGBA")
        

        filename = "/home/tim/Desktop/final_stacked_images/final_result_" + datetime.datetime.now().strftime("%d_%m_%Y_%H:%M:%S") + ".jpg"
ImageChops.lighter(background, overlay).save(filename)
                                                                                                
```



and names my final jpg like this
```
final_result_03_05_2014_09:16:31.jpg
```
Thanks a million steeldriver....

---

### Post by timsdeepsky on 2014-05-04
I spoke too soon....
This part,
```
ImageChops.lighter(background, overlay).save(filename)
```
is not being performed....
I think it is because it comes after everything else....
I will move things around and see if i can fix it....

---

### Post by steeldriver on 2014-05-04
If you want to save each file (in the loop) then you need to indent the save statement to match the rest of the loop statements

The way it is written now, the save statement is only executed once, after the loop has finished

---

### Post by timsdeepsky on 2014-05-04
Hello steeldriver,,and thanks for your help....
I can indent like you said,,,,and i am still only getting it to stack 2 images....
Let me show you what the issue is now....
With the original code i was using,
```
#!/usr/bin/python

import Image
import ImageChops
import sys
import glob
import os


try:
    dir_images = sys.argv[1]
    dir_results = sys.argv[2]
except IndexError:
    print "No directories specified."

images = []
os.chdir('/home/tim/Desktop/keep' )
os.mkdir('/home/tim/Desktop/keep/fat')

for files in glob.glob("*.jpg"): 
    images.append(files)
    if len(images) is 2: 
        print images[0]
        background = Image.open(images[0])
        overlay = Image.open(images[1])
        
        print images[1]
        background = background.convert("RGBA")
        overlay = overlay.convert("RGBA")
        
        ImageChops.lighter(background, overlay).save('/home/tim/Desktop/keep/final'+"result.jpg")
        
        images = []
        images.append('/home/tim/Desktop/keep/final'+"result.jpg")
```
I was able to stack multiple images and see the lighter results in all images(like all meteors in a shower in the final image)....
Now since i the timestamp is integrated into it and working,,(and works well thanks to your help)
```
#!/usr/bin/python

import Image
import ImageChops
import sys
import glob
import os
import datetime
# get the date to add to caption and file name
datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")

try:
    dir_images = sys.argv[1]
    dir_results = sys.argv[2]
except IndexError:
    print "No directories specified."

images = []
os.chdir('/media/SamsungDisk3/uhvo_replacement_test/images' )

for files in glob.glob("*.jpg"): 
    images.append(files)
    if len(images) is 2: 
        print images[0]
        background = Image.open(images[0])
        overlay = Image.open(images[1])
        
        print images[1]
        background = background.convert("RGBA")
        overlay = overlay.convert("RGBA")
        

        filename = "/home/tim/Desktop/final_stacked_images/final_result_" + datetime.datetime.now().strftime("%d_%m_%Y_%H:%M:%S") + ".jpg"
        ImageChops.lighter(background, overlay).save(filename)
   
```
the code only stacks 2 images and neglects the rest of them....
[IMG]http://www.timcline.org/pic_compare/finalresult_original.jpg[/IMG][IMG]http://www.timcline.org/pic_compare/final_result_04_05_2014_09:25:01.jpg[/IMG]

I have been studying this online for a time....Thanks for all your help....I am still learning python....

---

### Post by steeldriver on 2014-05-04
I don't really understand how your program works (appending the file to the images list and then setting images back to an empty list and appending the modified image?) but that seems to be the missing part of your new code i.e.

OLD:
```
        ImageChops.lighter(background, overlay).save('/home/tim/Desktop/keep/final'+"result.jpg")
        
[B]        images = []
        images.append('/home/tim/Desktop/keep/final'+"result.jpg")[/B]
```
NEW:
```
        filename = "/home/tim/Desktop/final_stacked_images/final_result_" + datetime.datetime.now().strftime("%d_%m_%Y_%H:%M:%S") + ".jpg"
        ImageChops.lighter(background, overlay).save(filename)
```

---

### Post by Vaphell on 2014-05-04
not related to the problem at hand, but you should avoid hardcoding paths all over the place. If you have crucial dirs called everywhere, store them in variables at the top of the script and use these instead. That way you would be able to easily reorganize should the need arise, because 1 change of the variable will propagate everywhere automatically. With hardcoded paths every one of them needs to be reevaluated and edited if necessary.

example
```
import os

keep_dir = os.path.join( os.environ['HOME'], 'Desktop/keep' )
src_dir = ...
...

filename = os.path.join( keep_dir, 'final_result.jpg' )
```

---

### Post by timsdeepsky on 2014-05-04
steeldriver,,
I am aware that i am missing part of the old code....I am still struggling to integrate this:
```
        filename = "/home/tim/Desktop/final_stacked_images/final_result_" + datetime.datetime.now().strftime("%d_%m_%Y_%H:%M:%S") + ".jpg"
        ImageChops.lighter(background, overlay).save(filename)
```
With this:
```
ImageChops.lighter(background, overlay).save('/home/tim/Desktop/keep/final'+"result.jpg")
        
        images = []
        images.append('/home/tim/Desktop/keep/final'+"result.jpg")
```
and make all of it work....
My original code would take my existing folder of images and stack them perfect ,so all the lighter pixels were in the final image(somehow this original code worked with ImageChops.lighter)....
When i originally asked for help to name the jpeg with the current date and time,,,,
i was able to use one of the codes you helped me with:
```
       filename = "/home/tim/Desktop/final_stacked_images/final_result_" + datetime.datetime.now().strftime("%d_%m_%Y_%H:%M:%S") + ".jpg"
ImageChops.lighter(background, overlay).save(filename)

```
and get it working with the date and time....But i could not use the:
```
images = []
        images.append('/home/tim/Desktop/keep/final'+"result.jpg")
```
because the code would fail,,and not produce the final image....
So in leaving out the:
```
images = []
        images.append('/home/tim/Desktop/keep/final'+"result.jpg")
```
now the code will only stack 2 images,,but saves the final image with the date and time like i wanted....
My task now is to figure out how to get it saving with date and time(this i can do),while actually stacking all the images in the folder(this i can do without saving the image with the current timecode)....
I know my codes are very crude and rough,,but i have been studying on this stuff for a while and sometimes the confusion sets in on me....
Just so you know what the heck i am even doing,,,,i have a meteor capture station..
It runs 24/7 and stacks 2 minute images from one camera,,and 27/7 video from another camera....
I currently use UHVO [https://sites.google.com/site/linuxuhvo/]("https://sites.google.com/site/linuxuhvo/")
to capture my 2 minute exposures....But i would like to upgrade to 14.04 from 12.04,,and UHVO does not work on 14.04,,and i can not seem to get in touch with the maintainers of UHVO....
So i think it is a dead project....I posted in these forums for help on a fix for the issue [http://ubuntuforums.org/showthread.php?t=2220380&p=13005198#post13005198]("http://ubuntuforums.org/showthread.php?t=2220380&p=13005198#post13005198"),but no luck and i feel the need to strike out on my own and learn to code for this so i may deal with issues myself in the future....
By the way,,this process starts with cron running a bash file,,and grabbing all the images from my meteor cam....The python script that is giving me issues is ran in the bash script....All works except what i said above....
Thank you for all the help....I know this is confusing....

---

### Post by timsdeepsky on 2014-05-04
Vaphell,,thank you....I will work on this too....

---

### Post by timsdeepsky on 2014-05-05
I have managed to get this working....
It now saves the jpeg with the time and date,,and actually stacks all images instead of a few before saving it....
Thanks to steeldriver and Vaphell for all the help....
Truly....
Here is the working code....
```
#!/usr/bin/python

import Image
import ImageChops
import sys
import glob
import os
import datetime
# get the date to add to caption and file name
datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")

try:
    dir_images = sys.argv[1]
    dir_results = sys.argv[2]
except IndexError:
    print "No directories specified."

images = []
os.chdir('/media/SamsungDisk3/uhvo_replacement_test/images' )

for files in glob.glob("*.jpg"): 
    images.append(files)
    if len(images) is 2: 
        print images[0]
        background = Image.open(images[0])
        overlay = Image.open(images[1])
        
        print images[1]
        background = background.convert("RGBA")
        overlay = overlay.convert("RGBA")
        
        ImageChops.lighter(background, overlay).save('/home/tim/Desktop/final_stacked_images/final_result_' + datetime.datetime.now().strftime("%d_%m_%Y_%H:%M:%S") + ".jpg")
        
        images = []
        images.append('/home/tim/Desktop/final_stacked_images/final'+"result.jpg")



```

---

