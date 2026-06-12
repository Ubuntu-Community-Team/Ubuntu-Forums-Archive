---
title: "Opening an .xdp file"
date: 2018-09-13
forum: General Help
---

### Post by jgwphd on 2018-09-13
I am not sure if this is the correct place to pose this question. If not, could someone give me a pointer to where. 

I am trying to open an .xdp file which is a "file format developed by Adobe Systems for packaging PDF data into XML files; contains the entire PDF document contents  including form and template data; may also include character-encoded  sections for binary content." (quote from [https://fileinfo.com/extension/xdp](https://fileinfo.com/extension/xdp) ) 

Are there any Ubuntu applications which will allow me to open, read and print these .xdp files or convert them to a standard PDF file? ...I don't need write privileges at this time.

Thanks for any assistance.

---

### Post by Autodave on 2018-09-13
The only thing that I can think of would be to install Adobe Reader for Windows into Wine.

---

### Post by jgwphd on 2018-09-13
Thanks for the response @Autodave but I tried wine a few years ago and gave up on it with all the problems I ran into. I rather have a solution that doesn't need wine. This is not a complaint about wine, but my reason for using Ubuntu is to get away from Microsoft and I only need to view and print an .xdp file.  

Does anyone else have any suggestions?  I'd really appreciate a non-wine solution. Thanks!!

---

### Post by jgwphd on 2018-09-14
Anyone? ...their has to be someplace that converts an .xdp file to a pdf (or something else) or an Ubuntu application that can open it....

Again Thanks for any assistance

---

### Post by #&amp;thj^% on 2018-09-14
The .xdp file extension was developed by Adobe Systems and used as XML files in an XML Data Package format. 
.XDP File Extension
File TypeXML Data Package
Developer	Adobe Systems
You are going to have to jump through hoops to get this done.
I just convert it to text file with:
```
pdftotext '/home/me/Documents/gimpbasics.pdf' /home/me/Sample.txt

```
Now the file reads:
```
GIMP Basics
Welcome to the GIMP
Kind of like a free Photoshop, the
GIMP (which stands for GNU Image
Manipulation Program) allows you to
do pretty much anything with images.
1. Tool Box
2. Tip of the Day (or the startup)
3. Layers and history panel.
Although the GIMP can do many
things, this tutorial is designed to show
you how to crop an image, recolor an
image black and white, slice and move
an object and how to save an image.

Opening an image
1. We open an image by clicking on
File-->Open in Panel 1 (Tool Box
panel).
2. The image appears in Panel 2, the
workspace (you can think of it as a
digital pasteboard where you are
looking at the photo in the middle of
your work area which is flanked by
tools and information pertaining to the
object you are working on).
3. Here you can see the layers in the
file. In this case I pasted this image into
the GIMP

GIMP Basics - 1

Cropping an image
The cropping tool is located in the
toolbox (circled in red). Select it and
draw a box around the area you want
to keep.

Results of the Cropped Image
Here are the results of the cropped
image.

GIMP Basics - 2

Scale Image
1. To resize an image, click on Scale
Image

Scale Image Dialogue box
1. In the Scale Image Dialog box, you
can resize the image by adjusting the
width and height.
2. Click on "Scale" to scale the image.

GIMP Basics - 3

Saving an Image
To Save an image, select File-->Save
as from the main work area where the
image is shown.

Save the image we scaled as a JPEG
Here is the scaled picture being saved
as a JPEG
1. Name the file
2. Location (in our case it is on the
desktop)
3. Select the File Type (the GIMP has
tons of these, but we want JPEG)
4. Click Save to save the file.

GIMP Basics - 4

To Recolor an image Black & White
Click on Image-->Mode-->Black & White
You can also work with other colors
here (B&W is just a common request)

Results of the Mode Transformation to Black & White
The transformation applied in one click.

GIMP Basics - 5

Moving Wilbur's head...
Wilbur is the mascot of GIMP. In this
example we will move Wilbur head into
the white space on our main image.
1. First we will take a screen shot and
crop it so that all we can see is his
head.

Moving Wilbur's Head (continued)
1. OK we have Wilbur and we have the
main image. We are going to use the
selection tool (circled in red) and draw
a box around Wilbur.
2. We will Edit-->Copy the selected
area (Wilbur)
3. We will edit paste into the other
window where the dialog box is.

Select Wilbur

GIMP Basics - 6

Wilbur is now ready to move into position...
1. Wilbur is now pasted as a new layer
in the window containing the screen
shot.
2. We can now click on him and move
him into position for our next screen
shot.

GIMP Basics - 7

Wilbur finds a perfect position
Note, when you click away from him,
the marching ants (or the fence around
Wilbur will disappear.

GIMP Resources
For More on the GIMP:
Download it at home:
http://www.gimp.org/
Help and Tutorials:
http://www.gimp.org/tutorials/

GIMP Basics - 8


```
EDIT: Also worth noting "Be careful not to rename the extension on .xdp files, or any other files. This will not change the file type. Only special conversion software can change a file from one file type to another. "
Also this just might help: [https://help.adobe.com/en_US/livecycle/10.0/ProgramLC/WS624e3cba99b79e12e69a9941333732bac8-7d3d.html](https://help.adobe.com/en_US/livecycle/10.0/ProgramLC/WS624e3cba99b79e12e69a9941333732bac8-7d3d.html)

---

### Post by jgwphd on 2018-09-14
1fallen, thanks for the info/instructions. This is getting a bit complicated for something I am unlikely to repeat ...as you stated, "You are going to have to jump through hoops to get this done". 

Anyone know what the real purpose of these .xdp files are? IMHO, it seems to be more about purposeful file format restrictions that result in pushing adobe products than allowing wide access and sharing documents. I assume the reason for the lack of tools to work with .xdp files is intellectual property restrictions, but I don't know for sure. Comments anyone? 

Anyone else have any solution suggestions? 

Again, thanks for any assistance.

---

### Post by him610 on 2018-09-15
You may want to check out this link...
[https://fileinfo.com/extension/xdp]("https://fileinfo.com/extension/xdp")

---

### Post by #&amp;thj^% on 2018-09-15
> **jgwphd said:**
> 

I have learned over the years, when someone needs to send me a file like this that they send it to me in a PDF format.
I have heard that Foxit Reader also "might" work on your .xdp. But I have no first hand knowelge to say for sure.
[quote]Software that will open, convert or fix XDP files

    Foxit Reader
    Verified
    Adobe LiveCycle Designer ES
    User Submitted
    Adobe LiveCycle Designer
    User Submitted
    Adobe Reader
    User Submitted
    Adobe Acrobat Reader DC
    Us
info found here: [https://www.foxitsoftware.com/company/press.php?title=foxit-reader-now-available-on-mac-and-linux&id=408](https://www.foxitsoftware.com/company/press.php?title=foxit-reader-now-available-on-mac-and-linux&id=408)

This is how I install it: [https://www.linuxbabe.com/desktop-linux/install-foxit-pdf-reader-ubuntu-16-04](https://www.linuxbabe.com/desktop-linux/install-foxit-pdf-reader-ubuntu-16-04)

---

