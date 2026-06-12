---
title: "smooth font gone after installing microsoft true type fonts"
date: 2007-07-14
forum: General Help
---

### Post by Barleyman on 2007-07-14
I have just installed the microsoft true type fonts, but now my fonts appear very sharp and jagged in firefox and no longer smooth like before.

Ubuntu Feisty

Any thoughts?

---

### Post by nelamvr6 on 2007-07-14
> **Barleyman said:**
> I have just installed the microsoft true type fonts, but now my fonts appear very sharp and jagged in firefox and no longer smooth like before.

Ubuntu Feisty

Any thoughts?

In the preferences panel you should find "Font".  Select "Subpixel Smoothing", that should help some.

---

### Post by Barleyman on 2007-07-14
That is already selected.

---

### Post by RAH66 on 2007-07-16
Try This

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

