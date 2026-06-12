---
title: "Editing an audio file in Audacity"
date: 2013-10-30
forum: General Help
---

### Post by coljohnhannibalsmith on 2013-10-30
Hello,

I have some very long audio files, some 12 hours long, that I need to edit in audacity; and the instructions are not clear about how to mark the area I want to keep, with the cursor.

It seems I can only move the cursor at the normal rate; and this is completely useless for a file that is 12 hours long.

Can anyone give me the scoop on how I can do this efficiently?

Thanks Hannibal

---

### Post by Dennis N on 2013-10-30
You should be able to drag with the mouse to define the section of a project you want to retain - same as selecting text. Then trim the rest off. I don't see here any limitations on the speed of dragging the mouse. The tooltip should help you find the trim button on the toolbar.

---

### Post by Dennis N on 2013-10-30
A bit more...
If you want to cut out a section of the audio to use: select with mouse, listen, drag and adust the endpoints, listen again until you get it right. Then copy. Then, Open a new file (File >Open) and then paste. You can normalize you selection for optimum volume. Or incorporate other effects as needed (such as fade in and fade out). When done, export to a file name and format of your choice. You really need to study the manual to get all the options.

---

### Post by tgalati4 on 2013-10-31
Use *sox* to cut the file into 2-hour pieces and then edit those.  Audacity slows down with files longer than 2-hours due to the way it stripes the data over several files.  You would need huge RAM and 8-core processor to get audacity to perform with those files.  Even then, I don't think it is really the best tool for handling files that long.  You could set up audacity to run its project files from a RAMdisk and that would speed it up significantly.  But I agree, zooming into a file that large is a pain.

---

### Post by coljohnhannibalsmith on 2013-11-14
> **Dennis N said:**
> A bit more...
If you want to cut out a section of the audio to use: select with mouse, listen, drag and adust the endpoints, listen again until you get it right. Then copy. Then, Open a new file (File >Open) and then paste. You can normalize you selection for optimum volume. Or incorporate other effects as needed (such as fade in and fade out). When done, export to a file name and format of your choice. You really need to study the manual to get all the options.

How do I set the endpoints; since it appears I can't FF the cursor?

Thanks Hannibal

---

### Post by tgalati4 on 2013-11-14
Try a smaller file.  I think the file is just too big for audacity and it's zoom tool.  Sometimes the keyboard shortcuts work better, but moving around a large file in audacity is a pain.

---

