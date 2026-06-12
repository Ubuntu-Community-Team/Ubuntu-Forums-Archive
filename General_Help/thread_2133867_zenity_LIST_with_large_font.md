---
title: "zenity LIST with large font ?"
date: 2013-04-09
forum: General Help
---

### Post by Rebelli0us on 2013-04-09
I can get zenity to display large fonts in a text message:

```
zenity --info --text \
"<span font-family=\"sans\" font-weight=\"900\" font-size=\"xx-large\">1 2 3 4</span>"

```

But when I ask for a list box it doesn't work:

```
zenity --list --width=640 --height=480 --column "Items" \
"<span font-family=\"sans\" font-weight=\"900\" font-size=\"xx-large\">1 2 3 4</span>"

```

Any ideas?

---

### Post by Rebelli0us on 2013-04-09
BTW I got the formatting from here

[http://www.w3.org/wiki/CSS/Properties/font-size](http://www.w3.org/wiki/CSS/Properties/font-size)

---

