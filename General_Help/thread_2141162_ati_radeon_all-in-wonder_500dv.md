---
title: "ati radeon all-in-wonder 500dv"
date: 2013-05-01
forum: General Help
---

### Post by dkino14 on 2013-05-01
hey guys i could use some help.  i have the ubuntu version 10.04 lts, and i cant install any other versions due to an older computer. where can i find some proper drivers for this video card? if not, what video card should i purchase for an asus a7v266-e motherboard? if anybody has any answers for me please post on this thread.

---

### Post by Mark Phelps on 2013-05-02
With a card that old, there are no AMD drivers that you will be able to install anymore.  Fortunately, there are default open-source ATI drivers that will get installed automatically with the OS.  IF you have the OS running and are able to see a desktop, the drivers are already installed.

I did a quick search on your motherboard, and with a 266MHZ bus, and AGP video slot -- you are unlikely to be able to install and run any recent version of Ubuntu, and probably won't be able to find any new AGP video cards anymore.

Sorry, but this is a 12-year old board and technology has long since moved on.

---

### Post by dkino14 on 2013-05-02
ok thanks. and yeah i kind of ran into the ubuntu problems and went to the oldest version possible. so mark what card should i get for this older computer that i have? i cant afford a new computer just yet.      also thanks lowan for editing that out, this is the first forum that i have ever joined so i didnt really think about that

---

### Post by Mark Phelps on 2013-05-03
Nearly all the video cards produced recently use the PCI-Xpress bus, and you would need either AGP (which haven't been made in years) or PCI.

In terms of All-in-Wonder cards, the problem here in the US is that TV broadcasting has switched over to SD, such that the older TV tuner cards that predate this technology will no longer work (AFAIK).  So, any card that works today is most probably NOT going to be a AGP or PCI bus card.

In terms of ATI cards, they are infamous in terms of dropping Linux support.  Only last summer, they dropped support for their HD 2x/3x/4x-series cards -- which you MIGHT have been able to find in PCI form factor.

Don't know about Nvidia cards, haven't used them in a long time.

Basically, you need to look for the newest PCI-bus video card you can find.

Sorry I can't be of more help.

---

### Post by dkino14 on 2013-05-04
yeah i figured that would be the main problem. my dad looked into the nvidia, and there is one but it costs over 100$ still. unless i get a used one from ebay xD

---

### Post by gordintoronto on 2013-05-05
In Toronto we have several shops which sell computers which have come off lease, typically three or four years old, for $179 or less. Except for the rare units with just 512 MB of memory, these machine will run Ubuntu beautifully.

Have you tried Xubuntu on your old system?

---

### Post by Yellow Pasque on 2013-05-06
What makes you think you need different video drivers or a different video card?
>  i cant install any other versions due to an older computer
I'm guessing your CPU doesn't support PAE (and your system may not have a lot of RAM). Lubuntu 12.04 is lightweight and uses non-PAE kernel by default, so hopefully, it will install.
[http://cdimages.ubuntu.com/lubuntu/releases/precise/release/lubuntu-12.04-desktop-i386.iso](http://cdimages.ubuntu.com/lubuntu/releases/precise/release/lubuntu-12.04-desktop-i386.iso)

---

### Post by dkino14 on 2013-05-06
no i havent tried xubuntu or lubuntu. im not100% interested in getting another computer, just a new video card. i can try the specified versions of ubuntu, and if that doesnt work, then i need to try new cards. what do you guys recommend?

---

### Post by mörgæs on 2013-05-07
The motherboard supports these CPU's:
[http://support.asus.com/cpusupport/list.aspx?SLanguage=en&m=A7V266-E&p=1](http://support.asus.com/cpusupport/list.aspx?SLanguage=en&m=A7V266-E&p=1)

and as there are no problematic Pentium M's on the list you don't have to worry about PAE. Besides, to the best of my knowledge the Pentium M was never used in desktops.

Lubuntu 12.04 is a buggy one. Go for 13.04 before investing in more hardware.

---

### Post by dkino14 on 2013-05-08
not interested in a new cpu, just video cards

---

