---
title: "How can I import Widows/Ms Office fonts to Openoffice"
date: 2007-03-08
forum: General Help
---

### Post by bash on 2007-03-08
I currently have one machine on which there is a dualboot for the preinstalled Windows and Ubuntu. I also own a copy of MS Office 2003 which is installed on that Windows partition. Now I have noticed that some of the fonts I get in MS Office, are not available in OOo. I Windows I know all fonts are stored in the Fonts folder in system32 or system. Is there something similar for Ubuntu, so I could just copy all the fonts from the Windows font folder to the Ubuntu one

---

### Post by Ek0nomik on 2007-03-08
[http://www.ubuntuforums.org/showthread.php?t=376982&highlight=fonts](http://www.ubuntuforums.org/showthread.php?t=376982&highlight=fonts)

Hope that helps!

---

### Post by Ek0nomik on 2007-03-08
[http://www.ubuntuforums.org/showthread.php?t=208396&highlight=microsoft+fonts](http://www.ubuntuforums.org/showthread.php?t=208396&highlight=microsoft+fonts)

[http://www.ubuntuforums.org/showthread.php?t=359749&highlight=microsoft+fonts](http://www.ubuntuforums.org/showthread.php?t=359749&highlight=microsoft+fonts)

[http://www.ubuntuforums.org/showthread.php?t=374228&highlight=microsoft+fonts](http://www.ubuntuforums.org/showthread.php?t=374228&highlight=microsoft+fonts)

Here's a few more.  Good luck!

---

### Post by vayde on 2007-03-08
Unfortunately it's a little more involved than that.  There may be an easier way to do it, but here's how I solve that problem:

go to command prompt
```

cd /usr/share/fonts/truetype

sudo mkdir winfonts

```

copy the fonts you want to move over into that folder
```

sudo cp <filename> /usr/share/fonts/truetype/winfonts

```

move to the new directory (all subsequent commands assume you are in the new font directory)
```

cd /usr/share/fonts/truetype/winfonts

```

make sure the font files you copied are readable by everybody
```

sudo chmod +r *

```

install ttmkfdir 
```

sudo apt-get install ttmkfdir

```

create font 'helper' files
```

ttmkfdir -o fonts.scale

mkfontdir

```

rebuild font lists
```

sudo fc-cache

```

If there's an easier method, hopefully someone will post

---

### Post by Sefrin on 2007-03-08
This isn't the site I originally found when I had this same question, but it sounds fairly simple:

[http://www.davidsterry.com/2007/01/installing-truetype-fonts-on-ubuntu.html]("http://www.davidsterry.com/2007/01/installing-truetype-fonts-on-ubuntu.html")

---

