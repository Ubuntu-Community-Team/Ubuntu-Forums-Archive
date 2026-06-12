---
title: "How to make a cursor theme"
date: 2018-02-12
forum: General Help
---

### Post by meetdilip on 2018-02-12
I checked a few other cursor themes and created some SVGs. I believe, I have almost completed the graphics part of creating a cursor theme. Can someone tell me what all files are needed for it to work other than regular SVGs ? In some cursor themes, I saw filename.cursor, build.sh and a few other files which I don't know how to include in my cursor theme. Any help would be appreciated.

---

### Post by Dennis N on 2018-02-12
Cursor files are a special type identified as "X11 cursor" by the file command:

```
dmn@Sydney:/usr/share/icons/DMZ-White/cursors$ file left_ptr
left_ptr: X11 cursor

```
Creation:
There is a command line utility called **xcursorgen** that generates cursor files from .png images. It's installed by default in Ubuntu. Read the man page for more information. It doesn't say anything about using .svg files to generate a cursor file. You need a separate file for each cursor type (left pointer, hand, cross, etc). 

Editing:
Also, you can edit existing cursors by loading them into Gimp, editing, and then resaving as an X11 mouse cursor file (.xmc).

---

### Post by meetdilip on 2018-02-12
Thanks @DennisN

This is what I have now

[https://github.com/meetdilip/Simple-Cursor](https://github.com/meetdilip/Simple-Cursor)

I have a few questions

1. What is the recommended size of cursor icons ?

2. In which format they need to be used inside a cursor ?

3. What other files are required in a cursor theme ?

> generates cursor files from .png images. It's installed by default in Ubuntu. Read the man page for more information.

Should I use PNG instead of SVG for a cursor theme ? Can you link me to the man page (?)

---

### Post by Dennis N on 2018-02-13
I think you need .png files. Size of the cursors is up to you. 24 px is the default size in Ubuntu for the DMZ cursors. The xcursorgen program creates the set of cursor files using the .png images and a configuration file that you supply for each cursor in the theme. That's all explained in the man page. You can read the man page in Ubuntu terminal by typing:

 **man xcursorgen**

The cursor's theme folder has to have a folder named **cursors** inside with the actual cursor files. You need to have all the standard cursors in there, so if you start from nothing, you have lots of artwork to do. xcursorgen program outputs the correct file type, so you don't need to specify that. Also you may see index.theme and cursor.theme files. 

It's not clear from the man page, but resizable cursors can be made by including a line for each cursor size in the config file for generating each cursor.

Example:
Run in terminal from work folder, with config and all image files in work folder:
```
dmn@Sydney:~/work$ xcursorgen left-ptr.cfg left_ptr
```
where left-ptr.cfg is
```
24 5 5 left-ptr-24px.png
32 5 5 left-ptr-32px.png
48 5 5 left-ptr-48px.png
```
creates left pointer cursor resizable to 24,32, and 48 px.

---

### Post by meetdilip on 2018-02-13
Thanks @DennisN

What about wait and progress icons ? I have 23 variants to give rotation for both of them. LaCapatine has 24. How many do we need ? Is it actually our choice ?

---

### Post by Dennis N on 2018-02-14
> **meetdilip said:**
> Thanks @DennisN

What about wait and progress icons ? I have 23 variants to give rotation for both of them. LaCapatine has 24. How many do we need ? Is it actually our choice ?

Those would be animated cursors, for which this is the advice in the man page:
> Multiple  images  with the same <size> are used to create animated cursors, the <ms-delay> value on each line indicates how long  each  image should  be  displayed  before switching to the next.  <ms-delay> can be elided for static cursors.

So the conf file would have one line for each step of the animation, the time each displays (in thousandths of a second) at the end of each line. You could have as many steps in the animation as you like. 

For spinning, I would draw just one image, then use a rotate option in Gimp to get easily make the others. No need to redraw. You could start with 4 steps (steps should be a divisor 0f 360 degrees for even motion 360/4 means use 90 degree rotations).   

config file for 32px wait cursor with 4 steps, each step lasts 250/1000 = 1/4 second.
```
32 5 5 step1-32px.png 250 
32 5 5 step2-32px.png 250
32 5 5 step3-32px.png 250
32 5 5 step4-32px.png 250

```
If your cursor theme is going to have just one size (many themes have just one size), then you are done. If you plan a resizable cursor, To get another size, just resize these 4 images using Gimp to get the images for the next size.

---

### Post by meetdilip on 2018-02-15
Thanks. Can you please share a sample config file ? I have all artwork ready ( as SVG ) other than wait and progress in the repo shared above.

My understanding so far

1. Generate required png files from SVG

2. Create a config file within the same folder as png files

3. Run this from the folder with PNGs and config file

> xcursorgen left-ptr.cfg left_ptr

---

### Post by Dennis N on 2018-02-15
> Can you please share a sample config file ?

The code display in post #4 is the contents of the actual configuration file for a left pointer (left_ptr) resizable cursor, so I will just elaborate on that. The configuration file needs to be in same folder as the image file(s) it uses. (Good idea: you might want to use a separate folder for each cursor type to avoid confusion). For a single-size regular (not animated) cursor, your configuration file would have just one line and use one image. Once all images and configuration file are in the work folder, the xcursorgen command is run from the same folder and the output appears there too. 

I would first make a single size cursor theme. What size is the cursor you are using now? Use that size for your new cursor theme. You need a configuration file and png image(s) for each cursor type.

_Animated Left Pointer Cursor:_
Config file:
```
40 14 8 left_ptr1.png 500
40 14 8 left_ptr2.png 500
```
Images attached.

Experiment and have fun. Suggest you start with one cursor and replace that one cursor in your current cursor theme to see how it looks. Back up the current cursor folder first before making any substitutions in case you want to restore the originals.

---

### Post by meetdilip on 2018-02-16
Thanks. I am using SVG right now. So, I can make the PNG at any size. Would using 24x24 be fine for a normal cursor theme ?

Do I need a config file for every PNG ? Or, one for all ( for a single size, say 24 ) ?


> 24 5 5 left-ptr-24px.png

What does 24 5 5 indicate ?

I need to put 23 files each for wait and progress. Is watch = progress ?

---

### Post by Dennis N on 2018-02-16
> Would using 24x24 be fine for a normal cursor theme ?
That's up to the user. The cursor I use is 40x40, one size only. Do a test run and see what the result looks like. Then decide.
> Do I need a config file for every PNG ? Or, one for all ( for a single size, say 24 ) ?
You need a configuration file for every named cursor, not every .png image.
> What does 24 5 5 indicate ?
The two 5's are the location of the cursor hot spot, measured from upper left corner of the square containing the cursor image - first number is pixels from left edge, second number is pixels from top edge. Adjust those coordinates to be the place you want as hot spot for the particular cursor. 24 is for selection purposes - if you have multiple sizes, the computer uses it to pick cursor of the size that you selected to use. Not sure about this, but if the actual image you used is bigger, I don't think xcursorgen will resize the .png image for you, so be sure the image used is correct size. 
> I need to put 23 files each for wait and progress. Is watch = progress ? 
Not necessarily. The watch and progress cursors are different on my current cursor theme here (Flatbed Cursor).

---

### Post by meetdilip on 2018-02-16
> You need a configuration file for **every named cursor, not every .png image**.

What does that mean ? 1 config file for all png for a single size ?

update 1 : Got it

Thanks :)

> Not necessarily. The watch and progress cursors are different on my current cursor theme here (Flatbed Cursor).                 

I am planning to use 23 icons for watch and progress. If you don't mind, which commands should I be using on them ?
> 
my current cursor theme here (Flatbed Cursor). 

Could you link to it please..

Update :

Got it, nice work

---

### Post by Dennis N on 2018-02-16
> I am planning to use 23 icons for watch and progress. If you don't mind, which commands should I be using on them ?

The configuration file would be like the code display in post #6, but with 23 lines for your 23 PNG images. The time for each line is the time you want it to display before it switches to the next image - value of 100 ms would be 1/10 sec. The xcursorgen command to create the watch cursor would not be different than any other cursors. 

A suggestion: Make the easier cursors first and leave the animated ones for later. When you finish each cursor, replace the existing cursor having the same name in your current cursor theme and see how that new cursor works. Make a backup of the current cursor theme in case you want to restore the originals.

---

### Post by meetdilip on 2018-02-16
My artwork is almost done. Can you please check this repo

[https://github.com/meetdilip/Simple-Cursor](https://github.com/meetdilip/Simple-Cursor)

---

