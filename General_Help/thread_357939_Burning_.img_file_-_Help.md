---
title: "Burning .img file - Help"
date: 2007-02-10
forum: General Help
---

### Post by Randy101 on 2007-02-10
Sorry if I'm in the wrong place or if this has been asked before and I can't find it - this is my first post !

I'm using the LTS version (6.06). I've downloaded an img file and I need to make it into a bootable CD - how to I do this?  Is there a graphical packageI can download to do it ??

Thanks for the help!

---

### Post by taurus on 2007-02-10
You can use k3b to burn it.  Make sure you pick the burn it as an ISO option and when you browse to the directory where that file is located, click the menu at the bottom to show all files so it would dappear in the window for you to choose.

---

### Post by Randy101 on 2007-02-10
Want I want to do is make a bootable CD from a zip file I downloaded; I've got it downloaded & I've extracted the files (3 of them) into a folder.  The folder now has a .cue file & 2 .img files.

I've got Kb3 installed; I navigate to the folder & select them for the Kb3 'project'; now, all 3 files are on the top of the Kb3 pane;  I them highlight & move all 3 down into the 'current projects' panel at the bottom - all fine so far. 

I go to Tools, Burn CD Image, and another box pops up ('Burn CD Image') but it only sees the .cue file.  I can't seem to get it to see the /img files and burn them 'bootable' to the CD.

Thanks for the help

---

### Post by taurus on 2007-02-10
Is the .cue file pointed to the .img files?

---

### Post by Randy101 on 2007-02-10
How do I tell if it's 'pointed' at them ??  There are just the 3 files listed at the bottom (in the 'Current Projects' part of the pane) - the large img file is 600 MB & its file type is listed as 'unknown'; the other img file is listed as a 'plain text document'.

Thanks again

---

### Post by taurus on 2007-02-10
From a terminal, read it with more.

```
more **filename**.cue
```

---

### Post by Maestro23 on 2007-02-10
In most disc burning programs, they look for the .cue file if there is one because it will generally point to the image file. If you click on the cue file in the program you are using, it should start burning the image that is in the same folder as it is.

FYI: [http://en.wikipedia.org/wiki/Cue_sheet](http://en.wikipedia.org/wiki/Cue_sheet)

---

### Post by Randy101 on 2007-02-10
Again, how do you tell if it's 'pointed' at anything ? It says it's an executable text file. When I go to the terminal, it says no such file or directory exists.

You know, this is kinda funny.  I was actually talking to my advisor yesterday about possibly doing my dissertation on something re: GUI user "intuitativeness"  (sp?) -  I've got hours & a stack of coasters tied up in this...

Thanks

---

### Post by forgreatsource on 2007-06-06
open the text file

---

### Post by cookies on 2007-06-06
You all make this MUCH to hard:

In Ubuntu

   1.

      Insert a blank CD into your burner. A "CD/DVD Creator" file browser will pop up. Close this browser as we will not be using it. (Edgy will say "Choose Disk Type", click 'Ignore")
   2.

      Find the downloaded ISO image in the file browser (available at Places &#8594; Home menu on top of the screen.) Right click on the ISO image file and choose Write to Disc and wait for burning to complete.


In Kubuntu

   1.

      Find the ISO image in the file browser (available at System Menu > Home Folder on bottom of the screen next to KMenu.)
   2.

      Right click on the ISO &#8594; Actions &#8594; Write CD Image with K3b...
   3.

      K3b will now automatically verify the md5sum, make sure these match.
   4.

      Place Blank CD in burner and click on start.


Thank you Ubuntu website.

---

