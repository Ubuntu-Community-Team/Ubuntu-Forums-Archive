---
title: "Open PDF file directly in file browser in gedit"
date: 2012-11-15
forum: General Help
---

### Post by windlove on 2012-11-15
Is there any way or plug-in that supports opening pdf file directly in gedit from file browser?

gedit seems open everything inside it as a source file rather than recognize the software to open the file. 

So What I mean is that instead of opening the file by going to the folder, I can read the file by double clicking it in the file browser. Then pdf can be opened in "Document Viewer".

Thanks and Regards

---

### Post by bootedguy on 2012-11-15
Gedit a text editor. For opening PDFs in Ubuntu you want to use the Evince Document Viewer.  Clicking on on a PDF file in a default install of Ubuntu should open it in the Evince Document Viewer.

---

### Post by stinkeye on 2012-11-15
Navigate to a pdf file in the file browser and right click on it....
Properties > Open with
and check that **Document Viewer** is the default application.
If not, hit the **Show other applications** button and choose **Document Viewer** and set as default.

---

### Post by windlove on 2012-11-15
> **stinkeye said:**
> Navigate to a pdf file in the file browser and right click on it....
Properties > Open with
and check that **Document Viewer** is the default application.
If not, hit the **Show other applications** button and choose **Document Viewer** and set as default.

Right click on the pdf in the file browser, there is no "Properties". The options are remove, rename, open folder, open terminal here, new folder and etc.

---

### Post by Parker32 on 2012-11-16
You might need to look in your nautilus and tell it on what to do to an executable file.

Open Nautilus -> Edit -> Preferences -> Behaviour -> Executable Text Files.

Files might not have default application when opening it.

Right Click on the file -> Properties -> Open with.

Set a default application of that file. If gedit is already selected and you want to change it just go over with your desired application.

---

### Post by stinkeye on 2012-11-16
> **windlove said:**
> Right click on the pdf in the file browser, there is no "Properties". The options are remove, rename, open folder, open terminal here, new folder and etc.
You should have.
Anything you may have done to cause this?

---

### Post by windlove on 2012-11-18
> **stinkeye said:**
> You should have.
Anything you may have done to cause this?

Here is what pdf looks like when open in the file browser in gedit:
The default setting to view pdf is Document Viewer. 
But inside gedit, it doesn't open as pdf.

---

### Post by Impavidus on 2012-11-19
Obviously, that's exactly what a pdf shoud look like in gedit. Gedit is a text editor and only knows about plain text. Opening a binary file there is generally useless.

What do you mean by "open in the file browser in gedit"? Start gedit, click "open", navigate to a file and then click open, so no nautilus or thunar involved? Then you command gedit to try and display the pdf as plain text. Some people may even want that, because pdf's header is plain text (first few lines anyway) so it could be tweaked. Automatically selecting the application to open a file only works from a file manager like nautilus (or from your desktop, but that's still controlled by nautilus).

---

### Post by windlove on 2012-11-19
> **Impavidus said:**
> 
What do you mean by "open in the file browser in gedit"? Start gedit, click "open", navigate to a file and then click open, so no nautilus or thunar involved? .

What I want to achieve is similar to the following program,Rstudio. However if it is how gedit works, then I just need to get used to it. Thanks for the reply.

---

### Post by Aaron Christianson on 2012-11-19
What are you actually trying to accomplish? What are you trying to do with your PDF?

---

### Post by windlove on 2012-11-19
> **Aaron Christianson said:**
> What are you actually trying to accomplish? What are you trying to do with your PDF?

Nothing to do with PDF itself, just trying to open the PDF without opening additional windows or directories. If I create some files or some files in my working directory, I can open it just in the file browser inside gedit, like Rstudio or MATLAB. However gedit opens everything as plain texts without recognizing the file extension. 

In the attachment, in Rstudio, I am working in this directory, I create a image file named footer.jpg. Then I can directly open it inside Rstudio. In the same working directory in gedit, the image file opens as a plain text. 

This is just how I do my work. I assumed that gedit had the same functionality too.

---

### Post by bob-linux-user on 2012-11-19
Gedit (as somebody said earlier) is used for opening text only files(much like the somewhat simpler Windows Notepad) Even if gedit could open a non text file at all (and I will not bother to try) it would be almost useless. Other files containing text and /or graphics like pdf, odt, doc files etcetera are similarly of no use to gedit as it handles **plain** text only.

---

### Post by Aaron Christianson on 2012-11-19
Ah. I see. The general trend on Linux (and other Unix-related systems) is to focus on writing programs that do one thing well and are able to interface well with other programs. It's rare to find programs that try to do everything. Gedit is very capable at editing text, especially code, but It's not going to be useful for dealing with any kind of binary file formats.

The "Ubuntu Way" to do this would probably be to simply hit the window key and begin typing the name of the file you wish to open. Should appear in the dash, as long as it is somewhere in your home folder. recently used files appear first.

---

### Post by andrew.46 on 2012-11-20
A little aside of this discussion: some may be interested to know that Firefox has a built in pdf viewer:

[http://docs.slackware.com/howtos:software:firefox_pdf_viewer](http://docs.slackware.com/howtos:software:firefox_pdf_viewer)

Works very nicely on my system.

---

### Post by mc4man on 2012-11-20
Gedit's file browser plugin seems much better behaved here, it will only show files that gedit can open.
(which makes sense as the 'file browser' is just for gedit, no more than that

ex. in screen, browser doesn't show the .pdf's nor any other file in Downloads except   a text file

---

### Post by vasa1 on 2012-11-21
> **andrew.46 said:**
> A little aside of this discussion: some may be interested to know that Firefox has a built in pdf viewer:
...
Which I think is not enabled by default even in Firefox 17 (beta) which is what I'm using. I don't what its status is in the latest stable release of Firefox 17 (out any time now).

In any case, if one wants to use it, it has to be enabled in about:config by toggling pdfjs.disabled;true to false.

---

### Post by andrew.46 on 2012-11-21
> **vasa1 said:**
> Which I think is not enabled by default even in Firefox 17 (beta) which is what I'm using. I don't what its status is in the latest stable release of Firefox 17 (out any time now).

There will be no tears when and if the adobe plugin becomes redundant...

---

### Post by vasa1 on 2012-11-21
> **andrew.46 said:**
> There will be no tears when and if the adobe plugin becomes redundant...
We could have a separate thread on this.

---

