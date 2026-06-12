---
title: "Change Launcher Icon?"
date: 2020-04-23
forum: General Help
---

### Post by bionic3epl on 2020-04-23
How do I change the Launcher Icon?

---

### Post by Ogden on 2020-04-24
Right click the launcher > click "edit launcher" > click on the icon and find the one you want.

---

### Post by bionic3epl on 2020-04-24
I tried right clicking and it doesn't do anything.

---

### Post by bionic3epl on 2020-04-24
Does anyone have any other ideas?

---

### Post by Dennis N on 2020-04-24
For the default Yaru icon theme in Ubuntu 20.04, that icon is called **view-app-grid-symbolic.svg**. It's in the Yaru icon theme folder in /usr/share/icons, inside the scalable/actions subfolder. You could replace it with another .svg icon, but use the same name. Then, logout and log back in and it should replace. I would backup the original before making changes so you can restore it.

---

### Post by bionic3epl on 2020-04-25
> **Dennis N said:**
> For the default Yaru icon theme in Ubuntu 20.04, that icon is called **view-app-grid-symbolic.svg**. It's in the Yaru icon theme folder in /usr/share/icons, inside the scalable/actions subfolder. You could replace it with another .svg icon, but use the same name. Then, logout and log back in and it should replace. I would backup the original before making changes so you can restore it.

I have .png, and .ico icons. How can I convert them to .svg icons w/out losing there color?

---

### Post by bionic3epl on 2020-04-25
How can I convert these to .svg w/out losing there current looks?

---

### Post by bionic3epl on 2020-04-30
> **bionic3epl said:**
> How can I convert these to .svg w/out losing there current looks?
Does anyone have any ideas for this?

---

### Post by CatKiller on 2020-04-30
> **bionic3epl said:**
> How can I convert these to .svg w/out losing there current looks?

SVG isn't an image format. It's a text format. It's a list of instructions of how to draw shapes. Following those instructions to create an image is entirely straightforward - that's what the instructions are for, after all - but working backwards to automatically guess at which instructions would provide a given image is non-trivial. There are algorithms that make an attempt to do so, which you could try. Or there are plenty of SVG Chrome icons already available. And the icon-picking engines don't require SVGs in any case.

---

### Post by Frogs Hair on 2020-04-30
> **bionic3epl said:**
> How can I convert these to .svg w/out losing there current looks?

Open the .png  in Inkskape and select save as and the icon will be saved as an .svg. 

```
sudo apt install inkscape
```

---

### Post by bionic3epl on 2020-04-30
> **Frogs Hair said:**
> Open the .png  in Inkskape and select save as and the icon will be saved as an .svg. 

```
sudo apt install inkscape
```

Thanks guys. You guys (Volunteers) sure know your stuff.

Results Below:

---

