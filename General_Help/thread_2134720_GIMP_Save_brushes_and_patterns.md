---
title: "GIMP: Save brushes and patterns"
date: 2013-04-12
forum: General Help
---

### Post by JackalopeSunDance on 2013-04-12
From what I've already read, I aparently need to get root access so I can get into a programs folders and files and move things/delete/whatever. But I have absolutely no idea how to do this (I'm not actually new to Ubuntu, just never needed to do this before) and am worried I'll mess things up.

So I use GIMP for creating images, and I have plenty of brushes and patterns I'd like to use, but I need to get into the files, and as of right now, I can't. =( I would be very greateful if I could get some help on this.

---

### Post by BlinkinCat on 2013-04-12
> **JackalopeSunDance said:**
> From what I've already read, I aparently need to get root access so I can get into a programs folders and files and move things/delete/whatever. But I have absolutely no idea how to do this (I'm not actually new to Ubuntu, just never needed to do this before) and am worried I'll mess things up.

So I use GIMP for creating images, and I have plenty of brushes and patterns I'd like to use, but I need to get into the files, and as of right now, I can't. =( I would be very greateful if I could get some help on this.

Hi,

I assume you have read all there is to read in this -

[https://help.ubuntu.com/community/TheGIMP](https://help.ubuntu.com/community/TheGIMP)

Cheers - :)

---

### Post by kurja on 2013-04-12
Open terminal and run **gksudo nautilus**, you will be prompted for root password and a nautilus file manager window inside which you will have root privileges will open.

this might be of interest to you [http://askubuntu.com/questions/11760/what-is-the-difference-between-gksudo-nautilus-and-sudo-nautilus](http://askubuntu.com/questions/11760/what-is-the-difference-between-gksudo-nautilus-and-sudo-nautilus)

---

### Post by ronald577 on 2013-04-12
Thanks for providing the link. Both the links are really helpful.

---

### Post by JackalopeSunDance on 2013-04-12
> **kurja said:**
> Open terminal and run **gksudo nautilus**, you will be prompted for root password and a nautilus file manager window inside which you will have root privileges will open.

this might be of interest to you [http://askubuntu.com/questions/11760/what-is-the-difference-between-gksudo-nautilus-and-sudo-nautilus](http://askubuntu.com/questions/11760/what-is-the-difference-between-gksudo-nautilus-and-sudo-nautilus)

Thank you, read it and am left with one more question; how do I close out of root once I'm done with the folders and files? I'm assuming it's a bad idea to just leave it open.

---

### Post by Vaphell on 2013-04-12
instance of file browser invoked with gksudo gets admin rights. Once you close the window, you are back to normal

---

### Post by deadflowr on 2013-04-12
> **JackalopeSunDance said:**
> Thank you, read it and am left with one more question; how do I close out of root once I'm done with the folders and files? I'm assuming it's a bad idea to just leave it open.

Close the file manager and you should be out of root.

My own take on working with files in the system (those which need root) is to copy the files into my home folder and then edit the files as needed. Then when done moving or copying the files into the system folder where they belong.
Files can be copied without root from the system folders to your home folder.
If it's a file I'm not sure how my changes will affect the system, I copy the file within the system folder and change the name to something like file.old, this way if the changes I make bork the system, I can still revert the file to the old one.

---

### Post by JackalopeSunDance on 2013-04-12
> **Vaphell said:**
> instance of file browser invoked with gksudo gets admin rights. Once you close the window, you are back to normal

> **deadflowr said:**
> Close the file manager and you should be out of root.

My own take on working with files in the system (those which need root) is to copy the files into my home folder and then edit the files as needed. Then when done moving or copying the files into the system folder where they belong.
Files can be copied without root from the system folders to your home folder.
If it's a file I'm not sure how my changes will affect the system, I copy the file within the system folder and change the name to something like file.old, this way if the changes I make bork the system, I can still revert the file to the old one.

Thank you very much!

Edit: It all works! Woo I'm very happy. Thanks again!

---

