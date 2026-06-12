---
title: "My fonts changed yesterday, and I want them to go back."
date: 2007-02-20
forum: General Help
---

### Post by AlucardZero on 2007-02-20
Hi,

Using XFCE on 6.10, 2.6.17 kernel.  Several of my fonts changed yesterday, and I have no idea what changed.  It's particularly annoying because I can't get my terminal font back to what it was.

I've had exactly one clue about this:```
Fontconfig error: line 1: no element found
Fontconfig error: Cannot load default config file
```
I tried apt-get install --reinstall fontconfig, and dkpg-reconfigure fontconfig, both complete but still spit that error at me.
 
I do have a ~/.fonts.conf:```
<?xml version="1.0"?><!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintmedium</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```

I don't know where else to look to fix this.  Help?

---

### Post by AlucardZero on 2007-02-21
It turned out to be my /etc/fonts/fonts.conf being corrupted.

-_-

---

