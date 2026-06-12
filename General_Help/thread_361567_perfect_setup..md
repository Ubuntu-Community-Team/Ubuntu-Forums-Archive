---
title: "perfect setup."
date: 2007-02-14
forum: General Help
---

### Post by mar225 on 2007-02-14
Two questions. 

1. I have what is the perfect setup with edgy and it works very well. How do I shut off the updates and stop any future intrusion from the outside world. 

2.  Has anyone seen or know how to make an ISO disk of an install. Kind of like the download CD for ubuntu so if the system crashes it is just a matter of reloading from the disk. One or two steps beyond and better than a backup.  

Thanks.

---

### Post by FluffyElmo on 2007-02-14
Launch a terminal window and run ***sudo cp /etc/apt/sources.list /etc/apt/sources.list.org*** to back-up your current configuration. Then run ***sudo gedit /etc/apt/sources.list*** from a terminal window. This lists the repositories that you are getting software from. Put a hash symbol '**#**' in front of any line you don't want to update from and save. I'd leave the security ones alone, the comments should give you a good idea what each repository is for. 

After saving run ***sudo apt-get update*** to make sure there are no errors.

As I said, I'd leave the security related updates active in case of future exploits. In fact that's the main reason to do it this way...update will still run but it will only pick up updates from the repositories you choose. You can also remove/enable repositories via Synaptic if you're not comfortable with the command line.

---

### Post by mcduck on 2007-02-14
System/Administration/Software Sources and the 'Internet Updates'-tab ;)

But if your computer is connected to the Internet I'd seriously recommend having at least security updates on.

---

### Post by Richard Kut on 2007-02-14
Hello! If I understand correctly, you have found that magical balance of software and settings that you want to freeze, kind of like rolling your own Linux distribution. If that is the case, then you may want to look here:

[http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37](http://reconstructor.aperantis.com/index.php?option=com_content&task=view&id=14&Itemid=37)

I hope that this helps. Good luck!

---

### Post by mar225 on 2007-02-14
Thanks people.  

You have given me just what I was looking for.

---

### Post by FluffyElmo on 2007-02-14
Sorry missed #2...I'm not sure how involved you want to get but you can create a custom LiveCD, or a LiveDVD for more space that is what be what you're looking for.
[https://help.ubuntu.com/community/LiveCDCustomization]("https://help.ubuntu.com/community/LiveCDCustomization")

Alternately you could just create a back-up image of your disk using Partimage and burn it to disk(s). [http://www.partimage.org/]("http://www.partimage.org/")

I think the drive image is what you want here unless you also wanted to be able to run directly from disk on other machines...

---

