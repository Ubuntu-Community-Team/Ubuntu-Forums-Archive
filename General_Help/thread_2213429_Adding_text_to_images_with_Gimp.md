---
title: "Adding text to images with Gimp"
date: 2014-03-26
forum: General Help
---

### Post by t0p on 2014-03-26
Don't know if it's me; but I can't find a way to add text to images using Gimp 2.6.12.  All the instructions I've found are for different versions, and I can't figure it out.

All I want to do is add my Creative Commons licensing info to certain pix: CC BY-ND 3.0; in an out-of-the-way corner. Or, better, the graphic.
 


Can someone please point me in the right direction for instructions?  Using Gimp 2.6.12 on Ubuntu 12.04 (precise) 64-bit.  Thanks.

---

### Post by howefield on 2014-03-26
Text Tool ?

---

### Post by 23dornot23d on 2014-03-26
There is a quick video here for one picture ......... [http://youtu.be/CbGWbLXELDU](http://youtu.be/CbGWbLXELDU)

If you need to do multiple photos ........ save the **text** you need to a png with a "alpha/clear" background and pull it in on each image - then pull it in as a separate layer on top of you photo .

Gimp - File - open as layers ........... the second layer being the copyright.png ........
place it where you want and resize if needed using the Layer - scale option.

There could be a few ways of doing this ...... and there used to be a script
[https://www.google.co.uk/search?client=ubuntu&channel=fs&q=gimp+copyright+script&ie=utf-8&oe=utf-8](https://www.google.co.uk/search?client=ubuntu&channel=fs&q=gimp+copyright+script&ie=utf-8&oe=utf-8)
 for it.

[http://www.skipser.com/p/2/p/how-to-watermark-photos-using-gimp.html](http://www.skipser.com/p/2/p/how-to-watermark-photos-using-gimp.html)

---

### Post by t0p on 2014-03-26
**23dornot23d**: thanks, I'll check all that out now.

**howefield**: obviously I did not explain my problem properly.  I'm aware of the text tool, but I don't know how to make it work.  I click on the text tool (A big letter "A"), but when I type the required text into the gtext box, it does not appear in the image.  That's why I needed help/advice.  In future I will try to explain my problem correctly.  Thanks anyway.

[Note: |I haven't marked this [SOLVED] yet.  Once I've got it working I'll mark it **[SOLVED]**.

---

### Post by 23dornot23d on 2014-03-26
I used to work a lot with Gimp and the scripts are what make it really good to use .........

If you want the scripts I did a Tutorial once on a site for photography and zipped them in on file
its around 9 meg ..... but its here should you want to try it ........ the watermark one is in there too.

[https://sites.google.com/site/gimpcutout/home/files-used-in-this-tutorial/TutorialScripts.zip?attredirects=0&d=1](https://sites.google.com/site/gimpcutout/home/files-used-in-this-tutorial/TutorialScripts.zip?attredirects=0&d=1)

I have left the original files in there too ........ its only copies from other peoples scripts - but they can take some
finding ........ and they do make Gimp a lot better to use once installed ( the information for installing scripts is in the link
in the last post I did should you want to add them ) .......

I just checked to make sure it still works ...... this was in Gimp 2.8 
( you can choose the text and the text is easily altered with undo and redo ..... as you may need to try different ones out )
( the opacity and text sizes can be changed so the copyright does not take over how we view the photo or design ...... )

[http://i.minus.com/iNVTisKC0JJap.png](http://i.minus.com/iNVTisKC0JJap.png)

but these scripts were made quite a while back now
so it may be worth picking and choosing what to install ..........

---

### Post by mcduck on 2014-03-27
> **t0p said:**
> **23dornot23d**: thanks, I'll check all that out now.

**howefield**: obviously I did not explain my problem properly.  I'm aware of the text tool, but I don't know how to make it work.  I click on the text tool (A big letter "A"), but when I type the required text into the gtext box, it does not appear in the image.  That's why I needed help/advice.  In future I will try to explain my problem correctly.  Thanks anyway.

[Note: |I haven't marked this [SOLVED] yet.  Once I've got it working I'll mark it **[SOLVED]**.

For starters, make sure the image is in RGB mode (Image->Mode->RGB). This could be an issue if, for example, you tried editing an image with indexed color palette (like a compressed GIF file).

Then, make sure you have a reasonable color selected, and that the font size is large enough to be seen but small enough to fit in your image/text box (too large font could result in the text not displaying if even a single letter can't fit in a text box). Also check the Tool Options-dialog when you have text tool selected, and if the "Box" option is set to "Fixed, try changing it to "Dynamic".

If even that fails, try painting something with paintbrush tool. Does it work?

---

