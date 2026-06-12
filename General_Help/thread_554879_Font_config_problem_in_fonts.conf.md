---
title: "Font config problem in fonts.conf"
date: 2007-09-19
forum: General Help
---

### Post by AaronMT on 2007-09-19
Hi, I am trying to install mscorefonts and I get the error

Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

My fonts.conf looks like this

```
<?xml version=”1.0” ?>
<!DOCTYPE fontconfig SYSTEM “fonts.dtd”>
<fontconfig>
<match target=”font” >
<edit name=”autohint” mode=”assign” >
<bool>true</bool>
</edit>
</match>
</fontconfig>

```

I also get the error when editing that file

---

### Post by AaronMT on 2007-09-19
> **AaronMT said:**
> Hi, I am trying to install mscorefonts and I get the error

Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

My fonts.conf looks like this

```
<?xml version=”1.0” ?>
<!DOCTYPE fontconfig SYSTEM “fonts.dtd”>
<fontconfig>
<match target=”font” >
<edit name=”autohint” mode=”assign” >
<bool>true</bool>
</edit>
</match>
</fontconfig>

```

I also get the error when editing that file

Even inputing this following I get an error

```
<?xml version="1.0"?><!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target=”font” >
  <edit name=”autohint” mode=”assign” >
   <bool>true</bool>
  </edit>
 </match>
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

Fontconfig error: "~/.fonts.conf", line 3: not well-formed (invalid token)

---

### Post by somfi on 2007-09-19
that's hard

---

### Post by AaronMT on 2007-09-19
> **somfi said:**
> that's hard

Thanks for the informative reply.

---

### Post by kerry_s on 2007-09-19
ya want to try mine->

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

---

### Post by AaronMT on 2007-09-19
No difference in syntax. What the heck?

---

### Post by kerry_s on 2007-09-19
from your error's> "
don't look right here>
```
<match target=**”**font**”** >
  <edit name=**”**autohint**”** mode=**”**assign**”** >
```

---

### Post by fragos on 2007-09-20
Have you tried using synaptic to install package "msttcorefonts"?

---

