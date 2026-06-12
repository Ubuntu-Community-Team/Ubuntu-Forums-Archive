---
title: "Trying to install Libreoffice in maverick?"
date: 2012-10-24
forum: General Help
---

### Post by gabriella on 2012-10-24
I'm trying to install LibreOffice into Maverick instead of the default open office.

I followed these instructions:
[http://www.liberiangeek.net/2011/01/install-libreoffice-ubuntu-10-10-maverick-meerkat-ppa/](http://www.liberiangeek.net/2011/01/install-libreoffice-ubuntu-10-10-maverick-meerkat-ppa/)

But it's not finding it in the Software Centre! I suspect its something to do with the repository but I don't know what. I followed the instruction about adding Software source in the above link "ppa:libreoffice/ppa"

Please tell me someone what I did wrong

Thanks

---

### Post by claracc on 2012-10-24
I think the problem is there is not  libreoffice software package for maverik in the ppa you are trying to add. So you will have to try to install it through the deb package if possible.

I supose you know that "Support of Ubuntu Maverick Meerkat 10.10 was officially dropped on 10 April 2012"

---

### Post by bart.a on 2012-10-24
+1 to claracc..

maybe it's time to upgrade to 12.04 (LTS)? How do you feel about that?

---

### Post by oldos2er on 2012-10-24
Because Maverick's no longer supported its repositories have been moved to 'old-releases'. You can try the suggestions here: [http://www.prash-babu.com/2011/02/get-repositories-for-no-longer.html](http://www.prash-babu.com/2011/02/get-repositories-for-no-longer.html) but I would urge you to upgrade to a supported version of Ubuntu.

---

### Post by snowpine on 2012-10-24
10.10 is dead, time to switch to the current release or 12.04 LTS (either of which will give you Libreoffice by default).

---

### Post by Lyfang on 2012-10-24
> **snowpine said:**
> 10.10 is dead, time to switch to the current release or 12.04 LTS (either of which will give you Libreoffice by default).
Does anyone know if the Maverick repository is still useable?

---

### Post by snowpine on 2012-10-24
> **Lyfang said:**
> Does anyone know if the Maverick repository is still useable?

Define "usable"? 

It's been moved to old-releases.ubuntu.com as happens with all "end of life" releases, where you are free to use it (at your own risk) if you wish.

I do not consider this repository "usable" as it receives no security patches, bug fixes, or support of any kind from Canonical. The only valid use for Maverick in my opinion for historical research, like if you are writing an article about the history of Ubuntu releases for example.

---

### Post by Lyfang on 2012-10-24
> **snowpine said:**
> Define "usable"? 
[http://www.thefreedictionary.com/usable](http://www.thefreedictionary.com/usable)
> **snowpine said:**
> It's been moved to old-releases.ubuntu.com as happens with all "end of life" releases, where you are free to use it (at your own risk) if you wish.

I do not consider this repository "usable" as it receives no security patches, bug fixes, or support of any kind from Canonical. The only valid use for Maverick in my opinion for historical research, like if you are writing an article about the history of Ubuntu releases for example.
In order to use apt one must use old-releases.ubuntu.com once the release reaches EOL. Every 18 months or LTS 3 years on the desktop. Thanks for that information snowpine. See also: [The Increasing Size Of The Linux Kernel]("http://www.phoronix.com/scan.php?page=news_item&px=MTAxNDg")

---

### Post by snowpine on 2012-10-24
> **Lyfang said:**
> [http://www.thefreedictionary.com/usable](http://www.thefreedictionary.com/usable)

In order to use apt one must use old-releases.ubuntu.com once the release reaches EOL. Every 18 months or LTS 3 years on the desktop. Thanks for that information snowpine. See also: [The Increasing Size Of The Linux Kernel]("http://www.phoronix.com/scan.php?page=news_item&px=MTAxNDg")

Not sure I understand your point. The complete source code for the current Linux kernel is 78.5 MB. A 1tb hard drive costs less than $99. This means the storage required for the current Linux kernel costs less than a penny! If you feel the Linux kernel has become too large for your current system, then buy a larger drive, don't use an obsolete release with no security support!

---

### Post by philinux on 2012-10-24
Let's keep this on topic. The OP needs to install a supported OS.

---

### Post by Lyfang on 2012-10-24
**@gabriella:** May I ask why you want to use Ubuntu 10.10 (Maverick Meerkat)? I would recommend to copy all of your personal files to an external hard and install a supported release. I personally use Lubuntu 12.10 which includes LibreOffice in the repository, but AbiWord by default.

---

### Post by gabriella on 2012-10-25
> **Lyfang said:**
> **@gabriella:** May I ask why you want to use Ubuntu 10.10 (Maverick Meerkat)? I would recommend to copy all of your personal files to an external hard and install a supported release. I personally use Lubuntu 12.10 which includes LibreOffice in the repository, but AbiWord by default.

Thanks for all the comments. Yes I'm aware that Maverick is no longer supported, however, I'm away from home at this moment and upgrading/fresh installing a newer release is not an option for me. Thats why I asked about Maverick. When I return I plan on updating.

G

---

### Post by bart.a on 2012-10-25
oldos2er posted how you can get the repositories for maverick..

> **oldos2er said:**
> Because Maverick's no longer supported its repositories have been moved to 'old-releases'. You can try the suggestions here: [http://www.prash-babu.com/2011/02/get-repositories-for-no-longer.html](http://www.prash-babu.com/2011/02/get-repositories-for-no-longer.html) but I would urge you to upgrade to a supported version of Ubuntu.

After completing these steps I think you can install libreOffice just like you first tried it.. right?

---

