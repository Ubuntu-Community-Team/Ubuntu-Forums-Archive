---
title: "I Broke BURG... By Installing it..."
date: 2015-11-20
forum: General Help
---

### Post by &amp;*@Fth&amp;% on 2015-11-20
I don't know what else to say. When I run burg-emu it looks like this:
[http://s000.tinyupload.com/?file_id=91802224793562075004](http://s000.tinyupload.com/?file_id=91802224793562075004)
Pressing F1 and F2 does nothing. I'm afraid to reboot in case I can't get past the broken BURG.

---

### Post by cariboo on 2015-11-20
Burg is no longer maintained, so it may be better to remove it use ppa=purge:

```
sudo apt-get install ppa-purge
```

to remove it use the following command:

```
sudo apt-get ppa-purge  ppa:n-muench/burg
```

---

### Post by &amp;*@Fth&amp;% on 2015-11-20
Sooooo.... Is there anything that looks a bit nicer than GRUB? And maybe not quite as slow?

---

### Post by yancek on 2015-11-20
If you want a different background image for Grub2, check the site below.

[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by &amp;*@Fth&amp;% on 2015-11-20
I guess that works. Kind of sad that burg isn't maintained anymore... oh well. Thanks guys!

---

### Post by mcduck on 2015-11-21
Grub2 can do pretty much what Burg did, it's just that for some reason most people (and even guides) only stick a background pic there instead of creating a full theme for it.

I'm using this theme [http://gnome-look.org/content/show.php/?content=146396]("http://gnome-look.org/content/show.php/?content=146396"), and looking at the files, it doesn't look like proper Grub2 themes are even complicated to do. so I guess it's just because it's not a well known feature. Either way I'm pretty sure Burg isn't maintained exactly because it became redundant when Grub itself gained proper theme support.

---

### Post by oldfred on 2015-11-21
New computers use UEFI.
Apple since it converted to Intel and Windows since Windows 8.

With Apple there was refit, but that has not been maintained, so rEFInd was created.
 And rEFInd works with all PCs in UEFI boot mode.

       [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

