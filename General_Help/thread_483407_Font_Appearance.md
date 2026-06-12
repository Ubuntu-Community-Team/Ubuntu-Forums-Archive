---
title: "Font Appearance"
date: 2007-06-24
forum: General Help
---

### Post by jsimmons on 2007-06-24
I just installed 7.04, and to be quite frank, the fonts look like crap.  I even tried installing the msttcorefonts package, and even those look bad. The monitor is set to its native resolution (1680x1050).

How do I fix the font appearance?    I want them to display as clear as they do on Windows.

---

### Post by avik on 2007-06-24
Try going to System->Preferences->Font you can try changing some settings.

If you still aren't happy with the way the fonts look, have a look at [http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396).

---

### Post by nick_h on 2007-06-25
I assume this is an LCD screen.

Installing the improved sub-pixel font rendering in the [Ubuntu Feisty Starter Guide](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty) improved my fonts significantly.

Then go into System->Preferences->Font and check that you have LCD selected and the highest value for hinting.

You may also need to change the dpi.

---

### Post by RAH66 on 2007-07-16
this worked for me at 1440x900

Ubuntu Linux has an option for font smoothing that isn’t turned on by default for some strange reason. This makes fonts significantly smoother, enough to be very noticable. To enable this option, you need to edit the .fonts.conf file in your home directory.

To create and open the file, run this command and paste in the xml data below it.

sudo gedit ~/.fonts.conf

Paste in this text:

<?xml version="1.0" ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
<edit name="autohint" mode="assign">
<bool>true</bool>
</edit>
</match>
</fontconfig>

You’ll have to log out and back in to see the difference.

---

