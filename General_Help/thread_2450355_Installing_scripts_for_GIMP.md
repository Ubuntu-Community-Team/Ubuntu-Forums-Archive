---
title: "Installing scripts for GIMP"
date: 2020-09-11
forum: General Help
---

### Post by Panawe on 2020-09-11
Would someone talk me through how to install a tone-mapping script in GIMP?

TIA

P

NB: If I could find the directory where GIMP 2.10 is located it would help but although I am running GIMP 2.10 the only folder I can find says GIMP 2.8.

---

### Post by norobro on 2020-09-12
What does gimp --version yield? (N.B. I'm running 20.04)```
$ gimp --version
GNU Image Manipulation Program version 2.10.18
```If you are running 18.04, GIMP 2.8 is what you should have installed. [https://packages.ubuntu.com/bionic/gimp](https://packages.ubuntu.com/bionic/gimp)

I assume you are looking at this site: [https://www.gimphelp.org/color_tone-mapping.html](https://www.gimphelp.org/color_tone-mapping.html)

Notice at the bottom of the page the windows instructions show v. 2.8 so I would try copying the file to ~/.config/GIMP/2.8/scripts to see if it works. Otherwise you could try searching for a 2.8 Tone-Mapping script. There is an older version here: [https://github.com/pixlsus/registry.gimp.org_static/blob/master/registry.gimp.org/files/advancedtonemapping.scm](https://github.com/pixlsus/registry.gimp.org_static/blob/master/registry.gimp.org/files/advancedtonemapping.scm)

---

### Post by ajgreeny on 2020-09-12
If you're running the snap version of gimp your problem may be related to that type of installation; snaps are often very limited and I am aware that gimp plugins will not work in the snap version, or at least, not without a bit of fiddling around, and even then I am not certain if they work.

Let's see the output of ```
snap list
``` and if it shows gimp is installed as a snap, you can also install the version from the normal repos with ```
sudo apt install gimp
```
The two versions can coexist and run side by side so there is no need to uninstall the snap unless you prefer to have just the one version to avoid confusion. If you want to remove the snap version run ```
sudo snap remove gimp
``` using whatever the snap package is known as in the list command.

---

### Post by Panawe on 2020-09-12
Thanks for replying.

[https://www.gimphelp.org/color_tone-mapping.htmlNotice](https://www.gimphelp.org/color_tone-mapping.htmlNotice) seems to be a dead link!

I have downloaded the packages from [https://packages.ubuntu.com/bionic/gimp](https://packages.ubuntu.com/bionic/gimp) - but Terminal isn't my favourite environment.

Thanks again.

---

### Post by Panawe on 2020-09-12
Hi,

Thanks for responding.

Running "snap list" shows I have GIMP 2.10.20.

I'll run the full install and see.

Thanks again.

---

### Post by norobro on 2020-09-12
> **Panawe said:**
> [https://www.gimphelp.org/color_tone-mapping.htmlNotice](https://www.gimphelp.org/color_tone-mapping.htmlNotice) seems to be a dead link!
Sorry about that. The first word of the next sentence seems to have made it into the link. 
Here's the correct link: [https://www.gimphelp.org/color_tone-mapping.html](https://www.gimphelp.org/color_tone-mapping.html) I corrected it above also.

The installation instructions are in the file. The script works fine in my package manager installed version of GIMP but 
I the guess it won't be of use to you since, per @[COLOR=#000000]ajgreeny,[/COLOR] scripts won't run in snap versions. I don't use snaps.

---

### Post by Panawe on 2020-09-12
I've got hold of the 210_color_tone-mapping.scm file (thanks) and installed it in /usr/share/gimp/2.0/scripts folder and refreshed the Script FU menu but still nothing in Filters/Enhance in GIMP. I have installed GIMP as per ajgreeny.

With messing around I find that I have almost the same functionality using GMIC-Qt so I think I'm going to give up.

Thanks for your efforts.

---

