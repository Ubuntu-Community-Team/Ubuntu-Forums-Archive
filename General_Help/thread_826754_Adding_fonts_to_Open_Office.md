---
title: "Adding fonts to Open Office"
date: 2008-06-12
forum: General Help
---

### Post by katkin on 2008-06-12
Hi guys,

I need to add some ttf fonts so that I can use them in Open Office writer, presentation etc. 

Does anyone know how to do this easily?

I have tried the following, but after doing so, I still can't see the fonts in my font list in OO Writer. :(

- copy the ttf files into to a directory called ".fonts" in your home directory
- go to Places->Home Directory
- then hold down the Ctrl key on your keyboard and press H
- you should see all the hidden directories/files, one of which is .fonts
 if it doesn't exist already, you can just create the directory

Thanks,

Kat

---

### Post by _sAm_ on 2008-06-12
After you add ttf files to your .font folder run this in a terminal:
sudo fc-cache

---

### Post by katkin on 2008-06-12
I have tried running that and I still can't see the fonts in my font list in Writer. :(

The fonts I am trying to add are:

ArialRouMT.ttf
ArialRouMTBol.ttf
ArialRoundedMT.ttf
Ubuntu-Title.ttf

I have attached a screen grab of my font list, which isn't showing them at the moment.

Thanks,

Kat

---

### Post by kaibob on 2008-06-12
> **katkin said:**
> I have tried running that and I still can't see the fonts in my font list in Writer....

I don't know why the fonts in the ~/.fonts directory aren't showing. I assume you have restarted the computer. 

You may want to have a look at the following document, which has some alternate directories for fonts:

[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

---

