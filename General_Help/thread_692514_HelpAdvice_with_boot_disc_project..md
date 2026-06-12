---
title: "Help/Advice with boot disc project."
date: 2008-02-09
forum: General Help
---

### Post by Wiebelhaus on 2008-02-09
Hello , Thanks for reading , this is more or less a personal project for use around a computer shop , I'm looking to consolidate the various boot disc's a tech would use in an average work week and expanding it , For instance combining and possibly customizing [UBCD]("http://www.ultimatebootcd.com/") , [Hirens]("http://www.hiren.info/pages/bootcd") , [DUBCD]("http://digg.com/software/David_s_Ultimate_Boot_CD_2.0_4in1") , DOS , A modified DSL or Feather distro as well as possible Bart'sPE or maybe ReactOS and possibly anything else that may be needed , I'd love to keep it fully legal and OSS as that's where my loyalty is.

I'm cogitating over using DOS or Syslinux or possibly Grub? What would be your input , ideas or advice with this venture? by the way there's no limitations with this project , Environments , Money , Moonlighting time all is available , I'm not a cheap scape nor am I looking for charity advice , I'm experienced but a total DOS noob , although I have a buddy who is willing to help who grew up with DOS but on the same token isn't Linux savvy.

Thanks for listening.

---

### Post by paultag on 2008-02-09
My Advice:

Create a folder and debootstrap it ( sudo aptitude install debootstrap ) and install some flavor of Debian. This will lay out Debian in that folder as the root (/)

Then chroot into it, add all the tools you want, and edit it to your taste. From there you can use something like ISOLINUX (google for that one) or Linux-Live ([http://www.linux-live.org/](http://www.linux-live.org/)) to create a CD-ROM OS image.

---

### Post by Wiebelhaus on 2008-02-09
> **paultag said:**
> My Advice:

Create a folder and debootstrap it ( sudo aptitude install debootstrap ) and install some flavor of Debian. This will lay out Debian in that folder as the root (/)

Then chroot into it, add all the tools you want, and edit it to your taste. From there you can use something like ISOLINUX (google for that one) or Linux-Live ([http://www.linux-live.org/](http://www.linux-live.org/)) to create a CD-ROM OS image.

Great suggestions , thanks.

---

