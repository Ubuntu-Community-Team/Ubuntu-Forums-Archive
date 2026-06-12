---
title: "Make small area of a web page image into link."
date: 2016-09-16
forum: General Help
---

### Post by Bucky Ball on 2016-09-16
Hi all. Not sure where else to park this, not directly Ubuntu, but getting a headache searching (I have a head cold which doesn't help ...). If another staff member thinks this should be somewhere else, be my guest. :)

Am creating a clickable map for a project I'm doing at uni. Don't want help with the academic stuff and the dissertation has nothing whatsoever to do with computers. :)

I've found plenty of 'link *to* a specific area on a web page' but no 'link *from* a specific area of an image on a webpage', which is what I'm after. I have attached the map in question so you get a better idea of what I'm on about.

Bottom line: how do I make a small area (a circle with a number in it on the map) of a large graphic (the map) into a link? I understand this might not be easy, I also understand I might need to use Java which I have no experience of. I'm game to try any suggestions ... within reason. :)

PS: Kompozer 0.8b3 on Xubuntu-core 16.04 LTS. (Yes, Kompozer still works!) The original was done in Libreoffice Draw where I *can* create links from the circles. Wonder if there's some trick there ... :-k

---

### Post by The Cog on 2016-09-16
I guess my first question is how do you put the pitch circle on the image? I guess the image is a GIF? 

Your browser clearly needs to know where the clickable bits are. I can think of two ways, both of which require a list of all the clickable areas details as you build the HTML page..

One is to use HTML map and area tags like this:
[http://www.w3schools.com/tags/tag_map.asp](http://www.w3schools.com/tags/tag_map.asp)
[http://www.w3schools.com/tags/tag_area.asp](http://www.w3schools.com/tags/tag_area.asp)
The area can have an href property that makes it a clickable link.

The other would be to use inline SVG to place SVG versions of the pitch icon over the image, and make the SVG object clickable. This would give more flexibility for further animation in the future, but will involve learning about SVG.

I would probably go for the second method, but I think probably the HTML map and area tags are best for you because of the simplicity.
Either way, getting the x,y positions of the pitches on the image might be the hardest and most laborious challenge. Probably a manually typed list.

EDIT: 
Re-reading, I see the image is a JPEG and the pitches are already drawn on the JPEG. This means you don't need SVG to draw the pitches, so again I think the map and area tags is the way to go. 
That is, unless you want to get fancy and have the clickable bits change colour or throb as you hover over them, in which case a tranaparent (until hovered) SVG shape drawn over the image might be useful.

---

### Post by Bucky Ball on 2016-09-16
> **The Cog said:**
> I guess my first question is how do you put the pitch circle on the image? I guess the image is a GIF?

Details at the bottom of my last. The image is a .png but I could export it as anything Draw is capable of. I was busy editing my post and didn't see yours. Thanks for the useful info. :) 

> **The Cog said:**
> Your browser clearly needs to know where the clickable bits are. I can think of two ways, both of which require a list of all the clickable areas details as you build the HTML page..

One is to use HTML map and area tags like this:
[http://www.w3schools.com/tags/tag_map.asp](http://www.w3schools.com/tags/tag_map.asp)
[http://www.w3schools.com/tags/tag_area.asp](http://www.w3schools.com/tags/tag_area.asp)
The area can have an href property that makes it a clickable link.

Figured I could do it with something along these lines. That's where I've been looking but not quite knowing how to refine my search criteria don't think (find the right words!). 

> **The Cog said:**
> The other would be to use inline SVG to place SVG versions of the pitch icon over the image, and make the SVG object clickable. This would give more flexibility for further animation in the future, but will involve learning about SVG.

Hmm. Hadn't thought of that and no, know nothing about svg, but will have a sniff there, too.

> **The Cog said:**
> ... I think probably the HTML map and area tags are best for you because of the simplicity.

... and because I don't really need much more than that. Just a link from an area of an image. Won't be expanding it beyond this map. 

> **The Cog said:**
> Either way, getting the x,y positions of the pitches on the image might be the hardest and most laborious challenge. Probably a manually typed list.

All good with that. At the project when I'm not here (and sometimes when I am) or in bed anyway, so what's a bit more in the bucket!?

Got to dash off for a bit but will drill in to those links a bit later tonight. Thanks again.

---

### Post by dragonfly41 on 2016-09-16
I suggest that you explore sikuli slides ...

[http://slides.sikuli.org/](http://slides.sikuli.org/)

To capture the target images used by sikuli I use a browser plugin ..

[https://qsnapnet.com/](https://qsnapnet.com/)

this can be installed in Firefox or Chromium browsers.

Note that there is also [http://www.sikuli.org/](http://www.sikuli.org/) for automation scripting.

---

### Post by Bucky Ball on 2016-09-16
@dragonfly41: Thanks but doubt sikuli will be of much use to me, unless I'm missing something. What I'm asking about here has nothing to do with slides. Sikuli way too involved for what I need to do. The digital section of the project needs to be straight-forward point and click for examiners, no stuffing about installing stuff from anywhere. The whole kit and kaboodle needs to be in one folder on a DVD, click the digital document and you're off! :) 

* Worth noting and not sure if I mentioned it: this is not for the web. It will come self-contained on a DVD. index.html will be opened from a link in an intro document and from there the data is viewed on a web browser locally, using local files and folders (well, on the DVD anyway) and software examiners already have installed on their computers (vid player, audio player, PDF viewer, image viewer). 

I want to turn a small section of a larger image in to a link. Please see the attachment in my first post. :)

PS: Concerning qsnap; I don't need to capture web pages. Am I missing something here?

* Update: 

[QUOTE=The Cog]One is to use HTML map and area tags like this:
[http://www.w3schools.com/tags/tag_map.asp](http://www.w3schools.com/tags/tag_map.asp)
[http://www.w3schools.com/tags/tag_area.asp](http://www.w3schools.com/tags/tag_area.asp)
The area can have an href property that makes it a clickable link.[/QUOTE]

Exactly what I'm looking for. Simple enough in theory, now to try and get my head around it! Those links were a good place to get me started. [Currently looking at this]("http://html.com/images/how-to-make-an-image-map/") and taking me a little further. Tnx. :)

---

### Post by dragonfly41 on 2016-09-16
The svg overlay route is a good one to follow.

...

Install Inkscape Vector Graphics Editor (from Ubuntu repo).

Open new file.

Set View > Zoom > Zoom 1:1

File > Import > your Rundlee Mall Map as jpg

Your targets are the circles: 1a, 1b etc.

To create a window to embed your image size go to top menu bar, extreme right cog button .. Edit properties of this document.

e.g. width: 1200 px
       height: 800 px

In left panel, Create circles, ellipses and arcs (F5)

Create first circle object ..

Set width, height to be roughly the size of your target image (set w=40, h=40)

To select created circle object, switch to the arrow at top of left panel
Select and Transform Objects (F1)

Drag circle object to overlay first target - 1a

Right click Object Properties and set opacity to about 50% just to have some idea of where your circle objects are overlaying your image.
After completion all link objects will be set to 0% opacity so they are invisible.

You can set the Title property for each overlay circle .. e.g. 1a

You can write Description for each link.

Since you require interactivity you must set the interactivity settings for each overlay object.

This is explained in this tutorial

[http://eclipsesource.com/blogs/2012/07/03/wireframing-inkscape-javascript/](http://eclipsesource.com/blogs/2012/07/03/wireframing-inkscape-javascript/)

e.g.. for the 1a link you can add

[COLOR=#665d59]window.location='1a.svg' ... where you have some description in text.   Or it could be an html file.[/COLOR]

Repeat for all targets you have in your background image.
You can clone circle objects  you have created, only changing the Description and Interactivity settings.

After completion you need to set opacity of all objects to 0%.
You can do this in the Inkscape editor but if you have many links to edit it might be easier to edit the raw svg file (view source).

Now save your svg file.

When you launch your svg file in your browser you will see your image (with clickable objects).

Hover over any target (e.g. 1a) and you will see the title of that object.

Click on any overlaid object and it will jump to the page defined in interactivity.

svg can be embedded in html.

---

### Post by dragonfly41 on 2016-09-17
Reviewing my earlier suggestion to explore use of slides.sikuli

Quoting from here ...

[http://slides.sikuli.org/docs/controls/](http://slides.sikuli.org/docs/controls/)

[COLOR=#666666]> Sikuli Slides is most suited for describing interactions that follow a linear pattern, that is, interactions that have a well-defined sequence of steps. Each slide represents a step. A deck of slides are executed from the beginning to the end. In certain situations, however, one might need to break away from this linear pattern. To support this, Sikuli Slides provides the following set of control tags.[/COLOR]
So, for example, if you wanted to walk users through a course in linear fashion (without necessarily referring to the web) then Sikuli Slides files can be placed self contained on a DVD.
This requires only Libre Office Impress to create the workflow.pptx file.

On the other hand if you require the users to *randomly* click on your target areas, Sikuli Slides is not the best choice.

In conclusion SVG is a better choice than Sikuli in your particular case.

But you could improve the navigation experience by drawing the entire map as an SVG file, dropping the use of overlaying (and intrusive) buttons such as 1a, 1b, .. 7a, 7b. 
(unless you particularly intend to lead viewers through a sequence ... 1a to 7b?).


========================================================

[color=maroon]
[Later edit]

I've just read this in your original post ...

> [COLOR=#000000]The original was done in Libreoffice Draw where I [/COLOR]*can create links from the circles. Wonder if there's some trick there .*[I]

Do you realise that in Libre Office Draw you can export as SVG format?

Then you can view the exported SVG file in Inkscape and add interactivity (onclick, onhover etc.) to any/all of the SVG objects. 
You could get rid of the overlaying buttons and just hover over  / click on any object (such as the pavilion object).

[/color]

[/I]

---

### Post by Dennis N on 2016-09-17
Hello, I hope this contribution from my tool box helps.

I use this template for images with "hot areas" as links. In the HTML web page, each image has a corresponding "map" section to define the areas and targets. To get the coordinates, I use Gimp. Just hover over a point to read the coordinates from each hot area of the image. The template below has two. Add more area tags as needed. Coords are upper-left corner then lower-right corner of the rectangular hot area as read from Gimp.

```
<map name="pages">
	<area shape="rect" coords="48,22,163,41" href="(insert hyperlink here)">
	<area shape="rect" coords="201,64,332,82" href="(insert hyperlink here)">
</map>
<p align="center">
<img src="images/linkmap.png" usemap="#pages">
</p>

```

You can use other shapes for image hot areas as explained in the links given in other posts in this thread.

---

### Post by Bucky Ball on 2016-09-17
Thanks for all your input. I had a head cold yesterday, courtesy of my wife, and got somewhere with this, after which I went to bed and spent the night in something of a hallucinatory fever as the cold turned into something worse. Believe it or not, I was stuck in a computer program that was linking entries in a list, but for the life of me I couldn't get it to do the same for a map area!

Anyway, been in bed all day so no further progress. I got to here, though. Gimp will create an image map from Filters> Web> Map image. Great, but it has drawbacks, one of which is that, while it will save your work as a .map file, it won't load it back in again if you want to make changes! 

I managed to map a couple of circles and fiddle around with getting them working and think it will. Just didn't have the right stuff in the right folder don't think, but was getting tired and blurry sniffly, so understandable ...

Will crash into it when I'm feeling a bit better, hopefully tomorrow.

---

### Post by DuckHook on 2016-09-19
Just a trial post as a favour to Bucky who hasn't been able to post for the past 10 hours due to posting glitch and doesn't want you to think he has been ignoring this. (This thread is way over my head)

---

### Post by dragonfly41 on 2016-09-19
As I suggested in my "[Later Edit]" at bottom of post #7 it seems that Bucky already has the objects defined in Libre Office Draw.
So, no need for Gimp to define the coordinates of each of the many objects.
Just export drawing from Libre Office Draw as SVG and take it from there.   It can be tweaked (interactivity added) in Inkscape.

I also dug out these references to SVG tutorials which I found useful when I was learning about SVG and maps.

[http://www.carto.net/papers/svg/samples/#iact](http://www.carto.net/papers/svg/samples/#iact)

---

