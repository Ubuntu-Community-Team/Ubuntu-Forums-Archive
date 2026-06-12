---
title: "Regarding copying and pasting the .xvg or .agr files into Libreimpress writer"
date: 2017-12-21
forum: General Help
---

### Post by dilip.h.n on 2017-12-21
Hello all,
I have a graph which is in .xvg/.agr format. Now since i am writing an article in LibreOffice writer, i want to import/copy and paste the graph which is in .xvg/.agr format. How do i do this..?? 
[COLOR=#000000]I tried going to insert option but couldn't get suitable options to do this.

How to solve this issue..??

Any suggestions are appreciated...[/COLOR]

---

### Post by Holger_Gehrke on 2017-12-21
Is this .xvg file produced by the plotting software grace ? Then you can't use it directly in LibreOffice, it's a grace internal file-format. But grace can export to various formats that LibreOffice does understand including (E)PS,SVG,PNG and JPEG. The option to do this is 'hidden' in the printing setup - just select a file format as the device, print to file with a custom page size in pixels and then "print".
Holger

---

### Post by dilip.h.n on 2017-12-21
Yes, this .xvg file is produced by the plotting software grace. I can now export the file into png, jpeg format and copy paste into the LibreOffice writer, but there is compromising with the image quality...which gets blurred when zoomed in...
But if i save the file in .ps/eps format, the image quality is perfect, and there is no any blurred image when zoomed, but the ps/eps files can't be inserted into the LibreOffice writer... So, how to insert the images in .ps/eps format into LibreOffice writer..??

---

### Post by Holger_Gehrke on 2017-12-21
There's one more export option you didn't try: SVG - Scalable Vector Graphics. While LibreOffice says it can use EPS, it says the EPS-files grace produces are invalid. The SVG Output on the other hand seems to be exactly what LO likes...

Holger

---

### Post by dilip.h.n on 2017-12-21
Thank you very much sir,

Now i have a .xvg file in which i have plotted around 5-6 graphs (basically i have plotted with varying concentration), and i have to label the graphs with lines and text ( as GAW, GAW-10:90, etc... ) and i have tried it as shown in the image attached. 
1] How to align the all those labeled indication lines... since it looks aligned and neat..??
2] How to copy the labeling from one .xvg format into another .xvg file (since the labeling is the same, it is tedious again to label and align it every time). Here i have converted the .agr file into . png format and then uploaded the .png image file

---

### Post by Holger_Gehrke on 2017-12-22
These Labels should be set as "legends" for each dataset. Use "View"->"Set Appearance" -> Tab "Main" to set the legends for each dataset, then use "View"->"Graph Appearance" and set "Display Legend" on the "Main"-Tab on and position the legend box on the tab "Leg. Box".

 As far as copying the legends from one file to another, I see two options: 

[LIST=1]
[*].agr and .xvg files are simple text, edit them in your favorite text editor. 
[*]In a terminal, display the (source) .xvg with less. Mark the text you want to copy with the left mouse button. Open the target .xvg in Grace, go to "View"->"Set Appearance"->Tab Main, click with the left Mouse Button in the field "Legend" to activate it then with the middle mouse button to paste the marked text from the terminal. 
[/LIST]
 
Holger

---

