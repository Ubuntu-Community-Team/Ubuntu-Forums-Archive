---
title: "Fonts on Inkscape"
date: 2018-01-13
forum: General Help
---

### Post by byelich13 on 2018-01-13
So I was on Inkscape and I wanted to download a new font and I went back to Inkscape to use it and it wasn't there. I then saved my project and closed then reopened it. From there every font I downloaded before was gone. If anyone has any ideas on how to get them back that would be great.

---

### Post by Dennis N on 2018-01-13
Just downloading a font file doesn't make it available. The font file has to be placed in one of several special locations. These come to mind: 
/usr/share/fonts
~/.fonts
~/.local/share/fonts
I doubt that your downloaded files disappeared. Did you use Firefox to download them? They should be in it's downloads folder. See the Firefox preferences.

---

### Post by ajgreeny on 2018-01-13
All the fonts you will use in Ubuntu are stored in either:-
1. /usr/share/fonts
2. ~/.fonts  (these will be available for that user only)

I recommend you install them in the #1 location as they will be usable by all user accounts on the computer, including the system utilities.
First make a folder to hold your custom fonts.
```
sudo mkdir /usr/share/fonts/truetype/myfonts
```
I am using myfonts as an example.
Next open a terminal in the folder where you downloaded your fonts and use command
```
sudo cp ./*.ttf /usr/share/fonts/truetype/myfonts
```
This will copy the truetype fonts to that folder. You may need to do this separately for any named fonts where the file suffix .TTF is in upper case, as linux is case sensistive.
Finally open a terminal in your myfonts folder and run command```
sudo fc-cache -f -v
```
This will install the fonts systemwide so that both your applications like LibreOffice, and any other users including the system utilities can use them.

---

### Post by coffeecat on 2018-01-14
*Thread moved to **General Help**.*

---

### Post by byelich13 on 2018-01-16
I see them in the folder but they still wont show up in inkscape

---

### Post by ajgreeny on 2018-01-16
Did you run the **sudo fc-cache -f -v** command after moving the ttf font files to make sure they are all available?

I do, however, see many problems of fonts not appearing in inkscape when searching askubuntu and these forums using my own custom google search engine; try it yourself at [https://cse.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao](https://cse.google.co.uk/cse/publicurl?cx=003847201077524938900:ukjniuf1wao) using "fonts inkscape" as your search term and you may find something more useful than me searching for you and trying to figure out what you've tried so far.

---

### Post by Juhele on 2018-01-17
Not sure about other Ubuntu flavors but for example Kubuntu has a graphic tool to install fonts (I would expect similar tool also in Gnome and other "big" environments). I think I can use right click on font file and then choose somethink like "Install font" or I just open it in font viewer and then install it. It offers me to install for user only or as system font. In both cases the font appears in Inkscape (you have to restart Inkscape).

---

