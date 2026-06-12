---
title: "Libreoffice disapeares"
date: 2016-01-17
forum: General Help
---

### Post by miniKOX on 2016-01-17
Hello.

I am sorry if I have choosen bad subforum, but I really don't know where to ask.

My problem is, that my libreoffice often disapeares unexpetedly(for example I am writting in Writer and the program disapeares while I am writting, then the only option to get my document back is to read it from previous autosave(if it happen before Libreoffice crashes).

My Ubuntu is 12.04 and Libreoffice is 4.4.

I really searched for the solution over internet, tried everything: turning off Java, turning off anti-alliasing i LO, installing from official debs, removing Libreoffice profile catalog(.libreoffice)(in /home - if I remeber) - nothing helped, the problem still apeares veeery often, and the one thing that I can do is to make autosave with 2min. interval so I am able to recover my documents.

I am using computer in school and I really need Office  to be stable...but it is not....

I ask for help.

---

### Post by speartip on 2016-01-18
Weird problem, never heard of that happening before.
The only thing I can suggest is that some config file is corrupted somewhere.
To get rid of LO completely, try:
```
sudo apt-get remove --purge libreoffice*
```
Then make sure that you remove it's config folder in /home/username/.config.
Make sure that /opt is empty of anything "libreoffice".
Then reinstall using the 5.0.4 version from here:
[https://www.libreoffice.org/download/libreoffice-fresh/](https://www.libreoffice.org/download/libreoffice-fresh/)
If you need any help there, post back. Otherwise no idea.

---

### Post by miniKOX on 2016-01-18
Will the fresh version be ok? I mean: won't it have to many errors - will not be too "unstable"? Though my LO 4.4.7 was "stable", and was - in my opinion the most unstable and unpredictable office suite in da great-great world....:/

---

### Post by speartip on 2016-01-18
It's been rock solid stable for me.
All you can do is try it, and hope for the best. It can't be any worse than the problems you're having. Don't forget to delete the configs mentioned in the last post though.

---

### Post by miniKOX on 2016-01-19
I installed it as you told by downloading and installing *. debs with command: dpkg*-someting with i.

And now it has problem with opening files: documents are opening in archives manager....

---

### Post by speartip on 2016-01-20
That's easy to resolve. It's probably just lost it's file association after uninstalling.
Just right click any file you want LO to open. Go to properties, and change the "open with" back to LO.
If there is a list of apps, make sure LO is at the top.
All files with that suffix should now open with LO.

---

### Post by miniKOX on 2016-01-20
And I have to do so with every filetype, that is going to be opened with LO? There is no way to do it automatically?

---

### Post by speartip on 2016-01-20
> **miniKOX said:**
> And I have to do so with every filetype, that is going to be opened with LO? There is no way to do it automatically?
Only those that LO won't open on clicking. Not every file. Just file-type. There can't be more than 4 or 5???

---

### Post by miniKOX on 2016-01-20
I kniow that filetype. 
*.odt
* doc
*. docx
*. ppt
*.ppts
*. ppsx
*.pptx
*.odb
*.xls
*. Open-xls
and God(because I don't) knows what else...

---

### Post by speartip on 2016-01-20
And do none of them open with LO automatically?
It may be the old version of Ubuntu you are using. Most are now on 14.04 or later.
When I installed the latest LO, all my file type defaults were kept. The only exception to that would be if you tried to open a file without LO installed at all, then it would look for another app. & possibly make it the default.
I don't know of any way to change that automatically.

---

### Post by miniKOX on 2016-01-20
My system treats these files as Libreoffice was never installed - not recognizing them to open in LO.
Very sorry, but I do not know really if all that Ubuntu is so intelligent that I can not realize that with my small brain, or if I am the greatest moron, idiot in the world, so that I never should been install Linux :/... I do not realize how it all may be...

---

### Post by speartip on 2016-01-20
I can understand your frustration. We've all been there.
Just one question.
When you right click on a file you want opened with LO, then go to properties/open with.. When you have LO as the default app, have you clicked the "set as default" button on the bottom right of the box?
Or maybe hit the reset button and see what happens.

---

### Post by miniKOX on 2016-01-20
It all looks like this - sorry fot the bad images order
.[ATTACH=CONFIG]266855[/ATTACH][ATTACH=CONFIG]266856[/ATTACH][ATTACH=CONFIG]266857[/ATTACH]

---

### Post by speartip on 2016-01-20
OK. Sorry I'm struggling with the language.
So on the 2nd picture, are you saying that when you scroll down that list, that LibreOffice is not there?

---

### Post by speartip on 2016-01-20
This is the screenshot from my "open with" box if it helps.
I just highlight LibreOffice writer in the list & click "set as default".
If it's not there then I click the add button, find the app that way, highlight it and click "set as default"

---

### Post by miniKOX on 2016-01-20
I can set writer/database/calc as default application for opening certain filetypes, but:
1st - I must know with application opens with file
2nd - there are too many extensions as for me to append applications manually for each extension...(there are about 20 extensions i think...)
3rd - when I choose option to "find application online to open file" system wants to download libreoffice 5-something as it was not installed/present in system(but it IS installed and present, and I can open fies with it, and even write in all the writers and so on. And it may be - with help of God - that the LO will not disappear: but to be so, i really must be a man of great faith - otherwise it will "disapear" - and I think that I do not have so great faith for LO not to disappear, so it will be disappearing...

---

### Post by speartip on 2016-01-20
Writer opens documents. Calc opens spreadsheets. Impress opens presentations. Draw is for pictures. 
Finding application online is pointless, when LO is already installed.
Just try one file type to start with. If LO doesn't crash, then all is ok.
Even if you have 20 file types it shouldn't take longer than 5 minutes.

---

