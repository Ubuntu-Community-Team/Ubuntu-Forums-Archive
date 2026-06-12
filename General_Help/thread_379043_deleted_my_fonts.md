---
title: "deleted my fonts?"
date: 2007-03-08
forum: General Help
---

### Post by sirjis on 2007-03-08
I was trying to install some new fonts, and I tried to move a directory containing some fonts into my /usr/share/X11/fonts folder.  Unfortunately, I think that it instead replaced that folder...I did something like:
```

sudo mv ./some_fonts /usr/share/X11/fonts
```

After that, I (maybe even worse), deleted the fonts directory, since I noticed it had none of the folders that were in it before.

I haven't restarted the x server since then, but if I do, I bet I'll have some problems.  I tried doing:
```

sudo aptitude reinstall xfonts-100dpi xfonts-75dpi xfonts-base xfontsel xfonts-encodings xfonts-scalable xfonts-utils
```

since those seemed like they might fix it, but it just gives the following output

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REINSTALLED:
  xfonts-100dpi xfonts-75dpi xfonts-base xfonts-encodings xfonts-scalable 
  xfonts-utils xfontsel 
0 packages upgraded, 0 newly installed, 7 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/14.5MB of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 169099 files and directories currently installed.)
Preparing to replace xfonts-base 1:1.0.0-3ubuntu1 (using .../xfonts-base_1%3a1.0.0-3ubuntu1_all.deb) ...
Unpacking replacement xfonts-base ...
Preparing to replace xfonts-100dpi 1:1.0.0-2ubuntu1 (using .../xfonts-100dpi_1%3a1.0.0-2ubuntu1_all.deb) ...
Unpacking replacement xfonts-100dpi ...
Preparing to replace xfonts-75dpi 1:1.0.0-2ubuntu1 (using .../xfonts-75dpi_1%3a1.0.0-2ubuntu1_all.deb) ...
Unpacking replacement xfonts-75dpi ...
Preparing to replace xfonts-encodings 1:1.0.0-5.1 (using .../xfonts-encodings_1%3a1.0.0-5.1_all.deb) ...
Unpacking replacement xfonts-encodings ...
Preparing to replace xfonts-scalable 1:1.0.0-4ubuntu1 (using .../xfonts-scalable_1%3a1.0.0-4ubuntu1_all.deb) ...
Unpacking replacement xfonts-scalable ...
Preparing to replace xfonts-utils 1:1.0.0-6ubuntu3 (using .../xfonts-utils_1%3a1.0.0-6ubuntu3_i386.deb) ...
Unpacking replacement xfonts-utils ...
Preparing to replace xfontsel 1:1.0.1-0ubuntu1 (using .../xfontsel_1%3a1.0.1-0ubuntu1_i386.deb) ...
Unpacking replacement xfontsel ...
Setting up xfonts-encodings (1.0.0-5.1) ...
Setting up xfonts-utils (1.0.0-6ubuntu3) ...

Setting up xfontsel (1.0.1-0ubuntu1) ...
Setting up xfonts-base (1.0.0-3ubuntu1) ...
warning: /usr/lib/X11/fonts/misc does not exist or is not a directory
warning: /etc/X11/fonts/misc does not exist or is not a directory
warning: /usr/lib/X11/fonts/misc does not exist or is not a directory

Setting up xfonts-100dpi (1.0.0-2ubuntu1) ...
warning: /usr/lib/X11/fonts/100dpi does not exist or is not a directory
warning: /etc/X11/fonts/100dpi does not exist or is not a directory
warning: /usr/lib/X11/fonts/100dpi does not exist or is not a directory

Setting up xfonts-75dpi (1.0.0-2ubuntu1) ...
warning: /usr/lib/X11/fonts/75dpi does not exist or is not a directory
warning: /etc/X11/fonts/75dpi does not exist or is not a directory
warning: /usr/lib/X11/fonts/75dpi does not exist or is not a directory

Setting up xfonts-scalable (1.0.0-4ubuntu1) ...
Updating font configuration of fontconfig...
Cleaning up category cid..
Cleaning up category truetype..
Cleaning up category type1..
Updating category type1..
Updating category truetype..
Updating category cid..
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory
warning: /usr/lib/X11/fonts/Type1 does not exist or is not a directory

```

If I make the /usr/share/X11/fonts directory manually before doing this, it is just automatically deleted afterward.

Any ideas on how to fix this?  Or is it even a problem?

Thanks

---

### Post by fragos on 2007-03-08
You need to run "sudo fc-cache -fv" for the fonts to be included.

---

### Post by sirjis on 2007-03-09
Thanks, it seems that those weren't the fonts that were being used...the more important ones were in /usr/share/fonts/X11 (instead of X11/fonts), but your advice helped me install the fonts I was trying to in the first place.

---

### Post by fragos on 2007-03-09
You can also put fonts you wish to add in /home/{user}/.fonts and they will also be added when you run "sudo fc-cache -fv".   This is where I put all the fonts I add directly from a ttf file.

---

