---
title: "Installing packages on different drives"
date: 2005-08-22
forum: General Help
---

### Post by Zotova on 2005-08-22
I originally setup ubuntu on a 3 gb partition on my hard drive to test it (I never expected to be using it full time). Now however I have very little space left on this partition but have plenty of space on another mounted fat32 partition. However in synaptics I can find no way to specify where the packages are installed. Thus at the moment I am unable to install new software as I do not have the required space. Is there anyway to choose another install location?

Thank you.

---

### Post by nad on 2005-08-23
You may be able to free up considerable room if your package cache is large. In a terminal window, type the command: sudo apt-get autoclean. There may be a way to do this in synaptic. I don't know.

If this does not free up enough space, you may wish to make your fat32 partition smaller and create an ext3 partition to move your /home and/or /var directories to. I suppose that you could move these directories to your fat32 partition, but, I would not recommend it.

If it will be necessary to move some directories, please post back for instructions as it can be a little tricky and there is some housekeeping that needs to be done.

---

### Post by Zotova on 2005-08-23
Thanks for the reply.

I have sypnaptics set to delete all downloaded packages after they are installed and I have tried the command line and I still have just 55MB left on the ubuntu partition.

Is there a way to install elsewhere though without having to move everything? As it seems a bit over complex to move everything when I only really want to install a few more programs.

I suppose what I am looking for is some sort of popup/dialog which asks me where I want to install such and such a program a tad like you get with windows installers.

---

### Post by nad on 2005-08-23
The short answer, "No". How about moving _some_ of the data in your /home directory to your second file system? Will this free up enough space? You may also tune your / file system (tune2fs) to reduce the amount of space reserved for the superuser.

3GB is just a minimum amount for any desktop operating system. You are seeing the constraints of such a choice.

While you can move anything you want to anywhere you can connect to, the complexities of doing so quickly become very technical and can be unreliable in a connection without fault protection. As I intimated in my previous reply, just moving your /home and/or /var directories requires fundamental changes to your operating system configuration.

---

### Post by Zotova on 2005-08-23
My home folder has nothing in it apart from some ndis wrapper files and some real player files. All my personal files are on the seperate fat32 partition.

It seems a bit daft really though as to me this would seem a basic feature, how has this been missed? I mean surely I'm not the only one who would like to install elsewhere now and again - certain programs in a different area for easy access etc.

So by what your saying I can get it to install if I move everything over but I don't fancy that. Looks like I'm going to have to go down the road of resizing the partition then, which again I don't really fancy as everything is working perfectly and knowing my luck it'll all get screwed up somehow.

Finally, is there anyway around this if I compile the program manually? I compiled gaim from source last week as I couldn't be bothered to wait for the new version of gaim (1.5.0) to become available via synaptics. But when I compiled the files seemed to automatically go into the directories they wanted. (I was under the impression the files would appear in the directory from what I had compiled in).

---

### Post by nad on 2005-08-23
In these days of multi-hundred gigabyte hard drives, it is very unusual for someone to expect to install a full fledged desktop environment with all of its bells and whistles and accompanying productivity, multimedia and communications applications into a 3GB partition.

Part of the inherent stability and security of a GNU/Linux system is the fact that executable binaries and libraries are not scattered about the file system.

---

