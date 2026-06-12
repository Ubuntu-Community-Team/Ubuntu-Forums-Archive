---
title: "Simple way to install Gentoo?"
date: 2008-03-15
forum: General Help
---

### Post by intense.ego on 2008-03-15
Is there ***any*** simple way to install Gentoo? either by a GUI, or an automated process? I am interest in using it because from what I've heard, it is the fastest distro.

---

### Post by calraith on 2008-03-15
Have you seen Gentoo's [installation docs]("http://www.gentoo.org/doc/en/index.xml?catid=install#doc_chap2")?  There is no simple way to install Gentoo (not as simple as Ubuntu, Debian, or other distros, anyway).  That's half the Gentoo experience, though -- piecing your operating system together component-by-component, specifing your USE flags to squeeze every last drop of optimization out of the libraries and apps you compile.  The nicest thing about Gentoo is that it can help someone who's not terribly familiar with Linux learn a lot about how Linux is put together.  So, inherently, installation cannot be made simple (although one might argue that as long as you're willing to RTFM, installation isn't really difficult, anyway).

The novelty wears off, though.  Although there are precompiled binaries for apps and suites that would take days to compile from source (such as X or OpenOffice), most anything you emerge (what you would equate to apt-get) gets compiled from source.  Whatever 0.5% performance gain you would see by optimizing your binaries for AMD K7 with 3D Now rather than just the generic i686 binaries is quickly outweighed by discovering you forgot to install a needed package, swearing and dreading the long compile, emerging the package, going to have a cup of coffee, returning to discover that you didn't have your USE flags set up *quite* right and Quicktime support is missing, and going back to step 1.  And IMHO, the ebuild package management is not nearly as resilient as apt (although it has been two or three years since I've run Gentoo).

---

### Post by vpsville on 2008-03-15
You can download a pre-installed gentoo template from OpenVZ.  You can also get a Gentoo VPS to play around with on the net pretty cheap.

---

### Post by Joeb454 on 2008-03-15
I think the whole purpose of Gentoo is that you have to compile everything yourself, so you can pick and choose the things you want installed, and they will be optimized for your PC :)

---

### Post by kellemes on 2008-03-15
If you're not able to install Gentoo as explained in the handbook, you can't manage you system either, not for long anyway..

---

### Post by intense.ego on 2008-03-15
Yeah, I read that there is almost no graphical interface for configuring things. I have decided that there is no hope a noob like me could handle gentoo.

---

