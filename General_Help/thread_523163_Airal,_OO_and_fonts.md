---
title: "Airal, OO and fonts"
date: 2007-08-11
forum: General Help
---

### Post by nikomax on 2007-08-11
Hi there!
I have installed the Microsoft fonts using apt-get and when I fonts:/// into nautilus I can see them there also when I go to /usr/share/fonts/truetype/msttcorefonts they are also there.

Ok my first Question is:
Where is the directory fonts:///?
I ask as it look different from /usr/share/fonts/
I pasted a lot of fonts into fonts:/// is that a bad thing?

Ok Question 2:
When I use Open Office only some of the Microsoft fonts come up Arial Narrow for instance
In the fonts:/// place/folder thingy the missing fonts have padlock emblems and are owned and can only be accessed by root. and I cant change this. I ran nautilus as root and got told I couldn't change any permissions or ownership, I tried chown and I really don't get chown to try by myself yet.

Any ideas anyone?

---

### Post by TheExplorer on 2007-08-12
**First of all install the following fonts using the Synaptic:**
> xfonts-intl-european
xfonts-intl-phonetic
gsfonts-x11
msttcorefonts
**Then run the command:**
> sudo fc-cache -f -v

Seems to me that you should put the desired fonts into /usr/share/fonts/ really. Also you may paste your MS fonts into /usr/share/fonts/truetype/msttcorefonts.

**After adding any font you have to create the font cache by executing:**
> sudo fc-cache -f -v
Hope this would be helpful.

---

### Post by nikomax on 2007-08-22
Sorry for the week long reply.
I had tried copying the fonts to both locations and i read about the fc-cache command. I used those to no avail. 
As it happens i gave my hard drive away to a friend in need and reinstalled ubuntu. I have done what you suggested and i do have arial fonts in OO. 
Thank you for the help!

---

