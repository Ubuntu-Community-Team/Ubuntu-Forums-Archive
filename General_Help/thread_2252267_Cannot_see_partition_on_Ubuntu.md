---
title: "Cannot see partition on Ubuntu"
date: 2014-11-10
forum: General Help
---

### Post by jet-san on 2014-11-10
Hello,

Yesterday I have installed Windows 7 and Ubuntu 14.04 on my PC.
I created additional partition for Win7 as well as for Ubuntu (as on pictures below).

[[IMG]http://s27.postimg.org/kladu9a3z/DSC_0033.jpg[/IMG]]("http://postimg.org/image/kladu9a3z/")

[[IMG]http://s27.postimg.org/y0st5yt7z/DSC_0035.jpg[/IMG]]("http://postimg.org/image/y0st5yt7z/")

However I cannot access the Ubuntu's second partition from Ubuntu - why?
I can see the partition using GParted, but I cannot see it on the left hand menu in opened folders, where I thought it will be same as Windows' partitions.

Thanks,
Damian

---

### Post by yancek on 2014-11-10
You created /home as a separate partition on sda7 so if you click on home under Places on the left of the file manager or navigate to the /home directory you should see the files.

---

### Post by jet-san on 2014-11-10
Wow, you're right, thanks!
[[img]http://s13.postimg.org/enfjl70hf/Home.jpg[/img]](http://postimg.org/image/enfjl70hf/)
However I'm a bit confused now...
How does it work?
All my Ubuntu system files are on the 41GB partition and /home (?) is on the 142GB partition...
Where are files stored now - which partition for example from my desktop, from my documents, etc.
Confusing!!!;]

---

### Post by yancek on 2014-11-10
> All my Ubuntu system files are on the 41GB partition and /home (?) is on the 142GB partition...

Yes.  All of your user files under /home are on the 142GB partition.  If you have multiple users, personal files such as Documents, Downloads directories are under /home/user.  This is not the default, you had to choose this during the installation.  From a standard user perspective there really isn't any difference in the way you access the files, use it the same way you would with a file manager if you had everything on one partition.  The basic advantage of a separate /home partition is that you can upgrade or reinstall a new version and still keep your home partition.  Many just install to one / (root) partition and then create a separate data partition.  Your choice.

---

### Post by jet-san on 2014-11-11
> **yancek said:**
> The basic advantage of a separate /home partition is that you can upgrade or reinstall a new version and still keep your home partition.  Many just install to one / (root) partition and then create a separate data partition.  Your choice.

That's exactly why I created the other partition:)
Should I do it the other way round then?
Have the big partition as "/" and then system one on "/home"?
If I want to reinstall the system with new Ubuntu where should I store my e.g. music, videos, document to do not get them erased?

---

### Post by yancek on 2014-11-11
> If I want to reinstall the system with new Ubuntu where should I store  my e.g. music, videos, document to do not get them erased? 		

On the /home partition.  When you upgrade or reinstall, you are installing the system files and they will go on the / partition.  During the install, make sure you don't format or make any changes to the /home partition.  If you install with just a / partition and leave unallocated space you can easily create a separate partition or partition on which to put your videos, documents and music.  Two different options to get the same result so
s it's your choice.

---

### Post by jet-san on 2014-11-11
Ok, I think I've got most of it. The only thing I don't understand is how can I re-install Ubuntu and not remove Documents, Music and Videos if my second partition is under /home and all my stuff are under Computer => home => damian => HERE. Also, when I re-installed Ubuntu last time it says that my previous version of Ubuntu is going to be removed with all Documents, Music, Videos etc. How does it work then? What is the structure? On Windows it's easy - you see disc C and disc D, there are separate and if you format one of them, the other one remain unchanged. It's totally different on Ubuntu, isn't it? One seems to be kind of extension of another...

---

