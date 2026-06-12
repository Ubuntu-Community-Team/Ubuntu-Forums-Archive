---
title: "gimp or draw or krita"
date: 2020-11-02
forum: General Help
---

### Post by cmcanulty on 2020-11-02
I have spent all afternoon trying to use one of these programs to delete parts of a pdf file. I select rectangle OK then click cut or delete key and nothing ever happens, very frustrating. File opens OK in all three and lets me select rectangle but never let me cut anything. I have read tutorials and they say click cut or hit delete and nada.

---

### Post by T6&amp;sfpER35% on 2020-11-02
in GIMP:
open PDF and select _tools_ and _selection tools_
then circle/rectangle whatever part of PDF you want to cut,then right click inside the selected part and select _edit - cut_
then click anywhere outside selected box
then go to _file_ - _export as_ 

tip : if the document is white and you want the cut piece to show white also , instead of edit-cut , use edit-fill with FG color 

FG color is here 



        [ATTACH=CONFIG]287288[/ATTACH]

---

### Post by T6&amp;sfpER35% on 2020-11-06
don't ya just hate it when u try give sound advice , and there's no response?
like did it work ? did u die ? what?
i mean i had to go and actually try editing a pdf in gimp ,so as to help ...but noooo...
:D

---

### Post by cmcanulty on 2020-11-06
I'm sorry I just got the reply notice tonight. I will try that tomorrow, thank you. I usually get an email right away but didn't this time.  I do appreciate the help! I was doing as you said-crate the box click inside it and select edit cut but nothing happens. Will tru again tomorrow and let you know.

---

### Post by HermanAB on 2020-11-07
Easiest is with xournal.  You can scribble all over and then export to a new PDF.

---

### Post by Impavidus on 2020-11-07
Gimp is a raster image editor. Pdf is a vector image format (which may contain raster graphics). When you use gimp to edit a pdf, it will first rasterise the image. Then you can edit it and export to pdf, but that will give you a pdf containing a single raster image. The quality will suffer, in particular the quality of text present on the page.

It's probably better to use a vector image editor. Personally, I avoid editing pdfs, as it's a much better idea to edit the sources from which the pdf was generated, but occasionally you have to.

---

### Post by cmcanulty on 2020-11-09
OK the same result nothing happens. I select rectangle, draw it around part to cut. Rt click and say cut. then I click somewhere else and absolutely nothing happens

---

### Post by Holger_Gehrke on 2020-11-09
By default GiMP opens the pages of a PDF on separate layers stacked with the first page on top but the last page (hidden behind all the other pages) active. So your action probably worked, but on that last page. 

I don't know how you've got GiMP configured, but there's a (dockable) form with all the layers which I always keep open in GiMP's dock. A click on a layer in that form will make it active. There are icons in front of the layer (eye and chain) which allow you to make layers visible or invisible and to link them together to move multiple layers at once.

Holger

---

### Post by T6&amp;sfpER35% on 2020-11-13
> [COLOR=#000000]then I click somewhere else and absolutely nothing happens[/COLOR]
yes nothing seems to happen ,until u go to next step  , [ [I]then go to _file_ - [U]export as ]
[/U][/I]the exported /saved PDF would show the editing

i could make u a little video demonstrating , it'll be fun
just say the word

---

### Post by T6&amp;sfpER35% on 2020-11-13
ok u said it lol

[https://youtu.be/oZTaJJzOA5c](https://youtu.be/oZTaJJzOA5c)

---

### Post by HermanAB on 2020-11-14
You will have more joy with xournal.
$ apt install xournal pdfshuffler

---

### Post by cmcanulty on 2020-11-14
OK I did your procedure and again nothing changes. I found a web service that woeks. This is for pdf music scores of several pages that I have to remove every other staff and then print. I know gimp is really good and thorough but it is beyond me. I also tried xournal which lets me select rectangles but as soon as I touch my mouse to do something with the rectangle it disappears. Thanks for all the help. I give up.

---

### Post by HermanAB on 2020-11-14
By the sounds of it, you need some basic help - find a LUG and go to a meeting - ask someone to show you.

---

