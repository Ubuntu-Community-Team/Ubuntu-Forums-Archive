---
title: "Mostly blank page when print to pdf using the default evince viewer (Ubuntu 18.04)"
date: 2019-07-03
forum: General Help
---

### Post by jiifon on 2019-07-03
Hello everyone,

I recently started using Ubuntu 18.04 (fresh install), and noticed some problem with printing (or maybe font issue related with PDF). I have spent quite some time these days googling about it but with no success. Any information that you think might help solve the problem is greatly appreciated.

**Problem details**: 
[LIST=1]
[*]I tried to print this [pdf]("https://link.springer.com/content/pdf/10.1007/JHEP02%282018%29095.pdf") on my HP printer (in evince). But got a mostly blank page in the preview, like this [ATTACH=CONFIG]283553[/ATTACH]. 
[*]Also in evince I tried printing it to file pdf (yes, print this pdf again to pdf), but the pdf produced is not right either, still the same mostly blank page. 
[*]I opened the problematic pdf in firefox, and tried printing on the HP printer. This time all the text appeared but seriously blurred. 
[*]All other pdf files I tried will correctly print on the HP printer or to pdf files. The problem so far only occurs with that particular pdf mentioned in 1. 
[/LIST]

**Info: **
[LIST]
[*]OS is Ubuntu 18.04.2 desktop version (freshly installed four days ago) 
[*]hplip is installed 
[*]Before this installation of 18.04 I had been using 16.04 for more than one year, and the same HP printer (DeskJet 1112) worked perfectly. In the current 18.04 I also used more or less the same procedure to set up the printer. 
[/LIST]

**Some thoughts: **At first I thought it was a problem with my installation of the HP printer, but after I tried print to file (and the problem remains) I guess it might have something to do with missing fonts used when producing pdf files?

I've tried some methods found on google, like installing microsoft fonts but none of them worked :(. Any ideas how this can be fixed?

Thank you very much!

[HR][/HR]***UPDATE: ***
The problem is solved/circumvented by using the commandline printing tool [I][B]lpr
[/B][/I]```
lpr -P printername file.pdf
```

Thanks to all the feedbacks and infos provided by [**[COLOR=#000000]SeijiSensei[/COLOR]**]("https://ubuntuforums.org/member.php?u=698195"),                                                                                      [**[COLOR=#000000]Claus7[/COLOR]**]("https://ubuntuforums.org/member.php?u=164533"),                                                                                      [**[COLOR=#000000]Impavidus, [/COLOR]**]("https://ubuntuforums.org/member.php?u=1417721")**[COLOR=#000000][[B][COLOR=#000000]dragonfly41, [/COLOR]**]("https://ubuntuforums.org/member.php?u=1261878")[/COLOR][/B](Thank you very much!),  I became quite sure this is a problem related with the interaction between Evince and my font configuration (or perhaps my locale). So I tried to start Evince from command line and then printed to see if any error message could appear, but no error at all. Again, in order to see possible error pops out, I tried lpr to print the pdf, and then it just worked! 

In my case, Evince can correctly display the pdf and it also reports that all embedded fonts are installed in the property info. It just gets into trouble when it talks to (virtual) printer.  To really solve the problem I think it is necessary to check further how fonts are chosen by evince when producing the pdf for printing. According to some infos I got by Googling, Evince and cups actually use different mechanisms to print pdf files. Somehow evince is confused by my font configuration but cups is not, and lpr uses cups, so works correctly. 

So far I am quite happy with using lpr. Actually I find lpr is more convenient for my particular printer model and my use cases. Maybe I will simply write some script to print pdfs in the future :).

---

### Post by SeijiSensei on 2019-07-03
I just printed the first two pages of that document using Okular, the KDE utility for PDFs.  You can install it on vanilla Ubuntu with "sudo apt install okular". It will install a bunch of dependencies since KDE uses the Qt libraries, not GTK like GNOME-based flavors use.

---

### Post by jiifon on 2019-07-05
Hello SeijiSensei, 

thanks for your attention and the info about Okular. It is good to know that at least there is something working, and I will try that way as a last resort. But I still wonder if there is any other way without installing those KDE related packages (because I don't seem to need any other KDE tools so far). It seems to me a little bit overkill to install the whole KDE just for this problem (or maybe I should have installed Kubuntu right from the start :-k ). 
But thanks any way :).

---

### Post by Claus7 on 2019-07-05
Hello,

I can print (actually save) that file via the print option in a new pdf file without problems under ubuntu. Okular is a really nice application for pdf viewing but mainly pdf editing. Your problem should lie elsewhere though...

Suggestions:
1) reinstall some fonts of yours
2) reinstall evince
3) check okular if working
4) try another lighter pdf reader and see what you get: qpdf?

Regards!

---

### Post by Impavidus on 2019-07-05
I've no problem at all with that file on Xubuntu 19.04. Evince, gv and firefox display it correctly, the print preview in evince is fine and so is the print to file. I didn't try an actual print on paper. Evince tells me that all fonts in that pdf are embedded (partially, i.e., only those characters actually used). I doubt it's a problem with the fonts installed on your computer.

---

### Post by dragonfly41 on 2019-07-05
I can [download from here]("https://link.springer.com/content/pdf/10.1007%2FJHEP02%282018%29095.pdf").
Another PDF reader to try is [Foxit Reader]("https://www.foxitsoftware.com/pdf-reader/").

---

### Post by jiifon on 2019-07-12
> **SeijiSensei said:**
> I just printed the first two pages of that document using Okular, the KDE utility for PDFs.  You can install it on vanilla Ubuntu with "sudo apt install okular". It will install a bunch of dependencies since KDE uses the Qt libraries, not GTK like GNOME-based flavors use.

> **Claus7 said:**
> Hello,

I can print (actually save) that file via the print option in a new pdf file without problems under ubuntu. Okular is a really nice application for pdf viewing but mainly pdf editing. Your problem should lie elsewhere though...

Suggestions:
1) reinstall some fonts of yours
2) reinstall evince
3) check okular if working
4) try another lighter pdf reader and see what you get: qpdf?

Regards!

> **Impavidus said:**
> I've no problem at all with that file on Xubuntu 19.04. Evince, gv and firefox display it correctly, the print preview in evince is fine and so is the print to file. I didn't try an actual print on paper. Evince tells me that all fonts in that pdf are embedded (partially, i.e., only those characters actually used). I doubt it's a problem with the fonts installed on your computer.

> **dragonfly41 said:**
> I can [download from here]("https://link.springer.com/content/pdf/10.1007%2FJHEP02%282018%29095.pdf").
Another PDF reader to try is [Foxit Reader]("https://www.foxitsoftware.com/pdf-reader/").

Thank you all! :) My problem solved/circumvented. See the update if interested.

---

