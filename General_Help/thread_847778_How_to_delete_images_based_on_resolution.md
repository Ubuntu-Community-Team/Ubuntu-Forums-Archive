---
title: "How to delete images based on resolution?"
date: 2008-07-02
forum: General Help
---

### Post by AustinMatherne on 2008-07-02
I have a folder full of 400 animated gifs, and I need to delete any of them that have a width, or hight over 100 pixels. I also need to delete those that are under 80 pixels in width or hight.

Is there a script, or program that can do this?

Thanks,
~Austin

---

### Post by kaibob on 2008-07-02
I'm trying to learn shell scripting and wanted to give this a try. It's important to have a backup of all files until the script is properly tested.  

> #!/bin/bash
cd /target/directory
for file in *.gif ; do
newfile=$file[0]
imageheight=$(identify -format %h $newfile)
imagewidth=$(identify -format %w $newfile)
if [ $imageheight -gt 100 -o $imageheight -lt 80 ] ; then
rm $file
elif [ $imagewidth -gt 100 -o $imagewidth -lt 80 ] ; then
rm $file
fi
done

To save a text file with a listing of the removed files and their image height and width, add the following after the rm commands:

> echo $file ${imageheight}x${imagewidth} >> removed_files

---

### Post by unutbu on 2008-07-02
First install the imagemagick package.

Next, save the following in a file called unlink-big-images.py.
```

#!/usr/bin/python
# Usage
#     ./unlink-big-images.py   path/to/directory/of/gifs
# This script will unlink any image that has a width or height over 100 pixels

import os
import sys
import re
pat=r'^(?P<width>\S+)\s+(?P<height>\S+)'
                
dir=os.path.normpath(sys.argv[1])
if not os.path.isdir(dir):
    print "%s is not a valid directory"%dir
    exit

for root, dirs, files in os.walk(dir,False):
        for name in files:
            filename=os.path.join(root, name)
            (pathpart,ext)=os.path.splitext(filename)

            if ext == '.gif':
                print "Processing %s (%s)"%(filename,ext)

                cmd='identify -format \"%w %h \" '+"%s"%filename
                try:
                    sock=os.popen(cmd,'r')
                except:
                    print "%s failed"%cmd                
                    continue
                else:
                    result=sock.readline()
                    amatch=re.search(pat,result) 
                    if amatch:
                        width=amatch.group('width')
                        height=amatch.group('height')
                        print "    width=%s, height=%s"%(width,height)
                        if (width>100) or (amatch.group('height')>100):
                            try:
                                print "    unlink %s"%filename
#                                os.unlink(filename)
                            except:
                                print "    Failed to unlink %s"%filename
                                
                                
                        else:
                            print "No match"
                                

```
Make the script executable:
```

chmod 755 unlink-big-images.py

```
If the directory with the gifs is called images, run the script like this:
```

./unlink-big-images.py images

```

As it stand, the script will only print out messages like this:
```

unlink a.gif
unlink b.gif

```
This is to give you an opportunity to check that the script is working properly without actually deleting anything. When you are satisfied the script works, edit it by removing the pound sign (#):

Change
```

                            try:
                                print "    unlink %s"%filename
#                                os.unlink(filename)

```

to 

```

                            try:
                                print "    unlink %s"%filename
                                os.unlink(filename)

```

(PS. I can't wait to see y'alls awk one-liners that can do the same thing! hehe!)

---

### Post by AustinMatherne on 2008-07-02
unutbu, it deleted all of them, except for "animated-avatars0096.gif" that was 70x60. I backed them up, so it's fine.

```
Processing images/animated-avatars0214.gif (.gif)
    width=100, height=100
    unlink images/animated-avatars0214.gif
[B]Processing images/animated-avatars0096.gif (.gif)
identify: Corrupt image `images/animated-avatars0096.gif'.[/B]
Processing images/animated-avatars0686.gif (.gif)
    width=80, height=100
    unlink images/animated-avatars0686.gif
```

Any ideas?

---

### Post by twistedumbrella on 2011-07-07
> **kaibob said:**
> I'm trying to learn shell scripting and wanted to give this a try. It's important to have a backup of all files until the script is properly tested.  



To save a text file with a listing of the removed files and their image height and width, add the following after the rm commands:

I did a restore on an sdcard that was wiped recently and the 500 lost photos were now 99000 icons, thumbnails, and pictures. The folder took almost 15 minutes just to open and my original idea was to simply delete any files under a certain size until it hit me that I have some 5MP images that aren't any more than 500kB. After seeing your post, and being a little crazy when it comes to scripting, I wrote something a little more reusable that I have tested and worked out perfect. Thanks for the inspiration

#!/bin/bash

# Thunbnailer thumbnail removal
# Original by kaibob of Ubuntu Forums
# Modified by Twisted Playground

cd /
echo "Please enter file directory:"
echo -n "/"
read imagedir
echo "Please enter image dimensions:"
echo -n "Height/Width? "
read userheight
echo -n "Width/Height? "
read userwidth
imageloc="/"$imagedir
cd $imageloc
echo "# Thumbnailer Deleted Files" > thumbnailer.bak
for file in *.jpg ; do
newfile=$file[0]
imageheight=$(identify -format %h $newfile)
imagewidth=$(identify -format %w $newfile)
if [ $imageheight -lt $userheight ] ; then
   if [ $imagewidth -lt $userwidth ] ; then
      rm $file
      echo $file": "$imageheight" x "$imagewidth >> thumbnailer.bak
   fi
elif [ $imagewidth -lt $userheight ] ; then
   if [ $imageheight -lt $userwidth ] ; then
      rm $file
      echo $file": "$imagewidth" x "$imageheight >> thumbnailer.bak
   fi
fi
done
echo "Would you like to view deletions?"
echo -n "(Y/n) "
read showdeleted
case $showdeleted in
y)
cat thumbnailer.bak
echo "Process complete. Thank you!" 
exit
;;
Y)
cat thumbnailer.bak
echo "Process complete. Thank you!" 
exit
;;
*)
echo "Process complete. Thank you!" 
exit
;;
esac

---

