---
title: "Fonts"
date: 2007-05-19
forum: General Help
---

### Post by merlinus on 2007-05-19
Can someone please tell me if I can safely remove some of the many fonts (seemingly for languages other than English) that were installed by Feisty, or point me in a direction to get more information?

Many thanks!

-merlin

---

### Post by AnRa on 2007-05-19
Yes, you can. :)

---

### Post by merlinus on 2007-05-19
OK, but I am concerned that I NOT remove system fonts.  Also, it seems that this can be done only as root.

Is there a list somewhere that I can consult, because some of them look like regular English language fonts, but their names would seem to indicate otherwise.

Many thanks!

-merlin

---

### Post by Happy_Man on 2007-05-19
Since you're in New Mexico, delete everything but the en_us fonts. Because the rest are languages you'll never need, like Latvian and Hebrew. Your system uses english, i hope? So then that won't be a problem. 
To get rid of the fonts as root, run
```
gksudo nautilus
``` 
in a terminal.

---

### Post by merlinus on 2007-05-19
So I got rid of many of these fonts.  Now when I open a terminal, I get this message:

An error occurred while loading or saving configuration information for gnome-terminal.

And now there are no menus in the terminal, so I cannot, for example, copy and paste.

Here is another error:

Adding client to server's list failed, CORBA error: /CORBA/COMM_FAILURE:1.0

-merlin

---

### Post by merlinus on 2007-05-19
Looks like I solved the problem by copying fonts from my other Ubuntu machine.

-merlin

---

### Post by AnRa on 2007-05-19
> **merlinus said:**
> OK, but I am concerned that I NOT remove system fonts.  Also, it seems that this can be done only as root.

Is there a list somewhere that I can consult, because some of them look like regular English language fonts, but their names would seem to indicate otherwise.

Many thanks!

-merlinYou should use Synaptic, search "tff" by name, there you can see the description of each package and decide if you want it or not.

I don't think it's a good idea to directly remove the fonts as root.

---

### Post by merlinus on 2007-05-19
Thanks for the suggestion.  Clearly this is a better way.  Too bad I did not do this the first time....

Now all I need to figure out is why some of my installed Type 1 fonts do not show up in Open Office.

-merlin

---

### Post by dangermouse28 on 2007-06-11
In Dapper, I just went into /usr/share/fonts and deleted all the fonts I didn't want - no problem. Now in Feisty, I delete the fonts and my system won't boot anymore!

I'll have to put them back in and try the Synaptic method - BOOOOO!#-o

---

### Post by fragos on 2007-06-11
If you don't use Synaptic you'll need to rebuild the font cache.  Synaptic does this for you as well as identifying in descriptions what language the fonts are intended for.  Here's the list of the ones I kept:

ttf-bitstream-vera
ttf-dejavu
ttf-freefont
ttf-opensymbol
msttcorefonts

Truth is, this is more than you need but still represents a managable font set in applications like OpenOffice.

---

