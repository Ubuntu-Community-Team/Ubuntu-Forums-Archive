---
title: "texlive fonts package not showing up after install"
date: 2007-08-12
forum: General Help
---

### Post by weedenbc on 2007-08-12
Hi - 

Been using Fiesty for a couple months now and love it. I needed to install the Garamond font for a school paper so I installed texlive-fonts-extra from Synaptic.  Downloaded and installed okay but the fonts don't show up in Open Office (latest version).

According to the package manager the install put the files under /usr/share/texmf-texlive/fonts and there are tons of subdirectories.  Is that the right location?  Is there something I was supposed to do after install to get them working?

Thanks!

---

### Post by linuxwizard on 2007-08-12
Note: After you install a new font, you will need to make sure that programs in which you want to use the new fonts can recognize them. In most cases this is done by closing and reopening the programs; however, some programs may require you to log out and log back in.


[https://help.ubuntu.com/community/FontInstallHowto](https://help.ubuntu.com/community/FontInstallHowto)

---

### Post by euler_fan on 2007-08-12
> **weedenbc said:**
> Hi - 

Been using Fiesty for a couple months now and love it. I needed to install the Garamond font for a school paper so I installed texlive-fonts-extra from Synaptic.  Downloaded and installed okay but the fonts don't show up in Open Office (latest version).

According to the package manager the install put the files under /usr/share/texmf-texlive/fonts and there are tons of subdirectories.  Is that the right location?  Is there something I was supposed to do after install to get them working?

Thanks!

You have a completely different problem:

You installed a LaTeX font package. AFAIK, you simply installed the wrong package.

Unless, of course, you want to write your paper in LaTeX . . . which if you are studying math or physics no one will mind you doing anyway.

I suggest doing as the last responder suggested and also a Google search for "Garamond Open Office" or something like that. There should also be a font pack in Add/Remove with a bunch of windows fonts that will handle the issue automatically. It is called "Microsoft Core Fonts" but does not include Garamond (at least not in the Edgy version). But it will get you several of the other common MS fonts.

---

### Post by weedenbc on 2007-08-12
Now that makes a lot of sense - thanks.

I have the font on my windows install - I assume there is a way to get the ttf over to Ubuntu (I think I saw it in one of the FAQs).

Thanks!

---

