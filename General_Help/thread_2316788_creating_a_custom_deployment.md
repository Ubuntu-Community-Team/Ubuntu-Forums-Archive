---
title: "creating a custom deployment"
date: 2016-03-10
forum: General Help
---

### Post by guilly on 2016-03-10
Hi,

I'm trying to create a custom deployment of kubuntu for a client. My approach is to build an image apply the necessary software and then capture the image and generate a bootable USB so that the image can be re applied.

Some of the features I need to integrate are:

LDAP authentication
Samba shares to AD file shares
Company branding (background etc...)
Virtual box images

Ive done some reading on Ubuntu customization kit but before I go too far is this the best approach to try and accomplish this? I was hoping I could take the windows approach by simply building an image then use something along the lines of imagex to capture my image. But after some reading it seems UCK take a different approach.....

I'm sure someone has had similar requirements so any help would be appreciated.

---

### Post by Bucky Ball on 2016-03-10
*Thread moved to **General Help**.*

Not related to Desktop Environments.

---

### Post by sudodus on 2016-03-11
Would it work for you to use the [Ubuntu OEM installation method](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)?

---

### Post by guilly on 2016-03-12
Thanks,

That does seem like more of an approach like on Windows with imagex. After I go through the OEM configuration and install all of the necessary software. Is there a way to capture the image and create a bootable USB so I can clone each machine with the exact configuration ?

---

### Post by sudodus on 2016-03-12
I use ***Clonezilla*** to clone or to create a compressed image. From that image it is possible to create cloned systems, that the end users use and installs their own user IDs and configurations.

[http://www.clonezilla.org/](http://www.clonezilla.org/)

It is straightforward to restore to the original drive or install a cloned copy to a drive of exactly the same size.

In BIOS mode installing from the cloned image to larger drives (than the original one) is straightforward, but it is more complicated in UEFI mode. You need to fix the backup partition table at the end of the drive space (for example with gdisk in expert mode).

You cannot use Clonezilla to clone to smaller drives (than the original one).

---

### Post by guilly on 2016-03-12
Perfect,

I'll give OEM imaging / Clonezilla a go and see how it works out.

Thanks for the help!

---

### Post by sudodus on 2016-03-12
Let us know how it works!

Good luck :-)

---

