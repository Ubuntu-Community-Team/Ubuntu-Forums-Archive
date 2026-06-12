---
title: "Help with image editing with GIMP"
date: 2013-06-11
forum: General Help
---

### Post by rdh61 on 2013-06-11
Hi,

I need some very kind soul to talk me through (in baby language) what I assume should be a simple task of image editing with GIMP.

Here's my problem:

I have an eps image file containing a simple graphic and some text. I want to change the wording and move the whole text to a slightly different position. That is all. Yet I cannot figure out how to do it, and I cannot make head or tail of the users' manual. Additionally, I have no experience of using any advanced graphics editor.

Please, how do I start?
What do I do next?
And next?
Etc?

Many thanks.

---

### Post by sudodus on 2013-06-11
Can you see the image (of the eps file) in gimp?

In that case you can

- select the marking tool (the square icon at the top left cormer in the toolbox)

- mark the area (with the text you don't want)

- delete it

- select the text tool

- write the text you want

- make the image 'flat' (I don't have the English term, but it's similar to joining the objects or layers)

- and save it (and export it if gimp 2.8)

But this method will remove the background in the marked area. If that is not accepted, it is probably harder to do it with gimp.

---

### Post by rdh61 on 2013-06-11
@ sudodus

Thank you very much for your reply. Yes, I can open the eps file in GIMP and see the image. However, I get stuck with your first instruction "mark the area (with the text you don't want)".

Here's what I did:

1) I right clicked my file, then clicked "Open with GIMP Image Editor". A window appeared entitled "Import from PostScript". I clicked "Import" and then image file became visible. 
2) I clicked on the area of text I want to modify and tried to mark out the area. But by default there is a paintbrush tool open which just marks the area in black.
3) I clicked "Edit" -> "Undo Paintbrush".
4) I clicked on the Text Tool on the left hand toolbar and used it to select my text. A window opened called "GIMP Text Editor". In this window the text area is empty. It allows me to enter new text but not to edit the text I have selected with the Text Tool. So I am stuck.

Reading further on in your instructions, you say this method will remove the background in the marked area. No, that would not be acceptable, I need the background to stay as it is!

Thanks again.

---

### Post by sudodus on 2013-06-11
Select the marking tool (the square icon at the top left cormer in the toolbox)

- mark the area ...

---

### Post by sudodus on 2013-06-11
> **rdh61 said:**
> 
Reading further on in your instructions, you say this method will remove the background in the marked area. No, that would not be acceptable, I need the background to stay as it is!

Thanks again.

You need to keep the background. Do you know if the eps file uses an object to show the text? In that case a tool, that manages the image on the object level would be preferred. If the text is not an object but integrated in the pixel image, there is no easy way to remove it. Maybe you can use a 'smearing' tool.

---

### Post by rdh61 on 2013-06-11
> **sudodus said:**
> Select the marking tool (the square icon at the top left cormer in the toolbox)

- mark the area ...

Thank you, that is clear to me now.

---

### Post by rdh61 on 2013-06-11
> **sudodus said:**
> Do you know if the eps file uses an object to show the text? In that case a tool, that manages the image on the object level would be preferred. If the text is not an object but integrated in the pixel image, there is no easy way to remove it.


I don't know, but I can find out. Watch this space!

---

### Post by rdh61 on 2013-06-11
> **rdh61 said:**
> I don't know, but I can find out. Watch this space!


OK, I am informed that it is not a pixel image but a vectorial image created with Adobe Illustrator. The text is a separate level. You said that a different tool would be preferred. Can you suggest which?

---

### Post by Impavidus on 2013-06-11
If I had seen this thread two hours ago I would have told you at once...

Most .eps files with text are vector graphics. Gimp can only edit raster graphics, so it converts to raster graphics, losing a lot of information and image quality. Try inkscape instead. If you feel really adventurous you can open the eps in a text editor, search for the text string and modify it that way.

---

### Post by rdh61 on 2013-06-11
@ Impavidus

Thank you for your answer. I am pressed for time right now, but will try both of your suggestions in my next free half-hour. I'll let you know how I get on.

---

### Post by sudodus on 2013-06-11
> **Impavidus said:**
> If I had seen this thread two hours ago I would have told you at once...

Most .eps files with text are vector graphics. Gimp can only edit raster graphics, so it converts to raster graphics, losing a lot of information and image quality. Try inkscape instead. If you feel really adventurous you can open the eps in a text editor, search for the text string and modify it that way.
I'm reading and learning :-)

---

### Post by rdh61 on 2013-06-11
I managed to do what I needed to do using Inkscape.

Moral of the story: "If you have a nail, even the best screwdriver isn't much good."

Thanks to both of you for your time and suggestions.

---

### Post by rdh61 on 2013-06-11
P.S. I'm not sure how to mark this "solved". It isn't under Thread Tools as it used to be.

---

### Post by Impavidus on 2013-06-11
No, that button has disappeared because of some sort of software incompatibility. See this thread (post 2) for a workaround: [http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

---

### Post by rdh61 on 2013-06-12
OK. Got it.

---

