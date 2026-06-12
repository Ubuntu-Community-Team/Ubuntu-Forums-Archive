---
title: "Are Compiz (3D Cube) and Gnome 16.04 compatible?"
date: 2017-02-05
forum: General Help
---

### Post by al14 on 2017-02-05
Like the title says, are Compiz (3D Cube) and Ubuntu Gnome 16.04 compatible?


Thanks!

---

### Post by speartip on 2017-02-06
Ubuntu Gnome, uses Gnome Shell as the Desktop Environment, which in turn uses Mutter as the window manager. As far as I understand it the 2 are tightly integrated, which would make it very difficult to use Compiz. If Compiz & 3D Cube is a must, then plain Ubuntu + Unity is the way to go. You could also use Xubuntu & add Compiz, or I think Linux Mint 18.1 XFCE already has compiz pre-installed.

---

### Post by vasa1 on 2017-02-06
You may want to look at [https://ubuntuforums.org/showthread.php?t=2338316&p=13556922#post13556922](https://ubuntuforums.org/showthread.php?t=2338316&p=13556922#post13556922). From that post, I understand that Compiz in 16.10 contains many of the animations that were removed in earlier versions. See the image attached in that post.

---

### Post by speartip on 2017-02-06
> **vasa1 said:**
> You may want to look at [https://ubuntuforums.org/showthread.php?t=2338316&p=13556922#post13556922](https://ubuntuforums.org/showthread.php?t=2338316&p=13556922#post13556922). From that post, I understand that Compiz in 16.10 contains many of the animations that were removed in earlier versions. See the image attached in that post.

According to the OPs 1st Post he is running "Ubuntu Gnome" not Unity. Not sure that will apply to His system.

---

### Post by vasa1 on 2017-02-06
> **speartip said:**
> According to the OPs 1st Post he is running "Ubuntu Gnome" not Unity. Not sure that will apply to His system.
I don't use either and don't have any idea whether Compiz in one has more effects than Compiz in the other (for the same version).

---

### Post by speartip on 2017-02-06
No. In Ubuntu Gnome Compiz isn't used at all. Hence if the OP needs or wants Compiz, I think he'd be better changing his Desktop Environment. I have googled around, & it seems using Compiz on Gnome is best not done, unless you're prepared for breakages.

---

### Post by wildmanne39 on 2017-02-06
Compiz works well in Ubuntu Mate, I know it use to work well in Ubuntu with Unity, in the last post it was posted the user needs to change Operating systems, I think he meant Desktop Environment's.

---

### Post by speartip on 2017-02-06
> **wildmanne39 said:**
> in the last post it was posted the user needs to change Operating systems, I think he meant Desktop Environment's.
True. Post now edited.

---

### Post by yildizak on 2017-02-06
I'm using 3D cube and Wobbly windows on ubuntu 16.10

---

### Post by speartip on 2017-02-06
> **yildizak said:**
> I'm using 3D cube and Wobbly windows on ubuntu 16.10

Ubuntu or Ubuntu Gnome? Which is what the OP is using.

---

### Post by al14 on 2017-02-06
> **speartip said:**
> Ubuntu or Ubuntu Gnome? Which is what the OP is using.

I burned .iso install disk's for both Ubuntu 16.04.1 64-bit MATE *and* Ubuntu 16.04.1 64-bit Unity...

I like the way they both work and feel, however there are a couple of things I'm looking for before deciding which to install;

1) I would like to have a fully functional Compiz-
2) Can the Unity Splash Screens, Logins and Logouts  orange and purple colors be easily chnaged or at all-

Thanks!

---

### Post by deadflowr on 2017-02-06
>  I would like to have a fully functional Compiz-
install the package compiz-plugins.
This will bring in the extra goodies.

 > Can the Unity Splash Screens, Logins and Logouts orange and purple colors be easily chnaged or at all-
These are a separate issue as none of these things have anything to do with compiz.
The splash screens should be part of plymouth.
the login screen is part of lightdm, which unity uses with it's own login session called unity-greeter.
there are other greeters, such as lightdm-gtk-greeter and lightdm-webkit-greeter.

A little on Plymouth:
[https://wiki.ubuntu.com/Plymouth]("https://wiki.ubuntu.com/Plymouth")

A little on Lightdm:
[https://wiki.ubuntu.com/LightDM]("https://wiki.ubuntu.com/LightDM")

---

### Post by al14 on 2017-02-06
> **deadflowr said:**
> install the package compiz-plugins.
This will bring in the extra goodies.

 
These are a separate issue as none of these things have anything to do with compiz.
The splash screens should be part of plymouth.
the login screen is part of lightdm, which unity uses with it's own login session called unity-greeter.
there are other greeters, such as lightdm-gtk-greeter and lightdm-webkit-greeter.

A little on Plymouth:
[https://wiki.ubuntu.com/Plymouth](https://wiki.ubuntu.com/Plymouth)

A little on Lightdm:
[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)
 
Thanks *deadflowr*!

---

