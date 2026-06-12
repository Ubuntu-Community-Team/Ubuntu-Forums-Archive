---
title: "Ubuntu Linux 5.10"
date: 2006-12-19
forum: General Help
---

### Post by chrispche on 2006-12-19
I obtained a a copy of Ubuntu Linux 5.10 and have both an Install CD and a Live CD. I tried out the Live CD which seemed to run fine. It did almost everything I wanted. However, it did not:

Play DivX avi files or mpeg files.
Play Mp3s.
My 250gig ext hard drive picked up fine under the Live CD, unfortunately it is formated at NTFS and Ubuntu would not let copy files from and to it. It said something about not have access privileges to that drive. Obviously I want full access to the drive.

How do I go about doing this?

Will the newer version do the above. I believe 5.10 is quite an older version.

Also a few questions. Do I have to use Gnome desktop, while I guess it's quite nice. I think I prefer KDE.

Do RPM files install on Ubuntu?

I am pretty familiar with Mandrake/Mandriva so I guess thats why I like KDE and like the ease of install with RPM files.
Why don't I use Mandriva you probably are thinking. Well I would like to but can't afford to download it or even buy it at this time.

If I can get Ubuntu to do everything I want, then I might as well stick with it. My father who stays in the UK is going to send me over the latest DVD iso of Ubuntu 6.06. does that play mp3 and divx files from a straight install? Or do the above questions apply?

Thanks.

---

### Post by chrispche on 2006-12-19
I obtained a a copy of Ubuntu Linux 5.10 and have both an Install CD and a Live CD. I tried out the Live CD which seemed to run fine. It did almost everything I wanted. However, it did not:

Play DivX avi files or mpeg files.
Play Mp3s.
My 250gig ext hard drive picked up fine under the Live CD, unfortunately it is formated at NTFS and Ubuntu would not let copy files from and to it. It said something about not have access privileges to that drive. Obviously I want full access to the drive.

How do I go about doing this?

Will the newer version do the above. I believe 5.10 is quite an older version.

Also a few questions. Do I have to use Gnome desktop, while I guess it's quite nice. I think I prefer KDE.

Do RPM files install on Ubuntu?

I am pretty familiar with Mandrake/Mandriva so I guess thats why I like KDE and like the ease of install with RPM files.
Why don't I use Mandriva you probably are thinking. Well I would like to but can't afford to download it or even buy it at this time.

If I can get Ubuntu to do everything I want, then I might as well stick with it. My father who stays in the UK is going to send me over the latest DVD iso of Ubuntu 6.06. does that play mp3 and divx files from a straight install? Or do the above questions apply?

Thanks.

---

### Post by taurus on 2006-12-19
Doesn't matter which version you install, you still need to install codecs to play all your media stuff.  It's real easy and simple by install automatix2 and use that to install anything else for your mp3s and movies.

And for your Windows partition, you just have to mount it before you can access it.  Shouldn't be too hard to do that either.  

So, download Dapper, 6.06, or Edgy, 6.10, if you can since they are newer than Breezy...

---

### Post by chrispche on 2006-12-19
Automatix2 is that a program or website?

---

### Post by arochester on 2006-12-19
You are a bit behind the times. 5.10 codname breeZy badger, replaced by 6.06 codename dapper drake, replaced by 6.10 codename edgy eft.

If you prefer KDE either you can either install kubuntu-desktop through ubuntu or get just kubuntu.

You can use RPM through a program called "alien"

To play ewncoded DVDs and MP3s you need to look at Restricted Formats on [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by taurus on 2006-12-19
> **chrispche said:**
> Automatix2 is that a program or website?

Yes, automatix2 is a program that allows you to install other goodies on your machine...  It comes in real handy.

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

---

### Post by pay on 2006-12-19
> **chrispche said:**
> However, it did not:

Play DivX avi files or mpeg files.
Play Mp3s.
You need to install the required codecs> My 250gig ext hard drive picked up fine under the Live CD, unfortunately it is formated at NTFS and Ubuntu would not let copy files from and to it. It said something about not have access privileges to that drive.You need to install the experimental ntfs driver> Do RPM files install on Ubuntu?Ubuntu is based on debian so primarily it uses .deb files, but you could install alien or rpm if you really wanted.> Do I have to use Gnome desktopNo you don't. There is Kubuntu that is based on kde or you can install kde after installation.> My father who stays in the UK is going to send me over the latest DVD iso of Ubuntu 6.06. does that play mp3 and divx files from a straight install?It is not the latest. 6.10 is. It does not play mp3's either by default. mp3 codecs are propieritery, therefore you need to pay for use of them (like how mandrake charges).

---

### Post by arochester on 2006-12-19
Automatix is a script which downloads and installs a lot of useful stuff.

Generally for dapper look at the  Unofficial Ubuntu 6.06 (Dapper Drake) Starter Guide on [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) or Edgy at the  Unofficial Ubuntu 6.10 (Edgy Eft) Starter Guide on [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by xyz on 2006-12-19
Hi and Welcome,

First of all, why wouldn't you install Dapper with Long Support or Edgy for that matter? Why do you seem to want to install Breezy?

To (re) format, I like Gparted Boot CD. Download it, burn the .iso, run a 'md5sum' checks to see if the .iso is defect free.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

You'll need to convert your RPM:
[http://strabes.wordpress.com/2006/11/17/installing-rpm-packages-in-ubuntu/](http://strabes.wordpress.com/2006/11/17/installing-rpm-packages-in-ubuntu/)

Unofficial Breezy Guide:
[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)
If you decide to move to Dapper or Edgy, simply search "ubuntu guide" in Google.

Codecs:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

OR
[www.getautomatix.com](www.getautomatix.com)

For Pure KDE:
[https://www.psychocats.net/ubuntu/purekde](https://www.psychocats.net/ubuntu/purekde)

Stop here...as this is quite a bit of work already!
Good luck and feel free to ask questions.

---

### Post by taurus on 2006-12-19
I merged your two threads together since they are the same...

---

