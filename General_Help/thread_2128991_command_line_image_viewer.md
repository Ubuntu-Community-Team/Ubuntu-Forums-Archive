---
title: "command line image viewer"
date: 2013-03-24
forum: General Help
---

### Post by spiritech on 2013-03-24
i would like to load images from a script. the script involves loading the image, changing the original image then reload it. i have tried some of the image viewers only to find they dont work in this way. 

```
#!/bin/bash

code to load image
code to change image
code to reload image
```

what be the quickest, most efficient way of doing this? (without having to close then re-open a window everytime.)

spiritech

---

### Post by llamabr on 2013-03-24
How about imagemagick and then feh?

---

### Post by spiritech on 2013-03-24
i have tried feh. only problem is that i want to reload the image to the current window, not re-open a new window everytime i reload the image. also i would have to close the current image before running anything else in the script.

---

### Post by Rebelli0us on 2013-03-25
Try xnview mp "batch" commands, otherwise you probably need someone with programming skills.

---

### Post by rnerwein on 2013-03-25
> **spiritech said:**
> i would like to load images from a script. the script involves loading the image, changing the original image then reload it. i have tried some of the image viewers only to find they dont work in this way. 

```
#!/bin/bash

code to load image
code to change image
code to reload image
```

what be the quickest, most efficient way of doing this? (without having to close then re-open a window everytime.)

spiritech
hit
did "mogrify" will solve your problem ? --> the original image file is overwritten with any  changes you request so can use it in a batch script.
comes with ImageMagick
ciao

---

### Post by Slim Odds on 2013-03-25
There is NO command line tool that will do that. That's not how COMMAND LINE tools work in the first place. If you want to continuously view and edit images, that's what GUI programs like GIMP are for.

---

### Post by haqking on 2013-03-25
> **Slim Odds said:**
> There is NO command line tool that will do that. That's not how COMMAND LINE tools work in the first place. If you want to continuously view and edit images, that's what GUI programs like GIMP are for.

You mean like GIMP batch mode which is command line and not gui ? ;-)

To the OP try GIMP batch mode [http://www.gimp.org/tutorials/Basic_Batch/](http://www.gimp.org/tutorials/Basic_Batch/)

There are also plenty of ways to do this via command line but depends on your level of comfort with command line, and also you need to be more specific such as changes you want to make, here are some examples:

[http://playingwithsid.blogspot.co.uk/2010/08/how-to-resize-photos-with-bash-shell.html](http://playingwithsid.blogspot.co.uk/2010/08/how-to-resize-photos-with-bash-shell.html)
[https://jcornuz.wordpress.com/2007/10/26/imagemagick-and-bash-batch-power/](https://jcornuz.wordpress.com/2007/10/26/imagemagick-and-bash-batch-power/)

---

### Post by Slim Odds on 2013-03-25
Maybe I misunderstood the "requirements", but if it's just a need for command line progressing then ImageMagick is the best.

---

### Post by spiritech on 2013-03-25
maybe i will have a look at an image viewer source code and see whats going on in there. i am sure it cant be that hard.

i have also found a workaround to this problem when looking at PQIV. it has the function to monitor a file for changes and, i assume, update the image when the changes occur. does anyone know any other image viewers with this function?

---

### Post by spiritech on 2013-03-26
i have looked further into this and have some new information on this matter. i have found out that with the command 

```
eog image.png &
```

i can pass the proccess to the background and return to bash. so am half way there. now all i need to find out is how to reload the image to the current window and not a new one. i will read through the help and man pages of some of the image viewers and see if any of them have this option.

or maybe i can do this just with bash, something like.

```
eog image.png & > current window
```

maybe.

if not thankyou all for your help so far.

---

### Post by spiritech on 2013-03-26
.

---

