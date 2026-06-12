---
title: "imagemagick composite entire dir"
date: 2008-04-27
forum: General Help
---

### Post by killshot on 2008-04-27
I'm using imagemagick and i want to watermark an entire dir of images.

So far I have...

composite -compose atop -gravity southwest logo.gif *.JPG

Using mogrify doesn't work.. 
I also tried %x.jpg and that only made one image (and made the logo transparent for some reason)

Any suggestions?

Thanks!

---

### Post by ryanhaigh on 2008-04-27
```

#!/bin/bash
#Script to add watermark logo.gif to all jpg images

for imagefile in `ls *.jpg`
do
composite -compose atop -gravity southwest logo.gif imagefile
done
exit

```

Save the script in a text document in the directory containing the images and logo.gif called watermark.sh or whatever you want.

Open the terminal and cd  to the directory then use
```

chmod +x watermark.sh
./watermark.sh

```

---

### Post by noynac on 2008-04-28
ryanhaigh,

Thanks for the script. I'm trying to learn shell scripting and examples like this help.

I tried the script but couldn't get it to work as written. I have two (perhaps noobish) questions:

1) In the composite commandline, shouldn't imagefile be $imagefile?

2) Composite requires an output file. I tried new_$imagefile, and it seemed to work. 

I also wondered what would happen if the watermark file was the same image type as the input file type. I guess it would create a file named new_logo with the image type extension, which could be removed by the script with a rm command. 

Thanks again,

noynac

---

### Post by ryanhaigh on 2008-04-28
Yes thats right it should be $imagefile. You could also remove the original files if you don't want them by adding rm $imagefile after the composite line. 

So is the line now 
composite -compose atop -gravity southwest logo.gif $imagefile new_$imagefile?

---

### Post by noynac on 2008-04-28
> **ryanhaigh said:**
> ...So is the line now 
composite -compose atop -gravity southwest logo.gif $imagefile new_$imagefile?

I ran a few tests and that commandline works fine. Thanks!

---

