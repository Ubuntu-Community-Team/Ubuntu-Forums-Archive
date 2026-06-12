---
title: "Unable to open images"
date: 2020-07-30
forum: General Help
---

### Post by sniper8752 on 2020-07-30
I've copied off photos and videos from a micro sd card from my s9 onto my laptop, and can't seem to open them.  I've tried opening them in Chrome, Lximage, Firefox and ImageMagik, and for Video, VLC.  Any ideas on why they won't open?  They are .jpg and .mp4 files.

---

### Post by CelticWarrior on 2020-07-30
Both file types are correctly supported.
If you can't open them then probably you're dealing with corrupt files. Do they work in the phone?

---

### Post by guiverc on 2020-07-30
I personally don't trust extensions on files, and instead ask the system to identify the type of file.  For example 

1.  I grab a file to use as an example

```
guiverc@d960-ubu2:/de2900/lubuntu_64$   cp -pv /de2900/lubuntu/lubuntu_format_usb.png .
'/de2900/lubuntu/lubuntu_format_usb.png' -> './lubuntu_format_usb.png'
```

2. I give it a false name  (maybe lame, but best I could think of)

```
guiverc@d960-ubu2:/de2900/lubuntu_64$   mv lubuntu_format_usb.png unknown_file.jpeg
```

3.  I query system and ask what type of file it is

```
guiverc@d960-ubu2:/de2900/lubuntu_64$   file unknown_file.jpeg 
unknown_file.jpeg: PNG image data, 514 x 450, 8-bit/color RGB, non-interlaced
```

Even though I changed the name to a JPEG file, the system recognizes it as a* PNG image* type of file and provides color stats for the random image I selected.

I'd ask your system what type of file you're actually dealing with (the system will peek inside the file itself to provide the answer, not relying on the  filename; it can still be tricked by corrupted files, but it's a pretty good indicator I'd suggest trying)

---

### Post by sniper8752 on 2020-07-30
Renamed to extension .png, and when I run file against it, this is all I get: [FONT=monospace][COLOR=#000000]20200628_173431.png: data[/COLOR]
[/FONT]

---

### Post by guiverc on 2020-07-30
data implies it's unknown format, ie. data.

corrupt enough it's format is unrecognizable (to the rules used by `file` anyway).  I'd go and look for a backup of the SD card that hasn't been corrupted (ie. backup made before corruption occurred).

PS:  you didn't need to rename file, I renamed only to prove the extension was ignored by the `file` command (ie. it doesn't use the filename at all in it's deciding file type, but contents only)

---

### Post by ActionParsnip on 2020-07-30
Is your user the owner of the data you copied? May want to check that out

---

