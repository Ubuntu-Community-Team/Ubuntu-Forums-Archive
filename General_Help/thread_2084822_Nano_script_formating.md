---
title: "Nano script formating"
date: 2012-11-16
forum: General Help
---

### Post by towardstheedge on 2012-11-16
I am new to Linux, and computer science. I am taking a class in Linux which has me writing some simple scripts in the terminal. 

I have noticed and appreciated the colourized formatting (I think formatting is the right word) of the text in my scripts. Usually when I would save a nano doc then chmod +x filename... then open it back up it would have a special colour scheme to help me see the script better. I don't know what the cue for doing that was actually... does it colourize anything with a shabang line or is it because of execute permissions, or something else?

Anyway, it stopped working and I can't figure out why. I am writing a new script. I saved the beginning lines, did my chmod +x... open it back up and still all the same colour text. Of course I will be able to still write the script but the feature was helpful, so I want to try to turn it back on. 

I have read the man page for nano and couldn't find anything about it. I tried making another script and it didn't work. The old scripts I have are still colourized though and continue to adjust the colours as I type like they used to. I am wondering if something from an update had something to do with it. I did run one of the updates ubuntu prompts me for (it had like 42 updates) without checking what every one of them was.

---

### Post by Impavidus on 2012-11-16
The syntax highlighting (that's the word) is not stored in your script, but is deduced from the syntax by nano. Many other text editors have the same capability. Typically these editors look at the file name extension and the first few lines. If the file name ends in .c they assume it's C source code, if the file starts with %!PostScript-Adobe-3.0 they assume it's postscript and if it starts with #!/bin/bash they assume it's a bash script. Often automatic determination of the file type does not work with new files, as they are empty when first opened. Syntax highlighting can be toggled in nano using alt-y. In most editors you can also select the used language manually, but I don't know where to find that option in nano.

---

### Post by towardstheedge on 2012-11-16
Thanks for the response.

I tried using the toggle (alt-y). It just told me it was toggled off then toggled on, but didn't change the highlighting. 

I copied the text of the file (file1) to a new file (file2) with clipboard and still no highlighting. I copied the text from a file (file3) where highlighting was working into a another new file (file4) and the highlighting did work. I then copied the text from file1 into file4 and the highlighting still worked. I rm file1... rm file2... then cp file4 to same file1 name and now it works. 

I am still puzzled why it wasn't identifying the original file1 as a script, but it is working now. Is there a place I can look at the script that determines if the file will get highlighted so I can try to figure out what the problem was?

---

### Post by Impavidus on 2012-11-16
Maybe this helps: [http://askubuntu.com/questions/90013/syntax-highlighting-on-nano](http://askubuntu.com/questions/90013/syntax-highlighting-on-nano)
I haven't read it myself completely as it's geting late here in Europe, but it seems what you're looking for.

---

