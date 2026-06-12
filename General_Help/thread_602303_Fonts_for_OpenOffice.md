---
title: "Fonts for OpenOffice?"
date: 2007-11-04
forum: General Help
---

### Post by marenkar on 2007-11-04
I need fonts for Open Office 2.0 . Specifically some Medieval-style fonts.

---

### Post by Martje_001 on 2007-11-04
Create a directory:
```
sudo mkdir /usr/share/fonts/truetype/myfonts
```

Copy the font(s) into the newly created directory:
```
cp [fonts] /usr/share/fonts/truetype/myfonts
```

Run the following:
```
fc-cache -f -v 
```

---

### Post by marenkar on 2007-11-04
Thanks., but where can I get the fonts? 

This came out after i created the directory:
admin@admin-desktop:~$ cp [fonts] /usr/share/fonts/truetype/myfonts
cp: cannot stat `[fonts]': No such file or directory

---

### Post by forestpixie on 2007-11-04
> cp: cannot stat `[fonts]': No such file or directory

where [fonts] is in the command needs to be replaced by the font you're copying to the directory

as far as getting the fonts - try looking on google

---

### Post by Martje_001 on 2007-11-04
Or try to install fonts via synaptic. Search for 'ttf' (TrueType Font)

---

### Post by luisromangz on 2007-11-04
You can search in google for truetype fonts, and you can install any of them.

---

### Post by forestpixie on 2007-11-04
there are some medieval ones [here]("http://www.angelfire.com/la/bryde/fonts.html")

---

