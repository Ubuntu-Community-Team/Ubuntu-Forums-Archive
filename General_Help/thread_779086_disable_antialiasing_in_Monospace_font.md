---
title: "disable antialiasing in Monospace font"
date: 2008-05-02
forum: General Help
---

### Post by langriss on 2008-05-02
Just a simple question: how to disable antialiasing for the font Monospace, used in gnome console? I've tried to create a file in my home directory called .fonts.conf with a little XML to disable it, but without success. The Appearance control in Gnome have zero effect either, no matter what rendering I choose - even disabling all rendering had no effect at all.

So, how can I accomplish this feat? :confused:

And, if possible, is there a way to disable antialiasing for any font below a given size? :confused::confused:

the contents of ~/.fonts.conf:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<!-- /etc/fonts/fonts.conf file to configure system font access -->
<fontconfig>
<match target="font">
   <test name="family" qual="any">
          <string>Monospace</string>
   </test>
   <edit name="antialias"><bool>False</bool></edit>
</match>
</fontconfig>
```

---

