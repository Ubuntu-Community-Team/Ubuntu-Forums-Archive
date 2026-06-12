---
title: "Acronis True Image Echo Server for Linux"
date: 2008-02-14
forum: General Help
---

### Post by spliner on 2008-02-14
I was wondering if anyone had tried installing this software, and how they did it.  Acronis gives me a .i686 file on the trial download, yet the basic linux instructions on their website do not work.  They say to use chmod +x on the file, then execute it.  The file does nothing.  I assume something else has to be done with it before it will install on Ubuntu.  It would be nice if they offered instructions, but they don't (unless you request them).

I need to image my hard drive, and attempt restoring it to a VM on a different PC.  I'd buy their software if it works, but so far I can't even install it.  Sorry, I am a newb with Linux.

-Spliner

---

### Post by drakouc on 2008-03-13
Spliner,
   I was combing though Google for this same subject and came across this PDF... it doesn't help 100% but it does give some good information.

[http://us1.download.acronis.com/pdf/trueimageserverEcho_linux_ug.en.pdf]("http://us1.download.acronis.com/pdf/trueimageserverEcho_linux_ug.en.pdf")

One thing i noticed, it says you have "assign the setup file the attribute Executable", how you do this... you got me, but at least thats another step in the right direction...

Another thing i noticed was that the version of Ubuntu Echo is compatible with is 4.10 not 7.10.

Thats' all I've found so far so please let me know if you get any closer (BTW we are a partner with Acronis and their tech support wont even respond to my emails on how to install this.)

---

### Post by Kerry_W on 2008-03-13
try opening the terminal and then "sudo ./setup.i686" (assuming the file you downloaded is called setup.i686, if not, substitute with the actual name.)

---

### Post by drakouc on 2008-03-15
Spliner,
   I finally found the codes we need to install this!

sudo chmod +x theFullFileNameHere
sudo ./theFullFileNameHere

then you can continue the wizard installation

---

### Post by spliner on 2008-03-18
I'll give it a shot.. thanks for all who gave this a try.  I have been talking with Acronis about a fully functional trial version, which they have offered for 15 days.  The funny thing is that while I waited for their response, I learned much more about using tar to back up the system.  I havn't tried a restore yet, but getting ready to try a restore with tar today.  If I can get the restoral process down and the grub installation down, I won't need their expensive software at all.

Acronis seems like a "fire and forget" solution, but it's rather expensive (as is all server backup software).  I'm tempted now to save the money and just use tar.

-Spliner

---

