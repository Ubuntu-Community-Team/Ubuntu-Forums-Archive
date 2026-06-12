---
title: "xfce4-screenshot png file cannot be opened in windows 7"
date: 2014-10-01
forum: General Help
---

### Post by ineuw on 2014-10-01
PNG files I saved in Xubuntu cannot be opened in Windows 7 Irfanview. What am I doing wrong?

---

### Post by Bucky Ball on 2014-10-01
Does it know what a .png file is? Perhaps save them as .jpg and see if that helps.

(FYI when you take the screen shot with screenshooter and save it, you have the option to make it whatever you want. Change the .png at the end of the new filename to .jpg. Will then save as a jpeg.)

---

### Post by ineuw on 2014-10-01
> **Bucky Ball said:**
> Does it know what a .png file is? Perhaps save them as .jpg and see if that helps.
(FYI when you take the screen shot with screenshooter and save it, you have the option to make it whatever you want. Change the .png at the end of the new filename to .jpg. Will then save as a jpeg.)
Of course both Irfanview and I know all formats. I have prepared and uploaded thousands of images of .png and .jpg for Wikimedia Commons. Just look for my contributions User:Ineuw. Also, the xfce4 save dialog has no options. It saves it only as png. Earlier today, I repeated the screenshots, loaded them into fotoxx and save them in both formats. Then, installed gnome-screenshot and created images and saved it in both formats and copied all to an NTFS drive. None could be opened in Windows. I was able to do it in XU 12.04. I think something must be broken somewhere.

---

### Post by papibe on 2014-10-01
Hi ineuw.

Does it open on Firefox? or IE v9+?

Just a thought.
Regards.

---

### Post by ineuw on 2014-10-01
> **papibe said:**
> Hi ineuw.

Does it open on Firefox? or IE v9+?

Just a thought.
Regards.

Unfortunately, no.

---

### Post by Doug S on 2014-10-01
Could you run pngcheck on the file to determine if it finds anything. There should be versions available for both linux and windows. Could you post the file somewhere for us to try.

---

### Post by ineuw on 2014-10-02
> **Doug S said:**
> Could you run pngcheck on the file to determine if it finds anything. There should be versions available for both linux and windows. Could you post the file somewhere for us to try.

I installed pngcheck and when ran it in the terminal, as "pngcheck *.png" I immediately realized the error. Let this post be a reminder to those who save Linux file names containing Windows restricted characters. One can't even rename them in Windows.

All is well.

Thanks for the help and apologize for the trouble caused by a tired mind.

---

### Post by Bucky Ball on 2014-10-02
All good and good luck. ;)

---

