---
title: "Viewing Dicom Files in Linux"
date: 2014-06-30
forum: General Help
---

### Post by pancho5 on 2014-06-30
Hello!

I am trying to find a Free, easy to use software app to view Dicom files.  The x-ray technician gave me the MRI files in a CD, but they were generated in Windows using PC AutoPlay DICOM Viewer.  I have tried to use MRIcon software and followed the Installation procedures for Linux 32bit GTK2 widgeset (what ever that means....), but have been unable to read anything.

My laptop is running LXLE.  Also, I tried opening the files in the CD and of course, they will not open.

What am I doing wrong, or, provide some other alternative(s).  It may be a '**** pit' error on my part, something easy to figure out, but I am unable to figure it out.

Please advise.

---

### Post by yancek on 2014-06-30
A quick google search turned up this link.  You should be able to find it in the software center by just typing "aeskulap" in the Search box.  Have no idea how well it works.

[https://apps.ubuntu.com/cat/applications/natty/aeskulap/](https://apps.ubuntu.com/cat/applications/natty/aeskulap/)

---

### Post by pancho5 on 2014-06-30
> **yancek said:**
> A quick google search turned up this link.  You should be able to find it in the software center by just typing "aeskulap" in the Search box.  Have no idea how well it works.

[https://apps.ubuntu.com/cat/applications/natty/aeskulap/](https://apps.ubuntu.com/cat/applications/natty/aeskulap/)

Tried the above, but it asks to Open the file with a program but I don't know what to choose.

---

### Post by sandyd on 2014-06-30
> **pancho5 said:**
> Tried the above, but it asks to Open the file with a program but I don't know what to choose.

If you go to the software center on your computer (not the browser), you should be able to install it from there.

---

### Post by yancek on 2014-06-30
> Tried the above, but it asks to Open the file with a program but I don't know what to choose. 		

I don't think you "tried the above".  You move your mouse over the icons in the left panel to find the Software Center and click on it.  When it opens, you will see in the upper right a Search box.  Type:  aeskulap in and you should see the same window shown on the link I posted.  In the Software Center window, you then click on Aeskulap Viewer and you will see a tab on the right to Install.  You might also try:  sudo apt-get install aeskulap

---

### Post by pancho5 on 2014-07-10
> **yancek said:**
> I don't think you "tried the above".  You move your mouse over the icons in the left panel to find the Software Center and click on it.  When it opens, you will see in the upper right a Search box.  Type:  aeskulap in and you should see the same window shown on the link I posted.  In the Software Center window, you then click on Aeskulap Viewer and you will see a tab on the right to Install.  You might also try:  sudo apt-get install aeskulap
Tried the above, and I made some progress.  Still accustomed to Windows XP as far as installing software...haven't learned all the bells and whistles of Linux yet.

Though I am able to select files to try and open them, I still must have some other problem that won't let me view them...must be some other problem.  I will keep playing with it, but thanks for your help!

---

### Post by timjohn7 on 2014-10-20
I had the same problem using aeskulap.
The solution is to select "Any Files" from the Open File dialogue (it's in the bottom right corner).
The files that can be opened will be displayed and if you click on the opened image, you will see a Play button to run the video.

---

