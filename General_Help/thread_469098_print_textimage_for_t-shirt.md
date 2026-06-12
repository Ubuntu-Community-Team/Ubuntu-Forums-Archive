---
title: "print text/image for t-shirt"
date: 2007-06-09
forum: General Help
---

### Post by pickarooney on 2007-06-09
I'm trying to make a t-shirt by printing off some text to a special A4 transfer sheet. It should be pretty simple - I just need to print the text in landscape format and inverted (like in a mirror) so when the sheet is ironed on to the t-shirt it comes out the right way around. I've been fighting with open office and GIMP and gimp-print and CUPS and can't figure out what to do - invert the text in the GIMP (how?) or in the printer settings (where?) or in OOO somewhere...

---

### Post by hartz on 2007-06-09
Start Gimp
Click New.
In the Template box, select A4 (300dpi)
Click the twisty next to Advanced Options
Tune the X and Y resolution down to 150 pixels/inch
Select Fill with Transparency
Check the page orientation, set it to landscape or portrait as you wish.
Click OK
Resize the window and use View->Zoom to adjust it so that you get a reasonable view size.
- Double-click the Text tool (It looks like a big T) - The tool options will appear.
- Click anywhere in the image
The GIMP Text Editor will appear
- Type in your text, and use the Tool Options to change the Font, Size, etc.
- Click outside the text-box on the canvas to complete the new text operation.
- Select the Move Layers tool (It looks like resize-arrows)
- Carefully select the text and move it to the right spot on the page.
Repeat the last 6 steps for each font/color.
No click Image->Transform->Flip Horizontally.
Then print the image.  I advise making a few tests on plain paper.
Note: The Print option will warn you about having layers.  Just click Export.

---

### Post by pickarooney on 2007-06-10
Perfect. I owe you one :)

---

