---
title: "Google Sketchup Fails"
date: 2014-03-05
forum: General Help
---

### Post by Tristan_Williams on 2014-03-05
I installed Google Sketchup using Winetricks. (After attempting and failing the tutorial found [here]("http://ubuntuhandbook.org/index.php/2013/07/install-sketchup-2013-ubuntu-13-04/"))

I have the Google Sketchup Icon on my Desktop.
I can start the application, select a template, and press "Start using SketchUp"

After I press the button, it gives me an error that says this:




SketchUp was unable to initialize OpenGL!
Please make sure you have installed the correct 
drivers for your graphics card.

Error: ChoosePixelFormat failed



So what do I do?

---

### Post by tgalati4 on 2014-03-06
3D graphics requires a hefty graphics card and one that supports OpenGL.  What is your graphics card?

If this machine dual boots into Windows, does Sketchup work in Windows?

```
lspci | grep VGA
```

---

### Post by Portaro on 2014-03-06
I have this same problem but isnt constant sometimes i receive the same message, is a problem with graphic card performance, if you have open many processes i think this is the problem the sketchup stops because have short memory range RAM and processes of other apps colapse the init.

You can try two tricks 
one 

start sketchup on the pc without any proecesses execution like firefox, or
try launch the sketchup with 
**LIBGL_ALWAYS_SOFTWARE=1 wine sketchup** maybe works.

In my case I solve the problem with tricks I mention above.

I use sketchup 8 and 13 and also works on Wine.

---

### Post by Tristan_Williams on 2014-03-06
```

Tristan: ~ $lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

```

And no, I do not dual boot Windows. Ubuntu Minimal is my only OS.

---

### Post by tgalati4 on 2014-03-06
You might try running in WINE with the appropriate OpenGL drivers:  [https://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=2991&DwnldID=20046&lang=eng&iid=dc_rss](https://downloadcenter.intel.com/Detail_Desc.aspx?ProductID=2991&DwnldID=20046&lang=eng&iid=dc_rss)

---

