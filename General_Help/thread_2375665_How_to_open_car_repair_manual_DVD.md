---
title: "How to open car repair manual DVD?"
date: 2017-10-26
forum: General Help
---

### Post by palmgrower on 2017-10-26
How can I open a car repair manual on DVD in Ubuntu 16.04 LTS? The DVD is supposed to be used with any variant of Windows. All my home PC's were switched over to Ubuntu many years ago and I don't have a Windows PC. 
Thank you.

---

### Post by Mark Phelps on 2017-10-26
If the manual uses some proprietary third-party viewing app, it is NOT going to work in Linux, period -- and unfortunately, that happens all to often.

---

### Post by SeijiSensei on 2017-10-26
> **Mark Phelps said:**
> If the manual uses some proprietary third-party viewing app, it is NOT going to work in Linux, period -- and unfortunately, that happens all to often.

One option in this case is to install [Wine]("https://wiki.winehq.org/Ubuntu") and see if it will run the Windows app.

---

### Post by palmgrower on 2017-10-26
Thank you for the explanation. The DVD needs Adobe Acrobat and SVG Viewer (included on DVD). I suppose I am out of luck.

EDIT: I will install wine and see how it goes. Thank you.

---

### Post by palmgrower on 2017-10-26
Installed wine. Inserted DVD. Nothing happens. Am I to call out wine with a special command to read the dvd?

---

### Post by Andrew_Lucas on 2017-10-26
IIRC Acrobat is just a .pdf viewer? The CD might try to launch the viewer but if you can navigate to the .pdf files on the disc, you should be able to open them with another program (whatever it is that you're using - evince, etc).
Alternatively, if it isn't just a .pdf viewer, it'll be opening some other file format. Open the disc, find out what the file format is, then either post back here to see if anyone knows of a program that can open that format, or Google "Linux .xxx program", where .xxx is the file format. If it doesn't show it immediately in your file manager, right click and go to properties to identify the file type.

Lastly cars are fairly big things, traded for a long time. I'd expect the manufacturer has the manuals online and downloadable...

EDIT: I wasn't sure, so checked. .SVG is an open format and so there will be *loads* of Linux programs which can view/open it. EoG, Ristretto, Pinta...

---

### Post by SeijiSensei on 2017-10-26
> **palmgrower said:**
> Installed wine. Inserted DVD. Nothing happens. Am I to call out wine with a special command to read the dvd?
If there is a setup.exe program on the disc you can try running that in wine.

If it's just those viewers and a bunch of files, can you not navigate to the files on the disc and open them in a PDF viewer?  As for SVG, take a look at [https://askubuntu.com/questions/821612/opening-vector-files-in-ubuntu](https://askubuntu.com/questions/821612/opening-vector-files-in-ubuntu)

---

### Post by palmgrower on 2017-10-26
When I insert the dvd, nothing happens. Since I cannot read the dvd, I cannot run setup.exe, etc.

I have given up and am converting an Ubuntu PC to Windows 2000. Do I have to prepare the hard drive in a special way? Windows 2000 cannot find a partition that it likes. By the way, all hard drives I have were used in Ubuntu. Thank you.

---

### Post by oldos2er on 2017-10-26
I don't think either Windows ME or XP is supported anymore.

---

### Post by Frogs Hair on 2017-10-26
I would web search for the manual. You might find a usable file format. I've had good luck with this even for very old products.

---

### Post by palmgrower on 2017-10-26
> **oldos2er said:**
> I don't think either Windows ME or XP is supported anymore.Now I need to buy Windows 10 Home. Price varies from $40 to $100+. Which one should I buy? Thank you for your advice.

---

### Post by mörgæs on 2017-10-27
None of them. You should study thoroughly how much spyware is embedded in Windows 10 before considering that option.

Please browse the DVD without attempting to run its programs. Just post the contents here.

---

### Post by cdoublejj on 2017-10-27
xp is sometimes supported. i made a windows xp virtual machine using vmware vmplayer

---

### Post by Impavidus on 2017-10-27
The people providing these dvds are usually unaware of the existence of operating systems other than Windows, so the fact that they don't say it works on anything other than Windows doesn't imply that it doesn't work on anything other than Windows. "All versions of Windows" usually means all OSs they're aware of.

All versions of Windows includes some old versions that were supported when the dvd was first released and with the long life of this kind of documentation it can't really rely on non-standard file formats. You don't need the svg viewer included on the dvd, as Ubuntu already has an svg viewer built-in (they included an svg viewer because older Windows versions don't have one). Pdf files should be no problem either. So just insert the dvd, navigate to it in your file manager and see what's inside.

Unless you can't even mount the dvd, in which case it might be damaged and won't work in Windows either.

---

### Post by oldos2er on 2017-10-27
> **palmgrower said:**
> Now I need to buy Windows 10 Home. Price varies from $40 to $100+. Which one should I buy? Thank you for your advice.

That's a question best answered on a Windows forum; I have zero experience with it.

But if all you need is a PDF file reader, Ubuntu has several to choose from.

---

