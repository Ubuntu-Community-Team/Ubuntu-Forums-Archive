---
title: "Artwiz Fonts in Edgy??"
date: 2006-12-09
forum: General Help
---

### Post by johnnymac on 2006-12-09
Hey - has anyone been able to get artwiz fonts to work in edgy?  I've installed it, did the font config thing, uninstalled and reinstalled the fonts...nothing.

I do notice the following error during an uninstall of the fonts

```

warning: /usr/lib/X11/fonts/misc does not exist or is not a directory

```

Have any ideas??

---

### Post by johnnymac on 2006-12-09
NM - got it working...

---

### Post by limaunion on 2006-12-15
Could you please let me know how? I've been trying to setup these fonts and for some reason I can't. I've tried many things like copying them to my .fonts directory, running the 'fc' command, etc...
thanks in advance.

---

### Post by kb00heda on 2007-03-06
limaunion:

First install the Artwiz fonts package from the Ubuntu repositories. Afterwards you have to enable the use of bitmapped fonts. So run

  > sudo dpkg-reconfigure fontconfig-config

where the last dialog box (I guess it was the third) asked whether or not you wanted to do this. Once you are through, everything should work nicely.

Best regards,
David

---

### Post by Raavea on 2007-03-17
If I already got halfway through the installation in the Artwiz download's readme, what do I do? D:

 I just got to  [FONT="Courier New"]   fc-cache -fv ./[/FONT]
 And realised I can't do the next command as I don't have the file;
[FONT="Courier New"]    Add this path to your /etc/X11/XF86Config config
    FontPath "your_font_dir/artwiz-aleczapka-<LANG>-<RELEASE>"[/FONT]
So, having cleared the font-cache, should I be worried? D:

---

### Post by kb00heda on 2007-03-17
Raavea:

I don't think you need to worry about anything. The configuration file you're looking for is probably

  /etc/X11/xorg.conf

instead. 

But if I were you, I would install the fonts using the Ubuntu repositories, and remove the other Artwiz package. (But I'm just saying so because I never managed to get it in working condition by downloading and installing from source.)

Hopefully you'll soon be up and running! :)

---

### Post by Raavea on 2007-03-18
I decided to take a look at xorg shortly after making that post and there was similar lines in it. So I have done the steps in the installation, but I don't know how to check if it worked. XD

---

