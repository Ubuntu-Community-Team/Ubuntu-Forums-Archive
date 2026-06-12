---
title: "Edgy Eft: Installing Fonts"
date: 2007-01-25
forum: General Help
---

### Post by Kat of Zion on 2007-01-25
Hello

I have a whole bunch of TTF files that I want to install into the main font directory of my Edgy Eft Machine.  However Im not sure where the main fonts folder is for Ubuntu, nor how I could install those fonts the easiest (since I have so many of them)

Suggestions?

---

### Post by dcstar on 2007-01-25
> **Kat of Zion said:**
> Hello

I have a whole bunch of TTF files that I want to install into the main font directory of my Edgy Eft Machine.  However Im not sure where the main fonts folder is for Ubuntu, nor how I could install those fonts the easiest (since I have so many of them)

Suggestions?

There are forum posts about manually installing TTF fonts (usually Microsoft fonts), a search should reveal them.

---

### Post by Buck2348 on 2007-01-25
> **Kat of Zion said:**
> Hello

I have a whole bunch of TTF files that I want to install into the main font directory of my Edgy Eft Machine.  However Im not sure where the main fonts folder is for Ubuntu, nor how I could install those fonts the easiest (since I have so many of them)

Suggestions?
I've just been playing with this--I think the easiest way is to create a folder /home/<username>/.fonts and copy all the fonts in there.  The main folder for fonts seems to be /usr/share/fonts.  There are two or so levels of folders below that.  I believe you could make a new folder under /usr/share/fonts/truetype and put them there if you prefer--that should make them available to all users.  To see what I suppose is all the installed fonts in one place, in the location bar of a nautilus window type "fonts:///" (without the quotes).  I was not able to copy any fonts into that.

Buck

---

### Post by timestryder on 2007-02-01
They have instructions in the desktop guide for Ubuntu.

I installed a TTF font into fonts:///, but it didn't appear. When I went to /home/<username>/.fonts however, it showed up there, which means it did actually copy.

You also have to rebuild the font cache, which is also written in the desktop guide, page 77.

```
sudo fc-cache -f -v
```

It is working in all my programs now.

---

