---
title: "Can not print text"
date: 2015-07-13
forum: General Help
---

### Post by Stuart_Saunders on 2015-07-13
Hi,


 I'm trying to print a simple letter using Libreoffice  Writer but it will not print the text. It will however print draw  objects like a simple line or rectangle.
 

 I am running Ubantu (all updates done today) on my laptop  connected (wireless) to a HP printer. I have tested the printer via the  Ubantu "test print" and all is fine (including text). It will print draw  objects via Libreoffice Writer so I know that something is getting  through but never the text objects.


 I have tried exporting the  file as a pdf and the text shows together with draw objects when opened  in a pdf viewer. The same result happens if you print from a pdf file.  ie you get the draw objects but not the text!

I have also tried using the text editor but same thing, it wont print text. 


 Any help would be appreciated.


 thanks...

---

### Post by Stuart_Saunders on 2015-07-13
Note: I have the same problem if i connect the printer directly via a USB cable.

---

### Post by jay98 on 2015-07-13
What HP printer are you using?  What driver?  Is it supported?
Use CUPS to administer your printer - I have never found the GUI to work well.
Open a browser and go to: 
```
localhost:631
``` 
Check your parameters.
Try a different driver.
If that doesn't work, delete and re-install the printer.

[COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]

---

### Post by Bucky Ball on 2015-07-13
More to the point, do you have a driver installed? First up, try installing HPLip from the Software Centre and provide us with the model of the printer.

---

### Post by Stuart_Saunders on 2015-07-14
Hi...thanks for the replies. 

I'm using a HP officejet J4680 printer and have HPLip installed. I will try using CUPS and report back.

---

### Post by Stuart_Saunders on 2015-07-14
The printer appears in CUPS (localhost: 631) and I have printed a test page from the maintenance menu. 

All appears fine but when I try to print some simple words from the text editor it just prints a blank page!

---

### Post by amanchesterman on 2015-07-14
This is a puzzle, I've never met anything like it before. I can think of two possibilities for you to check:
1) If the printer is one of those with several print cartridges, one of them might have run out and that might just be the colour needed for your text. (I once had a problem not being able to print some images on a page while other text and images printed OK, and that was the cause.) Check the colour of the text you want to print, and maybe change it to a very different colour and try again -- this will at least help to eliminate the possibility.
2) Have you checked that you have not inadvertently created 'non printing text' in LO Writer? This will appear as normal text on your screen but -- by definition -- it will be omitted when you try to print.
Just a couple of ideas, trying to help.

---

### Post by Stuart_Saunders on 2015-07-14
Hi amanchesterman,

1) All the cartridges are fine. I can run a test page and get all the colours of the rainbow. It even prints text on the test page!
2) I've checked its the "non printing text" is off in LO. I've also tried printing using Text Editor and as it doesn't have this feature.

---

### Post by Stuart_Saunders on 2015-07-14
Update...

I have re-installed HPlip and now have the following message in system settings>printer>printer status "Stopped - Backend /usr/lib/cups/backend/hp does not exist!"

Further update...

The status is now "Idle-ready to print" as I *resumed printer* via CUPS.

Still now text printing via either LO or Text Editor. I can still print shapes, lines etc in various colours in LO.

---

### Post by tgalati4 on 2015-07-14
Sometimes you have to delete the printer and reinstall.  The printer queue gets messed up (not unlike in Windows) and needs to be deleted and reinstalled to get it working again.  This sometimes happens after updates to the kernel, CUPS, or both.

---

### Post by Stuart_Saunders on 2015-07-15
I have deleted and reinstalled the printer. The symptoms are still the same, ie can print shapes in various colours via LO but still no text. Tried printing in Text Editor and still no text will print.  

I'm going to take my laptop to work and try a different printer.

Any other suggestions welcome.

---

### Post by Bucky Ball on 2015-07-15
I suggest this is one of the more unusual problems I've seen on here! :-k

---

