---
title: "Where are the packages on source media?"
date: 2017-08-20
forum: General Help
---

### Post by daryl9 on 2017-08-20
I can't locate packages on source media?  I would think that they would be under ./dists/<distribution>/main/binary....   Other distribution that I work with, Red Hat, SuSE etc.. all have packages on the installation media that I can browse and install.  Where is it located on the Ubuntu installation media?

Thanks

Daryl

---

### Post by deadflowr on 2017-08-21
Try pool
typically pool > main > alphabetical listed directory > archived deb packages > profit

---

### Post by daryl9 on 2017-08-21
> **deadflowr said:**
> Try pool
typically pool > main > alphabetical listed directory > archived deb packages > profit

Is that all of the packages? 

I'm used to other distributions that have a single directory with all of the installation packages that I can browse through and install if I need something. Ubuntu seems more reliant on internet access for installation and updates, is that correct?  

Daryl

---

### Post by oldos2er on 2017-08-21
/var/cache/apt/archives

---

### Post by daryl9 on 2017-08-21
> **oldos2er said:**
> /var/cache/apt/archives

I mean on the DVD itself.

---

### Post by oldos2er on 2017-08-21
So it is, sorry for the misunderstanding.

After a bit of digging, I found this command: ```
isoinfo -f -i ubuntu-17.04-desktop-amd64.iso
``` Hope that helps.

---

### Post by vocx on 2017-08-21
> **daryl9 said:**
> Is that all of the packages? 

I'm used to other distributions that have a single directory with all of the installation packages that I can browse through and install if I need something. Ubuntu seems more reliant on internet access for installation and updates, is that correct?  

Daryl
There is no point in archiving, say, 20 GB of packages in the installation media. Many packages are constantly updated so you immediately end up with old packages that you will upgrade once you have Internet access anyway.

When the Ubuntu project started back in 2004-2005 it also had the philosophy of having a good set of programs that would fit nicely in the space provided by a CD, which is 650 MB. So, in this way you could go to a remote place, without Internet access and still have a running system. Currently the regular Ubuntu installation image is around 1 GB, so it is above the 650 MB limit, but still doesn't include every single package of the repository.

I remember back in those years, with some distributions like Suse, Debian and Mandriva, the installation media was two entire DVDs, meaning around 9 GB of packages. Of course, as soon as you installed your system, you immediately had like 2000 updates. In my opinion, Ubuntu's approach is nice. They don't pack everything in the CD or DVD or USB image. They give you a good set of programs, and if you want to install more, you do it online.

---

### Post by daryl9 on 2017-08-21
> **vocx said:**
> There is no point in archiving, say, 20 GB of packages in the installation media. Many packages are constantly updated so you immediately end up with old packages that you will upgrade once you have Internet access anyway.

When the Ubuntu project started back in 2004-2005 it also had the philosophy of having a good set of programs that would fit nicely in the space provided by a CD, which is 650 MB. So, in this way you could go to a remote place, without Internet access and still have a running system. Currently the regular Ubuntu installation image is around 1 GB, so it is above the 650 MB limit, but still doesn't include every single package of the repository.

I remember back in those years, with some distributions like Suse, Debian and Mandriva, the installation media was two entire DVDs, meaning around 9 GB of packages. Of course, as soon as you installed your system, you immediately had like 2000 updates. In my opinion, Ubuntu's approach is nice. They don't pack everything in the CD or DVD or USB image. They give you a good set of programs, and if you want to install more, you do it online.

Voxc,

The issue is that I don't have Internet access.  I'm trying to install print drivers which are missing dependencies.  I was confident that I could install the drivers if I could access the packages on the installation media, but now I'm beginning to think that isn't the case.  Fortunately, I can take the equipment to a location that does have Internet access, but that won't always be the case.  I need to be able to find a way to resolve dependencies without the need for internet.

Thanks

Daryl

---

### Post by daryl9 on 2017-08-21
> **oldos2er said:**
> So it is, sorry for the misunderstanding.

After a bit of digging, I found this command: ```
isoinfo -f -i ubuntu-17.04-desktop-amd64.iso
``` Hope that helps.

That's a good command.  I'll have to keep that in mind.  Didn't exactly resolve my issue, but I can peruse the image.  

Thank you.

Daryl

---

### Post by again? on 2017-08-22
At [http://cdimage.ubuntu.com](http://cdimage.ubuntu.com) you can find manifest files which list all the packages in each ISO version,
which may help in your endeavours.
eg [edubuntu-14.04.3-dvd-amd64.manifest]("http://cdimage.ubuntu.com/edubuntu/releases/14.04.3/release/edubuntu-14.04.3-dvd-amd64.manifest") <---direct download link

---

