---
title: "Add programs to &quot;Open With&quot; menu?"
date: 2007-07-08
forum: General Help
---

### Post by seanVT on 2007-07-08
Hi,

Can anyone tell me how to make a program show up in the "Open With" menu? I just installed Adobe Acrobat Reader via Automatix. I want to make it the default reader for PDFs. So I right-click on a pdf, and it gives me some choices to "Open With", but no Acrobat Reader. So I choose "Open with Other Application". Then I get a bigger list of programs, but still no Acrobat Reader. How can I get Acrobat Reader to show up on this list?

This isn't the first time I've tried to associate a file type with a certain app, but it just didn't appear in the list.

Thanks in advance for any help.

---

### Post by ltk5 on 2007-07-08
When you get the bigger list you could try typing in Acrobat's command name :).
You can find that in you main menu, under applications (I think). 
You just have to Right click on Applications > Edit menu. Then you get a new window. 
Again Right click on Adobe Acrobat. And copy the command
line from there to the "Open With menu"

Another option is, that you try to find Adobe Acrobat manually by browsing. Try /usr/bin.

Hope this helps a bit,
Cheers!

---

### Post by lagartoflojo on 2007-07-08
Right click on any PDF file, go to Properties, then to the Open With tab.
Click on the Add button.
Now you'll get that stupid list of programs in which Acrobat is NOT.
But right above the "Cancel" button you'll see "Use a custom command". Click on that.
On the textfield that appears type "acroread".
Click Add. On the "Open With" tab, Acrobat Reader should be listed. Click Close.
Now try right-clicking on the PDF file and going to "Open With"... hopefully Acroread will be there and you will be able to use it.

---

### Post by seanVT on 2007-07-08
> **lagartoflojo said:**
> Right click on any PDF file, go to Properties, then to the Open With tab.
Click on the Add button.
Now you'll get that stupid list of programs in which Acrobat is NOT.
But right above the "Cancel" button you'll see "Use a custom command". Click on that.
On the textfield that appears type "acroread".
Click Add. On the "Open With" tab, Acrobat Reader should be listed. Click Close.
Now try right-clicking on the PDF file and going to "Open With"... hopefully Acroread will be there and you will be able to use it.

That did it! Many thanks to both of you! :)

---

### Post by seanVT on 2007-07-08
Actually I spoke too soon. Acroread is now in the right-click menu and it opens the PDF when I select it. But it doesn't remember keep it as the default viewer. If I double-click the PDF again it still opens in Document Viewer.:(

---

### Post by lagartoflojo on 2007-07-08
Okay. In the "Properties" window, under the "Open With" tab, you see Acroread listed, right?
So now click on the Radio button to the left of its name to make it the default app for PDFs.

---

