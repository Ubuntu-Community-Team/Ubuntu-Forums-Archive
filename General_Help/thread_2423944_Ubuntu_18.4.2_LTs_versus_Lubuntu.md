---
title: "Ubuntu 18.4.2 LTs versus Lubuntu"
date: 2019-07-31
forum: General Help
---

### Post by cam17 on 2019-07-31
Why is it that firefox 68.01 on Ubuntu 18.04 (sha256 22580b9f3b186cc66818e60f44c46f795d708a1ad86b9225c458413b638459c4) cannot play Youtube live videos and Lubuntu a scaled down version of Ubuntu can?

---

### Post by uRock on 2019-07-31
This isn't a security issue. What are your system specs?

---

### Post by guiverc on 2019-08-01
I suspect they both have the same package(s) ([https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=firefox](https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=firefox)) so are you comparing the same release (if live), or same install method (ie. snap vs snap, deb vs deb).

---

### Post by ajgreeny on 2019-08-01
*Thread moved to **General Help**.* which is more appropriate and a better fit as this is not a security problem.

---

### Post by cam17 on 2019-08-23
The installation is default for both. Why is firefox operating differently for each

---

### Post by Impavidus on 2019-08-24
Lubuntu and Ubuntu (assuming both are 18.04) use exactly the same version of Firefox and the same supporting libraries. After all, the get their software from the same repositories. The one thing that could be different is additional codecs. I don't know if anything specific is required for youtube live videos, but some codecs may be required. Not all are installed by default for legal reasons. Maybe you clicked "install restricted software" (or something like that) when installing Lubuntu, but not on Ubuntu.

---

### Post by cam17 on 2019-08-26
They can not be the same. Lubuntu Firefox plays youtubes live videos while ubuntu does not.  Also I have been running lubuntu without any problems where as Ubuntu would crash.

---

### Post by uRock on 2019-08-26
I just played a Live Youtube video using Firefox on Ubuntu 18.04. It seems you may have missed something on the ubuntu install.

---

### Post by cam17 on 2019-08-27
I did a install both on a desktop and virtual machine and I get the following message on both hen playing  a youtube live.  The installed ISO sha256 is 22580b9f3b186cc66818e60f44c46f795d708a1ad86b9225c458413b638459c4.

---

### Post by uRock on 2019-08-27
Did you check this box during installation?  The ubuntu installation I recently completed, that is able to play live streams in Firefox, was done with the 18.04.2 installer.  Did you try redownloading the image?

---

