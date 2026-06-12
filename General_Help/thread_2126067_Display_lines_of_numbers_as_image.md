---
title: "Display lines of numbers as image"
date: 2013-03-15
forum: General Help
---

### Post by spiritech on 2013-03-15
if i have a file containing numbers that represent colours how can i display them as an image.

so file would look something like this.

```
#!/bin/bash

16 24 386 24 16 8 32 36 
386 24 8 26 16 36 386
28 16 32 42 342 98 36 8
342 98 36 8 386 24 16 8
8 26 16 36 8 386 24 16
386 24 8 26 36 8 386 24
98 36 8 386 8 386 24 16
16 36 8 386 342 98 36 8
```

so each newline in the file represents a new line in the image.

please note that the numbers are only an example and probably do not represent actual colours.

spiritech

---

### Post by Stonecold1995 on 2013-03-16
I don't really know what you mean...  Is this some kind of format which stores images as numbers in text?

---

### Post by sudodus on 2013-03-16
Please explain what you want to do!

- Do you want to make an own format for pictures (like jpeg, png ...)?
- Or do you want to create some specific output, for example an animated picture with some patterns?

I think the old icon format in Windows and the bmp (bitmap) format are  primitive and maybe possible to understand from looking at the data in a  hex viewer/editor.

---

### Post by Impavidus on 2013-03-16
Looks a bit like netpbm format: [http://en.wikipedia.org/wiki/Netpbm_format](http://en.wikipedia.org/wiki/Netpbm_format)

Maybe you can add a header using a text editor and make your image viewer believe it's a .pgm file. Else, you may have to write some code to convert it to something else or write your own viewer.

---

### Post by spiritech on 2013-03-17
>                                       [                                                      [IMG]http://ubuntuforums.org/customavatars/avatar1499021_1.gif[/IMG]                                              ]("http://ubuntuforums.org/member.php?u=1499021")                                                                                     [**[COLOR=#000000]sudodus[/COLOR]**]("http://ubuntuforums.org/member.php?u=1499021")

Please explain what you want to do!

- Do you want to make an own format for pictures (like jpeg, png ...)?
- Or do you want to create some specific output, for example an animated picture with some patterns?

I think the old icon format in Windows and the bmp (bitmap) format are   primitive and maybe possible to understand from looking at the data in a   hex viewer/editor.                 

what i want to do: i was hoping to be able to output those numbers to a program to generate an image. each line would (in this example) create an image 8 pixels in width and would be a totla of 8 pixels in height. i would have thought there would be a program or a way of doing this.

reason i want to do it: i figured if i had some files with many lines of values representing colours (not necessarily 8x8). i could then play around with the values using awk or something and see what happens, see what kind of results i can get.

would i really have to make my image format to do this. surely there is a program (some where) that can render values as colours line by line.

my procces would be along the lines of this. (i have written this in non code format)

```
read line one pass to render
read line two pass to render
read line three pass to render
```

welll i suppose the code would be something like this.

```
while read -r "value"; do "$value" render; done < value-file
```

i suppose i am half way there, i just need to figure out how to render the values as a picture on screen. i assume it is my graphics cards job to undrstand the values i am sending it.

---

### Post by spiritech on 2013-03-17
removed

---

### Post by sudodus on 2013-03-17
I suggest that you search for*** imagemagick tutorial*** on the internet and start reading some of the good tutorials about that program package. You will find ways to use some of the tools in the imagemagick package to render the pictures you want. Start with commands as described in the tutorials and manual pages of ***convert***, and later on maybe you can get the source code and work directly with that.

```
sudo apt-get install imagemagick
```

*Edit*: I'm using imagemagick convert, but I have not looked into the source code. Have a look at steeldriver's opencv, it might be be somewhere between convert and its source code in abstraction level.

---

### Post by steeldriver on 2013-03-17
You could also maybe take a look at opencv - perhaps python-opencv in particular, which seems to have methods to create image objects direct from numpy arrays:

[http://opencv.willowgarage.com/documentation/python/core_operations_on_arrays.html#fromarray](http://opencv.willowgarage.com/documentation/python/core_operations_on_arrays.html#fromarray)

[DISCLAIMER: I haven't used it, I'm just starting to play with opencv for a little image processing project]

---

### Post by Vaphell on 2013-03-17
have you figured out how the value=>rgb transformation is supposed to look like?

in python it's trivial

```
#!/usr/bin/env python

import Image

size = 8, 8
data = [ <array of pixel values> ] # figure this out and you are set

img = Image.new( "RGB", size )
img.putdata( data )
img.save( "file.png" )
```

i wrote 2 different functions for the tranformations, one in grayscale scaling all values down so max value becomes 255 and another that assumes R=255*hundreds/10, G=255*tens/10, B=255*ones/10 and i got abstract pixel soups :)

```

src = [ ... ] # input data

def f1( x, mx ):
  return ( x*255/mx, x*255/mx, x*255/mx )
data1 = [ f1(x,max(src)) for x in src ]

def f2( x ):
  return (255*(x%1000)/1000, 255*(x%100)/100, 255*(x%10)/10 )
data2 = [ f2(x) for x in src ]
```

---

### Post by prodigy_ on 2013-03-17
> **steeldriver said:**
> You could also maybe take a look at opencv
+1

```
sudo apt-get install libcv2.3 python-opencv python-numpy
```

A simple example (creates a 100x100 PNG file with a single 10x100 gray stripe at the top:
```
#!/urs/bin/env python

import cv

width = 100
height = 100
bit_depth = 8
channels = 3

image = cv.CreateImage((width, height), bit_depth, channels)

color = cv.RGB(127, 127, 127)
start = (0, 0)
end = (99, 9)
cv.Rectangle(image, start, end, color, -1)
 
cv.SaveImage("test.png", image)
```

Colors and start/end coordinates can be stored in lists of tuples. Then you can iterate over those lists in a for loop. For more info about python-opencv, see the [reference guide](http://opencv.willowgarage.com/documentation/python/index.html).

---

### Post by zero2xiii on 2013-03-17
Hay,

That format you wish to use if VERY similar to the ILDA standart used by laser displays.
[http://www.laserfx.com/Backstage.LaserFX.com/Standards/ILDAframes.html](http://www.laserfx.com/Backstage.LaserFX.com/Standards/ILDAframes.html)

Without any change you should be able to open a file containing that format of colour values in any of the ILDA tools and render a bitmap.

Good luck though. It MIGHT not be as easy, I can not try this at the moment.

:)

---

### Post by spiritech on 2013-03-19
maybe i should rephrase my quesion and explanation. 

how can i display a set of values as coloured pixels onscreen ( ideally   in another terminal, or if needs be, undressed onscreen somewhere )    from the terminal command line interface?

example.

[http://www.pasteall.org/pic/47554](http://www.pasteall.org/pic/47554)

i am not exactly sure how image rendering works. i dont really want to   have to create an image file if necessary. more over i would like to be   able to directly render the image to the graphics card for display.  this  must be what an image viewer does, at the core, read values from a  file  decodes them and then sends them to the graphics card for  processing  into an image. i imagine that it is sent in binary form (  maybe not ) to  the graphics card unless of course the graphics card is  capable  decoding. and this is what i would like to do. send values  directly to  my processor, graphics card to be displayed as coloured  pixels. i am not  bothered at what level i would have to do this at or  type of code.

what format would i have to send the graphics card. would it be binary. RGB values etc?

if i were rendering directly onto the screen and not into another   terminal. how would i control the position, through a co-ordinates   figure? or would i have to use a leading and trailing zero value?

if i were rendering into a terminal then, the terminal would need to be   active so that the image is refreshed and not have to open a new   terminal each time. so i understand that the terminals function would be   to tell the render where to start and where to finish. ( please note i am not fussed if it is displayed in a terminal or not. just on screen is fine).

i hope this explains enough of what i am trying to do. _




thankyou Vaphel and prodigy_ for your replies, however i am not really   concerned about how to generate an image file ( though your suggestions   are still helpful ). i have had a look at Impavidus's link and this   looks like the right type of file format i could use, though it would be   handy if i could use a format that had one value for each colour   instead of the three rgb values.

---

### Post by Impavidus on 2013-03-19
I don't know of a simple command that does this, but maybe it exists. You could also try a general data plotting library (like [pyplot]("http://matplotlib.org/examples/api/image_zcoord.html"), you'd have to learn python) or program ([gnuplot]("http://gnuplot.sourceforge.net/demo/heatmaps.html") for example. It's basic, but with some effort capable of producing images ready for publication). In both cases you can write a simple script to do the setup. I rarely use those tools, so I can't tell you exactly how to use them.

Directly sending the data to your graphics card (in binary) gives you ultimate flexibility, but is nothing less than writing your own image viewer. You need some knowledge of C and openGL programming to do so. Writing a tool to convert your numbers to some standard image format would be easier.

---

### Post by prodigy_ on 2013-03-19
With **fbterm** you could probably output directly to display instead of saving to a file. E.g using [pygame](http://stackoverflow.com/questions/11608454/frame-buffer-module-of-python).

---

### Post by spiritech on 2013-03-19
the link looks good. i had searched the synaptic for something that might be able to help and found other framebuffer tools like fim and fbi, maybe they can help. 

as to what Impavidus mentioned

> Directly sending the data to your graphics card (in binary) gives you  ultimate flexibility, but is nothing less than writing your own image  viewer. You need some knowledge of C and openGL programming to do so.

i do not have much scripting/programming experience. i learnt the very basics of bash and i am interested in learning more. are there any simple example programs, showing how to make windowed input boxes and buttons?

i realize this is changing subject so is there somewhere else this thread could go so that it can keep going?

---

### Post by spiritech on 2013-03-19
thankyou for all your help so far. i have looked at most the options, and well i am a little lost. so i will explain one more time, this time the overall reason for my questions.

i would like to display ( say a blank image ) then make changes to the image mathimatically, and view the results as they happen.

an example wold be, apply formula to each pixel or Nth pixel ,from left to right, from right to left or from middle to edges etc.

is there a program for this please?

---

### Post by sudodus on 2013-03-20
Maybe you can get the source code of some nice screensaver, and modify its engine to create your own patterns.

---

### Post by Impavidus on 2013-03-20
> **spiritech said:**
> 
i do not have much scripting/programming experience. i learnt the very basics of bash and i am interested in learning more. are there any simple example programs, showing how to make windowed input boxes and buttons?For windowed input boxes and buttons, have a look at the GTK library.

> **spiritech said:**
> 
i would like to display ( say a blank image ) then make changes to the image mathimatically, and view the results as they happen.

an example wold be, apply formula to each pixel or Nth pixel ,from left to right, from right to left or from middle to edges etc.

You can take the output functions of a nice screen saver (there are some that work more or less the way you want for your program) and add your own mathematical functions. Or you can use some scripting and a data plotting library. Python may be the right language, but I don't have much experience with it.

---

