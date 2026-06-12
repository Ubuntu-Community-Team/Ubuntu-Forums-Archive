---
title: "[SOLVED] Where can I download new colour schemes for GEdit?"
date: 2008-05-24
forum: General Help
---

### Post by Rytron on 2008-05-24
Hi,
Where can I download new colour schemes for GEdit?
I'd like a colour scheme with white text on a black background.
Thanks.

---

### Post by bwhite82 on 2008-05-24
There are a few installed by default in the preferences, here's some more:
[http://live.gnome.org/GtkSourceView/StyleSchemes](http://live.gnome.org/GtkSourceView/StyleSchemes)

---

### Post by Rytron on 2008-05-25
I settled for the darkmate scheme.
Its just a pity that the backgroung is not black, instead its a very dark grey.

---

### Post by kalibr on 2009-01-31
You can change the background color of the color scheme by editing the line in the xml file.

```

<style name="text"  foreground="#f3f3f3" background="#**333333**"/>

```

       to 

```

<style name="text"  foreground="#f3f3f3" background="#**000000**"/>

```

---

### Post by Rytron on 2009-01-31
> **kalibr said:**
> You can change the background color of the color scheme by editing the line in the xml file.

```

<style name="text"  foreground="#f3f3f3" background="#**333333**"/>

```

       to 

```

<style name="text"  foreground="#f3f3f3" background="#**000000**"/>

```


Hi kalibr. Which xml file?

---

### Post by cubeist on 2009-01-31
> **Rytron said:**
> Hi kalibr. Which xml file?

the xml color theme file you download for gedit.  See the link Soldierboy posted:
[http://live.gnome.org/GtkSourceView/StyleSchemes]("http://live.gnome.org/GtkSourceView/StyleSchemes")

---

### Post by fragos on 2009-01-31
> **Rytron said:**
> Hi kalibr. Which xml file?

/usr/share/gtksourceview-2.0/styles/

---

### Post by Rytron on 2009-01-31
I see, thanks guys.

---

### Post by badeagle on 2009-05-11
there is a style scheme editor available at [http://www.dabj01.co.cc/page4.php](http://www.dabj01.co.cc/page4.php)

---

### Post by bluefoot on 2010-09-15
> **badeagle said:**
> there is a style scheme editor available at [http://www.dabj01.co.cc/page4.php](http://www.dabj01.co.cc/page4.php)


hi. do you have an alternative url for that?

---

