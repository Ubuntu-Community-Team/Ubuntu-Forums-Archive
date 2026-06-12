---
title: "fonts.conf error"
date: 2007-11-05
forum: General Help
---

### Post by cchevy on 2007-11-05
I get this error in the terminal everytime after i write something

**Fontconfig error: "~/.fonts.conf", line 2: no element found**

how can i fix it?

---

### Post by por100pre1 on 2007-11-06
Check if configuring the **Font Preferences** helps:

```
gnome-font-properties
```

If using Gutsy use this:

```
gnome-appearance-properties
```

If that doesn't work, try opening it:

```
gedit .fonts.conf
```

and replace its contents with mines:

```
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
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```

Be aware it has custom settings.

---

### Post by cchevy on 2007-11-07
thanks...mine was blank...i was looking for this file

can u explain what are the custom settings of this file?

---

### Post by por100pre1 on 2007-11-07
Those are resolution, hinting and other settings. Those are the settings of my PC, that why my I posted them as custom settings. Everything it's setup in Font Preferences, I wonder why it was blank. :-k Glad to help. :)

---

### Post by cchevy on 2007-11-07
> **por100pre1 said:**
> Those are resolution, hinting and other settings. Those are the settings of my PC, that why my I posted them as custom settings. Everything it's setup in Font Preferences, I wonder why it was blank. :-k Glad to help. :)

did u do this manual in the .conf or just selected LCD's in appearance menu?

i need the settings for LCD, and its strange that changing from menu does not change this .conf

or it shouldnt? :)

---

### Post by por100pre1 on 2007-11-07
> **cchevy said:**
> did u do this manual in the .conf or just selected LCD's in appearance menu?

i need the settings for LCD, and its strange that changing from menu does not change this .conf

or it shouldnt? :)

I didn't change anything in the file itself! I adjusted the settings in **Appearance**.

---

