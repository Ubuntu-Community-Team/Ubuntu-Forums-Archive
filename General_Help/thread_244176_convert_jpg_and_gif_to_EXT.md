---
title: "convert jpg and gif to EXT"
date: 2006-08-26
forum: General Help
---

### Post by CameronCalver on 2006-08-26
hello i have pics on my palm and i want to send them to my friends phone but his phone can only hand .EXT so is there a program to convert pics to EXT

---

### Post by aysiu on 2006-08-26
.EXT? That's an image extension?

---

### Post by CameronCalver on 2006-08-26
yes

---

### Post by aysiu on 2006-08-26
Can you find online documentation for this *ext* extension? I've never heard of it and can't find it anywhere.

---

### Post by CameronCalver on 2006-08-26
no i cant thats why i came to the ubuntu forums lets e if anyone knoes

---

### Post by ifokkema on 2006-08-26
I think you might want to double-check; it's not on [http://www.filext.com/detaillist.php?extdetail=ext](http://www.filext.com/detaillist.php?extdetail=ext) either.

---

### Post by aysiu on 2006-08-26
Can you explain where you got .EXT from? Did the cell phone specifically say, "This image need to be an .EXT extension"?

---

### Post by CameronCalver on 2006-08-26
well i send a jpg and it said unsupported file format but another thing is i found it can support gif so can u convert a jpg to gif?

---

### Post by aysiu on 2006-08-26
Sure! You can do it through the command-line ```
sudo aptitude update && sudo aptitude install imagemagick
mogrify -format gif *nameoffile*.jpg
``` Or you can do it through GIMP--just double-click and open it with GIMP and then save it as a GIF.

---

### Post by CameronCalver on 2006-08-26
nah i love the freedom of cli ill let you no how it goes later on

---

