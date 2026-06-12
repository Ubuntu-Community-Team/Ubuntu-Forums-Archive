---
title: "Stumped by k9copy: no MP4 transcoding!"
date: 2008-01-01
forum: General Help
---

### Post by sarc on 2008-01-01
I want to copy DVDs into MP4 at 320x240 resolution.  I tried k9copy and it has an option for DVD transcoding into MP4 on its menu, however when I click on the MP4 icon it only gives me an option to backup to AVI.  The AVI works fine but will not play in my mobile phone.  I have spent quite some time to try to find documentation on k9copy and on this forum (including this thread [http://ubuntuforums.org/showthread.php?t=605554&highlight=k9copy+MP4);](http://ubuntuforums.org/showthread.php?t=605554&highlight=k9copy+MP4);) I tried to save as ISO and then remount it... same story... can someone help?  (I found DVD:Rip to be hard to use and anyways it gives me warnings that it cannot find mplayer although I have Totem Movie Player installed... [Totem cannot play DVDs although I followed the 'How to enable Multimedia in Feisty' instructions.

I am also stumped by the k9copy settings - it's asking for Devices and MEncoder with label, Video, Audio... what;s that?  Can it solve my problem?  Sorry but a I cannot find documentation on Google search on k9copy documentation or Sourceforge 

HELP PLEASE!

---

### Post by Hallvor on 2008-01-01
You haven`t by any chance VLC media player installed, have you?

[http://www.linux.com/articles/53757](http://www.linux.com/articles/53757)
[http://www.videolan.org/doc/videolan-howto/en/](http://www.videolan.org/doc/videolan-howto/en/)

---

### Post by sarc on 2008-01-01
Yes I do!!  Is that bad?  (Installed from repos)

---

### Post by Hallvor on 2008-01-01
Absolutely not. :) It is a great transcoding tool. Just read the first link in my previous post.

---

### Post by sarc on 2008-01-01
By the way update:  I noticed the Sourceforeg.net version is newer, so I downloaded it.  I follwoed the install instructions and ran ./configure from terminal.  It gave me this error message:

checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!

Then if I type make as per install instruction the package won't compile (I guess due to necessary script not created due to above problem)...

---

### Post by sarc on 2008-01-01
WOW Hallvor it works!  I transcoded to MP4 in 5 minutes... EXCEPT loading in the phone I found out the beast wants 3gp video format.  It said 'wrong format' to the MP4 encoded file (it played back fine on VLC).  Wikipedia says that 3gp is MP4 on .H263... what VLC streaming settings can I use to make it play on the stupid phone?  Thanks!

---

### Post by Hallvor on 2008-01-01
Am not sure. Have you tried selecting the .H263 codec?

---

### Post by sarc on 2008-01-07
First of all note that I was wrong and the stupid phone wanted 3GP, not MP4 files.

Then I found this app that worked really well, first time out, right out of the box.  Converted mpg to 3GP.  It's a binary so I would not put it in the enterprise server...

[http://www.miksoft.net/products/mmc-lin.tar.gz](http://www.miksoft.net/products/mmc-lin.tar.gz)

---

