---
title: "Text editor encoding problem"
date: 2013-03-24
forum: General Help
---

### Post by jamal15 on 2013-03-24
Does anybody know how can i open a .bin file with a text editor that does not scramble too much the text inside ? On Windows, if i open it with notepad (it uses ANSI encoding) the text is pretty ok, but on ubuntu with gedit it shows many many weird squares. If i open it with KWrite, the text shows a bit more ok, no squares, instead shows other characters. This is for a friend who use the .bin for a tv-receiver (i don't know details), and he uses lubuntu, while on my computer KWrite shows the file without squares, on his computer KWrite still shows the squares.

---

### Post by The Cog on 2013-03-24
My guess is that the bin file contains binary data and that you shouldn't be trying to view it as text at all. The difference you see in the text editors is a difference in how they try to cope with binary data and represent it as text. In ubuntu I would use the command-line program hd to view the file contents.

---

### Post by jamal15 on 2013-03-24
I have typed "hd filename.bin" and it shows some numbers and the TV channel name on a column on the right, first i thought this is weird too, but the person which asked me about said that this is perfect, the information is perfectly decoded, on the right is the TV channel name, and the numbers from the left represents the TV key. Now my question is if i can modify this file using this decoded information?  Copy and paste the output from terminal in text-bin file should do the job ?

---

### Post by The Cog on 2013-03-24
No. The numbers on the left are the actual byte values (16 bytes per line), and the text on the right is the same bytes as character values (if that bytes contains a printable character code). To edit such a file, install package ghex and use the editor that installs, called ghex2. But I have the feeling you might be better off asking your friend to give you some guidance as he seems to know more about what the file contents should be.

---

