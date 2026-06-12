---
title: "fonts problem after 7.04 installment"
date: 2007-04-20
forum: General Help
---

### Post by juanm8000 on 2007-04-20
Yes...
After I've installed the 7.04 version the general fonts are broken or missing
All the fonts of all the icons or directories are gone and in it's place I have a lot of ******* symbols that, obviously, I can't read. The disaster is that I can't change them.
Please, help me. I don't know too much of Ubuntu but I love it.

---

### Post by jiminycricket on 2007-04-20
I don't really know how to solve this problem, but maybe this can help a little...

sudo dpkg-reconfigure fontconfig
sudo dpkg-reconfigure defoma

Is ubuntu-desktop installed?

Is the locale you're using all installed?

Did you upgrade or clean install Feisty Fawn?

---

### Post by mungy on 2007-04-23
I have the same problem. 

tried:

```
sudo dpkg-reconfigure fontconfig
sudo dpkg-reconfigure defoma
```

without any effect.

any ideas?

---

### Post by radiobuzzer on 2007-04-25
I have the same problem with the deafult fonts, and it started in Edgy, wasn't fixed after the upgrade to Feisty, as I hoped. I get boxes for all the standard fonts, in most programs. Thunderbird also crashes after that.

---

### Post by juangoyeneche on 2007-04-27
hi . I had the same problem and I only run software upgrade again (with all the rare letters) and  fix it.
Works perfect.

---

