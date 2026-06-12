---
title: "why are GIMP saves are too big"
date: 2016-06-19
forum: General Help
---

### Post by argonvegell on 2016-06-19
My hobby is photo manipulations, and I use GIMP, but one thing that always bothered me was that GIMP saves are big, but I managed to workaround it using IrfanView to re-save the image, for example, when I created a 1920x1080 jpg in GIMP, the size of the saved jpg is about 2MB, but when I re-saved it using IrfanView, the image's size was cut down to 350KB, and I compared the quality of the two jpgs, same resolutions, no blurring or pixelation problems, no difference in quality between the two.

Is there anyway to fix this? Because using IrfanView to re-save my work is kind of a hassle.

I'm running Xubuntu 14.04 and I'm running Wine 1.8.2.

---

### Post by coldraven on 2016-06-19
In Gimp when you select "Export As" and choose jpg you can use the slider to select the output quality. 
By default it is high but you could just type in 60% and get a similar result to Irfanview.

---

### Post by kolibri on 2016-06-19
The difference in the jpg compression is the retention or loss of subtle (or, for high compressions, obvious) tonal variations.  If you made a difference image, you'd see the subtle differences.  Multiple consecutive jpg compressions can result in obvious tonal loss.  If you are running GIMP 2.9 you might also be running into differences in bit depth when you save/open the images.

---

### Post by xenon3 on 2016-06-19
you can also type the extension in the export name like "myimage.jpg" than you do not need to chose the format, GIMP recognizes it! And indeed you also get for .jpg format that output quality dialogbox. I'm tired of Microsoft and windows, I used to use the Microsoft Picture Manager for compressing to "web format" then 5 Mb went to 350 Kb or so. But I will use your trick of setting quality to 60%!

---

### Post by argonvegell on 2016-06-20
Thanks, it worked, reducing image quality to 60% reduced the size of my  work, so I no longer need to use IrfanView to re-save my work :)

> **xenon3 said:**
> I'm tired of Microsoft and windows

I'd love to get rid of Microsoft Windows and Wine, but I can't, why, because there are things that Windows can do and Linux doesn't do well, e.g. I ran Windows XP on Virtualbox for scanning multiple photos, unfortunately in Xubuntu, there is no software that can automatically crop photos from the scanning bed and split into separate jpg files, there are manual ways of doing this in Linux, but it's too time consuming, and Linux has lousy TTS speech engine voices, too robotic for my taste, I use SAPI5 voices via Wine, much for natural sounding, especially when reading Wikipedia articles.

---

### Post by vasa1 on 2016-06-20
> **argonvegell said:**
> Thanks, it worked, reducing image quality to 60% reduced the size of my  work, so I no longer need to use IrfanView to re-save my work :)
...
Then you may please mark your thread [SOLVED]: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) Thanks!

---

### Post by mastablasta on 2016-06-20
> **argonvegell said:**
> Thanks, it worked, reducing image quality to 60% reduced the size of my  work, so I no longer need to use IrfanView to re-save my work :)


.

it might be better to reduce the size (resolution) of image (if you need it for web) rather than reduce the quality. also explore the option of .png file format.

---

