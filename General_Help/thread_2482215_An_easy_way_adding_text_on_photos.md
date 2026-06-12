---
title: "An easy way adding text on photos"
date: 2022-12-24
forum: General Help
---

### Post by satimis on 2022-12-24
Hi all,

Ubuntu 22.04

What will be the easy way adding simple text on photos, such as name of person on the photo?  I don't expect running GIMP so complicate.

I have hundreds of photos to be treated.  I have done it before, long time ago.  Unfortunate I forgot how to do it.

Please advise.  Thanks

Regards

---

### Post by sudodus on 2022-12-24
I use gimp for such purposes, but you may find it easier to import a picture or a set of pictures to **libreoffice impress**, and use its tools to **add** objects (in this case **text**).

---

### Post by Dennis N on 2022-12-24
I discovered **ksnip**, some time ago, and have been using that as my go-to for annotating photos with text, arrows, boxes, and so on. Simple to use. I install it as a Flatpak.

---

### Post by satimis on 2022-12-25
> **sudodus said:**
> I use gimp for such purposes, but you may find it easier to import a picture or a set of pictures to **libreoffice impress**, and use its tools to **add** objects (in this case **text**).
Hi,

Thanks for your advice.

Start the image with Libre Office Draw

On top menu
-> Tools
I can't find "add objects"

Regards

---

### Post by sudodus on 2022-12-25
You can use both Impress and Draw (of LibreOffice). See the attached screenshots.

---

### Post by satimis on 2022-12-25
> **sudodus said:**
> You can use both Impress and Draw (of LibreOffice). See the attached screenshots.
Hi,

Thanks for your advice.

I performed the test on Draw.  I found the big "T" but the font is too small to see and also the box almost invisible.  Please advise how to format them.

Please refers to attached screenshot

Regared

---

### Post by satimis on 2022-12-26
**[COLOR="#FF0000"]I found the solution which is quite simple[/COLOR]**

Start the image on **Libre Office Draw**
Click the **[T]** (Insert Text Box (F2)) on top menu
Draw a **"Text Box"** on the image
Type in the text
Select the text -> right click -> select "Edit Style ..."
Start **"Graphic Styles: Default Drawing Style"** window

on **"Graphic Styles: Default Drawing Style"** window
Select **[COLOR="#FF0000"]"Font Effect"[/COLOR]** on the top menu
On Font color [click the inverted arrow] -> to select the color you want
-> OK

Again;
click **[COLOR="#FF0000"]"Font"[/COLOR]** on the top menu
Family: select the font
Style: select Regular/Bold/.....
Size: select the font size
-> OK

Adjust the size of **"Text Box"** on the image
Move **"Text Box"** to the place on the image which you prefer

That is all, the complete steps.

**See attached screenshot**

---

### Post by Dennis N on 2022-12-26
Much simpler would be to have followed the suggestion to use **ksnip**.

---

### Post by satimis on 2022-12-26
> **Dennis N said:**
> Much simpler would be to have followed the suggestion to use **ksnip**.
Could you please advise me where to find relevant documents for using ksnip?

Thanks

Regards

---

### Post by Dennis N on 2022-12-26
> **satimis said:**
> Could you please advise me where to find relevant documents for using ksnip?

Thanks

Regards

I see several tutorial videos about Ksnip on YouTube. Check those out. But you can just open any image with it and practice a bit. That's how I learned how to use it. In brief, in the attached screenshot, you click the Text Icon on the left and a menu bar appears. Select font and color from the menu bar. Click on photo and type text. You can later select and move the text with the selection tool (yellow arrow). Also you can change color, font or size while selected.

You can also take screenshots with this ('New' button), then crop and add text before saving. That's useful

There is a way to add it to the "open with" menu in Files. Ask about that if you decide to use this tool.

---

### Post by dragonfly41 on 2022-12-26
Flameshot does this nicely for me. I have it running (red icon in top toolbar) and when I have any image I just click "Take Screenshot" and a list of buttons surround the selected image (this list controls can be reduced in Settings). The n add text to the image and it can be saved in different ways.

---

### Post by satimis on 2022-12-27
Hi all,

Thanks for your advice.

I'll test both "ksnip and Flameshot" on an Ubuntu 22.04 VM.  Do they have AppImage ?

For adding Text/Water marks/graphics etc. on images, ImageMagick is a wonderful tool for command lines operation, especially for batch procession.

Regards

[B][COLOR="#FF0000"]Edit
===[/COLOR][/B]
Actually all those packages are not difficult to use when you are knowledgeable on their operation including GIMP

---

### Post by satimis on 2022-12-27
**[COLOR="#FF0000"]Further to my previous posting[/COLOR]**

**[COLOR="#FF0000"]GIMP[/COLOR]**
Start the image on GIMP
-> Tools -> Text (tool)
draw a rectangle on the place where you want to add the text
type in your text
select the text
change the number 82 on "Arial B82" to a number for the text size (in my case 70)
(see attached screenshot)
start -> Colors -> Colorize
Color [select your preferred color]
-> OK -> OK
Tools -> Transform Tools -> Move
Move the text to its final place
File -> Export As
(export the edited image as .jpg file)

That is all !!!

---

### Post by HermanAB on 2022-12-28
I am olde skool and would simply use imagemagick: [https://www.imagemagick.org/Usage/annotating/#anno_on](https://www.imagemagick.org/Usage/annotating/#anno_on)

That is likely what the above utilities use underneath anyway.

---

### Post by satimis on 2022-12-28
> **HermanAB said:**
> I am olde skool and would simply use imagemagick: [https://www.imagemagick.org/Usage/annotating/#anno_on](https://www.imagemagick.org/Usage/annotating/#anno_on)

That is likely what the above utilities use underneath anyway.
For batch processing of images I use ImageMagick

For editing single image I use GIMP, LibreOffice Writer/Impress/Draw

---

### Post by HermanAB on 2022-12-28
You missed one:
Xournal

---

### Post by satimis on 2022-12-28
To edit 1(one) or 2(two) images we have many solutions.

Have folks on the forum tried;
[B]
Batch Processing Millions and Millions of Images[/B]
[https://www.etsy.com/codeascraft/batch-processing-millions-of-images](https://www.etsy.com/codeascraft/batch-processing-millions-of-images)
[COLOR="#FF0000"]**GraphicsMagick**[/COLOR]
[B][COLOR="#FF0000"]Perl
Ganglia[/COLOR][/B]

?

Regards

---

