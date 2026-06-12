---
title: "Cannot use &quot;&quot; in Word with wine"
date: 2015-02-20
forum: General Help
---

### Post by teun95 on 2015-02-20
Hey forum,

I am still quite new to ubuntu only used it for a few weeks now but i think i'm getting there.

I have installed crossover to be able to install Microsoft office 2010, I would love to use only libreoffice but I really need word for college.
Everything of office 2013 is working except for one thing. I cannot type the quotation mark "" and therefore also not characters like this "ü".
When I open any other application typing this symbol is no problem, in libreoffice it works perfectly.
I live in the netherlands and we use the US keyboard layout but none of the keyboard layouts seem to work.

Any suggestions how I should solve this?
I hope this is not a really stupid question :)

---

### Post by Neill_R on 2015-02-20
have tried adding the dutch input control of the keyboard.

Don't give up so easily with LibreOffice it is possible to read and write files in all sorts of version of Office from with in LibreOffice. I think you should at least try it once just save your home in Office format to take to college. just remember when you save the file to click on All Formats drip down button and select the version of Office you need

---

### Post by ajgreeny on 2015-02-20
> **Neill_R said:**
> Don't give up so easily with LibreOffice it is possible to read and write files in all sorts of version of Office from with in LibreOffice. I think you should at least try it once just save your home in Office format to take to college. just remember when you save the file to click on All Formats drip down button and select the version of Office you need

^^^ +1
You can even set LO to save everything in the MS formats by default, which works very well; doing that means that you don't get the warning every time you save in .doc or .docx and neither do you need to remember the change of filetype every time you save.

Once your college work is finished you can reset to save in the open-format filetype again very easily.

I have been using OpenOffice and now LibreOffice for many years and have had no major problems regarding cross compatibility; in fact OO and LO have been much better in that respect than the version of Lotus Smartsuite that I used for several years before OpenOffice came along.

---

### Post by teun95 on 2015-02-20
I know and for individual assignments I do use Libreoffice but for group work I noticed that I destroy the graphs and tables when I use Libreoffice

> **Neill_R said:**
> have tried adding the dutch input control of the keyboard.

I have tried that but the thing is: nobody in the Netherlands uses the Dutch keyboard layout.
We use the US keyboard layout with a dollar sign on 4.

I have checked now. 
"English US" is working but "English (US, international with dead keys)"  is not, at least in word.
I need the "English (US , international with dead keys)" to type letters with accents. e.g. "ë" works everywhere except in word. 
This is the case on two seperate computers. My Zenbook and my desktop.

---

### Post by teun95 on 2015-02-20
After some digging I found this: [https://www.codeweavers.com/support/forums/general/?t=26;msg=163070](https://www.codeweavers.com/support/forums/general/?t=26;msg=163070)
I'm going to try it this afternoon.

---

### Post by teun95 on 2015-02-20
I think it is solved. I did what was on the forums and went to: system settings - langauge support 
There i put the "keyboard input method system" from "IBus" to "none".
After restarting everything worked like it should :)

---

### Post by SeijiSensei on 2015-02-20
I recently discovered that ibus grabbed keystroke combinations when I suddenly couldn't use Ctrl+SpaceBar to set a mark in Emacs.  I thought for a moment I was crazy when a keystroke I'd used for years suddenly stopped working!

---

