---
title: "Libre office draw"
date: 2023-07-11
forum: General Help
---

### Post by nigela on 2023-07-11
I am not certain if this is the right place but hope someone can help me.  My computer is i5 and 16gb ram with ssd.  I am trying to do a 20 page programme for a theatre show with about 120 photos in.  I am using libre office draw 7.5 but it is now taking we about 40 minutes to adjust one photo as draw is running so slow.  I have tried to change the memory in advanced settings. It has gone from 4 gb to 6gb and now 8b but it hasn't made any substantial improvements.  Is my computer hardware just insufficient or is it the software. I am using Ubuntu mate 20 lts

---

### Post by CharlesA on 2023-07-11
It might help to mention which version of Ubuntu you are using.

I also moved this thread to a different forum. It might get more attention here.

---

### Post by DuckHook on 2023-07-11
Welcome to the forums, nigela

You are forcing me to reach way back in memory to dig out this knowledge, but here are my two bits:

For your purposes, LibreOffice is the wrong suite of apps to use. The problem with any Office&#8209;type app is that they are all flat files. This means that *everything* is loaded into RAM at the outset. In your case, a 20 page programme with 120 photos is very RAM&#8209;intensive and although 16 GB of RAM is a lot, it may very well tap out with 120 simultaneous photos, at which point, either swap space is used (which is excruciatingly slow) or, if insufficient swap has been set aside, the OS will crash outright. Office apps, whether word processors or drawing apps are not designed for what you are doing.

In the proprietary world, you would use an app like InDesign or Quark Xpress. The FOSS equivalent is [Scribus]("https://www.scribus.net"). These are all powerful and proper desktop publishing/page layout apps. They do not load the entire document, but rather, employ a very useful trick: they load only the text and layout, which are relatively undemanding on RAM. Photos are kept as separate files and loaded only when the page you are actually working on is rendered. When you move to another page, the RAM&#8209;heavy photos are offloaded. When the whole document is eventually done and finalized, you must "export" it. The resulting file will consist of a master file with 120 linked photo files. The whole document is rebuilt at the printer's end with appropriate photos loaded only when the page being printed is rendered. It all happens transparently to you, but uses the resources of the computer sparingly and far more efficiently.

Many desktop publishing professionals scoff at Scribus, but I've found it to be more than ample for my needs. Mind you, I don't build high fashion magazine spreads, so the more exotic features are entirely lost on me. If you need that sort of power, then InDesign, Quark Xpress or some other expensive proprietary solution may be needed. However, if you are now just using Draw, then I suspect that you will find Scribus to be all that you need. It is far more powerful, intuitive, faster and easier to use.
```
sudo apt install scribus
```

---

### Post by dragonfly41 on 2023-07-12
I agree that Scribus is a powerful desktop publishing toolbut not designed for online presentations.
I have used it myself and it can be customised using extensions.

But I am focussed on online presentations design and I use Markdown. Lookup Zettrl.com and how to included images. Also Cloudinary. in a Reveal.js presentation (not LibreDraw).

Create your master file in Zettlr, embed your images, then File Export to Reveal.js presentation.

Here are a few examples taken from Zettlt discussions ..


[LIST]
[*]![Image Caption]([http://www.domain.tld/your-image.jpg](http://www.domain.tld/your-image.jpg))
[*]![Image Caption](C:\Users\user-name\Pictures\your-image.png)
[*]![Image Caption](../img/your-image.gif)
[/LIST]

My current task is to animate these resources.

You can pull in images from Cloudinary account you start.

---

### Post by Holger_Gehrke on 2023-07-12
You might want to think about scaling the images to the print resolution before you insert them in Draw. If an image is going to be printed 2 inches wide at 600 ppi then it shouldn't be more than 1200 px wide, otherwise you're just having your machine repeatedly rescaling hundreds of megabytes of image data for no reason. Don't forget: each pixel is three bytes at least (more if you're using transparency (alpha channel) or more than 8 bits per channel). So a photo at a relatively low resolution of 3000x2000 px which can be less than a megabyte when stored as a jpeg is 18 megabyte uncompressed when working on it in memory. Shovelling all that stuff around takes time. The less data has to be moved around, the faster it's going to be.

Holger

---

### Post by ian-weisser on 2023-07-12
> **Holger_Gehrke said:**
> You might want to think about scaling the images to the print resolution before you insert them in Draw.

+1 This is a primary was to improve performance.

I helped a person write a 150-page book in LibreOffice a couple years ago. It's a owner's manual for violins, and it has about a hundred photos of various sizes distributed through it. After the first 10 huge photos, the system (not too different from the OP) bogged down and threatened to crash. After proper resizing, the whole book -- all hundred photos, labels, formatting, etc. remained fast and responsive.

---

### Post by DuckHook on 2023-07-12
I agree that where photo integrity is unimportant, scaling is an effective way to keep RAM and CPU hogging under control.

My experiences were many moons ago, so maybe things have changed, but back in the day, it was usually not a good idea to rescale images. Especially when it comes to glossy high&#8209;end printing, image rescaling will introduce noticeable artifacts like banding and moirés that detract from the finished product. Jpegs are especially notorious for this and professional desktop publishers avoid them. Back in my day, they insisted on high resolution TIFFs, which I always found frustratingly bloated and resource hogging, but necessary.

If the OP is just producing a friendly neighbourhood B&W programme, then rescaled images might suffice, though care must be taken to avoid the worst artifacts. But if it is destined to be a glossy, magazine quality offering, then rescaled images will likely detract from the finished product.

I dunno. Maybe I'm prejudiced by my past training, but I feel that it's safer and easier to use the tools that are actually built for the job than to use a tool that isn't really designed for it. Word processors are designed to manipulate words, not produce beautiful programmes and magazine spreads. Likewise, drawing apps are designed to produce simple drawings, not professional programmes and brochures. It is possible to work around their flat file limitations, but such workarounds are unnecessary and can be avoided. Moreover, office suite apps offer very primitive control over characteristics that are important in presentation print, like kerning, tracking and font manipulation.

Not trying to be argumentative. But as often happens on these forums, advising on the best course of action depends on data that we do not have.

---

