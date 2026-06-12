---
title: "Xorg Questions On A Minimal System"
date: 2008-01-14
forum: General Help
---

### Post by DuckFOO on 2008-01-14
One of the things I like about Ubuntu is how good the fonts look when compared to other distributions. But I prefer a minimalistic system, with just X.org, Openbox, and Firefox.

If I were to install a minimal system, as detailed here:

[https://help.ubuntu.com/community/Installation/LowMemorySystems?highlight=%28installation%29](https://help.ubuntu.com/community/Installation/LowMemorySystems?highlight=%28installation%29)

would I still get the nice font rendering Ubuntu is known for? Or is that something only Gtk and Qt uses get?



Thanks in advance!

---

### Post by wolfen69 on 2008-01-14
you can always download extra font packages such as the Redhat liberation Fonts. download the tar.gz file and unpack  [https://www.redhat.com/promo/fonts/](https://www.redhat.com/promo/fonts/) they go in /usr/share/fonts/truetype

---

### Post by dagnabit dang doohickey on 2008-01-15
Yes, you can make your fonts look good on a minimal linux system.

You can configure your font choice within a ~/.gtkrc-2.0 file. As an example, this is my ~/.gtkrc-2.0 file:
```
# gtk-theme-name = "[theme-name]"
#
# gtk-icon-theme-name = "[icon-theme-name]"
#
# gtk-font-name = "[font-name] [size]"
#
# style "user-font"
# {
#       font_name = "[font-name] [size]"
# }
#
# widget_class "*" style "user-font"

gtk-theme-name = "Clearlooks"
gtk-icon-theme-name = "Tango"
gtk-font-name = "Sans 8"
style "user-font"
{
        font_name = "Sans 8"
}
widget_class "*" style "user-font"

```


Now, to make your fonts look good, use a ~/.fonts file to tweak them. Again, as an example, this is the ~/.fonts file I use:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">

<!-- the cathectic LCD tweaks, from linuxquestions.org,
http://www.linuxquestions.org/questions/showthread.php?postid=1361098#post1361098
-->

<fontconfig>

<!-- Disable sub-pixel rendering. X detects it anyway, and if you set
this as well, it just looks really horrible  -->
<match target="font" >
 <edit mode="assign" name="rgba" >
  <const>none</const>
 </edit>
</match>
<match target="font" >
 <edit mode="assign" name="hinting">
  <bool>true</bool>
 </edit>
</match>
<match target="font" >
 <edit mode="assign" name="hintstyle">
  <const>hintfull</const>
 </edit>
</match>

<!-- The first part of the 'magic.' This makes the fonts start to look
nice, but some of the shapes will be distorted, so hinting is needed
still -->
<match target="font" >
 <edit mode="assign" name="antialias">
  <bool>true</bool>
 </edit>
</match>

<!-- Autohinter is not turned on automatically. Only disable this if
you have recompiled Freetype with the bytecode interpreter, which is
run automatically. Although to be honest, Freetype are right, there
isn't much difference between the two. Note that OpenOffice is built
against the bytecode interpreter, so even if you have compiled it and
override it with the autohinter, OOo will still use the bytecode
interpreter -->
<match target="pattern" >
 <edit mode="assign" name="autohint">
  <bool>true</bool>
 </edit>
</match>

<!-- Helvetica is a non true type font, and will look bad. This
replaces it with whatever is the default sans-serif font -->
<match target="pattern" name="family" >
 <test name="family" qual="any" >
  <string>Helvetica</string>
 </test>
 <edit mode="assign" name="family" >
  <string>sans-serif</string>
 </edit>
</match>

<dir>~/.fonts</dir>
</fontconfig>

```

---

### Post by DuckFOO on 2008-01-15
Thanks!

---

### Post by urukrama on 2008-01-15
Also have a look [here]("http://kmandla.wordpress.com/2007/12/27/still-better-font-smoothing/") for smooth fonts.

---

