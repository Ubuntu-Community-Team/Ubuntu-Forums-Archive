---
title: "Inkscape export problem (help!)"
date: 2005-06-24
forum: General Help
---

### Post by Declan on 2005-06-24
Hi Inkscapists.

I've just spent 3 (THREE!) hours trying to export some svgs from Inkscape to png, or to any other format that is generally understood in Windowsworld. 

Why do I get that checked background.  
I installed sodipodi and it does the same.

Please help!  All I want is exports that look a bit like the original.
It's nothing to do my image: I made a new file with just a rectangle (for test purposes) and exported that, and it too had the check background.

I reset the configuration files, and that didn't do it.

I see in Document Preferences an option called Background (also for export), but pressing that button does nothing.
I thought that launching inkscape with -y argument might help, but that doesn't do it either.  

Help! :-|   

Declan

---

### Post by wolphin on 2005-06-24
Well I'm no guru, but from my knowledge of graphical programs I'd say you have the Background set to "Transparent", which the graphic program will display as checkered, and then for some odd reason when you export the file it actually saves it as if the checkered background is part of the file, which it isn't. Can you try to search around and if you see a "Background" option (possibly the one you explained in your post) then change the setting to "Blank" instead of "Transparent". Hope this helps,

Wolphin

---

### Post by Declan on 2005-06-24
That seems to be it alright.  The checkered background doesn't come up for other people when I send the files to them.  It is a curious convention that stands for transparency, is that right?

Thanks,

Declan

---

### Post by Alexander Kirillov on 2005-06-24
[QUOTE=Declan]That seems to be it alright.  The checkered background doesn't come up for other people when I send the files to them.  It is a curious convention that stands for transparency, is that right?

Thanks,

Declan[/QUOTE]
 Yes. Checkered is the way to show transparency - it is a convention in many graphical editors. Viewers, of course, just show it transparently :)

---

