---
title: "[SOLVED] Unable to boot Ubuntu normally"
date: 2007-10-24
forum: General Help
---

### Post by SFinn on 2007-10-24
Ubuntu is working well - I'm posting from it now - but I can't boot it normally. I'm on dual boot, using grub, and whenever I choose to boot ubuntu normally it just gives me a blank screen. The way I've been booting is to go into recovery mode, then exiting it, and then it works fine. But surely there's something wrong with my installation if it's can't just boot the normal way? Can anyone help?

---

### Post by mahousaru on 2007-10-24
Try this

[http://ubuntuforums.org/showpost.php?p=3568252&postcount=2](http://ubuntuforums.org/showpost.php?p=3568252&postcount=2)

---

### Post by SFinn on 2007-10-24
Thanks. Um... I'm completely new to Linux, and I don't know how to check the usplash file...
Also,does grub use usplash? My multiple boot dialogue is text-only, and from what i understand, usplash is for pics...?

sorry for the noob questions. I'll learn, i'm sure

---

### Post by mahousaru on 2007-10-24
No worries about the questions :)
We all had to start somewhere once.  I'm just glad you are not scared off by the need to use the command line!

usplash is the graphic after the grub menu before gnome starts.  For some reason it can crash your display, or make boot up really slow.

To check first you need to open up a terminal.

Applications, Accessories, Terminal

Then at the prompt type:

```

sudo gedit /etc/usplash.conf

```

Now the contents of the file should equal what ever your screen is most comfortable as.  My laptop's best resolution is 1024x768 so mine is:

```

# Usplash configuration file
xres=1024
yres=768

```

Now if this is correct, then usplash isn't the problem.  If it is wrong change it and then you need to update the theme using:

```

sudo update-usplash-theme usplash-theme-ubuntu

```

If it isn't causing the problem then have a look in 

/var/log/Xorg.0.log

and see if you can spot any glaring error messages

---

### Post by SFinn on 2007-10-24
Fantastic, thanks! Worked like a charm.

---

### Post by Maestro23 on 2007-10-24
> **SFinn said:**
> Fantastic, thanks! Worked like a charm.

Please mark this SOLVED using the Thread Tools.

Thanks.:)

---

