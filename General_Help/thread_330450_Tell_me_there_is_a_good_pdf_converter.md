---
title: "Tell me there is a good pdf converter"
date: 2007-01-03
forum: General Help
---

### Post by lapsey on 2007-01-03
Well, smashing: I've finally had to resort to Adobe Photoshop's PDF --> PSD function.

In the last few days I have tried:
[LIST]
[*]Imagemagick / Ghostscript - A neat set of tools, somewhere along the line someone dealing with pdf handling thought it would be a good idea to make heavy use of /tmp files. The result? Reading a 200Mb PDF will mean you run out of 5Gb very quickly. Especially great when you're running it on a limited web server.
[*]Koffice - Again, started working and never stopped. Huge amounts of cruft had to be found and removed.
[*]Kpdf - if there ever was an 'export to images' option it's not there anymore..
[*]Abiword - Exactly the same problem as Imagemagick. I suspect it's the same issue with Ghostscript as above, if that is the case there.
[/LIST] 

So: if you have any OTHER solution, **please post it here!**

I'm even tempted to look into running a virtual printer that saves images sent to it, but there seem to be nothing of the sort for linux which is very odd indeed..

---

### Post by NoNo_231 on 2007-01-03
What exactly are you trying to do and where is the problem? Are you trying to export images from pdfs or trying something else?

If trying to get images you can use gimp. Import pdf file, the page you want and then save it to the format you want. Or from the adobe reader you can copy the image and paste it in openoffice or gimp.

If you mean something else please specify.

---

### Post by martijn hoekstra on 2007-01-03
I am not an expert on the issue, and therefore I need a bit more info on what you actualy need.  In the simpelest possibility you just have the entire pdf rastered and bitmapped and convert it to .psd. This should be possible with ghostscript. If it's not (I'm not at my ubuntu machine at the moment, and have no possibility to test it) it could very well be a bug.
In *theory* it should also be possible to tear apart the PDF in text, image and graphic components, and place all these on seperate layers. Maybe GhostScript should even be able to do that. Maybe someone sees a task for him/herself and wants to make a tool for it.

If ghostscript is in fact fouling things up you might have a Big Problem as GhostScript is the standard GNU/Linux tool for handeling PDF, and it could very well be that a lot of applications that handle PDF do this using GhostScript.

Anyway, I'm looking into it, I'll let you know as soon as I have something more.
K.R.
M.

---

### Post by lapsey on 2007-01-03
> **NoNo_231 said:**
> What exactly are you trying to do and where is the problem? Are you trying to export images from pdfs or trying something else?

If trying to get images you can use gimp. Import pdf file, the page you want and then save it to the format you want. Or from the adobe reader you can copy the image and paste it in openoffice or gimp.

If you mean something else please specify.

to clarify: I'm trying to automatically convert a large pdf into a **series** of images. 

Thanks for pointing out GIMP. Hopefully one of the scripting extensions (on the command line) will allow for doing just this.... 
doing this manually with GIMP is not humanly possible.

---

### Post by lapsey on 2007-01-03
> **martijn hoekstra said:**
> If ghostscript is in fact fouling things up you might have a Big Problem as GhostScript is the standard GNU/Linux tool for handeling PDF, and it could very well be that a lot of applications that handle PDF do this using GhostScript


It doesn't have to be psd; Its just that is the only format that Adobe Photoshop allows with that process. I was originally trying to convert to png.


Here is what I have been doing with a ~200MB (image rich) pdf & imagemagick (which uses ghostscript):

```
convert "input.pdf[10-169]" output-page%03d.png
convert "input.pdf" output-page%03d.png   # doing these causes me to run out of HD space in /var/log - they seem mostly to be error messages.


convert "input.pdf[10]" output-page10.png # This is the only use of pdf conversion with imagemagick that works (but is very slow)
```

---

