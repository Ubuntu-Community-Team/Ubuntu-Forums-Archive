---
title: "Please help me with GIMP"
date: 2016-02-18
forum: General Help
---

### Post by vasa1 on 2016-02-18
I installed GIMP 2.8 from the software center.

I have close to no knowledge of graphics programs but I want to make certain changes to the image I've attached. It is a layout of six buildings.

I want to move some of the buildings about a bit
and
I want to have the final image just black and white.

My starting point was a scanned image of the layout which I opened in GIMP and saved as a .xcf file.

Thanks in advance for any advice!

(We're now having clashes over parking space in our housing society and so I want to make a layout of the space that can be allotted,)

---

### Post by Bucky Ball on 2016-02-18
You will need to create layers for each 'block' I'd think, and that will be time consuming, but if you're up for the learning curve ...

Just a thought. I think I'd tackle this in a slightly different way, and simpler. You could take screenshots (select region) of each 'block' then use, say, Libreoffice draw to arrange them as you like. You can set the background to whatever colour there easily and it looks like your 'blocks' are in black and white already from the attached screenie you provided.

Sorry I can't help in more detail with Gimp. Haven't used it for this kind of thing in quite a few years and forgotten most of what I knew about it (which means I've been learning other stuff!). :)

Good luck.

---

### Post by vasa1 on 2016-02-18
> **Bucky Ball said:**
> You will need to create layers for each 'block' I'd think, and that will be time consuming, but if you're up for the learning curve ...

Just a thought. I think I'd tackle this in a slightly different way, and simpler. You could take screenshots (select region) of each 'block' then use, say, Libreoffice draw to arrange them as you like. You can set the background to whatever colour there easily and it looks like your 'blocks' are in black and white already from the attached screenie you provided.

Sorry I can't help in more detail with Gimp. Haven't used it for this kind of thing in quite a few years and forgotten most of what I knew about it (which means I've been learning other stuff!). :)

Good luck.

Thanks, I'll look into LibO Draw as well because I have it installed. I reduced the colors so that the file I uploaded to the forum would be an acceptable size.

---

### Post by Bucky Ball on 2016-02-18
Just had a quick play. They are blurry as heck as I blew them up. I opened your attachment in image viewer, selected the region of three of the blocks with screenshot (xfce4-screenshooter I think it is), saved them as .png. Took me a couple of minutes.

You could then Libreoffice Draw> Insert> insert your blocks> reposition> export as PDF. You can also change the angle of objects in Draw so you can pretty much position them as you like (change to sideways, upsidedown, anywhere in between, straighten Pic3 in attachments to be same angle as Pic1 and 2, whatever). :)

It's an option.

---

### Post by vasa1 on 2016-02-18
I gave GIMP a try again. I learned how to cut out a building at a time and paste it into a new layer. Then, I could rotate the new layer by an arbitrary degree and move the image around. So I think I'm all set as far as the rotating/moving goes.

Now, I want to get rid of the background in certain parts; ideally, just black and white with no grey. But that's not really essential.

As I said, I had to reduce the quality of the image quite a bit to meet the permissible size. My original scanned jpg is 10.5 MB :(

My poor laptop's CPU is getting quite a workout!

---

### Post by coldraven on 2016-02-18
You can use Colours>Levels, grab the pointer on the left of Input Levels and move to the right until the "walls" in the image go more black.
Then go Tools>Selection Tools>By Colour Select, and click on one of the image "walls", you should see them all become dotted lines (selected).
Then Edit>Copy
Then Edit>Paste As>New image
Then in the layers Window add a White layer and drag it "below" the pasted image. (which by default is on a transparent layer, the checker board stuff)
At this point you can use a paintbrush to paint white over any unwanted artifacts. Paint on the top layer or create a new upper layer.  (the scribble in the lower right for example)
Then Save

At this point I would recommend printing out the cleaned up plans, using a marker pen to fill out the outlines. (Much quicker and easier than doing it in Gimp) 
Then cut out the individual plans, re-arrange them and glue to a sheet of white paper. Then scan again. Problem solved.

---

### Post by coldraven on 2016-02-18
I recommended using a marker pen because the plans are fairly low quality. If you want to try automating this use the "Stroke" function.
So select all the walls by colour (or select all from the transparent pasted layer) and use Edit>Stroke Selection. In the attached image I chose a stroke of 2 pixels. Make sure you have flipped the background/foreground colours with the widget in the left window. (black and white squares) The result is a bit messy but it may be adequate.

---

### Post by col48 on 2016-02-18
**LibO Draw:**
With layers in LibO Draw, once you have got a layer the way you want it you can Lock it so that you don't accidentally change it, and make it (temporarily) invisible while working on another layer.

**GIMP**
Often a scanned image is a bit dirty: The GIMP 'Unsharp Mask' Filter under Filters>Enhance does a reasonable job in reducing the effect of dirt - try applying it two or three times on the colour image then Image>Mode>Indexed to convert to pure black & white.  Makes a much smaller file, if that matters.

**GIMP + LibO Writer**
I've also used GIMP to select a part of a scanned image, fiddled around with it and saved it (as png or jpg) then imported it into LibO _Writer_, where I can move it around the page and expand it to print as big as possible on the page (although I can't edit it there).

---

### Post by vasa1 on 2016-02-18
Thanks, Coldraven and col48, the image I uploaded is of poor quality because of the image size restrictions here. The xcf file on my laptop is about 10 Mb and is pretty decent. I used Simple Scan set to its highest quality.

I've managed to reduce the background using *Colors > Threshold* which offers a nice slider and a preview.

Then, I cut out individual buildings outlines using *Edit > Cut* and pasted each building into its own layer which I could then rotate a few degrees (*Layers > Transform > Arbitrary Rotation*) and move around (*Tools > Transform Tools > Move*).

---

