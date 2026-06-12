---
title: "possible to install program without root access"
date: 2019-10-15
forum: General Help
---

### Post by rebeltaz on 2019-10-15
I have a program that I've downloaded - it's an PROGRAM_installer.run file. If I run this without sudo, it complains that it needs root access. I don't know that I trust it explicitly. Is there anyway to install this without giving it root access?

---

### Post by cruzer001 on 2019-10-16
Sound like you need a test box or maybe a virtual machine for that.

I do not know of any universal way to remove sudo if your package needs root access.

---

### Post by rebeltaz on 2019-10-16
I have virtual box installed. Is there any way to document any changes that may be made to see if the program is safe?

---

### Post by cruzer001 on 2019-10-16
What program are we talking about?

---

### Post by rebeltaz on 2019-10-16
It's a linux version of Simplify3D a buddy gave me so I could see if I liked it before plopping down big bucks on it. He's a bit shady, so... not so sure I trust his sources.

---

### Post by cruzer001 on 2019-10-16
Simplify3d has a 2 week trial version.
[https://all3dp.com/simplify3d-free-version/](https://all3dp.com/simplify3d-free-version/)

And their FAQ says Ubuntu is supported.
[https://www.simplify3d.com/support/faq/](https://www.simplify3d.com/support/faq/)

The site looks legit and one linux reference was dated 2014 so they have a history with Linux.

Talk about bootleg copies is forbidden in this community.

Good luck

---

### Post by rebeltaz on 2019-10-16
> **cruzer001 said:**
> Simplify3d has a 2 week trial version.
[https://all3dp.com/simplify3d-free-version/](https://all3dp.com/simplify3d-free-version/)

And their FAQ says Ubuntu is supported.
[https://www.simplify3d.com/support/faq/](https://www.simplify3d.com/support/faq/)

The site looks legit and one linux reference was dated 2014 so they have a history with Linux.

Talk about bootleg copies is forbidden in this community.

Good luck

Well... that's why I didn't mention the program :)

However...

> The only way to get a kind of Simplify3D free trial is to buy it for $149. You then have two weeks to try it out, and if by the end of that period it’s not to your liking, you can return the software for a full refund.

is not exactly what I would call a "free trial". This is a spend the money now and argue about getting it back later kind of deal. Thanks anyway, though.

---

### Post by dragonfly41 on 2019-10-16
As an alternative try Blender for 3D modelling. It is open source.

---

### Post by HermanAB on 2019-10-16
You can install a program in your home directory - you need not do it as root.  You could also create a so called chroot environment, just for a specific program.

---

### Post by TheFu on 2019-10-16
A few other options... 

If you make versioned backups before the install, do the install, then you can compare which files where changed post-install using the backup.  This assumes you have a good backup tool and know how to use it.  With my backup tool, this is easiest when there are 2 backups to be compared.
If you don't like the changes, restore from the backup made before the install.  Backups have 1001 uses.

Also, it is likely the installation tool is just a shell script, so you can probably read it and see what it does. This also assumes you have the skill to read and understand the shell script. PROGRAM_installer.run

---

### Post by rebeltaz on 2019-10-16
> **dragonfly41 said:**
> As an alternative try Blender for 3D modelling. It is open source.

Thanks, but Simplify3D isn't a modeler program. It's a slicer. You send the 3D model to the slicer, and it, well... slices the model horizontally so that it can be sent to the 3d printer. I currently use Cura, and occasionally slic3r for this purpose. As for modelers, I do use blender, but the learning curve on that is **steep**! I mostly use FreeCAD now, with an occasional relapse into SketchUp when working on my older models. 

> **HermanAB said:**
> You can install a program in your home directory - you need not do it as root.  You could also create a so called chroot environment, just for a specific program.

How would I go about installing that program in my home directory? 

> **TheFu said:**
> A few other options... 

Thanks guys. I will look at those suggestions. I appreciate all of the help.

---

### Post by dragonfly41 on 2019-10-16
> **rebeltaz said:**
> Thanks, but Simplify3D isn't a modeler program. It's a slicer. You send the 3D model to the slicer, and it, well... slices the model horizontally so that it can be sent to the 3d printer. I currently use Cura, and occasionally slic3r for this purpose. As for modelers, I do use blender, but the learning curve on that is **steep**! I mostly use FreeCAD now, with an occasional relapse into SketchUp when working on my older models. 

Intuitively I guessed that Blender might offer this but it is beyond my ken.

[https://blenderartists.org/t/dicer-a-blender-slicer-for-3d-printing/593492/7](https://blenderartists.org/t/dicer-a-blender-slicer-for-3d-printing/593492/7)

---

### Post by rebeltaz on 2019-10-16
Well I'll be hornswaggled! I did not know that. I appreciate that! I'll have to give that a try!

---

