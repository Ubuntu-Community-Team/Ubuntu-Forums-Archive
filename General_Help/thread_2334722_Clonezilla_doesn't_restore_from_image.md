---
title: "Clonezilla doesn't restore from image"
date: 2016-08-22
forum: General Help
---

### Post by Grigoriy on 2016-08-22
Hello!
                          
                          I have Ubuntu 14.04 with recently installed kernel 4.4 
                          A few month ago I did a backup image with  Clonezilla. I have a dual-boot system (Linux/W10). My laptop is  connected to USB HD. Ubuntu is on the external USB3 drive. Windows is  inside the laptop and on another partition inside the laptop, which is  formatted into ext4 there's a Clonezilla image (well, it's the directory  and the image is inside of it). So I want to use the image that resides  on the internal HD to recreated the whole disk that is external. What  happens after I boot into Clonezilla is that I get to the destination  screen and then I must choose the source. No restore option, just a  saving option and in the end I see my Ubuntu USB3 HD (as a source). I  don't how to explain to Clonezilla that I want to restore from image.  Unfortunately, there's no way to bluntly choose that option from the  start. Clonezilla itself gives you the options it considers correct.

---

### Post by sudodus on 2016-08-22
When you have gone through several steps in Clonezilla wizard (beginner mode), and you have selected partition and directory of the image you want to restore, there is a screen, where you can select the following modes

```
savedisk
saveparts
[B]restoredisk
restoreparts[/B]
1-2-mdisks
recovery-iso-zip
chk-img-restorable
exit
```

I think it will appear only if you select a directory which contains one or more Clonezilla image(s). Do not select an image directory itself, but a directory, which contains the image, that you want to restore.

For example, I have a backup drive with two partitions. In each partition there are several directories, one for each computer, that I back up. In the second partition there is the directory Mars-2013, and in that directory there are two images,

```
Mars-2013/2016-07-9-18_win10-n-old-ubuntu
Mars-2013/2016-07-9-23_win10-n-new-ubuntu
```

These images are directories containing a number of files, some small control files and a number of 2GB compressed files.

So to be clear, I select the second partition of that drive, and after that I ***select the directory [COLOR="#0000CD"]Mars-2013[/COLOR], which contains the image I want to restore***, and the restore options will be available.

---

### Post by Grigoriy on 2016-08-22
Maybe I had to choose the DIRECTORY where Clonezilla image files are in?
              I just chose a ext4 partition where they are. And then I  think I chose top directory. Maybe I had to specify the Clonezilla  directory in which there are all its files? So I would see restoration  options on the next Clonezilla screen. Please explain that to me. Like  first I choose the partition in which I have a backup files, then on the  next screen I see a few options to choose a DIRECTORY. Default option  is "Top directory" and in my particular case, I have a partition and in  it I have a folder and in that folder I have a bunch of Clonezilla  backup files.

---

### Post by Grigoriy on 2016-08-22
Ok, maybe I'll try again and see what happens.

---

### Post by howefield on 2016-08-22
If I am understanding what you are asking correctly, one first selects the device (disk/partition) that the image(s) are on, ie, the source disk, and then on the next screen one selects the folder that contains the Clonezilla images. If they are not in a folder, ie top level of the partition/disk you should select that option.

---

### Post by sudodus on 2016-08-22
Yes, try until it works for you. There are only a few feasible alternatives, at least if you try to follow my tips in post #2.

(If the Clonezilla images (directories) are directly in the top directory, you should stay there. Do not select an image directory directly at that first step, where you mount it. At least that is how it works in the versions of Clonezilla, that I have used and use now.)

---

### Post by Grigoriy on 2016-08-22
It was a wrong assumption. Clonezilla doesn't show its own directory (actually, it says that its own folder is **excluded**).  But... and it's a small miracle, this time I got a restoration option  and I did the restoration process till its successful end. I chose the  default "Top directory" option after choosing the partition on which the  Clonezilla backup directory was. 
              The only difference that this time was from when it did no  work was that this time I was restoring a backup of Ubuntu with a new  kernel (4.4.) and before that with the old one (3.16)

---

### Post by sudodus on 2016-08-22
Congratulations and thanks for sharing your solution :KS

If you need more help and have time to explore more details, you are welcome. Otherwise, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

