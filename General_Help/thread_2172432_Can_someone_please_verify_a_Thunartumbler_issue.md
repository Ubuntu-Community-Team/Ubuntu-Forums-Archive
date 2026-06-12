---
title: "Can someone please verify a Thunar/tumbler issue?"
date: 2013-09-04
forum: General Help
---

### Post by vasa1 on 2013-09-04
Can someone who has **Thunar** and **tumbler** installed, please download [the pdf file]("http://www.ratp.fr/informer/pdf/orienter/f_plan.php?nompdf=metro_geo&loc=secteur&fm=pdf") discussed in [Why do large PDFs take so long to load in Linux PDF viewers...]("http://ubuntuforums.org/showthread.php?t=2172099&p=12777657#post12777657") ?

Once the file is downloaded, use Thunar to open the folder containing the downloaded file. Do you see high and prolonged increased CPU usage attributed to **tumblerd**?

I've been using Thunar for quite a while and didn't have any such problem before. I'm wondering if the downloaded pdf file is to "blame". Could it be because it's mainly [a scalable graphic image]("http://ubuntuforums.org/showthread.php?t=2172099&p=12777883#post12777883")? I doubt it's just the size of the file. I have quite a few much larger Full Circle pdf files as well. Tumbler didn't have problems with those or with the images in them.

I'll be looking at this a bit later, but for now, I ran [font=courier new]sudo apt-get purge tumbler[/font].

---

### Post by ajgreeny on 2013-09-05
tumblerd seems to have a few problems when using thunar on my system as well.   

 If I attach a USB flash drive with images on it rhubarb opens as expected.  If I then copy images from the USB or view any of them, I am unable to eject the flash drive before removal as tumblers id still active on it; I have to use a keyboard shortcut I have made for killall tumblerdbetore I am able to use eject.

---

### Post by vasa1 on 2013-09-05
> **ajgreeny said:**
> ...
 If I attach a USB flash drive with images on it ....
What do you have for Thunar's Edit > Preferences > Show Thumbnails ? I've kept it as "Local Files Only". Would that help your situation?

---

### Post by ajgreeny on 2013-09-05
Not sure about that; I will check when I am at that computer later.

---

### Post by vasa1 on 2013-09-05
I reinstalled tumbler and edited ~/.config/tumbler/tumbler.rc. Seems fine now.

---

