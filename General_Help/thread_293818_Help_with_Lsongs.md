---
title: "Help with Lsongs"
date: 2006-11-05
forum: General Help
---

### Post by turkenator on 2006-11-05
Okay firstly i would like to thanks everyone that took the time to read and respond to my original question.
The problem has been solved thanks to maxpower for those that would like to install Lsongs maxpower has compiled
some .deb files that are required to install lsongs 

[http://www.sporadicspeculations.com/...untu1_i386.deb](http://www.sporadicspeculations.com/...untu1_i386.deb)
[http://www.sporadicspeculations.com/...re0.6_i386.deb](http://www.sporadicspeculations.com/...re0.6_i386.deb)
[http://www.sporadicspeculations.com/...untu1_i386.deb](http://www.sporadicspeculations.com/...untu1_i386.deb)
[http://www.sporadicspeculations.com/...re0.2_i386.deb](http://www.sporadicspeculations.com/...re0.2_i386.deb)

screen shot
[http://www.ubuntuforums.org/attachment.php?attachmentid=18982&d=1162833857]("http://www.ubuntuforums.org/attachment.php?attachmentid=18982&d=1162833857")

Can one of the admins please move this to the How-tos/Guides section so others can benefit from this thread as well thanks

---

### Post by aysiu on 2006-11-05
I've been around these forums a lot--seen a lot of threads.

Not once have I ever seen someone claim to have successfully installed LSongs in Ubuntu.

---

### Post by turkenator on 2006-11-05
damn i read those forums aswell circa 2005 so i thought maybe people made some progress 
well then can u tell me something else on edgy i cant "configure my collection" on amaroK because hidden folders arent displayed only /home & /media is displayed where as my music is in /mnt/hdd1/ how can i add this to my collection any ideas?

---

### Post by aysiu on 2006-11-05
/mnt/hdd1 shouldn't be a hidden folder. Something's weird.

What do you mean by "hidden"?

---

### Post by turkenator on 2006-11-06
hard to explain so i just posted a screen shot this is what i mean thanks aysiu

---

### Post by aysiu on 2006-11-06
Something's wrong. That's not what it's supposed to look like.

---

### Post by turkenator on 2006-11-06
yeah this wasnt the case in dapper but for somereason all of the folders in / are hidden except /home /media could this be something to do with priviledges ?

---

### Post by maxpower on 2006-11-06
I saw this thread this morning and figured I'd give it a go.  It took a lot of work but I did get Lsongs working. I had to change some references to python2.3 and use gcc-3.4 to compile pyxine.  If anyone is interested, i can post the steps I followed and maybe someone could build a package from that as packaging python stuff is a little different.

mAx

---

### Post by turkenator on 2006-11-06
omg YOU ARE A LEGEND 
please post the steps that would be great thanks so much :) 
U LEGEND

---

### Post by maxpower on 2006-11-06
Well, actually I think I got the debs working so here they are:

[http://www.sporadicspeculations.com/files/lsongs_0.2.46-0.0.0.50.linspire0.1_i386.deb](http://www.sporadicspeculations.com/files/lsongs_0.2.46-0.0.0.50.linspire0.1_i386.deb)
[http://www.sporadicspeculations.com/files/python-ipod_A0A7-0ubuntu1_i386.deb](http://www.sporadicspeculations.com/files/python-ipod_A0A7-0ubuntu1_i386.deb)
[http://www.sporadicspeculations.com/files/python-pynjb_0.1.0-0.0.0.50.linspire0.6_i386.deb](http://www.sporadicspeculations.com/files/python-pynjb_0.1.0-0.0.0.50.linspire0.6_i386.deb)
[http://www.sporadicspeculations.com/files/python-pyxine_0.1alpha2-1.0.0.50.linspire0.2_i386.deb](http://www.sporadicspeculations.com/files/python-pyxine_0.1alpha2-1.0.0.50.linspire0.2_i386.deb)


If you get ANY error please let me know I will update the debs.  I will work on removing the linspire stuff but I am kinda new at this.  I did a bit a messing around to get this working so I may not have included all of the dependencies in the debs.

mAx

---

### Post by turkenator on 2006-11-06
thanks im gonna try it right now ill let u know how it goes thanks heaps

---

### Post by maxpower on 2006-11-06
Cool, I just updated the debs to have ubuntu names. Anyone know the proper format (ie in 0ubuntu1 what are the 0 and 1 for? I think 1 is the release)?

[http://www.sporadicspeculations.com/files/lsongs_0.2.46-0.0.0.50-0ubuntu1_i386.deb](http://www.sporadicspeculations.com/files/lsongs_0.2.46-0.0.0.50-0ubuntu1_i386.deb)
[http://www.sporadicspeculations.com/files/python-pynjb_0.1.0-0.0.0.50.linspire0.6_i386.deb](http://www.sporadicspeculations.com/files/python-pynjb_0.1.0-0.0.0.50.linspire0.6_i386.deb)
[http://www.sporadicspeculations.com/files/python-pyxine_0.1alpha2-1-0ubuntu1_i386.deb](http://www.sporadicspeculations.com/files/python-pyxine_0.1alpha2-1-0ubuntu1_i386.deb)
[http://www.sporadicspeculations.com/files/python-pyxine_0.1alpha2-1.0.0.50.linspire0.2_i386.deb](http://www.sporadicspeculations.com/files/python-pyxine_0.1alpha2-1.0.0.50.linspire0.2_i386.deb)

---

### Post by turkenator on 2006-11-06
Omg Max Thanks So Much It Worked And For Those That Are Curious Heres A Screen Shot For Them Thanks

---

### Post by turkenator on 2006-11-06
hey btw the problems with folders in / not displaying in programs can be easily solved by
```
 sudo rm /.hidden

```
thats it

---

### Post by fog on 2006-11-06
> Error: Dependency is not satisfiable: python-ipod
python-ipod??? Any ideas?

I found this [http://code.connectical.net/](http://code.connectical.net/) but I don't what I'm doing next...
Lsongs working but I use --force for installation.
Any ideas?

[[IMG]http://img512.imageshack.us/img512/4530/screenshotmp8.th.jpg[/IMG]](http://img512.imageshack.us/my.php?image=screenshotmp8.jpg)

---

### Post by turkenator on 2006-11-06
umm it gave me the same error problem but its ok thats only for ur ipod to work ithink

---

### Post by maxpower on 2006-11-06
Do you download and install python-ipod from my previous message?  If you did, lsongs should install cleanly.  However, I would also presume that it is only need of you plan to use lsongs with an iPod.

mAx

---

### Post by fog on 2006-11-06
> **maxpower said:**
> Do you download and install python-ipod from my previous message?  If you did, lsongs should install cleanly.  However, I would also presume that it is only need of you plan to use lsongs with an iPod.

mAx

Now it's ok. I use you deb :oops: 
Thank you very much.

---

### Post by darthchaosofrspw on 2006-12-22
> **turkenator said:**
> Okay firstly i would like to thanks everyone that took the time to read and respond to my original question.
The problem has been solved thanks to maxpower for those that would like to install Lsongs maxpower has compiled
some .deb files that are required to install lsongs 

[http://www.sporadicspeculations.com/...untu1_i386.deb](http://www.sporadicspeculations.com/...untu1_i386.deb)
[http://www.sporadicspeculations.com/...re0.6_i386.deb](http://www.sporadicspeculations.com/...re0.6_i386.deb)
[http://www.sporadicspeculations.com/...untu1_i386.deb](http://www.sporadicspeculations.com/...untu1_i386.deb)
[http://www.sporadicspeculations.com/...re0.2_i386.deb](http://www.sporadicspeculations.com/...re0.2_i386.deb)

screen shot
[http://www.ubuntuforums.org/attachment.php?attachmentid=18982&d=1162833857]("http://www.ubuntuforums.org/attachment.php?attachmentid=18982&d=1162833857")

Can one of the admins please move this to the How-tos/Guides section so others can benefit from this thread as well thanks

It's working on here! (Ubuntu Edgy) These files need to be added to one of the Ubuntu repositories. Listening to the Alex Jones Show on GCN on Lsongs as I type this.

---

### Post by alessio_aguirre on 2007-06-17
I could not get to all the links shown below, they seem to be dead. Can someone please tell me a new location for them? 

Thanks

[http://www.sporadicspeculations.com/...untu1_i386.deb](http://www.sporadicspeculations.com/...untu1_i386.deb)
[http://www.sporadicspeculations.com/...re0.6_i386.deb](http://www.sporadicspeculations.com/...re0.6_i386.deb)
[http://www.sporadicspeculations.com/...untu1_i386.deb](http://www.sporadicspeculations.com/...untu1_i386.deb)
[http://www.sporadicspeculations.com/...re0.2_i386.deb](http://www.sporadicspeculations.com/...re0.2_i386.deb)

---

### Post by maxpower on 2007-07-24
Those links got truncated when you copied them. Us the links in my #12 post above.

mAx

---

### Post by Moamen on 2007-08-17
it can be done with apt without the need for any debs 
[http://jacksparrow.blogsome.com/2007/08/17/how-to-install-lsongs-on-ubuntu-feisty-704-2/](http://jacksparrow.blogsome.com/2007/08/17/how-to-install-lsongs-on-ubuntu-feisty-704-2/)

---

