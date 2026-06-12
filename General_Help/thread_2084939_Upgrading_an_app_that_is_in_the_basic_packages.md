---
title: "Upgrading an app that is in the basic packages"
date: 2012-11-16
forum: General Help
---

### Post by ubunwhat on 2012-11-16
I recently upgraded to 12.04, and along with that my version of Gwenview was upgraded to 2.8.  This upgrade is tragic for me as I require a very specific function that only Gwenview provided.  That function was accidentally broken in 2.8 but reinstated in 2.9, according to Gwenview's own site.  The problem is that I am still stuck using 2.8x, and have no idea how to get 2.9.  The package showing installed in Synaptic is 4.8.5, which is what KDE shows as the package containing the latest Gwenview.  So... I'm confused.  I'm not sure how to go about getting Gwenview 2.9 when the package allegedly containing 2.9 is the one showing up as installed in Synaptic, yet that package only give me 2.8x.  

Relevant links... 

Gwenview site: [http://gwenview.sourceforge.net/overview]("http://gwenview.sourceforge.net/overview")

Gwenview source as per Gwenview site:
[http://download.kde.org/stable/latest/src/]("http://download.kde.org/stable/latest/src/")

Any help would be appreciated as this totally screws me work wise.  I either have to get 2.9 or find something that does what Gwenview used to do, and so far I have sampled several of Ubuntu apps for this and nothing comes close.

---

### Post by BBQdave on 2012-11-16
> **ubunwhat said:**
> I either have to get 2.9 or find something that does what Gwenview used to do, and so far I have sampled several of Ubuntu apps for this and nothing comes close.

Have you tried the GNU Image Manipulation Program? For editing photos, GIMP will do the same and more as Gwenview.

For Desktop and Web publishing I use and recommend: *GIMP*, *Scribus*, Text Editor - like *Pluma*,  Simple Image viewer - like *Eye of MATE*, calculator, dictionary, and it does not hurt to have *Libre Office*.

Any uses you have for Gwenview can be accomplished with GIMP :)

---

### Post by Impavidus on 2012-11-17
The best thing is to try and find an alternative. Gimp is good, largely inspired by photoshop, so you can do almost any image manipulation you want with it. However, it can be a bit tricky to learn.

Sometimes the repos contain outdated versions of software. In these cases you can try installing manually, but be advised you won't get automatic updates and it's not guaranteed to work with your version of the OS (installing from PPA is sometimes possible too, but I never tried it). You can download stuff (make sure it's a reliable source!) and install it according to the instructions typically included with the download, typically installing in /usr/local. When you download programs and want to compile them yourselves, remember you often have to install some *-dev packages first. When starting from the command line, any installations in /usr/local take precedence over normal installations. In most cases you can keep two versions.

Installing from the repositories is a recommendation (especially for beginners), not an obligation. However, it's a recommendation for good reasons.

---

### Post by alphacrucis2 on 2012-11-17
It looks like I have the newer version in Ubuntu 12.10 (Gwenview 2.9.1). The app appears to be bundled with the KDE desktop. I suppose upgrading to 12.10 would do it but it would be a sledgehammer to kill a gnat. It may be that the feature the op is after is sorting images by shooting date (as held in EXIF data) as I read that feature of gwenview was broken in 2.8. Gimp isn't going to help with that.


Edit. Interesting program. I hadn't come across it before. It's similar to programs like google picasa, gthumb or  shotwell but I think I prefer it.

---

