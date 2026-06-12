---
title: "openoffice: pasting web content with images without having them linked dynamically"
date: 2006-10-10
forum: General Help
---

### Post by kiddo on 2006-10-10
I am begging for help on this issue, maybe, just maybe some other ubuntu users stumbled upon this annoyance and found an undocumented solution :neutral: 

Here it is: when you select and copy text from a web page with images,
when you paste it into openoffice writer (or anything else, I presume), openoffice will paste the images into the document, but as **linked images**. Stupid gawddarn LINKS! :evil: Instead of just saving the images and incorporating them to the document.

What does that mean?
[LIST]
[*]everytime you load that document, you will need an internet connection
[*]even if you have a 3mbits internet connection, it will make your computer hang for a LONG time loading those images.
[*]moving through the pages of a document makes you LAG in a terrible way (because images are loaded one at a time, although the time it takes to startup at first makes you think it loaded all the images)
[*]deleting those images is painful because, once again, you lag while doing that.
[/LIST]

Am I doomed?

[SIZE="1"]Note: I do these kinds of manipulations quite often, when I want to archive an interesting net article to opendocument format, for personal enjoyment purposes.[/SIZE]

---

### Post by Shay Stephens on 2006-10-10
Yes, I hate the direct connection stuff too.  I have to save content to the computer then rebuild the document.  But what if you saved the webpage to the computer, then opened it locally and copied and pasted that into OO?  I have not tried it, just a brainstorm idea.

---

### Post by robinl on 2006-10-10
Can't you just save it as HTML in your browser and open it with OOo or something?

---

### Post by kiddo on 2006-10-11
The I think OOo would still (logically?) link the images. The only difference is that it would link them locally. What is worse is that you, logically, might be tempted to delete the html document and its source files (images) afterwards, and I'm pretty sure openoffice will be (excuse my crude words) dumb enough to have linked the data instead of importing it, and you will end up with no images at all (the same would happen if you actually move them from a folder to another). I did not try yet though, I'll give it a shot, but I somewhat doubt the results...

---

### Post by kiddo on 2006-10-12
I just did the test. I made a local webpage on my computer with text and an image in it. I copy-pasted the page into an odt document with OOWriter, then deleted/moved the webpage and image.

The image shows itself as broken in the odt file. Brilliant. :-|

---

### Post by viciouslime on 2006-10-12
Wow, this is annoying. Have you tried asking over at the OO.org forums?

Might be worth a try, if you do find a solution there, please can you post it back here.

---

### Post by kiddo on 2006-10-13
I got [a reply]("http://www.oooforum.org/forum/viewtopic.phtml?p=179562")! :p I'm [blogging]("http://kiddo.ecchi.ca/blog/index.php?2006/10/13/141-pasting-web-content-with-images-in-openoffice") this :D
> Edit > Links, Shift + click on the last linked graghic and Break Links will embed them.

---

### Post by jethro10 on 2006-10-13
> **kiddo said:**
> I got [a reply]("http://www.oooforum.org/forum/viewtopic.phtml?p=179562")! :p I'm [blogging]("http://kiddo.ecchi.ca/blog/index.php?2006/10/13/141-pasting-web-content-with-images-in-openoffice") this :D

Yep, works for me.
edit->links, highlight all that you want broken.
It then takes a little while as it downloads and embeds the data locally.

J

---

