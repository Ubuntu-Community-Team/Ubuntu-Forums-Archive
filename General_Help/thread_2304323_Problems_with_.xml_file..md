---
title: "Problems with .xml file."
date: 2015-11-25
forum: General Help
---

### Post by annette3 on 2015-11-25
[COLOR=#000000]This is my first post. So, a huge THANK YOU in advance for your help and I apologise for my non tech savy is not adequate.[/COLOR]

[COLOR=#000000]I'm facing a huge problem, at least from my point of view. I was updating my animal stock records for my business I finished and saved it and went about my farming duties. When I came back and tried to restart the file it stated 
Read-Error 
Format error discovered in the file in sub-document content.xml at 2,28438 (row,col). 
[/COLOR][COLOR=#000000]I have a copy of the [/COLOR][COLOR=#417394]file[/COLOR][COLOR=#000000] but it is corrupted too. Both files cannot be opened on my computer, or laptop. [/COLOR]

[COLOR=#000000]I've been looking on internet to solve my problem but I've had no luck. 
I don't understand what was posted before as it went straight over my head.
[/COLOR][COLOR=#000000]Would it be possible to be helped, please? As this document has tag numbers, breeding records, health etc and I never thought Id loose it.. Ekk Help!![/COLOR]

[COLOR=#000000]I've attached the [/COLOR][COLOR=#417394]file[/COLOR][COLOR=#000000], just in case someone could have a look at it.[/COLOR]

Cheers
Annette

---

### Post by annette3 on 2015-11-25
[ATTACH=CONFIG]265774[/ATTACH]

---

### Post by Bucky Ball on 2015-11-25
*Posts moved to own thread.*

Welcome. The thread you originally posted on was old and inactive. This doesn't do anything for your chances of support. Best to post a new thread specific to your issue. There's plenty of room here. :)

---

### Post by annette3 on 2015-11-26
Thank You

---

### Post by dragonfly41 on 2015-11-26
There is a useful free XML editor in Ubuntu Software Centre you could try to open your file.

XML Copy Editor

Check "validate file" and "well formed".

I didn't see a link to view your file (you say it is attached?).

[COLOR=#000000]> Format error discovered in the file in sub-document content.xml at 2,28438 (row,col). [/COLOR]

...

[COLOR=#000000]Both files cannot be opened on my computer, or laptop.

What application uses these files?
[/COLOR]

---

### Post by howefield on 2015-11-26
Try this amended file..

The following steps to fix your file.

[list]Make a copy of the file so the "master" file is untouched.[/list]
[list]Working with the copy of the file, right click and select "Open With Archive Manager".[/list]
[list]Extract the content.xml file to the Documents folder.[/list]
[list]Use the following command to open the file in a text editor at the correct location.. (line 2, column 28438).[/list]
```
nano +2,28438 Documents/content.xml
```

It appears that the word "style" had an incorrect character in it, change it to say style and save the file.
Delete the content.xml from the ods file opened with archive manager and replace with the freshly saved content.xml.

---

### Post by dragonfly41 on 2015-11-26
I saw the uploaded file in post #2 and changed extension *.ods to *.zip then could unzip see inside (corrupted) content.xml.

The corrected file (posted above by howefield) seems to open in XML Copy Editor.

---

### Post by howefield on 2015-11-26
Not sure why you would change the extension as .ods already is a "zipped" file and no need to install extra software to fix it.

Shrug. :)

---

### Post by annette3 on 2015-11-29
OMgosh....

THANK THANK THANK THANK YOU Sooooooo Much....

---

### Post by howefield on 2015-11-30
You're welcome, can mark this one solved then.

---

